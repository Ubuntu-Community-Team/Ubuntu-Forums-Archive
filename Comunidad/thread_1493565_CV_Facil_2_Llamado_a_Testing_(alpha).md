---
title: "CV Facil 2: Llamado a Testing (alpha)"
date: 2010-05-26
forum: Comunidad
---

### Post by juancarlospaco on 2010-05-26
**[SIZE="5"]CV Facil 2: Creador de Curriculums Vitae! *(beta)*[/SIZE]**

[LIST]
[*]Pruebenlo y tiren ideas o lo que se les ocurra...
[*]Tener en cuenta que es Beta.
[*]Pocas dependencias, no instala QT en Gnome, no instala GTK en KDE
[/LIST]

[[IMG]http://img190.imageshack.us/img190/2950/cvfacil2alpha.jpg[/IMG]]("http://tecnicoslinux.com.ar/livecd/cvfacil2_0.5_all.deb")

*Gracias a [http://tecnicoslinux.com.ar/](http://tecnicoslinux.com.ar/)*

Consejo:
Cerrar todos las ventanas de OpenOffice antes de ejecutarlo *(por las dudas)*

Datos Tecnicos:
[LIST]
[*]Python
[*]32 y 64bit
[*]371,7Kb
[/LIST]

*[SIZE="1"]"Continuara..."[/SIZE]*
:)

---

### Post by alfplayer on 2010-05-26
Es interesante.

Aclaración: el link al deb está en la imagen.

Lo probé en Fedora 13: funciona bien (nombres de paquetes: tkinter y openoffice.org-pyuno).

Me gustó.

No es obvio que hay que cliquear "Completar los Datos de Experiencia Laboral" para llenar los datos.

No se qué más probar :)

---

### Post by juancarlospaco on 2010-05-26
Si, las dependencias son python-tk y python-uno.

La parte de Experiencia Laboral aun no esta terminada,
la plantilla de CV final sera mejor tambien, incorporara mas botones.

El cronometro es por que en algunos lugares *(comercios, cybers)*,
donde se tipea CV, se cobra dependiendo del tiempo que lleva el tipeo.
Permite personalizar la Piel y el Titulo del Programa.
Tiene un modo para usar en Netbooks.
Puede leer su propio codigo fuente, o conseguir ayuda on-line.
Te permite conseguir tu numero de CUIL o un Trabajo.

El link de descarga es:

[LIST]
[*]**[http://tecnicoslinux.com.ar/livecd/cvfacil2_0.5_all.deb](http://tecnicoslinux.com.ar/livecd/cvfacil2_0.5_all.deb)**
[/LIST]

dejo otra foto del programa donde se ve mejor:

[IMG]http://img189.imageshack.us/img189/4093/pantallazou.jpg[/IMG]


***Se agradece el Feedback!***
:)

---

### Post by alfplayer on 2010-05-26
Lo de los modos con pantallas de diferentes tamaños me pareció interesante.

Hay muchos bugs obvios que imagino que sabés cuáles son, por estar en desarrollo.

Cierro las dos ventanas, ejecuto ./cvfacil2.py y me aparece:

```
File "./cvfacil2.py", line 395, in <module>
    context = resolver.resolve("uno:socket,host=localhost,port=2002;urp;StarOffice.ComponentContext")
__main__.NoConnectException: Connector : couldn't connect to socket (Success)
```

y vuelvo a bash.

Si ejecuto de nuevo ./cvfacil2.py me abre todo bien y no me aparece el error.

En todos los segundos intentos me abre y funciona la aplicación sin error.

---

### Post by hictio on 2010-05-27
Si lo testeo en varias máquinas me gano una cita con la rubia de la foto? ;)

---

### Post by juancarlospaco on 2010-05-30
Gracias a las ideas que un usuario me comento,
este finde le agregue un "**Modo de Accesibilidad**", 
para personas con capacidades diferentes,
inspirado en el Tema de Ubuntu "Alto Contraste Grande"
*(Sistema--->Preferencias--->Apariencia--->Tema--->Alto Contraste Grande)*,
en un click la Interfaz Grafica se vuelve de fondo negro
y con letras mucho mas grandes de color blanco, ideal para problemas Visuales.

[CENTER][IMG]http://img580.imageshack.us/img580/3520/cvfacil2access.jpg[/IMG]
*[SIZE="1"](aun los cambios no estan en el .deb)[/SIZE]*
[/CENTER]

*To be continued...*
:P

---

### Post by juancarlospaco on 2010-06-03
**[SIZE="3"]Version 0.3:[/SIZE]**

[CENTER][IMG]http://img404.imageshack.us/img404/9716/norrischuckcv.jpg[/IMG][/CENTER]


[LIST]
[*]Grandes mejoras en la Plantilla de CV por defecto.
[*]Se agrego el Menu Herramientas.
[*]Se agrego la Opcion de *"Copiar mi CV a mi Nube Ubuntu One"*
[*]Se agrego la Opcion de *"Crear una cuenta nueva de Correo Electronico @Gmail.com"*
[*]Se agrego la Opcion de *"Abrir Ventana de Terminal de Linea de Comandos"*
[*]Se agrego la Opcion de *"Obtener .DEB de este programa para Instalar Off-Line"*
[*]Se agrego la Opcion de *"Apagar el Monitor"*
[*]Se agrego el Modo especial de *"Modo Accesibilidad: Interface grafica Blanco/Negro y Letras Grandes, para personas con capacidades diferentes" *
[*]Se agrego la Opcion de *"Usar mi propia Plantilla Personalizada OpenOffice para CV Facil 2"*(EDIT: deshabilitada temporalmente)
[*]Se agrego la Opcion de *"Restaurar la Plantilla OpenOffice Original de CV Facil 2"*(EDIT: deshabilitada temporalmente)
[*]No se necesita iniciar el Programa 2 veces para que realmente inicie.
[*]Se implemento *DocStrings* Internos a un 50%, a futuro sera una aplicacion que se documentara a si misma.
[*]Mencion especial a los Betatesters MHoyos, GabyMejia, alfplayer, hictio.
[*]Se agrego Aceleracion del programa mediante Psyco *(compilador JIT)*, es opcional*(anda igual)*, pero recomendado, se instalaria *sudo apt-get install python-psyco*
[/LIST]

**[SIZE="3"]Links de arriba cambiados.[/SIZE]**

:)

---

### Post by alfplayer on 2010-06-03
La primera ejecución (sigo con Fedora 13):

```
$ ./cvfacil2.sh 
mkdir: created directory `/tmp/cvfacil2/'
 &#10132; No PYTHON-PSYCO avaliable&#8252;, this application will run slower... 
Traceback (most recent call last):
  File "/usr/share/cvfacil2/cvfacil2.py", line 479, in <module>
    context = resolver.resolve("uno:socket,host=localhost,port=2002;urp;StarOffice.ComponentContext")
__main__.NoConnectException: Connector : couldn't connect to socket (Success)

$
```

En las posteriores inicia bien y sin errores.


**Mi opinión:**

Grandes mejoras en la Plantilla de CV por defecto.
*No es mejor dejarlo simple para que pueda personalizarse? Me gustaría como opcional.*

Se agrego la Opcion de "Copiar mi CV a mi Nube Ubuntu One"
*Muy bueno aunque no lo probé. Opción para Google Docs ?*

Se agrego la Opcion de "Crear una cuenta nueva de Correo Electronico @Gmail.com"
*No me gusta, pero no me quejo con tantos argentinos con mail de MS.*

Se agrego la Opcion de "Abrir Ventana de Terminal de Linea de Comandos"
*No entiendo para qué. Alt-F2 ?*

Se agrego la Opcion de "Obtener .DEB de este programa para Instalar Off-Line"
*No le veo sentido. Estas cosas no deben hacerse dentro de la aplicación.*

Se agrego la Opcion de "Apagar el Monitor"
*Lo probé, me funcionó bien. No entiendo para qué.*

Se agrego el Modo especial de "Modo Accesibilidad: Interface grafica Blanco/Negro y Letras Grandes, para personas con capacidades diferentes"
*Me gusta. No me parece útil llamar al magnificador, imagino que los ciegos ya tienen su programa que conocen y saben usar, con una shortcut de teclado o alguna otra forma de accederlo. No entendí qué es ese cuadradito titilando hasta que probé cliqueando en un lugar cualquiera de la pantalla.*

Se agrego la Opcion de "Usar mi propia Plantilla Personalizada OpenOffice para CV Facil 2"(EDIT: deshabilitada temporalmente)
*Me gusta.*

Se agrego la Opcion de "Restaurar la Plantilla OpenOffice Original de CV Facil 2"(EDIT: deshabilitada temporalmente)
*Me gusta.*

Se agrego Aceleracion del programa mediante Psyco (compilador JIT), es opcional(anda igual), pero recomendado, se instalaria sudo apt-get install python-psyco
*No lo probé.*

Me gusta este programa, las opciones de accesibilidad, la posibilidad de subir a Ubuntu One y el soporte para múltiples plantillas. Hay cosas que no entiendo, que pueden contaminar a los menús.

---

### Post by juancarlospaco on 2010-06-04
> **alfplayer said:**
> La primera ejecución (sigo con Fedora 13):

```
$ ./cvfacil2.sh 
mkdir: created directory `/tmp/cvfacil2/'
 &#10132; No PYTHON-PSYCO avaliable&#8252;, this application will run slower... 
Traceback (most recent call last):
  File "/usr/share/cvfacil2/cvfacil2.py", line 479, in <module>
    context = resolver.resolve("uno:socket,host=localhost,port=2002;urp;StarOffice.ComponentContext")
__main__.NoConnectException: Connector : couldn't connect to socket (Success)

$
```


Si, 
es mas un bug de la libreria de OpenOffice que del programa,
fijate que dice: 
*"couldn't connect"*(no anda), despues dice *"Success"*(andubo),
 ...pero veo como puedo solucionarlo.

> **alfplayer said:**
> 
*No es mejor dejarlo simple para que pueda personalizarse? Me gustaría como opcional.*
No, 
esta orientado a personas que no saben usar muy bien programas de Ofimatica,
igualmente puede personalizarse el CV Terminado, es a eleccion.

> **alfplayer said:**
> 
Se agrego la Opcion de "Copiar mi CV a mi Nube Ubuntu One"
*Muy bueno aunque no lo probé. Opción para Google Docs ?*


No se que hara en Fedora, 
como dice en la ventanita de About esta *"pensado para Ubuntu"*.
Estoy estudiando la posibilidad de Google docs..., 
pero requiere un volquete de librerias de Mono.

> **alfplayer said:**
> 
Se agrego la Opcion de "Crear una cuenta nueva de Correo Electronico @Gmail.com"
*No me gusta, pero no me quejo con tantos argentinos con mail de MS.*


Si,
Sabes que pasa, MUCHISIMA gente necesita sacar un correo para poder presentarse a un laburo,
hoy dia, hasta para Limpieza o Vigilancia te exijen tener Correo Electronico.

> **alfplayer said:**
> 
Se agrego la Opcion de "Abrir Ventana de Terminal de Linea de Comandos"
*No entiendo para qué. Alt-F2 ?*

Si,
La opcion ya fue Eliminada.

> **alfplayer said:**
> 
Se agrego la Opcion de "Obtener .DEB de este programa para Instalar Off-Line"
*No le veo sentido. Estas cosas no deben hacerse dentro de la aplicación.*

No se,
Fue a pedido de un Usuario, 
solicitaba que el programa instalado pueda generar un deb instalador,
para permitir instalarlo Off-Line.
La opcion ya fue Eliminada.

> **alfplayer said:**
> 
Se agrego la Opcion de "Apagar el Monitor"
*Lo probé, me funcionó bien. No entiendo para qué.*

No se,
La opcion ya fue Eliminada.

> **alfplayer said:**
> 
Se agrego el Modo especial de "Modo Accesibilidad: Interface grafica Blanco/Negro y Letras Grandes, para personas con capacidades diferentes"
*Me gusta. No me parece útil llamar al magnificador, imagino que los ciegos ya tienen su programa que conocen y saben usar, con una shortcut de teclado o alguna otra forma de accederlo. No entendí qué es ese cuadradito titilando hasta que probé cliqueando en un lugar cualquiera de la pantalla.*

Si,
La opcion ya no llama al Zo0m.

> **alfplayer said:**
> 
Se agrego Aceleracion del programa mediante Psyco (compilador JIT), es opcional(anda igual), pero recomendado, se instalaria sudo apt-get install python-psyco
*No lo probé.*

Ok,
probalo.

--------------------------------------------------------------------------------------------

[LIST]
[*]**[SIZE="3"]A los que lo han probado, se necesita mas Feedback.[/SIZE]**
[/LIST]

Anda en KDE?
Anda en Gnome-Shell?

:)

---

### Post by alfplayer on 2010-06-04
**Algunas ideas:**

[LIST]
[*]Un botón para cambiar el estilo, aunque la plantilla por defecto sea "lista para imprimir".

[*]No encontré un programa así en la web para linux. Puede ser buena idea subirlo a Debian o Ubuntu.

[*]Decir que va a ser GPL, con código abierto, uso y distribución gratuita, etc. puede ayudarte a tener más feedback, difusión, etc.

[*]Lo que encontré para subir a Google Docs: [http://code.google.com/apis/documents/docs/1.0/developers_guide_python.html#UploadingWPDocs]("http://code.google.com/apis/documents/docs/1.0/developers_guide_python.html#UploadingWPDocs")
[/LIST]

Saludos.

---

### Post by juancarlospaco on 2010-06-07
> **alfplayer said:**
> 
No encontré un programa así en la web para linux. Puede ser buena idea subirlo a Debian o Ubuntu.

Eso es lo que me gusta, crear programas simples pero utiles que no estan en Ubuntu Lignux.

> **alfplayer said:**
> 
Decir que va a ser GPL, con código abierto, uso y distribución gratuita, etc. puede ayudarte a tener más feedback, difusión, etc.


[B]Ayuda--->Leer Licencia de CV Facil 2
Ayuda--->Leer Codigo Fuente de CV Facil 2[/B]
Mas claro imposible :P
*No he visto otro programa que pueda leer su propio codigo fuente.*

> **alfplayer said:**
> 
Lo que encontré para subir a Google Docs: [http://code.google.com/apis/documents/docs/1.0/developers_guide_python.html#UploadingWPDocs]("http://code.google.com/apis/documents/docs/1.0/developers_guide_python.html#UploadingWPDocs")


Leyendo...

---

### Post by alfplayer on 2010-06-07
OK.

Había visto que no está LICENSE y no está el texto que hace referencia a la GPL en los .py.

Se puede usar Lintian para estas cosas.

---

### Post by juancarlospaco on 2010-06-12
**[SIZE="4"]Version 0.5:[/SIZE]**

[LIST]
[*]Soporte para idioma Ingles *[SIZE="1"](parcial)[/SIZE]*
[*]Splash Screen con barra de Carga.
[*]Efecto *StartUp Fade-In *en la Interface Grafica.
[*]Ventana para llenar la experiencia laboral funcionando e incluye Contenido de Ejemplo.
[*]Opcion para agregar automaticamente en el pie de pagina del CV en letra pequeña, cursiva, semitransparente *"Creado con Software Libre"*
[*]Opcion de copiar el CV Terminado a Ubuntu One.
[*]Opcion de copiar el CV Terminado a GoogleDocs. *[SIZE="1"](temporalmente desabilitada)[/SIZE]*
[*]Opcion Avanzada *"Ejecutar un comando luego de terminar el CV"* *[SIZE="1"](pedido de usuarios)[/SIZE]*
[*]Opcion para usar una plantilla OpenOffice personalizada.
[*]Opcion para restaurar la plantilla OpenOffice por defecto.
[*]Boton para Terminar el CV mas llamativo.
[*]Opcion "Abrir Ventana de Terminal de Linea de Comandos" fue Eliminada.
[*]Opcion "Obtener .DEB de este programa para Instalar Off-Line" fue Eliminada.
[*]Opcion "Apagar el Monitor" fue Eliminada.
[*]El "Modo Accesibilidad" ya No llama al Zoom en Pantalla
[*]Solo es necesario lanzarlo 1 vez para que inicie *[SIZE="1"](BugFix)[/SIZE]*
[*]Opcion "Informacion para resolucion de problemas" *[SIZE="1"](Trouble Shoot Information)[/SIZE]*
[*]Solo permite 1 Instancia.
[*]DocStrings 100%.
[*]Compatible con Python 3.x *[SIZE="1"](mantiene compatibilidad con Python 2.x, Meerkat+1)[/SIZE]*
[*]El programa es auto-documentado con ePyDoc
[*]Incluye Manual de Documentacion para Programadores de 15 Paginas.
[*]Probado en Gnome-Shell.
[/LIST]

```
[CENTER][**[SIZE="3"]http://tecnicoslinux.com.ar/livecd/cvfacil2_0.5_all.deb[/SIZE]**]("http://tecnicoslinux.com.ar/livecd/cvfacil2_0.5_all.deb")[/CENTER]
```

:)

---

### Post by alfplayer on 2010-06-13
Volví a Lucid...

Los cambios me parecen muy buenos.


**Feedback de algunos cambios**

*Ejecutar un comando...*
No entiendo.

Opción de agregar *Creado con Software Libre*
Buena idea! Hacer un check box? 

Aparecen unos caracteres raros en el pie de página.

Instalé Psyco y lo volví a ejecutar: no noté diferencia de velocidad en un C2D @ 3 GHz.

El inicio quedó lento para mi gusto.

---

### Post by juancarlospaco on 2010-06-17
Lo del Comando es a pedido de un usuario, 
permite imprimir o copiar a una carpeta compartida el CV terminado.

Lo del *"Creado con Software Libre"* lo vi en el Kompozer,
que tiene una opcion de poner en las web que crea *"Made in Kompozer"*

Lo de *"Informacion de resolucion de problemas"* lo vi en el Firefox,
esta bueno cuando estas dando soporte remoto a la aplicacion,
en vez de tirar tantos comandos para sacar info, con un click listo.

Con esa PC va andar rapido, con o sin Psyco.

El Delay en el inicio es por culpa de las Librerias de OpenOffice,
nada puedo hacer al respecto, por eso implemente el splash screen,
asi por lo menos el usuario tiene un feedback grafico de que la aplicacion se esta cargando,
la aplicacion usa de BackEnd las Librerias de OpenOffice.

:)

---

### Post by alfplayer on 2010-06-17
> **juancarlospaco said:**
> El Delay en el inicio es por culpa de las Librerias de OpenOffice,
nada puedo hacer al respecto, por eso implemente el splash screen,
asi por lo menos el usuario tiene un feedback grafico de que la aplicacion se esta cargando,
la aplicacion usa de BackEnd las Librerias de OpenOffice.

No lo probé, pero en una netbook seguramente es mucho más. No uso OpenOffice por que tarda mucho en cargar, y es un tiempo similar (o el mismo?) que tarda en cargar CV Fácil 2.

No se puede cargar en forma transparente para el usuario, mientras llena datos? El usuario probablemente tarda unos minutos hasta que carga el CV en OpenOffice, ni sería necesario bloquearlo.

---

### Post by juancarlospaco on 2010-06-24
> **alfplayer said:**
> 
No se puede cargar en forma transparente para el usuario, mientras llena datos?

No..., hace lo que hacia la version anterior, se sale.



Estaba probando con Gimp de hacerle unas cosas al programa...

**Tenemos un nuevo Icono de Programa Monocromo**,
como dice que deben ser los iconos:
[IMG]http://img580.imageshack.us/img580/3816/iconocvfacil2.jpg[/IMG]



**Tenemos ToolTips Informativos en la Interfaz Grafica**,
fondo oscuro, letras blancas, igual que los de Ubuntu:
[IMG]http://img23.imageshack.us/img23/5405/tooltipscvfacil2.jpg[/IMG]



**Aqui se ve como es el SplashScreen con barra de Carga**, 
mejor Tipografia y sin Borde del Decorador de Ventanas,
la imagen es del Wallpaper Animado *"Cosmos"* que trae por defecto Ubuntu:
[IMG]http://file.status.net/identica/juancarlospaco-20100624T021321-qapycyp.jpeg[/IMG]



**Este es un PopUp que permite enviar el CV Terminado por Mail**,
botones Graficos, en color de Ubuntu en vez de Aqua:
[IMG]http://img188.imageshack.us/img188/5713/screenshotcvfacil2.jpg[/IMG]


[I]Basicamente toma un .GIF estatico de una carpeta y lo usa,
opiniones???,
si no les gusta posteen una imagen y uso esa.[/I]
:)

---

### Post by juancarlospaco on 2010-09-15
No murio, aca mostramos como sigue:

[IMG]http://img214.imageshack.us/img214/1592/cvfacilupd.jpg[/IMG]

-El multiple choice de estado civil y disponibilidad horaria se cambio por ComboBox, los menucitos desplegables esos, fue facil de hacer.
-La fecha de nacimiento se cambio de tipearla a mano por un Calendario Grafico, tipo Pop-Up point-and-click, fue dificil de hacer.

*Lanzo otra version con Maverick.*

[SIZE="1"]Ademas estoy haciendo otra cosa mas, no se si me va salir asi que no me quiero quemar jijijijij, en especial pa los que tienen Android/Blackberry[/SIZE]
:)

---

### Post by alfplayer on 2010-09-15
Sigo opinando...

Dejá la opción de ingresar la fecha de nacimiento con teclado, ingresar con teclado el año es mucho más rápido y intuitivo, especialmente si los botones de + y - no hacen "fast forward" (o como se llame) manteniéndolos cliqueados. Podés hacer que los dos métodos de entrada estén sincronizados.

---

### Post by juancarlospaco on 2010-09-15
> **alfplayer said:**
> 
Dejá la opción de ingresar la fecha de nacimiento con teclado, 

Podés hacer que los dos métodos de entrada estén sincronizados.

Listo..., correjido de esa manera.
:p

---

### Post by mama21mama on 2010-09-15
lo probare y subiré a mi [repo]("http://mamalibre.eshost.com.ar/?q=content/mamalibre-tiene-repo-para-ubuntu-debian").

[hice un post en mi blog]("http://mamalibre.eshost.com.ar/?q=content/cv-facil-2-creador-de-curriculums-vitae-beta")

saludos

---

### Post by juancarlospaco on 2010-09-16
**_[COLOR="Purple"]Aclaracion:[/COLOR]_**

Por que alguien me dice que estoy distribuyendo Binarios,
por desconocimiento, y no es asi.

Para ver el Codigo Fuente, hay 2 maneras:

En el programa, Barra de menus--->**Ayuda--->Leer codigo fuente**

Con el .DEB, no hacerle doble click, sino **descomprimir el .deb**, 
se crean una carpeta con 2 archivos comprimidos, llamados DATA y CONTROL,
**descomprimir DATA**, hay esta todo el codigo fuente.

:)

---

### Post by mama21mama on 2010-09-16
mira, probé tu aplicación y esta buena.

hace poco quise hacer un cv y como soy vago igual a muchos necesitaba una plantilla y a una colega le pedí su plantilla la modifique con openoffice y listo mi cv. xD

esto hace lo mismo, genera una plantilla en formato para usar en openoffice o abiword, pero vi que con este ultimo se ve mal el cv.


**Critica**
La idea es interesante: me gusto

Lo que deberías poner para que la interfaz sea mas amigable es que al 
botón «click para terminar el curriculum vitae» especificar en la ayuda que llamara al editor de texto. por lo tanto debe haber uno.

por que digo esto, por que estaba esperando como un goludo que me hablara o abra una ventanita y esperando nada, claro es que no tenia el openoffice instalado.

falta de información tal vez, no hay una "ayuda" donde dice que hace cada cosa. perdí como mas de 10 min esperando algo cuando debía tener el openoffice instalado.

la opción de poner al final del documento «creado con software libre» la activo todo piola, pero no veo esa leyenda luego al ver la plantilla.

no se si es mas veloz pedirle a mi amigo mas plantillas o usar el CV Facil 2; seria una buena opcion que tengas mas plantillas entonces si seria mejor que mi colega el que tiene plantillas de cv.

Saludos

---

### Post by alfplayer on 2010-09-16
OpenOffice ahora no está como dependencia del paquete.

---

### Post by juancarlospaco on 2010-09-16
> **alfplayer said:**
> OpenOffice ahora no está como dependencia del paquete.

**+1** Claro.


La nueva version tiene Tooltips, el del boton de terminar el CV dice:
*'Click para abrir el CV Terminado con OpenOffice Writer'*

[IMG]http://img196.imageshack.us/img196/3517/cvf2info.jpg[/IMG] [IMG]http://img185.imageshack.us/img185/6955/cvf2info2.jpg[/IMG]

Yo no obligo a usar writer, el Documento abre con **xdg-open**
:)

---

### Post by mama21mama on 2010-09-16
> Yo no obligo a usar writer, el Documento abre con xdg-open
lo que trate de decir que si quieres que ande limpito aconsejes openoffice, 

por que yo en xubuntu 9.10 no lo tenia por defecto que el xdg-open abra con openoffice lo tenia que abra con abiword.

por lo tanto seria recomendado en un faq o "ayuda" explicar que el xdg-open abra con openoffice por que abiword se vería mal.

---

### Post by juancarlospaco on 2010-11-01
**[SIZE="3"]Version 0.6:[/SIZE]**

[LIST]
[*]Soporte temas GTK+
[*]Soporte nueva Font de Ubuntu
[*]Opcion de setear la Font de la GUI
[*]Chequea la version de Python al iniciar
[*]Chequea la version de TK al iniciar
[*]Chequea si estamos conectados a Internet al iniciar
[*]No permite mas de 1 Instancia
[*]No permite ejecutarlo como root
[*]Widget Calendario tipo Point-and-click para setear la fecha, tambien con campo de texto
[*]Multiple Choice reemplazados con ComboMenus
[*]Soporte para Rueda de Scroll del Raton
[*]Click en el Logo de Ubuntu abre Ubuntu-AR.org
[*]Acerca de Licencia abre un archivo local en lugar de un link de internet
[*]SplashScreen con imagen al azar de 10 paisajes en HDR
[*]SubMenus esconden las Opciones Avanzadas en los menus para que no queden tan largos
[*]Correcciones en el Modo Netbook
[*]Correcciones en el Modo de Accesibilidad
[/LIST]
*Alguna cosa mas que seguro me estoy olvidando...*

[CENTER][IMG]http://img836.imageshack.us/img836/2325/temptb.jpg[/IMG][/CENTER]

```

[CENTER][**http://tecnicoslinux.com.ar/livecd/cvfacil2_0.6_all.deb**]("http://tecnicoslinux.com.ar/livecd/cvfacil2_0.6_all.deb")[/CENTER]

```

:)

---

### Post by mama21mama on 2011-01-14
a la primera en lubuntu 10.10

```
mama@zeuza:~$ /usr/share/cvfacil2/cvfacil2.sh
mkdir: no se puede crear el directorio «/tmp/cvfacil2/»: El archivo ya existe
«/usr/share/cvfacil2/images/splash/imagen10.gif» -> «/tmp/cvfacil2/splashscreen.gif»
 
 Successfully acquired lock: /tmp/cvfacil2.lock...
 
Traceback (most recent call last):
  File "/usr/share/cvfacil2/splashscreentk.py", line 26, in <module>
    root.configure(cursor=('@/home/juan/cvfacil2/ubuntu-ar.xbm', '', 'purple', ''))
  File "/usr/lib/python2.6/lib-tk/Tkinter.py", line 1205, in configure
    return self._configure('configure', cnf, kw)
  File "/usr/lib/python2.6/lib-tk/Tkinter.py", line 1196, in _configure
    self.tk.call(_flatten((self._w, cmd)) + self._options(cnf))
_tkinter.TclError: cleanup reading bitmap file "/home/juan/cvfacil2/ubuntu-ar.xbm"
/usr/share/cvfacil2/cvfacil2.sh: línea 13: /usr/bin/openoffice.org: No existe el fichero o el directorio
 
/usr/share/cvfacil2/cvfacil2.sh: línea 15: /usr/bin/openoffice.org: No existe el fichero o el directorio
 
 &#10132; No PYTHON-PSYCO avaliable&#8252;, this application will run slower... 
 
 TK Version = 8.5.8

 Python version > 2.6.0

 You are normal user... 

 GTK-On-TK Theme Hack:
 I will try to mimic: Clearlooks GTK Theme
 By Parsing the file: /usr/share/themes/Clearlooks/gtk-2.0/gtkrc
 This is not perfect, if you are on KDE install QTCurve... 
Traceback (most recent call last):
  File "/usr/share/cvfacil2/cvfacil2.py", line 1179, in <module>
    context = resolver.resolve("uno:socket,host=localhost,port=2002;urp;StarOffice.ComponentContext")
__main__.NoConnectException: Connector : couldn't connect to socket (Conseguido)
 
directorio borrado: «/tmp/cvfacil2.lock»
mama@zeuza:~$ 

```

---

### Post by juancarlospaco on 2011-01-18
No tenes el OpenOffice completo, que viene a ser como el Motor de la GUI.

---

### Post by mama21mama on 2011-01-18
uso libreoffice no se si habrá mucha diferencias.

---

### Post by juancarlospaco on 2011-01-18
Puede que funcione, puede que no, esta fuera de mi alcance.
*El Developeo de este, que no es perfecto, esta pausado hasta que venga Libre por defecto.*

---

