# Funciones puras para procesar las operaciones
# Devuelven un nuevo estado (nuevo balance).

def calcular_deposito(balance_actual, monto):
    """Calcula el nuevo balance tras un depósito."""
    if monto > 0:
        return balance_actual + monto, True
    return balance_actual, False

def calcular_retiro(balance_actual, monto):
    """Calcula el nuevo balance tras un retiro validando fondos."""
    if 0 < monto <= balance_actual:
        return balance_actual - monto, True
    return balance_actual, False

def mostrar_mensaje_operacion(exito, tipo_operacion):
    """Función de orden superior simple para notificar estados en consola."""
    if exito:
        print(f"\n[ÉXITO] La operación de {tipo_operacion} se realizó correctamente.")
    else:
        print(f"\n[ERROR] No se pudo procesar el {tipo_operacion}. Verifique el monto o fondos.")


# CONTROLADORES 

def autenticar_usuario():
    """
    Controla el acceso al sistema (Unidad 3: Estructuras Condicionales y Repetitivas).
    Retorna True si el PIN es correcto tras los intentos.
    """
    PIN_CORRECTO = "1234"
    intentos_maximos = 3
    intentos = 0
    
    print("=== BIENVENIDO AL BANCO DIGITAL ===")
    
    # Bucle de autenticación 
    while intentos < intentos_maximos:
        pin_ingresado = input("\nPor favor, ingrese su PIN de 4 dígitos: ")
        
        # Validación lógica 
        if pin_ingresado == PIN_CORRECTO:
            print("\n¡Autenticación exitosa! Accediendo al sistema...")
            return True
        else:
            intentos += 1
            intentos_restantes = intentos_maximos - intentos
            print(f"[PIN INCORRECTO] Le quedan {intentos_restantes} intentos.")
            
    print("\n[CUENTA BLOQUEADA] Ha superado el límite de intentos seguros.")
    return False


def ejecutar_cajero():
    """
    Administra el menú interactivo del cajero automático.
    """
    # Variables de estado inicial
    balance = 500.00  # Saldo inicial simulado
    cajero_activo = True
    
    # Bucle principal del menú (Unidad 3)
    while cajero_activo:
        print("\n=======================================")
        print("           MENÚ PRINCIPAL ATM          ")
        print("=======================================")
        print("1. Consultar Saldo")
        print("2. Depositar Dinero")
        print("3. Retirar Dinero")
        print("4. Salir del Sistema")
        print("=======================================")
        
        opcion = input("Seleccione una opción (1-4): ")
        
        if opcion == "1":
            # Consulta de saldo
            print(f"\nSu saldo actual disponible es: ${balance:.2f}")
            
        elif opcion == "2":
            # Proceso de Depósito
            try:
                monto_deposito = float(input("\nIngrese el monto a depositar: $"))
                balance, exito = calcular_deposito(balance, monto_deposito)
                mostrar_mensaje_operacion(exito, "DEPÓSITO")
            except ValueError:
                print("\n[ERROR] Ingrese un valor numérico válido.")
                
        elif opcion == "3":
            # Proceso de Retiro
            try:
                monto_retiro = float(input("\nIngrese el monto a retirar: $"))
                balance, exito = calcular_retiro(balance, monto_retiro)
                mostrar_mensaje_operacion(exito, "RETIRO")
            except ValueError:
                print("\n[ERROR] Ingrese un valor numérico válido.")
                
        elif opcion == "4":
            # Cierre de sesión y ruptura del bucle repetitivo
            print("\nGracias por utilizar nuestros servicios financieros. ¡Hasta pronto!")
            cajero_activo = False
            
        else:
            print("\n[OPCIÓN INVÁLIDA] Por favor, seleccione una opción del 1 al 4.")


# PUNTO DE ENTRADA AL PROGRAMA
if __name__ == "__main__":
    # Primero se ejecuta la lógica de autenticación
    if autenticar_usuario():
        # Si pasa la validación, se despliega el menú del cajero
        ejecutar_cajero()
