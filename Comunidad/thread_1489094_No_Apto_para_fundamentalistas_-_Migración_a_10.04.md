---
title: "No Apto para fundamentalistas - Migración a 10.04"
date: 2010-05-20
forum: Comunidad
---

### Post by hectorivand on 2010-05-20
Estimados, me presento. espero que anden todos bien y les paso a comentar mi caso.

Desde hace 10 años que vengo trabajando con diferentes distribuciones de Linux, arranque en el 2000 con Corel, una distro que nunca pude hacer funcionar, pase por redhat, suse, ubuntu (versiones más viejas) Opensuse, mandriva, etc. Si bien las usaba en los trabajos donde requeriamos el uso de diferentes servidores, nunca me meti de lleno me segui especializando en Microsoft, de hecho, soy un ex empleado de la filial local y soy especialista en infraestructura y comunicaciones de soluciones de la misma compañia, aunque harto de la vida corporativa, me abri un local de computación en mi pueblo y les digo que no gano fortunas pero vivo feliz.

Actualmente estoy con mucho tiempo libre y he intentado trabajar con Ubuntu varias veces, lo he instalado en varias maquinas pero nunca tuve un resultado bueno, algunos problemas de Hardware, otro porque no llegaba a replicar mi trabajo que actualmente tengo con Windows 7 (Licencia Original) en Ubuntu o en otras distribuciones.

Una vez introducido y poniendolos en contexto, les cuento que tengo ganas de instalar Ubuntu de forma completa en la notebook de todos los días, sinceramente lo que más me preocupa es no poder aprovechar todo el potencial del hardware es por eso que le pregunto lo siguiente: Como ven Ubuntu 10.04 x64 en la siguiente maquina? Si bien estuve viendo documentación, son muchassss las cosas que no me quedan claras y algo que me preocupa de versiones anteriores de Ubuntu es la gestión de la energia, particularmente probe la versión 9.04 y era muy mala para que se den una idea con el procesador en minimo una bateria que con Windows 7 me dura 2:30 en Ubuntu me duraba 1:00. Sinceramente es algo que me preocupa.: Pero bueno, en definitiva como ven este hardware.:

Notebook Toshiba L305D-SP6981A
Video: ATI HD300
Disco de 250GB
2GB de RAM
Webcam y demas b*******s.

Perdón la lata, pero realmente me gustaria intentar replicar mi día a día de Windows en Ubuntu y también me gustaria conocer a la comunidad.

Saludos y muchas gracias por leer :)

Nacho Van Droogenbroeck

---

### Post by Tosh78 on 2010-05-20
Hola! Con ese hardware no creo que vayas a tener problemas. Es mas, te diria que te sobra. Lo mejor que podes hacer para estar bien seguro es probar el livecd (lo podes probar desde un pendrive tambien) y probar como te funciona el hardware. Me llama la atencion lo de la gestion de energia, ya que en mi caso es totalmente al reves (tambien tengo notebook) y me la gestiona mejor Ubuntu que wingarch.

---

### Post by guillermolisi on 2010-05-20
Cuando la administracion de energia por parte de Linux es mala lo mas probable es que existan problemas con el reconocimiento de ACPI entre el kernel y el BIOS.

Personalmente no instalaria Ubuntu 64 bits en una maquina que solo tiene 2Gb RAM. El consumo de memoria adicional que acompaña a los sistemas de 64 bits no justifica lo que puedas ganar por otro lado (si es que hay alguna ganancia marginal). Ahora si la llevas a 4Gb RAM, eso es otra cosa.

---

### Post by hectorivand on 2010-05-21
> **Tosh78 said:**
> Hola! Con ese hardware no creo que vayas a tener problemas. Es mas, te diria que te sobra. Lo mejor que podes hacer para estar bien seguro es probar el livecd (lo podes probar desde un pendrive tambien) y probar como te funciona el hardware. Me llama la atencion lo de la gestion de energia, ya que en mi caso es totalmente al reves (tambien tengo notebook) y me la gestiona mejor Ubuntu que wingarch.

Estimado, con el hardware y la potencia ya se que no voy a tener problemas, el comentario era por el miedo de no poder explotar la capacidad de mi hardware. LiveCD no me sirve para medir un real rendimiento de como se vería Ubuntu en mi equipo, uso la live cd para rescatar info de particiones Win dañadas.

Con respecto a la gestión de energia, es tal como te lo cuento y lo he probado ya en mi toshiba como en Compaq y las chinas Olivetti, pero ya te digo, fue la versión 9.04, veremos que cambios hay en 10.04. 

¿Por qué Wingarch? dejemos el fundamentalismo de lado, por favor.

Gracias por comentar.

---

### Post by hectorivand on 2010-05-21
> **guillermolisi said:**
> Cuando la administracion de energia por parte de Linux es mala lo mas probable es que existan problemas con el reconocimiento de ACPI entre el kernel y el BIOS.

Personalmente no instalaria Ubuntu 64 bits en una maquina que solo tiene 2Gb RAM. El consumo de memoria adicional que acompaña a los sistemas de 64 bits no justifica lo que puedas ganar por otro lado (si es que hay alguna ganancia marginal). Ahora si la llevas a 4Gb RAM, eso es otra cosa.

Guillermo, gracias por comentar, te cuento que si bien esto es parte de un "experimento" si logro replicar mi día a día, es muy probable que me quede con Ubuntu y la instalación de 2GB adicionales es inminente en los proximos meses, con lo cual instalaría la versión x64 solamente por el hecho de no tener que repetir la instalación en unos meses.

Aunque, tomo en cuenta tu comentario.

Saludos
Nacho

---

### Post by guillermolisi on 2010-05-21
Estuve buscando las especificaciones de esa maquina y no encontre nada que explicitamente diga que es un procesador de 64 bits. Un AthlonX2 doble nucleo para notebooks es 64 bits ?

Si no lo es, vas a tener que usar Ubuntu 32 con kernel PAE si queres llegar a utilizar los 4Gb. Esta bueno eso pero no es lo mismo que 64 bits posta dese el punto de vista del rendimiento.

---

### Post by hectorivand on 2010-05-21
> **guillermolisi said:**
> Estuve buscando las especificaciones de esa maquina y no encontre nada que explicitamente diga que es un procesador de 64 bits. Un AthlonX2 doble nucleo para notebooks es 64 bits ?

Si no lo es, vas a tener que usar Ubuntu 32 con kernel PAE si queres llegar a utilizar los 4Gb. Esta bueno eso pero no es lo mismo que 64 bits posta dese el punto de vista del rendimiento.

Guillermo, si, el procesador que tiene mi notebook es Athlon x2 64 bits es una toshiba L305D.

La especificación del equipo: 

[http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/modelContent.jsp?ct=SB&os=&category=&moid=2346328&rpn=PSLC8U&modelFilter=L305D-SP6981A&selCategory=3&selFamily=1073768663](http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/modelContent.jsp?ct=SB&os=&category=&moid=2346328&rpn=PSLC8U&modelFilter=L305D-SP6981A&selCategory=3&selFamily=1073768663)

Te dejo la info del micro, donde indica su arquitectura de 64.

[http://www.cpu-world.com/CPUs/K8/AMD-Athlon%2064%20X2%20QL-65%20-%20AMQL65DAM22GG.html](http://www.cpu-world.com/CPUs/K8/AMD-Athlon%2064%20X2%20QL-65%20-%20AMQL65DAM22GG.html)

¿Alguna otra duda?, seré una novato de toda la vida con el sistema del pinguino, pero creame que no dejo nada al azar y conozco bastante, no solo hablo por hablar! :)

Saludos
Nacho

---

### Post by juancarlospaco on 2010-05-21
*LessWatts.org*

---

### Post by hectorivand on 2010-05-21
> **juancarlospaco said:**
> *LessWatts.org*

Excelente, muchas gracias! voy a revisarlo.

Ya estoy en Ubuntu 10.04. Precioso, terrible el salto desde 9.04.

---

### Post by tychocity on 2010-05-21
yo tengo una notebook vieja ya y la verdad nunca tuve problemas y la bateria siempre me duro igual o mas que en windows.

---

### Post by hectorivand on 2010-05-21
> **tychocity said:**
> yo tengo una notebook vieja ya y la verdad nunca tuve problemas y la bateria siempre me duro igual o mas que en windows.

Hola, gracias por comentar. Que notebook vieja? Marca?

Saludos
Nacho

---

### Post by guillermolisi on 2010-05-21
Hector

Como habras visto, en el foro tratamos de que los hilos mantengan cierta consistencia tematica y, ademas, que resulten mas o menos claros para clasificarlos segun el origen del problema o cuestion planteada.

Este hilo lo movi a Comunidad porque me parecio algo que daba para conversarlo cerveza o cafe de por medio dada la forma en que venia planteado.

Ahora le estas dando un giro que lo desvirtua, con consultas mas especificas y relacionadas con soporte que con asesoramiento, asi que te pido que las plantees en thread aparte ya que asi seran mas faciles de ubicar por aquellos que pasen por tu misma experiencia.

Gracias.

Edit: los posts sobre consumo de RAM estan [aqui]("http://ubuntuforums.org/showthread.php?t=1489980").

---

### Post by madbyte on 2010-06-18
Sorry por reflotar un post viejo pero queria dejar mis impresiones al respecto.

Yo me inicie en Ubuntu el año pasado con la 9.10 64 bits y quede muy  impresionado, Windows me tiene ya las 'quetejedi' por el piso, es un  sistema que se va 'degradando' con el tiempo, y siempre quice probar  algo alternativo y en Ubuntu veo el futuro. Pero lamentablemente no me  fue bien con el hardware, tengo unos f****ing problemas que desde mi  punto de vista son criticos y hacen que no me pueda desligar  completamente de Windows. Como ingeniero electronico no acepto que  Ubuntu no reconozca que tengo un CPU el cual puede ser escalable en  frecuencia tal cual lo hacen XP y Seven, si busco una opcion por lo  menos tiene que ser capaz de funcionar igual o mejor de lo que tenia  antes. Hoy sin internet no haces nada, y por ahi pasan mis otros 2  problemas, primero no entiendo porque hay conflictos con el IPV6 porque  tengo que deshabilitarlo para poder navegar ¿Porque no tengo que hacer  lo mismo en Seven? eso es otra cosa que me hace ruido...  y para  terminar, mi WiFi en Ubuntu anda mal y hay dias que navego bien y otros  en que casi no se puede usar y termino haciendo en Windows lo que queria  hacer en Ubuntu. Y lamentablemente la 10.04 termino replicando  exactamente los mismos problemas. Mi filosofia es, desde el punto de  vista del hardware, si Windows lo hace solo y sin problemas, quiero que  por lo menos Ubuntu tambien lo haga. No creo que solucione lo de la  frecuencia del CPU, siendo ya que mi placa  tiene mas de 3 años, pero lo demas es salvable, y se que hay soluciones  alternativas para lo del WiFi, aunque le reste puntos por tener que  meter mano. Hoy uso Ubuntu 'pelado', como vino, sin instalarle nada adicional, salvo  las actualizaciones, estoy en un proceso de aprendizaje, prueba y  error, sigo usando Windows para mi trabajo y tareas cotidianas pero sigo creyendo que Ubuntu puede llegar a ser mi sistema operativo base  en el futuro.

Saludos

---

