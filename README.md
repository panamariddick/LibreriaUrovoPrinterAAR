# 📦 Cómo Agregar un Archivo `.aar` a un Proyecto Android

Puedes agregar un archivo `.aar` a tu proyecto Android como librería local de dos maneras principales, dependiendo de si estás usando **Gradle con sintaxis Groovy (`build.gradle`)** o **Kotlin DSL (`build.gradle.kts`)**.

---

## 🧩 1. Colocar el `.aar` en tu proyecto

Primero, copia el archivo `.aar` en una carpeta local del proyecto, típicamente:

```
/libs/BluetoothPrinterLib.aar
```

Si no existe la carpeta `libs`, créala tú mismo dentro del módulo donde deseas usar la librería (por ejemplo: `app/libs`).

---

## ⚙️ 2. Registrar la librería

### 🔸 a) En Groovy (`build.gradle`)

Edita el archivo `app/build.gradle` del módulo:

```groovy
repositories {
    flatDir {
        dirs 'libs'
    }
}

dependencies {
    implementation(name: 'BluetoothPrinterLib', ext: 'aar')
}
```

> 🔁 **Nota**: Asegúrate de **no incluir la extensión `.aar`** en el campo `name`.

---

### 🔸 b) En Kotlin DSL (`build.gradle.kts`)

Edita el archivo `app/build.gradle.kts` del módulo:

```kotlin
repositories {
    flatDir {
        dirs("libs")
    }
}

dependencies {
    implementation(name = "BluetoothPrinterLib", ext = "aar")
}
```

---

## ✅ 3. Sincroniza el proyecto

Después de hacer esto:

1. Haz clic en **"Sync Project with Gradle Files"** en Android Studio.
2. Verifica que el archivo `.aar` se haya reconocido correctamente (debería aparecer en la sección **External Libraries**).

---

## 📌 Recomendaciones adicionales

- Si tu `.aar` depende de otras bibliotecas (por ejemplo, `core-ktx`, `zxing`, etc.), agrégalas manualmente a tus dependencias.
- Asegúrate de versionar o documentar la ubicación del `.aar` si trabajas en equipo o publicas el proyecto.

---
