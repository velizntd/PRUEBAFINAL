# PRUEBAFINAL
PRUEBAFINAL
import Libreria as lb
productos= {
    "8475HD": ["HP", 15.6, "8GB", "DD", "1T", "Intel Core i5", "Nvidia GTX 1050"],
    "2175HD": ["LENOVO", 14, "4GB", "SSD", "512GB", "Intel Core i5", "Nvidia GTX 1050"],
    "JjfFHD": ["ASUS", 14, "16GB", "SSD", "256GB", "Intel Core i7", "Nvidia RTX 2080 Ti"],
    "fgdxFHD": ["HP", 15.6, "8GB", "DD", "1T", "Intel Core i3", "Integrada"],
    "GF75HD": ["ASUS", 15.6, "8GB", "DD", "1T", "Intel Core i7", "Nvidia GTX 1050"],
    "123FHD": ["LENOVO", 14, "6GB", "DD", "1T", "AMD Ryzen 5", "Integrada"],
    "342FHD": ["LENOVO", 15.6, "8GB", "DD", "1T", "AMD Ryzen 7", "Nvidia GTX 1050"],
    "UWU131HD": ["Dell", 15.6, "8GB", "DD", "1T", "AMD Ryzen 3", "Nvidia GTX 1050"]
}

stock = {
    "8475HD": [387990, 10],
    "2175HD": [327990, 4],
    "JjfFHD": [424990, 1],
    "fgdxFHD": [664990, 21],
    "123FHD": [290890, 32],
    "342FHD": [444990, 7],
    "GF75HD": [749990, 2],
    "UWU131HD": [349990, 1]
}
op1 = 0
while op1 != 4:
    print("""MENU PRINCIPAL

1-. STOCK MARCA
2-. Búsqueda por precio
3-. Actualizar Precio
4-. Salir
""")

    try:
        op1 = int(input("Ingrese una opción 1, 2, 3 o 4 para salir: "))

        if op1 == 1:
            marca = input("Ingrese marca a consultar: ").upper()
            total_stock = 0
            encontrados = False
            for modelo, detalles in lb.productos.items():
                if detalles[0].upper() == marca:
                    total_stock += lb.stock[modelo][1]
                    encontrados = True
            if encontrados:
                print(f"Stock total de la marca {marca}: {total_stock}")
            else:
                print("No se encontraron productos de esa marca.")

        elif op1 == 2:
            precio_min = int(input("Ingrese precio Mínimo: "))
            precio_max = int(input("Ingrese precio Máximo: "))
            encontrados = False
            for modelo, datos in lb.stock.items():
                if precio_min <= datos[0] <= precio_max:
                    print(f"Modelo: {modelo}, Precio: ${datos[0]}, Stock: {datos[1]}")
                    encontrados = True
            if not encontrados:
                print("No hay notebook en ese rango de precio.")

        elif op1 == 3:
            continuar = "SI"
            while continuar.upper() == "SI":
                modelo = input("Ingrese el modelo para actualizar el precio: ").upper()
                if modelo in lb.stock:
                    precio_actual = lb.stock[modelo][0]
                    print(f"Precio actual del modelo {modelo}: ${precio_actual}")
                    try:
                        nuevo_precio = int(input("Ingrese nuevo precio: "))
                        if nuevo_precio > 0:
                            lb.stock[modelo][0] = nuevo_precio
                            print("Precio actualizado correctamente.")
                        else:
                            print("El precio debe ser mayor a 0.")
                    except ValueError:
                        print("Debe ingresar un número entero válido para el precio.")
                else:
                    print("El modelo no existe!!.")

                continuar = input("¿Desea actualizar otro precio? (SI/NO): ")

        elif op1 == 4:
            print("Programa Finalizado")

        else:
            print("Debe seleccionar una opcion valida!!.")

    except ValueError:
        print("Debe ingresar valores enteros!!.")


