---
title: "LiveCD Limpia Virus"
date: 2009-04-12
forum: Comunidad
---

### Post by juancarlospaco on 2009-04-12
**[SIZE="6"][COLOR="Sienna"]LiveCD Limpia Virus! *...ideas?*[/COLOR][/SIZE]**

Me encuentro desarrollando un nuevo Sistema Operativo, su objetivo no es usarlo para todos los dias,
su objetivo principal sera** servir de herramienta para limpiar el windows de Virus/Spyware/Malware/etc**,
para eso la PC se iniciara desde el CD, lo que se llama un LiveCD, las caracteristicas principales son:

[LIST]
[*]**LiveCD** *(opcional instalacion, ocupa 1 CD, 669Mb)*
[*]**Completamente en Español **de Argentina
[*]**Kaspersky Antivirus Auto-Actualizado ***(siempre la ultima version, siempre las ultimas Firmas de Virus)*
[*]ClamAV Antivirus Auto-Actualizado, GUI [ClamTK ]("apt:/clamtk")*(siempre la ultima version, siempre las ultimas Firmas de Virus)*
[*]Legal, **Solo OpenSource y Freeware.**
[*]**Carpeta Compartida en 1 Click** por HTTP *(una pagina web muestra el contenido de la carpeta, para hacer backup)*
[*]Recibir archivos desde otros equipos en 1 Click por HTTP *(una web con 2 botones "Examinar" y "Enviar", para Backup)*
[*]Se puede **controlar el equipo remotamente por VNC** sin configurar nada *(1 Click)*
[*]Integracion con **[Google Docs ]("apt:/prism-google-docs")***(leer, enviar, crear, editar, ver Documentos)*
[*]**Posibilidad[ de agregar mas Software]("http://appnr.com")** que no este instalado, a traves de una sencilla pagina Web *(1 Click)*
[*]Te dice si la Memoria RAM esta rota
[*]Te dice si la lectora o el CD estan rotos
[*]Saca Fotos de Pantalla *(Screenshots)* de toda la pantalla, 1 ventana sola, Area Seleccionada, con/sin Puntero de mouse
[*]Opcion Modo Grafico Seguro desde el inicio* (640x480pixeles)*
[*]**Linea de Comandos eliminada**
[*]**Interface grafica tipo XP **
[*]Puntero del mouse, Boton de inicio, Iconos y Bordes de Ventana estilo Vista
[*]Block de Notas
[*]Calculadora
[*]**Firefox 3**
[*]Configuracion Automatica de la Pantalla/Monitor/LCD
[*]Configuracion Automatica de Red *(solo Ethernet, cable de red, [WICD]("apt:/wicd"))*
[*]Iconos al lado del Reloj *(el reloj muestra los Segundos)* para configurar la Pantalla y la Red
[*]NumBlock controla el Mouse.
[*]**Wallpaper Climatico** *(el fondo del escritorio predice el clima, si hay nubes de fondo llovera, si hay sol de fondo habra sol)*
[*]No tiene ningun programa "Peligroso" para los que no tienen muchos conocimientos *(no tiene editor de particiones, etc)*
[*]Funciona en PC, MAC y Maquina Virtual.
[/LIST]

Las ventajas de este Sistema son varias, primero que es Legal, tambien que al ser un LiveCD, 
no existen los problemas que pasan frecuentemente, por ejemplo al pasar un Antivirus de Windows estando en Windows,
el Antivirus no puede borrar un archivo por que esta en uso, o bloqueado, 
o dice permiso denegado *(algunas cosas no se pueden acceder estando Windows corriendo)* ,
asi mismo muchas veces los antivirus logran borrar el archivo maligno, 
pero luego al reiniciar y volver a scannear de nuevo el archivo sigue ahi* (nadie escanea mas de 2 veces seguidas)*,
este sistema al correr desde el CD no usa ningun archivo de Windows, 
lo que te permitira BORRAR definitivamente los virus, scannear TODO el disco sin que diga bloqueado o denegado,
ademas de siempre contar con las Ultimas Firmas de Virus de Kaskersky Labs, y el Antivirus ClamAV *(Updates Diarios para Ambos)*.


[CENTER]
**Screenshots :**

[IMG]http://img152.imageshack.us/img152/7996/tempipb.jpg[/IMG]


[IMG]http://img179.imageshack.us/img179/1975/tempw.jpg[/IMG]


[IMG]http://img261.imageshack.us/img261/1616/temp2h.jpg[/IMG]


[IMG]http://img178.imageshack.us/img178/7938/kasper2.jpg[/IMG]


[IMG]http://img223.imageshack.us/img223/4636/temp3.jpg[/IMG]


[IMG]http://img220.imageshack.us/img220/7216/kasper.jpg[/IMG]

*Si ven 2 punteros de mouse es por que estaba corriendo en una Maquina Virtual *=)
[/CENTER]



Orientado a usuarios muuuuuuuuuuy pero muuuy faltos de conocimientos (en plan de Seduccion "pasate a Linux" ;) ).

Basado en Jaunty, creado con [VM-Builder]("apt:/python-vm-builder") de Ubuntu Server.




:p

---

### Post by guillermolisi on 2009-04-12
Muy buena iniciativa !

Y como para tener una referencia de un producto parecido en cuanto a su fin (limpiar una maquina infectada con viruses), echale una mirada al TRK - Trinity Rescue Kit [http://trinityhome.org/Home/index.php?wpid=1&front_id=12](http://trinityhome.org/Home/index.php?wpid=1&front_id=12) - que te permite correr, en consola y con una interface mas cruda que la que propones, hasta 5 antivirus que se actualizan on line antes de ser corridos.

Me parece que si los que hicieron el TRK pudieron usar cinco AV nada impedidira que los incluyas en tu proyecto.

El TRK lo vengo usando desde hace un año con excelentes resultados en ambitos en produccion, asi que no tengo problemas en apoyar tu proyecto haciendo pruebas para adecuarlo/mejorarlo.

Felicitaciones

---

### Post by juancarlospaco on 2009-04-12
Si, lo conosco, justamente por que no me convence el TRK hice este.
Fuera de la Filosofia y todo lo que es lo ideal, en la Vida Real :

CLI only = No lo usa Nadie.

CLI only = No incentiva al usuario acostumbrado a la GUI Vista a probar Linux.

TRK=CLI / Este LiveCD=no hay CLI Accesible, todo grafico, todo en 1 Click.

Todos reconocen que los 2 mejores Antivirus Pagos son Nod32 y Kaspersky *(Nod32 no esta para Linux)*

No veo la necesidad de tener que Actualizar 5 AV si con 1 bueno ya alcanza.

Capacidad de Backup Facilmente gracias a la Grafica/HTTP (*hice Scripts de Bash para esto)*

Tiene SSH, pero tambien tiene VNC, en la vida real pocos saben usar SSH.

Instala aplicaciones via APPNR.com, usa Google Docs de Ofimatica.

[I]Ademas no creo que entren 5 Antivirus con interface grafica en 600Mb,
si queres hago uno que tenga 10 Antivirus y ocupe 1 DVD, pero creo que con lo que tiene este alcanza.[/I]

---

### Post by Hei Ku on 2009-04-12
Con 1 bueno no alcanza. Necesitas varios.

---

### Post by juancarlospaco on 2009-04-13
[B]    * AVG Antivirus Agregado
    * Download StatusBar Agregado
    * FireFTP Agregado[/B]


Vi mas Antivirus mas pero:
[I]Uno tiene interface grafica, pero en Ruso solamente, descartado.
Otro vence luego de 60 Dias, descartado.
Otro es solo de Linea de comandos, descartado.
No tienen Actualizaciones Diarias, descartados.[/I]

---

### Post by santiagoward2000 on 2009-04-13
Hola!
Está buena la idea. Tiro una idea, a ver si alguien conoce algo. ¿Hay algún antivirus online que ande en Linux? Así te olvidás de ver cuando se actualiza. Vi uno que necesita tener java para correr: [Trend Micro Housecall]("http://housecall.trendmicro.com/"). No sé si alguien conoce alguna otra alternativa.
Saludos!

---

### Post by juancarlospaco on 2009-04-13
> **santiagoward2000 said:**
> Hola!
Está buena la idea. Tiro una idea, a ver si alguien conoce algo. ¿Hay algún antivirus online que ande en Linux? Así te olvidás de ver cuando se actualiza. Vi uno que necesita tener java para correr: [Trend Micro Housecall]("http://housecall.trendmicro.com/"). No sé si alguien conoce alguna otra alternativa.
Saludos!

el Kaspersky que lleva este es el Kaspersky Scanner OnLine adentro de un [Mozilla Prism.]("apt:/prism")
Es OnLine pero el Mozilla Prism te da una sensacion de que es una Aplicacion local, me voy a fijar lo del Trend.
*Por eso es Legal este CD...*

---

### Post by guillermolisi on 2009-04-13
> **Hei Ku said:**
> Con 1 bueno no alcanza. Necesitas varios.
Bueno, pienso lo mismo y de hecho la paractica diaria me ha confirmado esto.

Hubo veces en que el AVG resolvio algunos casos y hubo otras en que lo hizo BitDefender, por ejemplo.

Yendo un poco mas en detalle, el TRK no solo trata de antivirus. Tiene otras herramientas orientadas a trabajar con particiones NTFS fundamentalmente. Esto no lo hace ni mejor ni peor que otras alternativas. Una herramienta para cada necesidad es lo mejor.

---

### Post by juancarlospaco on 2009-04-14
[B]Se agregaron 3 Programas para Identificar Hardware y Drivers *(Hardinfo, Sysinfo, lshw-GTK )*.

Se agrego un Icono para Apagar el Monitor *(sin apagar nada mas)*

Se agrego un Programa Grafico para Correjir Discos/Particiones NTFS *(Zenity+NTFS-3G)*[/B]

---

### Post by sergiom99 on 2009-04-14
muy buena idea, te felicito por el laburo che.

Existe algun removedor de spyware/adware en linux? Asi como el Ad-aware de Wind$, para pasar desde este LiveCD al disco de Win$.

---

### Post by juancarlospaco on 2009-04-15
**[COLOR="Blue"]Quiero expresar publicamente el Agradecimiento a z37a por la Colaboracion con el Proyecto.[/COLOR]**

    * Agregado " **Identificador de Placas PCI** " *(zenity+lspci)*
    * Agregado " **Identificador de CPU** " *(zenity+CPUinfo)*
    * Agregado " **Identificador de Dispocitivos USB** " *(zenity+lsusb)*
    * Agregado " **Temperatura y Caracteristicas del Disco** " *(zenity+HDDtemp+HDparm)*

Gracias, seguimos preparando la ISO *(siempre alguien sale con alguna buena idea para agregar jeje)*

---

### Post by kernelito on 2009-05-19
Es buena idea este proyecto, cuando estaria listo el cd ?

Saludos

---

### Post by z37a on 2009-05-20
Sigo interesado yo tambien en esto, , solo me interesa mas que nada lo de los antivirus desde un live, muchas veces tengo que ir a lugares donde usan windows y no hay forma facil de sacar los virus, solo desde fuera del so se podrian sacar, y no consigo nada grafico y util como este cd!!!!

---

### Post by majatu on 2009-05-20
Danos un adelanto de como va la cosa, que pinta muy bueno tu live cd! ;)

---

### Post by MPx1 on 2009-05-20
Que buena idea! los felicito.. de 10! :D

---

### Post by guidito73 on 2009-05-20
La verdad que está muy grosa la idea, va a ayudarme en un par de cositas... Sigan así!

PD: Para cuándo una beta??? Me ofrezco de tester :D

---

### Post by agel1 on 2009-05-21
spyware doctor es el mejor antispyware, si lo agregas al cd o dvd va a ser mejor que ubcd4win

thanks

---

### Post by majatu on 2009-05-21
> **agel1 said:**
> spyware doctor es el mejor antispyware, si lo agregas al cd o dvd va a ser mejor que ubcd4win

thanks

spyware doctor es de pago...

---

### Post by majatu on 2009-06-01
Ya tienen una ISO como para ir probándolo? me tiene impaciente jaja ;)

Un saludo!

---

### Post by z37a on 2009-06-01
> **majatu said:**
> Ya tienen una ISO como para ir probándolo? me tiene impaciente jaja ;)

Un saludo!

Aca hay otro mas esperando, aunque sea la beta!!! jejejej

---

### Post by Daniel TL on 2009-07-03
Muy buen proyecto! Y me sumo a la "Hinchada": ¿Ya tenés alguna versión usable? Gracias!

---

### Post by caudio on 2009-07-03
Muy buena la iniciativa!!

El avast tiene una version nativa para Linux. yo la uso en mi Ubuntu para escanear los archivos que se bajan de la mula. 

Saludos!

---

### Post by Bytesn+1 on 2009-08-17
Superantispyware o spyboot, son validos como aporte de ideas? cualquier ayuda a sus ordenes. saludos

---

### Post by matute2001 on 2010-01-05
Genial proyecto, me apunto a la lista de beta testers. Es lo que estoy buscando hace tiempo, para limpiar maquinas con Windows. Si logras darle forma a todo lo propuesto, tendrás un cacho de cielo ganado ;)

Un saludo desde Tenerife.

---

### Post by leosr on 2010-01-15
Muy bueno el proyecto! Para cuándo una beta?

Saludos.

---

### Post by cepfpg264 on 2010-04-25
Muy buena iniciativa, y dime para cuando liberas el beta???? seria bueno saberlo... Bendiciones :)

---

### Post by PoNcHo87 on 2010-04-27
A mi me salvo muchas veces el [COLOR=Blue]***[Malwarebytes'  Anti-Malware]("http://www.malwarebytes.org/mbam.php")***[/COLOR] la verdad que si se puede incluir sería genial...[URL="http://www.malwarebytes.org/mbam.php"]
[/URL]

---

### Post by granjero on 2010-04-29
excelente iniciativa.

yo he usado estos en el pasado:

bitdefender: [http://download.bitdefender.com/rescue_cd/](http://download.bitdefender.com/rescue_cd/)

avira live cd: [http://www.free-av.com/en/tools/12/avira_antivir_rescue_system.html](http://www.free-av.com/en/tools/12/avira_antivir_rescue_system.html)

pero me quedo leyendo a ver cuando sale la beta!

salud!

---

### Post by juanuni on 2011-03-23
pues a mi me gustaria saber para cuando sale, dado que conozco de varias pc's infectadas en las cuales me gustaria probar el cd....de antemano felicidades por el proyecto !!

---

### Post by LU7HQW on 2011-12-04
Che, alguna novedad si este proyecto tuvo alguna release? Realmente interesante, y podría ayudar en lo poco que sé.

Si alguien tiene alguna noticia de que haya salido, algún link para descarga, o algo...

Muy buena idea para continuarlo...

Saludos.

---

