# Fundamentos-de-programacion-Fase-5-
" Solucion al problema 5  - Fase 5 Evaluación Final POA UNAD".
# ==============================================================================
# UNIVERSIDAD NACIONAL ABIERTA Y A DISTANCIA - UNAD
# Curso: Fundamentos de Programación (Código: 213022)
# Fase 5 - Evaluación Final POA
# Problema 5: Registro y Clasificación de Horas Laborales Semanales
# ==============================================================================

def calcular_y_clasificar_jornada(recurso):
    """
    Calcula la suma total de horas trabajadas en la semana por un recurso
    y clasifica su jornada según la regla de negocio (umbral de 40 horas).
    
    Parámetros:
        recurso (list): [Nombre del recurso, Lunes, Martes, Miércoles, Jueves, Viernes]
        
    Retorna:
        tuple: (nombre, total_horas, clasificacion)
    """
    nombre = recurso[0]
    # Sumar las horas diarias trabajadas de Lunes a Viernes (índices 1 al 5)
    total_horas = sum(recurso[1:])
    
    # Lógica de negocio para clasificación
    if total_horas > 40:
        clasificacion = "Sobretiempo"
    else:
        clasificacion = "Horario estándar"
        
    return nombre, total_horas, clasificacion


def mostrar_informe(resultados):
    """
    Función de presentación que imprime el reporte consolidado tabulado.
    """
    print("\n" + "=" * 65)
    print("        INFORME DE HORAS SEMANALES Y CLASIFICACIÓN DE JORNADA")
    print("=" * 65)
    print(f"{'Nombre del Recurso':<22} | {'Horas Semanales':<18} | {'Clasificación':<15}")
    print("-" * 65)
    
    for nombre, total, clasificacion in resultados:
        print(f"{nombre:<22} | {total:<18.1f} | {clasificacion:<15}")
        
    print("=" * 65 + "\n")


def main():
    """
    Función principal que coordina la matriz de datos y el flujo del programa.
    """
    # Matriz con 4 recursos y sus horas diarias de Lunes a Viernes
    matriz_recursos = [
        ["Carlos Pérez", 8.0, 8.5, 9.0, 8.0, 8.0],   # Total = 41.5 -> Sobretiempo
        ["Ana Gómez", 8.0, 8.0, 7.5, 8.0, 8.0],      # Total = 39.5 -> Horario estándar
        ["Luis Rodríguez", 9.0, 9.0, 8.5, 9.0, 9.0],  # Total = 44.5 -> Sobretiempo
        ["María López", 8.0, 7.0, 8.0, 8.0, 8.0]     # Total = 39.0 -> Horario estándar
    ]
    
    resultados = []
    for recurso in matriz_recursos:
        nombre, total_horas, clasificacion = calcular_y_clasificar_jornada(recurso)
        resultados.append((nombre, total_horas, clasificacion))
        
    mostrar_informe(resultados)


if __name__ == "__main__":
    main()
