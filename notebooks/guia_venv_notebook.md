# Guía: Entorno Virtual y Jupyter Notebook en VSCode

## 1. Crear un entorno virtual (venv)

Abre la terminal integrada de VSCode con `Ctrl + `` ` (acento grave) o desde el menú **Terminal → New Terminal**.

```bash
# Crear el entorno virtual (se crea una carpeta llamada "venv")
python -m venv venv
```

### Activar el entorno virtual

**En Windows:**
```bash
venv\Scripts\activate
```

**En macOS / Linux:**
```bash
source venv/bin/activate
```

Una vez activado verás el prefijo `(venv)` al inicio de la línea en la terminal.

### Desactivar el entorno virtual

```bash
deactivate
```

---

## 2. Instalar las librerías necesarias

Con el entorno activado, instala las librerías del curso:

```bash
pip install jupyter notebook ipykernel
pip install numpy pandas scipy scikit-learn
pip install matplotlib plotly seaborn
pip install ydata-profiling
```

Registra el entorno como kernel de Jupyter:

```bash
python -m ipykernel install --user --name=venv --display-name "data_mining (venv)"
```

---

## 3. Crear un Jupyter Notebook desde la terminal

```bash
# Crear un notebook vacío con nombre específico
jupyter nbconvert --to notebook --execute /dev/null --output mi_notebook.ipynb
```

O simplemente crea el archivo directamente:

```bash
# Opción más sencilla: crear el archivo y abrirlo con Jupyter
jupyter notebook
```

Esto abre el navegador con el explorador de Jupyter. Desde ahí seleccionas **New → data_mining (venv)**.

---

## 4. Trabajar con notebooks directamente en VSCode

VSCode tiene soporte nativo para notebooks `.ipynb`. Solo necesitas:

1. Instalar la extensión **Jupyter** de Microsoft (si no está instalada).
2. Crear un archivo nuevo con extensión `.ipynb`:

```bash
# Desde la terminal, crear el archivo vacío
echo "" > mi_notebook.ipynb
```

3. Abrir el archivo en VSCode — se abrirá automáticamente como notebook.
4. En la esquina superior derecha, selecciona el kernel **data_mining (venv)**.

---

## 5. Flujo de trabajo recomendado

```bash
# 1. Navegar a tu carpeta de proyecto
cd mi_proyecto

# 2. Crear y activar el entorno
python -m venv venv
source venv/bin/activate        # macOS/Linux
# venv\Scripts\activate         # Windows

# 3. Instalar dependencias
pip install jupyter ipykernel numpy pandas scipy scikit-learn matplotlib plotly seaborn ydata-profiling

# 4. Registrar el kernel
python -m ipykernel install --user --name=venv --display-name "data_mining (venv)"

# 5. Abrir VSCode en la carpeta actual
code .
```

Desde VSCode creas o abres tu `.ipynb` y seleccionas el kernel **data_mining (venv)**.

---

## 6. Guardar dependencias del proyecto

```bash
# Exportar las librerías instaladas
pip freeze > requirements.txt

# En otro equipo, restaurar el entorno
pip install -r requirements.txt
```

---

> **Tip:** Si VSCode no detecta el kernel automáticamente, presiona `Ctrl+Shift+P`, escribe `Jupyter: Select Interpreter to Start Jupyter Server` y selecciona el Python de tu carpeta `venv`.
