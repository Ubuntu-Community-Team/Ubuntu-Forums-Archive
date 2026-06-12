---
title: "[SOLVED] ¿Cómo creo una variable de entorno en Ubuntu?"
date: 2007-06-06
forum: Colombia Team - Colombia
---

### Post by sirgazil on 2007-06-06
Hola,

Hace poco instalé el Java 6 JDK y el entorno de desarrollo Netbeans. Netbeans localizó automaticamente la carpeta de Java que instalé y funciona perfectamente. Mi problema es que ahora instalé otro programa que depende del JDK de Java pero, al ejecutarlo, me dice que no encuentra a JAVA_HOME. Por eso creo que necesito crear una variable de entorno que indique la ruta al Java 6 JDK.

¿En dónde se configuran las variables de entorno en Ubuntu?
Si no hay una interfaz gráfica para hacer esto, ¿Cómo lo hago desde un terminal?

NOTA: Hace 2 días me deshice de Windows XP y ahora estoy trabajando con Ubuntu 7.04. Digo esto para que tengan en cuenta que soy nuevo en el mundo de gnu/linux.

¡Gracias de antemano!

---

### Post by magicfab on 2007-06-08
"Depende". Mir éstos sitios para tener ejemplos y decidir por tí mismo:
[http://www.laliluna.de/blog/2007/02/22/ubuntu_environment_variable_java_home.html](http://www.laliluna.de/blog/2007/02/22/ubuntu_environment_variable_java_home.html)
[http://www.linuxtopia.org/online_books/linux_beginner_books/unofficial_ubuntu_starter_guide/index_159.html](http://www.linuxtopia.org/online_books/linux_beginner_books/unofficial_ubuntu_starter_guide/index_159.html)
[http://ubuntuforums.org/showthread.php?t=1586http://ac12.wordpress.com/2007/04/18/ubuntu-environment-variables/](http://ubuntuforums.org/showthread.php?t=1586http://ac12.wordpress.com/2007/04/18/ubuntu-environment-variables/)

---

### Post by sirgazil on 2007-06-08
Gracias [COLOR="YellowGreen"]magicfab[/COLOR] por la información.

Busqué en [[COLOR="Sienna"]_la documentación en línea de Ubuntu_[/COLOR]]("https://help.ubuntu.com/community/")  y, después de leer bastante, armé este procedimiento que resolvió mi problema:
[COLOR="Red"]
NOTA: Yo soy nuevo en Ubuntu. No me gustaría que este procedimiento se convierta en la desgracia de algún usuario. Así que les pido el favor a los usuarios con más experiencia que lean el procedimiento en busca de malas prácticas.[/COLOR] 

**[SIZE="4"]¿En dónde se definen las variables de entorno globales?[/SIZE]**

Según [[COLOR="Sienna"]_esta página de la documentación de Ubuntu_[/COLOR]]("https://wiki.ubuntu.com/environment_variables"), estas variables pueden ponerse en cualquiera de estos archivos:

**/etc/environment** (recomiendan usar este primero)
**/etc/profile**

Seguí la recomendación de la documentación y pasé a revisar el contenido del archivo **environment** para saber cómo estaba estructurado. Entonces:

1.Abrí el editor de texto **gedit** que está en **Aplicaciones > Accesorios > Editor de textos**.
2.Luego abrí el archivo **environment** cuya ruta es **/etc/environment**.

Esto decía en el archivo **environment** original:

```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
LANG="es_CO.UTF-8"
```

Noten que en la parte superior del editor de texto se indica que el archivo es de Solo lectura. Esto es porque **environment** solo puede modificarlo un usuario con privilegios administrativos. Esto fue lo que hice para poder modificar el archivo:

1.Cerré gedit.
2.Presioné la combinación de teclas **Alt+F2**. En la ventana que se abrió escribí el comando **gksudo gedit /etc/environment**, que me permite abrir el archivo **environment** con **gedit** y con privilegios administrativos. Luego lo ejecuté.
3.Apareció una ventana para ingresar una clave y escribí la clave del usuario que creé al instalar Ubuntu. Esto confirma que tengo permiso para modificar el archivo.
4.Se abrió gedit con el archivo **environment** y ahora puedo agregar mi variable de entorno. En este caso mi necesidad era crear la variable JAVA_HOME que contiene la ruta al directorio raíz del JDK de Java. Así que modifiqué el archivo **environment** [_[COLOR="Sienna"]como me indicaba la documentación de Ubuntu[/COLOR]_]("https://wiki.ubuntu.com/environment_variables"). Así quedó:

```
JAVA_HOME="/usr/local/jdk1.6.0_01"
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:$JAVA_HOME:"
LANG="es_CO.UTF-8"
```

5.Guardé los cambios hechos en el archivo y cerré gedit.
6.Cerré mi sesión para que los cambios surtieran efecto.
7.Volví a abrir la sesión.
8.Abrí un terminal y escribí el comando

```
echo $PATH
```

para verificar los cambios. Efectivamente, ahora el contenido de la variable PATH muestra la ruta al directorio raíz del Java JDK.
9.Por último, ejecuté el programa que antes no encontraba la ruta al JDK de Java y listo, ahora funciona perfectamente.

Espero que esto le sirva a alguien.

---

### Post by fabafarmer on 2011-06-03
Excelente!!! bien detallado, gracias!!

---

