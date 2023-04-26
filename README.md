# 1. Instrucciones de configuración

Git se utiliza principalmente a través de la interfaz de línea de comandos, a la que podemos acceder con nuestros terminales del sistema.

Sin embargo, primero tenemos que asegurarnos de que tenemos Git instalado en nuestros ordenadores.

ℹ️ Puedes descargar Git aquí: [https://git-scm.com/downloads](https://git-scm.com/downloads)

Haz clic en el enlace de descarga para tu sistema operativo específico y luego sigue el asistente de instalación para configurar todo en tu ordenador.

Después de instalarlo, inicia tu terminal y escribe el siguiente comando para verificar que Git está listo para ser usado en tu ordenador:

```bash
git --version
```

Si todo ha ido bien, debería devolver la versión de Git que está instalada en tu ordenador.

>Si estás usando una máquina Mac o Linux, entonces puedes utilizar el terminal Bash por defecto que viene preinstalado en tu máquina.

> Si estás usando Windows, puedes usar su terminal Powershell integrada, o la terminal Git Bash que viene incluida con la instalación de Git. Para obtener instrucciones detalladas sobre la instalación de Git y Git Bash en Windows, consulta esta entrada del blog: [https://zarkom.net/blogs/how-to-install-git-and-git-bash-on-windows-9140](https://zarkom.net/blogs/how-to-install-git-and-git-bash-on-windows-9140)


### Configuración de tu nombre y correo electrónico

En tu terminal, ejecuta los siguientes comandos para identificarte con Git:

```bash
git config --global user.name "Tu Nombre"
git config --global user.email "your@email.com"
```

Para obtener los datos de la configuración existente.

```shell
git config --list
```

Sustituye los valores entre comillas por tu nombre y dirección de correo electrónico.

# 2. Repositorios

Cuando se trabaja con Git, es importante estar familiarizado con el término **repositorio**. Un repositorio Git es un contenedor para un proyecto que es rastreado por Git.  

Podemos distinguir dos tipos principales de repositorios Git:

- **Repositorio local** - un repositorio aislado almacenado en tu propio ordenador, donde puedes trabajar en la versión local de tu proyecto.
- **Repositorio remoto** - generalmente almacenado fuera de tu sistema local aislado, normalmente en un servidor remoto. Es especialmente útil cuando se trabaja en equipo - este es el lugar donde puedes compartir el código de tu proyecto, ver el código de otras personas e integrarlo en tu versión local del proyecto, y también empujar tus cambios al repositorio remoto.

# 3. Inicializar un repositorio

Para crear un nuevo repositorio y comenzar el seguimiento de tu proyecto con Git, utiliza tu software de terminal y navega a la carpeta principal de tu proyecto, a continuación, escribe el siguiente comando:

```bash
git init
```

Este comando generará un directorio oculto **.git** para tu proyecto, donde Git almacena todos los datos internos de seguimiento del repositorio actual.

# 4. Preparación y confirmación del código

El commit es el proceso en el que los cambios se añaden *'oficialmente'* al repositorio Git.

En Git, podemos considerar los **commits** como puntos de control, o instantáneas de tu proyecto en su estado actual. En otras palabras, básicamente guardamos la versión actual de nuestro código en un commit. Podemos crear tantos commits como necesitemos en el historial de commits, y podemos avanzar y retroceder entre commits para ver las diferentes revisiones del código de nuestro proyecto. Esto nos permite gestionar eficazmente nuestro progreso y realizar un seguimiento del proyecto a medida que se desarrolla.

Los commits suelen crearse en puntos lógicos a medida que desarrollamos nuestro proyecto, normalmente después de añadir contenidos, características o modificaciones específicas (como nuevas funcionalidades o correcciones de errores, por ejemplo).

>📌 Antes de poder hacer commit de nuestro código, necesitamos colocarlo dentro del **staging area**.

## 4.1. Comprobando el estado

Situados dentro de la carpeta del proyecto en nuestro terminal, podemos escribir el siguiente comando para comprobar el estado de nuestro repositorio:

```bash
git status
```

Este es un comando que se utiliza muy a menudo cuando se trabaja con Git.  Nos muestra qué archivos han sido modificados, qué archivos están rastreados, etc.

Podemos añadir los archivos no rastreados del proyecto a la **zona de preparación** basándonos en la información del comando `git status`.

Más adelante, `git status` nos informará de cualquier modificación que hayamos hecho en nuestros archivos rastreados antes de que decidamos añadirlos de nuevo a la zona de preparación.

## 4.2. Puesta en escena de archivos

Desde la carpeta del proyecto, podemos utilizar el comando **git add** para añadir nuestros archivos al área de staging, lo que permite su seguimiento.

Podemos añadir un archivo específico al área de staging con el siguiente comando:

```bash
git add archivo.js
```

Para añadir varios archivos, podemos hacer lo siguiente:

```bash
git add archivo.js archivo2.js archivo3.js
```

En lugar de tener que añadir los archivos individualmente, también podemos añadir todos los archivos dentro de la carpeta del proyecto al área de preparación:

```bash
git add .
```

Por defecto, esto añade **todos los archivos y carpetas** dentro de la carpeta del proyecto al área de preparación, desde donde están listos para ser confirmados y rastreados.

## 4.3. Haciendo commits

Un **commit** es una instantánea de nuestro código en un momento determinado, que estamos guardando en el historial de commits de nuestro repositorio. Después de añadir todos los ficheros que queremos seguir al área de preparación con el comando `**git add`**, estamos listos para hacer un commit.

Para confirmar los archivos desde el área de preparación, utilizamos el siguiente comando:

```bash
git commit -m "Mensaje de confirmación"
```

Dentro de las comillas, debemos escribir un **commit message** que se utiliza para identificarlo en el historial de commits.

El mensaje de confirmación debe ser un resumen descriptivo de los cambios que estás confirmando en el repositorio.

Después de ejecutar ese comando, obtendrás los detalles técnicos sobre el commit impresos en el terminal. Y eso es básicamente todo, ¡has realizado con éxito un commit en tu proyecto!

>📌 Para crear un nuevo commit, necesitarás repetir el proceso de agregar archivos al área de staging y luego hacer el commit después. De nuevo, es muy útil usar el comando **git status** para ver qué archivos fueron modificados, staged, o untracked.


## 4.4. Historial de commits

Para ver todos los commits que se hicieron para nuestro proyecto, puedes usar el siguiente comando:

```bash
git log
```

Los registros mostrarán detalles de cada confirmación, como el nombre del autor, el hash generado para la confirmación, la fecha y hora de la confirmación, y el mensaje de confirmación que hemos proporcionado.

Para volver a un estado anterior del código de tu proyecto que has confirmado, puedes utilizar el siguiente comando:

```bash
git checkout <commit-hash>
```

Sustituye `<commit-hash>` por el hash real del commit específico que quieres visitar, el cual se lista con el comando `git log`.

Para volver al último commit (la versión más reciente del código de nuestro proyecto), puedes escribir este comando:

```bash
git checkout master
```

## 4.5. Ignorar archivos

Para ignorar archivos que no quieres que sean rastreados o añadidos al área de preparación, puedes crear un archivo llamado `.gitignore` en la carpeta principal de tu proyecto.

Dentro de ese archivo, puedes listar todos los nombres de archivos y carpetas que definitivamente no quieres rastrear (cada archivo y carpeta ignorado debe ir a una nueva línea dentro del archivo **.gitignore**).

Puedes leer un artículo sobre cómo ignorar archivos [en este enlace](https://help.github.com/en/articles/ignoring-files).

# 5. Ramas

Una **rama** podría interpretarse como una línea de tiempo individual de los commits de nuestro proyecto.

Con Git, podemos crear muchos de estos entornos alternativos (es decir, podemos crear diferentes **ramas**) para que otras versiones del código de nuestro proyecto puedan existir y ser rastreadas en paralelo.

Esto nos permite añadir nuevas características (experimentales, inacabadas y potencialmente defectuosas) en ramas separadas, sin tocar la versión '*oficial'* estable del código de nuestro proyecto (que normalmente se mantiene en la rama **master**).

Cuando inicializamos un repositorio y empezamos a hacer confirmaciones, éstas se guardan en la rama **master** por defecto.

## 5.1. Crear una nueva rama

Puedes crear una nueva rama usando el siguiente comando:

```bash
git branch <nombre-de-nueva-rama>
```

La nueva rama que se crea será la referencia al estado actual de tu repositorio.

>📌 Es una buena idea crear una rama de **desarrollo** donde puedas trabajar en mejorar tu código, añadir nuevas características experimentales y similares. Después de desarrollar y probar estas nuevas características para asegurarte de que no tienen errores y que se pueden utilizar, puedes fusionarlas a la rama maestra.

## 5.2. Cambiar de rama

Para cambiar de rama, se utiliza el comando **git checkout**:

```bash
git checkout <nombre-de-la-rama>
```

Con eso, cambias a una línea de tiempo aislada diferente de tu proyecto cambiando de rama.

>📌 Por ejemplo, podrías estar trabajando en diferentes características de tu código y tener una rama separada para cada característica. Cuando se cambia a una rama, puede confirmar los cambios de código que sólo afectan a esa rama en particular. Luego, puedes cambiar a otra rama para trabajar en una característica diferente, que no se verá afectada por los cambios y commits realizados desde la rama anterior.

Para crear una nueva rama y cambiar a ella al mismo tiempo, puedes usar el flag **-b**:

```bash
git checkout -b <nombre-de-nueva-rama>
```


>ℹ️ Para listar las ramas de tu proyecto, usa este comando: `git branch`

Para volver a la rama **master**, utiliza este comando:

```bash
git checkout master
```

## 5.3. Fusionar ramas

Puedes fusionar ramas en situaciones en las que quieras implementar los cambios de código que hiciste en una rama individual a una rama diferente.

Por ejemplo, después de implementar y probar completamente una nueva característica en tu código, querrás fusionar esos cambios a la rama estable de tu proyecto (que normalmente es la rama **master** por defecto).

Para fusionar los cambios de una rama diferente en su rama actual, puede utilizar este comando:

```bash
git merge <nombre-de-la-rama>
```

Reemplaza `<nombre-de-la-rama>` por la rama que quieres integrar en tu rama actual.

## 5.4. Borrar una rama

Para borrar una rama, puedes ejecutar el comando **git branch** con la bandera **-d**:

```bash
git branch -d <nombre-de-la-rama>
```

>ℹ️ Lee más sobre ramificación y fusión [en este enlace](https://git-scm.com/book/en/v2/Git-Branching-Basic-Branching-and-Merging).

Para borrar una rama en remoto, debemos ejecutar el comando git push origin --delete:

```bash
git push origin --delete <nombre-de-la-rama>
```

# 6. Aprendizaje adicional

Para aprender más sobre Git, asegúrate de consultar los siguientes recursos:

- Documentación oficial de Git: [https://git-scm.com/doc](https://git-scm.com/doc)
- El libro gratuito **Pro Git**: [https://git-scm.com/book/en/v2](https://git-scm.com/book/en/v2)
- Más información sobre GitHub: [https://guides.github.com/](https://guides.github.com/)

>ℹ️ GitHub es un sitio web donde podemos almacenar nuestros repositorios online. En otras palabras, GitHub funciona con Git como un servicio de alojamiento de repositorios.



