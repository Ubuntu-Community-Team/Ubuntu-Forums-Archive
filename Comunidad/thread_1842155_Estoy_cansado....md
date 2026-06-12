---
title: "Estoy cansado..."
date: 2011-09-10
forum: Comunidad
---

### Post by marcelo_bur on 2011-09-10
Hola. Desde que comencé a usar Ubuntu me gustó mucho el sistema operativo, use la versión 8.04 durante mucho tiempo sin problemas, e incluso aún tengo esa versión en otra pc mas vieja que esta y anda al pelo.
Pero desde que me pase a 10.04 solo he tenido problemas.
Primero porque lo instalaba "dentro de Windows". Me dijeron que no era recomendable y lo instalé en una partición aparte del disco.
Salvo algunos problemas que se solucionaron, anduvo bien por unos meses y estaba muy contento, hasta hace una media hora atrás.
Lo primero que noté, fuera de lo común, fue que una carpeta común y silvestre aparecía ahora con el candado y los permisos se habían configurado, solos, como de solo lectura. No le dí mucha importancia, reconfiguré los permisos  e intenté abrir un archivo PDF que estaba dentro de esa carpeta. El visor de documentos no respondió, tampoco me respondio OpenOffice, que había estado usando hasta pocos minutos antes con hojas de cálculo.
Alguna que otra vez esto me había sucedido y se solucionaba reiniciando la máquina. Fue lo que hice, pero ya no se inicia el sistema operativo, muestra el grub, pero cuando tiene que arrancar solo aparecen una cantiddad de lineas de código que no comprendo. Dice algo de archivos que no se encuentran, y montones de cosas más.
Supongo que puedo reinstalar, pero eso no está bien. Finalmente noto que esta partición que tengo con windows xp trucho ha funcionado bien desde el día que mandé armar el cpu.
Hoy bajo una actualizacion de seguridad, un par de archivos, no se si tendrá algo que ver, pero tampoco es el caso.
Me gustaría saber si a alguien más le ha ocurrido que Ubuntu 10.04 le haya dado tantos problemas.
Por el momento creo que retornaré a XP, lo cual me pone mal, pero peor me pone instalar de nuevo Ubuntu 10.04 con miedo a que en cualquier momento me deje de nuevo de a pie y con importantes perdidas de información, las cuales por suerte no son tan graves ya que desde mis anteriores problemas opté por llevar un respaldo en un pendrive y a no borrar los e-mails de mi servidor.
Agradeceré cualquier comentario sobre este problema.
Saludos

---

### Post by juancarlospaco on 2011-09-10
Yo probaria chequear el estado del disco, con la herramienta de discos,
y tambien escannear la RAM, con Memtest, aunque le desconfio mas al disco,
si nadie mas que vos mete mano en la PC, y no tubiste cortes subitos de energia,
me parece MUY raro que se desaparescan cosas asi por que si.

---

### Post by guillermolisi on 2011-09-11
Coincido con las apreciaciones de Juan Carlos.

---

### Post by marcelo_bur on 2011-09-11
Hola. Gracias por las respuestas. 
Nadie mete mano en mi pc. A veces dejo que mi nieto use un programa para dibujar especial para chicos, pero aún en ese caso lo hace desde un usuario aparte, sin ningún privilegio.
Hemos tenido cortes de energia últimamente, pero no justamente en los últimos dias, y mi maquina tiene un protector bastante bueno para esos casos.
Todo se vino abajo de un momento a otro, haciendo uso normal de la pc, sin instalar nada, excepto la actualización de seguridad que me marco el Gestor de Actualizaciones.
Cuando me dicen que revise el disco supongo que se refieren a que lo haga con las herramientas de Windows, ya que al no arrancar Ubuntu no tengo idea de como hacerlo.
Hoy apenas me levanté volvi a intentar iniciar Ubuntu, esperando que todo hubiese sido solo un mal sueño, pero no.
Bue, ya veremos. Luego voy a copiar todo lo que aparece escrito en la pantalla y lo voy a publicar, a ver si eso les dice algo a ustedes que saben mucho de esto.
Saludos

---

### Post by rojojuan on 2011-09-11
Estoy usando la 10.04 desde que salió y nunca un problema.Espero que puedas solucionar los inconvenientes.

---

### Post by marcelo_bur on 2011-09-11
> **rojojuan said:**
> Estoy usando la 10.04 desde que salió y nunca un problema.Espero que puedas solucionar los inconvenientes.

Se que el SO es bueno, pero no he tenido suerte. Tal vez se deba a un problema de la máquina, no se. Pero el caso es que XP sigue fiel, con sus problemas de virus y todo eso. Y tal vez también se deba a que casi no lo he utilizado.
Estoy buscando en Google si existe alguna manera de reparar el daño, ya veremos. Lo próximo que hare es arrancar con un livecd, a ver si al menos consigo rescatar datos.
Saludos

---

### Post by guillermolisi on 2011-09-11
> **marcelo_bur said:**
> Hola. Gracias por las respuestas. 
Nadie mete mano en mi pc. A veces dejo que mi nieto use un programa para dibujar especial para chicos, pero aún en ese caso lo hace desde un usuario aparte, sin ningún privilegio.
Hemos tenido cortes de energia últimamente, pero no justamente en los últimos dias, y mi maquina tiene un protector bastante bueno para esos casos.
Todo se vino abajo de un momento a otro, haciendo uso normal de la pc, sin instalar nada, excepto la actualización de seguridad que me marco el Gestor de Actualizaciones.
Cuando me dicen que revise el disco supongo que se refieren a que lo haga con las herramientas de Windows, ya que al no arrancar Ubuntu no tengo idea de como hacerlo.
Hoy apenas me levanté volvi a intentar iniciar Ubuntu, esperando que todo hubiese sido solo un mal sueño, pero no.
Bue, ya veremos. Luego voy a copiar todo lo que aparece escrito en la pantalla y lo voy a publicar, a ver si eso les dice algo a ustedes que saben mucho de esto.
Saludos
No hace falta que "alguien" meta mano en el disco. Alcanza con que el disco se degrade, cosa que le puede ocurrir a cualquiera ya sea por temas termicos, fallas de fabrica que se hacen evidentes con el tiempo, etc.

Tampoco es necesario utilizar herramientas basadas en Windows. Hay muchas y mejores basadas en Linux que realizan un excelente trabajo, y que te permiten iniciar la maquina desde un CD o un pendrive. De hecho muchas veces los analisis de superficie, por ejemplo, realizados bajo Windows no detectan fallas que si se manifiestan con equivalentes en Linux.

---

### Post by gmunioz on 2011-09-11
Hola Marcelo:
Sumimasen, por la intromisión.
Estoy en Adrogué y los cortes de luz estimo son tan frecuentes como en Burzaco, hasta la salida de ext4, siempre usé reiserfs como sistema de archivos y soportó perfectamente todos los cortes, no así ext3. Ext4 lo uso desde que salió sin ningun problema.
En mi oficina, tengo 12 máquinas funcionando con distintas distribuciones Gnu/Linux (Debian, Ubuntu, Mint Debian) manejadas por profesionales expertos en sus temas (son peritos oficiales) pero completamente ignorantes de lo que es una computadora y naturalmente una distribución Gnu/Linux que frecuentemente apagan sus computadoras desenchufando el cable power y salvo en mi caso particular que luego de 25 días un disco dejó de funcionar, jamás tuvimos problemas con los sistemas de archivos, ext4 y resiserfs. Por el contrario el resto de los 45 integrantes, que usan Windows XP, Vista y Seven aparte de los diarios problemas de virus que inutilizan sus sistemas pierden archivos a montones o requieren reinstalaciones del sistema con particiones ilegibles.
No tengo nietos, tengo nietas, entre ellas una de 3 años y otra de 9 años, cuando me visitan, frecuentemente, utilizan mi computadora desde el usuario principal sin jamás haber sufrido contratiempo alguno, salvo los consabidos cambios de configuraciones.
Conclusión: personalmente activaria el smart en el setup para verificar si el disco no esta feneciendo, para el caso de cambios de voltaje en el sistema o errores de memoria utilizaria desde un live-cd las herramientas de disco de Gnu/Linux dado que Microsoft ignora por completo nuestros sistemas de archivos.
Suerte en la recuperación de datos.

---

### Post by guillermolisi on 2011-09-11
> **gmunioz said:**
> 
Conclusión: personalmente activaria el smart en el setup para verificar si el disco no esta feneciendo, para el caso de cambios de voltaje en el sistema o errores de memoria utilizaria desde un live-cd las herramientas de disco de Gnu/Linux dado que Microsoft ignora por completo nuestros sistemas de archivos.
Suerte en la recuperación de datos.
+1 a instalar y utilizar smartmontools. Recomendacion no solo para Marcelo sino para todo aquel que quiera prevenir problemas de discos rigidos y no enterarse de los mismos cuando ya es tarde.

---

### Post by madjr on 2011-09-11
para mi ha sido lo contrario, en xp he perdido archivos (y de los cuales nunca pude rescatar).

Es mas ubuntu ha podido semi-rescatar compus viejas en las cuales XP solo mostraba pantalla azul despues de unos minutos. Eso demuestra que linux es mucho mas robusto.

Pero el que lo haya semi-rescatado y el funcionamiento mejore para alargar la vida de la maquina, no significa que los problemas del hardware desaparescan milagrosamente.

Como todos han mencionado, el hardware se degrada y ubuntu no se descompone por si solo al menos que algo haya pasado.

y tampoco es necesario actualizarlo constantemente. Una vez que funciona seguira igual por todo el tiempo que desees

---

### Post by juancarlospaco on 2011-09-11
Pregunto, Sabes como hacer lo que mencione...?

---

### Post by marcelo_bur on 2011-09-11
> **juancarlospaco said:**
> Pregunto, Sabes como hacer lo que mencione...?


Hola.
Realmente no, al menos no se como verificar el estado del disco si no puedo arrancar Ubuntu. Tengo ideas de como usar fsck desde una consola, pero no es el caso...
En este momento estoy usando un llivecd buscando rescatar datos y ver que herramientas existen.
La recuperaci'on de datos fue un fracaso, cuando trato de montar la particion donde esta, o estaba, ubuntu, me sale un mensaje de error que dice que no se puede montar.
Abr'i un par de aplicaciones, pero como en verdad no se usarlas muy bien, prefer'i no hacer nada, a ver si tambi'en hago bolsa XP.
Ahora voy a dejar un par de screenshots que tom'e de las aplicaciones GPARTED y DISK UTILITY

---

### Post by marcelo_bur on 2011-09-11
Ahora, repentinamente, me salio este mensaje de error, aunque ya no estaba intentando montar la unidad 

DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

---

### Post by marcelo_bur on 2011-09-11
Y estas son las capturas de pantalla..  

[http://www.ruta000.com.ar/uploads/images/screenshot.png](http://www.ruta000.com.ar/uploads/images/screenshot.png)

[http://www.ruta000.com.ar/uploads/images/screenshot1.png](http://www.ruta000.com.ar/uploads/images/screenshot1.png)

---

### Post by madjr on 2011-09-11
es la marca del disco **Western Digital**?

he tenido 3 de esos y todos han muerto o se han degradado antes de tiempo, ya nunca mas uso de esas **basuras**.

y segun el error que veo, parece que el disco no esta mandando ninguna comunicacion al sistema. Aunque no significa que no sea posible recuperar los datos de otras formas.

tambien seria bueno que checkiaras en el **bios** de la pc. Y si lo soporta y tiene la opcion de verificacion de disco **SMART**, activala. Es muy dificil diagnosticar el disco sin esta opcion. ya todos los discos modernos deben tenerla.

---

### Post by madjr on 2011-09-11
> **marcelo_bur said:**
> Y estas son las capturas de pantalla..  

[http://www.ruta000.com.ar/uploads/images/screenshot.png](http://www.ruta000.com.ar/uploads/images/screenshot.png)


hm en esta imagen se ve la opcion de "**check filesystem**".


es una herramienta para verificar el disco. prueba a ver

---

### Post by juancarlospaco on 2011-09-11
*Veo un Disco nuevo en tu futuro . . .*

---

### Post by guillermolisi on 2011-09-11
> **marcelo_bur said:**
> Y estas son las capturas de pantalla..  

[http://www.ruta000.com.ar/uploads/images/screenshot.png](http://www.ruta000.com.ar/uploads/images/screenshot.png)

[http://www.ruta000.com.ar/uploads/images/screenshot1.png](http://www.ruta000.com.ar/uploads/images/screenshot1.png)

Marcelo

La particion que hay que revisar es /dev/sda2 con la opcion "check filesystem".

No estaria nada mal iniciar con XP y hacer lo propio con la particion NTFS (que en Gparted se ve como /dev/sda1).

---

### Post by marcelo_bur on 2011-09-12
Hola. 
Estoy realmente agradecido por toda la atención brindada a este tema.

Creo que lo dicho por Juan Carlos Paco es profético, tengo que pensar en un nuevo disco.

En cuanto a lo expresado por Madjr, no recuedo la marca, hace más de dos años que mandé armar la máquina, pero por la informacion que recogio el programa y que se ve en la captura, más una rápida busqueda en google, casi no hay duda de que asi es. Tambien voy a verificar lo de la BIOS-

A Guillermo, ya revise la partición NTFS desde XP y no me tiró ningún error. En cuanto a usar "check filesystem" para intentar reparar sda2 no se si será posible. Si prestán atención a la imágen veras que en esa partición se ve como el programa intenta cargar la información de ese sector, pero no lo logra, espere un buen rato y no pasó nada.

Por si las moscas dejo otras imágenes, en este caso tomadas con mi cámara del monitor, ya que es bastante engorroso copiar todo. Se trata de lo que queda visible cuando quiero abrir Ubuntu, aparecen otras cosas antes, pero es imposible verlas, al menos yo no lo logro. Si algo de estas imágenes les parece importante pero no se ve con claridad en la imagen, me avisan y lo transcribo.

[http://www.ruta000.com.ar/uploads/images/dsc07137.jpg](http://www.ruta000.com.ar/uploads/images/dsc07137.jpg)
[http://www.ruta000.com.ar/uploads/images/dsc07139.jpg](http://www.ruta000.com.ar/uploads/images/dsc07139.jpg)
[http://www.ruta000.com.ar/uploads/images/dsc07140.jpg](http://www.ruta000.com.ar/uploads/images/dsc07140.jpg)

Por el momento no estoy usando la pc todo el día, como cuando usaba Ubuntu. Luego de dos años largos de no pensar en virus y cosas por el estilo, me siento mal e intranquilo usando windows, incluso he perdido la practica, extraño los escritorios separados y muchas otras cosas.

Salvo que mediante algo que ustedes me puedan aportar pueda salvar la instalación actual, creo que seguiré usando XP hasta que el disco reviente del todo. Guardaré mis datos en soportes externos, incluso tengo Terabox, que espero no me falle.

Y para cuando reviente el disco les agradecería me aconsejen una buena marca para el próximo, esperando no tener más problemas y, por las dudas, voy a tomar nota del comentario de Guillermo: **"+1 a instalar y utilizar smartmontools. Recomendacion no solo para  Marcelo sino para todo aquel que quiera prevenir problemas de discos  rigidos y no enterarse de los mismos cuando ya es tarde"** Que todavía no se lo que es, pero ya lo averiguaré

Saludos y nuevamente, gracias.

---

### Post by madjr on 2011-09-12
si, es un poco lamentable Marcelo lo de tu disco.

quisas exista forma de alargarle un poco la vida, por ejemplo lo puedes usar como disco secundario o externo donde puedas guardar cosas no tan importantes.

ya como disco principal no te va a durar mucho, y XP no detecta estos problemas (nunca me pudo ayudar a salvar los mios...), solo la capacidad **SMART** lo puede hacer y es muy importante que tu proximo disco cuento con eso.

En cuanto a marcas los Seagate, Hitachi, etc. son buenos. Nunca me han dado problemas. Es mas creo que la mayoria de las marcas duran mas tiempo que los Western digital... (lo cual no se si es algo intencional o que... o quisas los ultimos discos ya no sean asi, pero no me arriesgaria en comprar otro!!.... :o)

sea cual sea pregunta por o verifica la capacidad SMART.

Mucha suerte Marcelo y ya sabes que aqui estamos para cualquier otra cosa que necesites :guitar:

---

### Post by juancarlospaco on 2011-09-12
**Target filesystem doesnt have /sbin/init**

Dice en la foto de pantalla, eso es grave...

---

### Post by madjr on 2011-09-12
> **juancarlospaco said:**
> **Target filesystem doesnt have /sbin/init**

Dice en la foto de pantalla, eso es grave...

si creo que ya esa particion esta perdida, quisas todavia se pueda formatear y usar como disco secundario/externo

---

### Post by juancarlospaco on 2011-09-12
No recomiendo usar un disco defectuoso, ni de secundario ni de externo (hoy dia no sale caro nuevo),
en algunos casos puede agregar lentitud al sistema por el Delay de I/O y por el tiempo de Spin Up.

---

### Post by guillermolisi on 2011-09-12
Yo tampoco recomiendo usar un disco que se ha degradado o esta en pleno proceso.

smartmontools es un paquete que esta en los repos que brinda mucha valiosa informacion relativa al disco, entre la que se encuentra la cantidad de fallas operativas del disco (lectura, escritura, spin-up, etc.) y, si el disco esta preparado, tambien la temperatura de la unidad.

Se podria perfeccionar instalando tambien hddtemp y Conky o similar y tenes toda la informacion necesaria a la vista en el escritorio.
Sino, consultas simples y periodicas via consola/terminal te brindan algo equivalente (pero no tan vistoso).

---

### Post by marcelo_bur on 2011-09-12
Hola.

Definitivamente voy a esperar que reviente el disco usando XP y entretanto voy a ver precios y comprar otro de mejor calidad, con las especificaciones que me han recomendado.
Y este pasará definitivamente al olvido.

En verdad nunca se me ocurrió que podría ser un problema del disco, es bantante nuevo y tengo otros, mucho más viejos, que aún funcionan y que no utilizo simplemente porque son chicos, los nuevos programas y archivos necesitan de mucho espacio.
**Menos mal que le pedí al que me armó el CPU que me pusiese hardware de primera!!!!!** Imaginense si le hubiera dicho que baje los costos....

Muchas gracias a todos, creo que ya quedó claro cual es el problema y cual la solución.
Saludos

---

### Post by alfplayer on 2011-09-12
Tengo las mejores opiniones de Western Digital.

---

### Post by guillermolisi on 2011-09-12
> **alfplayer said:**
> Tengo las mejores opiniones de Western Digital.

Yo tambien, es mas los prefiero antes que otras marcas (de hecho hay alguna vinculacion entre Seagate e Hitachi).

Lo que hay que considerar es que en Argentina hay mucho material "refurbished", reacondicionado y hasta de segunda clase para todas las marcas. Pasa con los discos y hasta con los equipos electronicos del tipo "consumer". No se salva nada.

Y si no me creen, consulten sitios como BestBuy y veran la cantidad de equipamiento reacondicionado que venden, de primera marca y con garantia.

Aqui es donde la seriedad del proveedor juega un papel primordial (y nuestro criterio tambien, o no les parece raro que un mismo disco tenga 25% aprox. de diferencia de precio final entre una oferta y otra ?)

---

### Post by alfplayer on 2011-09-12
> **guillermolisi said:**
> Aqui es donde la seriedad del proveedor juega un papel primordial (y nuestro criterio tambien, o no les parece raro que un mismo disco tenga 25% aprox. de diferencia de precio final entre una oferta y otra ?)

Esto podría deberse también al "nivel de legalidad" del vendedor.

---

### Post by marcelo_bur on 2011-09-12
Bueno, los ultimos mensajes me han confundido un poco con respecto a que disco comprar y, por otra parte, han restaurado mi confianza en la persona que usualmente se ocupa de mis maquinas.

Tal vez haya sido mala suerte, o los muchos cortes de luz, que en muchas ocasiones se cortaba y retornaba inmediatamente, y se volvia a cortar, sin darte tiempo a nada, y tal vez el equipo de protección no dio a basto.

Lo principal, creo, es que la diferencia de opinión respecto a esta marca de discos no cambie en nada lo que ya aparentemente había quedado claro en cuanto a la causa del problema (disco dañado) y a su solución (comprar uno nuevo)....

Saludos

---

### Post by madjr on 2011-09-12
> **marcelo_bur said:**
> Bueno, los ultimos mensajes me han confundido un poco con respecto a que disco comprar y, por otra parte, han restaurado mi confianza en la persona que usualmente se ocupa de mis maquinas.

Tal vez haya sido mala suerte, o los muchos cortes de luz, que en muchas ocasiones se cortaba y retornaba inmediatamente, y se volvia a cortar, sin darte tiempo a nada, y tal vez el equipo de protección no dio a basto.

Lo principal, creo, es que la diferencia de opinión respecto a esta marca de discos no cambie en nada lo que ya aparentemente había quedado claro en cuanto a la causa del problema (disco dañado) y a su solución (comprar uno nuevo)....

Saludos

bueno los cortes si que son malos para los discos.

y ya como habia dicho antes compra solo los que soporten SMART

---

### Post by marcelo_bur on 2011-09-13
Hola. Resulta que este disco soporta SMART e incluso está habilitado, como se ve en esta captura de pantalla:

[http://www.ruta000.com.ar/uploads/images/dsc07141b.jpg](http://www.ruta000.com.ar/uploads/images/dsc07141b.jpg)

La verdad es que desde hace un tiempo me están pasando todas, tengo una racha de mala suerte, o lo que sea, terrible. Y no solo con mi máquina, lamentablemente.
Saludos y gracias.

---

### Post by alfplayer on 2011-09-13
Hace muchos años todos tienen SMART.

---

### Post by guillermolisi on 2011-09-13
> **marcelo_bur said:**
> Hola. Resulta que este disco soporta SMART e incluso está habilitado, como se ve en esta captura de pantalla:

[http://www.ruta000.com.ar/uploads/images/dsc07141b.jpg](http://www.ruta000.com.ar/uploads/images/dsc07141b.jpg)

La verdad es que desde hace un tiempo me están pasando todas, tengo una racha de mala suerte, o lo que sea, terrible. Y no solo con mi máquina, lamentablemente.
Saludos y gracias.
Una riestra de ajo, cintas rojas y alguna estampita de un santo para complementar no matan gatitos y tal vez corte la mala racha. :)

Para mi que te pasa todo eso que contas porque seguis usando Windows :P

---

### Post by madjr on 2011-09-13
> **marcelo_bur said:**
> Hola. Resulta que este disco soporta SMART e incluso está habilitado, como se ve en esta captura de pantalla:

[http://www.ruta000.com.ar/uploads/images/dsc07141b.jpg](http://www.ruta000.com.ar/uploads/images/dsc07141b.jpg)

La verdad es que desde hace un tiempo me están pasando todas, tengo una racha de mala suerte, o lo que sea, terrible. Y no solo con mi máquina, lamentablemente.
Saludos y gracias.

si ya se me hacia raro que no lo soportase.

quisas podrias probar formatear la particion que no funciona a ver si se le puede dar un diagnostico con la herramienta de disco de el live-cd de ubuntu. Digo, solo si es posible, sino esta bien.

y con los cortes de enegia te aconsejo una unidad UPS (si no tienes una).

---

### Post by marcelo_bur on 2011-09-13
> **guillermolisi said:**
> Una riestra de ajo, cintas rojas y alguna estampita de un santo para complementar no matan gatitos y tal vez corte la mala racha. :)

Para mi que te pasa todo eso que contas porque seguis usando Windows :P


Con lo primero ya vengo probando, pero nada...

Y Windows, si, está en una partición de mi disco, y ahora lo estoy usando, pero usualmente no lo hago. Lo he conservado casi exclusivamene para scanear, lo cual es importante para mi. XSanner es muy lento y suele colgarse.

Saludos

---

### Post by marcelo_bur on 2011-09-13
> **madjr said:**
> si ya se me hacia raro que no lo soportase.

quisas podrias probar formatear la particion que no funciona a ver si se le puede dar un diagnostico con la herramienta de disco de el live-cd de ubuntu. Digo, solo si es posible, sino esta bien.

y con los cortes de enegia te aconsejo una unidad UPS (si no tienes una).

Hola. Conseguí analizar el disco desde el live cd, pero tan  solo me da un mensaje que dice, no recurdo las palabras exactas, que la partición NO esta bien, pero de repararla ni vistas. Tampoco pude montarla, para intentar agregar el archivo faltante. Supongo que en cualquier momento, apenas se me pase el mal humor, voy a formatear la partición y reinstalar. Ya veremos.

Lo del UPS lo tenía pensado, pero muchas veces la máquina queda sola funcionando, quizás deba cambiar esa costumbre. Lo que si tiene es un estabilizador de tensión bastante bueno.

Saludos.

---

### Post by alfplayer on 2011-09-13
> **marcelo_bur said:**
> Y Windows, si, está en una partición de mi disco, y ahora lo estoy usando, pero usualmente no lo hago. Lo he conservado casi exclusivamene para scanear, lo cual es importante para mi. XSanner es muy lento y suele colgarse.

Querés decir xsane? Hay otro que se llama iscan que podés probar.

---

### Post by madjr on 2011-09-14
> **alfplayer said:**
> Querés decir xsane? Hay otro que se llama iscan que podés probar.

tambien se podria probar simple scan:
[http://robersoft.blogcindario.com/2011/07/00018-simple-scan-aplicacion-para-escanear-en-ubuntu.html](http://robersoft.blogcindario.com/2011/07/00018-simple-scan-aplicacion-para-escanear-en-ubuntu.html)

y segun lo que he leido aqui, parece que lo que mas ha afectado a la particion han sido los cortes de energia.

La de windows todavia funciona porque se ha usado muy pocas veces y los cortes no la han afectado igual. Pero igual el disco en si ya tiene problemas, asi que si puedes conseguir un ups podrias alargarle la vida un poco mas y sin mencionar que si compras un nuevo disco tambien lo vas a necesitar.

y no solo los cortes son malos, tambien cualquier apagado brusco va afectando poco a poco.

yo vivo en un pais que los cortes son **a diario**! Asi que decidi comprar una laptop (en la cual la bateria integrada funciona igual o mejor que un ups), y desde entonces no me preocupo si la dejo encendida.

y tambien tengo otra grande pero esa si que no la dejo encendida mucho tiempo sin supervision.

---

### Post by marcelo_bur on 2011-09-14
Hola.
Si, creo que lo del UPS va a ser muy positivo. Me voy a ocupar de eso apenas disponga de tiempo para ver modelos y precios. Y también voy a tener que cambiar mis costumbres y apagar la PC cuando no la estoy usando. No me gustan las laptops, o notebooks como les decimos en Argentina.

Este fin de semana voy a ver si de alguna forma consigo recuperar el sistema, aun me quedan un par de cosas por probar, pero sucede que estoy en una época de mucho trabajo y tengo poco tiempo. Si nada resulta voy a formatear la partición, con lo cual supongo que tendrían que saltar los errores en el disco, para reistalar. También voy a investigar sobre herramientas para recuperar el sistema y voy a ver si puedo bajar SMART TOOLS a un cd para seguir trabajando en el disco.
Lo que más me llama la atención es que, estando SMART habilitado en la máquina, nunca me haya enviado una advertencia....

Con respecto a SIMPLE SCAN ya lo probé y es mucho peor que XSANE.

Solo por curiosidad, Madjr, en que país vives???

Bue, ya veremos, porque sigo sintiendome extraño con XP.

Saludos y hasta cualquier momento.

---

### Post by alfplayer on 2011-09-14
En general no veo necesidad de un UPS. Más importante es tener una buena fuente. Los sistemas de archivos tienen protecciones contra pérdidas de datos (se puede buscar información de cómo funciona el *journal* de ext3 y ext4).

---

### Post by guillermolisi on 2011-09-14
> **marcelo_bur said:**
> Hola.
Si, creo que lo del UPS va a ser muy positivo. Me voy a ocupar de eso apenas disponga de tiempo para ver modelos y precios. Y también voy a tener que cambiar mis costumbres y apagar la PC cuando no la estoy usando. No me gustan las laptops, o notebooks como les decimos en Argentina.

Este fin de semana voy a ver si de alguna forma consigo recuperar el sistema, aun me quedan un par de cosas por probar, pero sucede que estoy en una época de mucho trabajo y tengo poco tiempo. Si nada resulta voy a formatear la partición, con lo cual supongo que tendrían que saltar los errores en el disco, para reistalar. También voy a investigar sobre herramientas para recuperar el sistema y voy a ver si puedo bajar SMART TOOLS a un cd para seguir trabajando en el disco.
Lo que más me llama la atención es que, estando SMART habilitado en la máquina, nunca me haya enviado una advertencia....

Con respecto a SIMPLE SCAN ya lo probé y es mucho peor que XSANE.

Solo por curiosidad, Madjr, en que país vives???

Bue, ya veremos, porque sigo sintiendome extraño con XP.

Saludos y hasta cualquier momento.
S.M.A.R.T. no avisa sobre problemas en forma activa, solo registra informacion operativa sobre el disco y se requiere de una herramienta que permita acceder a esa informacion, que es, en definitiva, lo que hace Smartmontools (ya sea consultando periodicamente y leyendo la informacion o usando cosas tipo Conky que la exponen todo el tiempo en pantalla).

Si queres un monitoreo activo tenes que pensar en cosas mas sofisticadas tipo Nagios, Zabbix, etc.

Ubuntu posee una herramienta de consulta que es la que usaste para mostrar los primeros screenshots que indica cuando el disco tuvo algun error, pero tambien es de monitoreo pasivo.

---

### Post by madjr on 2011-09-15
> **alfplayer said:**
> En general no veo necesidad de un UPS. Más importante es tener una buena fuente. Los sistemas de archivos tienen protecciones contra pérdidas de datos (se puede buscar información de cómo funciona el *journal* de ext3 y ext4).

parece que no tienes mucha experiencia con discos en cuanto a cortes de energia frecuentes.

Los apagones y apagados bruscos los destruyen.

ahora si tienes un disco ssd es lo contrario, los apagones no le afectan tanto, pero la escritura constante si.

los ups tambien ademas de la bateria, tienen buenas fuentes y reguladores de voltaje incorporados.

> Solo por curiosidad, Madjr, en que país vives???

en DR !

dominican republik! :p

---

### Post by alfplayer on 2011-09-15
> **madjr said:**
> parece que no tienes mucha experiencia con discos en cuanto a cortes de energia frecuentes.

Los apagones y apagados bruscos los destruyen.

Podría suceder con fuentes genéricas, pero no sería el caso de fuentes de marca. Es importante usar una fuente con un mínimo de calidad (ej. evitando las genéricas, que son mucho más baratas).

> **madjr said:**
> los ups tambien ademas de la bateria, tienen buenas fuentes y reguladores de voltaje incorporados.

Esto sería redundante usando una fuente de computadora de marca (PSU). La importancia del UPS es que permite mantener a la PC funcionando para dar tiempo a que se grabe todo y que las aplicaciones terminen normalmente grabando los datos normalmente. Los dispositivos de la computadora se pueden asegurar con una PSU de marca sin UPS. Aunque el UPS sea de una marca con reputación y de los más caros, se pueden proteger los dispositivos con un PSU de marca por un precio menor.

Como con ext3 y ext4 los bugs mayores de corrupción de datos fueron solucionados (por lo menos fallas mayores), sólo pueden existir problemas con aplicaciones que no hayan grabado correctamente en el disco antes del corte de energía, y esto aparentemente no es frecuente. A veces por esto hay fallas en el sistema, pero fallas arreglables de aplicaciones y archivos específicos.

Los UPS baratos introducen fallas propias, y otros que protejen efectivamente al hardware tienen un costo muy elevado.

Para el caso de una PC hogareña no es común trabajar con archivos importantes, por lo que creo que los backups son la mejor opción para resguardar archivos, con un costo menor al UPS, preferentemente con una fuente con un mínimo de calidad para resguardar los dispositivos de fallas eléctricas.

---

### Post by madjr on 2011-09-15
> **alfplayer said:**
> Podría suceder con fuentes genéricas, pero no sería el caso de fuentes de marca. Es importante usar una fuente con un mínimo de calidad (ej. evitando las genéricas, que son mucho más baratas).



Esto sería redundante usando una fuente de computadora de marca (PSU). La importancia del UPS es que permite mantener a la PC funcionando para dar tiempo a que se grabe todo y que las aplicaciones terminen normalmente grabando los datos normalmente. Los dispositivos de la computadora se pueden asegurar con una PSU de marca sin UPS. Aunque el UPS sea de una marca con reputación y de los más caros, se pueden proteger los dispositivos con un PSU de marca por un precio menor.

Como con ext3 y ext4 los bugs mayores de corrupción de datos fueron solucionados (por lo menos fallas mayores), sólo pueden existir problemas con aplicaciones que no hayan grabado correctamente en el disco antes del corte de energía, y esto aparentemente no es frecuente. A veces por esto hay fallas en el sistema, pero fallas arreglables de aplicaciones y archivos específicos.

Los UPS baratos introducen fallas propias, y otros que protejen efectivamente al hardware tienen un costo muy elevado.

Para el caso de una PC hogareña no es común trabajar con archivos importantes, por lo que creo que los backups son la mejor opción para resguardar archivos, con un costo menor al UPS, preferentemente con una fuente con un mínimo de calidad para resguardar los dispositivos de fallas eléctricas.

ven a vivir a mi pais un tiempo y aprenderas a las malas. ;)

y aqui no solo es obligatorio usar UPS, tambien inversor (y no, no son lo mismo).

reparo pc y quisas no te imaginas la cantidad de discos hechados a perder que he visto.

cheers!

---

### Post by alfplayer on 2011-09-15
No sé a qué le llamas inversor ni si tiene relación con el tema.

Leí de un reparador aquí en Argentina que tiene tasas de fallas de dispositivos mucho mayores con los UPS que se venden aquí en el mercado; seguramente es trasladable a la mayoría de los países sudamericanos que compran UPS baratos de origen chino.

En Buenos Aires, donde vivo, en los últimos años fueron comunes durante el verano los cortes de luz, y afectaron a varias de mis computadoras.

Además de las experiencias personales, los casos que se ven de pérdida de datos importantes en los foros de internet son relativamente pocos.

Por supuesto, los discos rígidos siguen siendo uno de los componentes que más fallan, aún sin que falle el PSU.

madjr, sugiero que uses PSU de marca.

Saludos.

---

### Post by madjr on 2011-09-15
> **alfplayer said:**
> No sé a qué le llamas inversor ni si tiene relación con el tema.

Leí de un reparador aquí en Argentina que tiene tasas de fallas de dispositivos mucho mayores con los UPS que se venden aquí en el mercado; seguramente es trasladable a la mayoría de los países sudamericanos que compran UPS baratos de origen chino.

En Buenos Aires, donde vivo, en los últimos años fueron comunes durante el verano los cortes de luz, y afectaron a varias de mis computadoras.

Además de las experiencias personales, los casos que se ven de pérdida de datos importantes en los foros de internet son relativamente pocos.

Por supuesto, los discos rígidos siguen siendo uno de los componentes que más fallan, aún sin que falle el PSU.

madjr, sugiero que uses PSU de marca.

Saludos.

bueno aqui tenemos apagones diarios de hasta 10 horas desde hace mas de 40 años... (si, muchas propuestas de solucion por parte del gobierno y pocos hechos... ademas de los "intereses" que ganan bastante dinero con los apagones...)

seguro en todo el verano de cortes de tu pais no llegaron ni a 10 horas..

claro cualquiera diria como sobrevivimos !!?

pues todo el mundo tiene un inversor y entre 4 y ocho baterias industriales para tratar de aguantar algo asi (si un negociaso para las tiendas)...

ves, es lamentable, pero lo unico positivo que te puedo decir es que la poblacion es mas autonoma e independiente (los cortes no producen ni panico , ni crisis, ni desgracia como en otros paises.. porque ya estamos mas que acostumbrados :p)

estoy listo para el 2012 ! jeje

en cuanto a lo otro, tanto el inversor que poseo, como el UPS tienen un psu (o comun mente llamado: regulador de voltaje) y si, de marca.

te puedo decir que chino o no es mejor cualquier ups que no tener nada (por lo menos en la situacion de mi pais). Tengo una tienda que repara compus, asi que alguna experiencia tengo que tener :) . Claro no te voi a discutir que las cosas de marcas se supone deben salir mejores.

cheers!

---

### Post by biale on 2011-09-15
¿A que llaman "inversor"?

Para discos WD existe un programa del fabricante "DLGdiag 5.19" (WD Data LifeGuard Diagnostic). Es un .exe que corre bajo freeDOS. Basicamente se ubica al exe en un pendrive y se arranca un CD con freeDOS en modo comando. Desde allí se ejecuta el DLGdiag en modo comando.

---

### Post by marcelo_bur on 2011-09-15
Hola a todos.

He aprendido unas cuantas cosas a partir de este tema, pero sigo sin poder restaurar mi sistema,
Estoy haciendo los últimos intentos antes de formatear y reinstalar.
Buscando y buscando encontre esto: [http://ubuntuforums.org/showthread.php?t=1555031](http://ubuntuforums.org/showthread.php?t=1555031) , que es lo más parecido a lo que me ocurrió a mi. 
De todas formas, y aunque figure como SOLVED, con lo que lei ahí no pude lograr nada, a no ser que mi relativo dominio del inglés haya hecho que pase algo por alto.

Madjr, debe ser difícil vivir asi. Argentina no es justamente un paraiso ni se acerca siquiera a la perfección, pero un corte cada tanto que dure unas horas nos pone locos. Lo que no entiendo es lo de las BATERIAS... ¿Porqué no usan generadores portátiles???
Saludos

---

### Post by alfplayer on 2011-09-15
> **madjr said:**
> bueno aqui tenemos apagones diarios de hasta 10 horas desde hace mas de 40 años... (si, muchas propuestas de solucion por parte del gobierno y pocos hechos... ademas de los "intereses" que ganan bastante dinero con los apagones...)

seguro en todo el verano de cortes de tu pais no llegaron ni a 10 horas..

Interesante.

La situación es diferente, mis mensajes anteriores eran pensados para una situación como la de la ciudad de Buenos Aires. En mi casa creo que superaron las 10 horas el último verano, aunque no significativamente.

A eso me refiero, la electrónica interna del UPS y el PSU típico de las PC (a este PSU me refería en mis mensajes anteriores, la "fuente") regulan la tensión, ambos cumplen esa función entre otras, por eso pueden redundar aumentando innecesariamente el precio total. En [http://www.hardwaresecrets.com/]("http://www.hardwaresecrets.com/") muestran la diferencia de los circuitos y componentes electrónicos que filtran las señales de entrada entre fuentes genéricas y de marca. Hay diferencias muy grandes de los valores límites que aceptan.

Aumentando las fallas en el suministro de energía el riesgo de pérdida de datos evindentemente es mayor, y por eso es entendible que la demanda de UPS es mayor.

---

### Post by madjr on 2011-09-16
> **biale said:**
> ¿A que llaman "inversor"?

Para discos WD existe un programa del fabricante "DLGdiag 5.19" (WD Data LifeGuard Diagnostic). Es un .exe que corre bajo freeDOS. Basicamente se ubica al exe en un pendrive y se arranca un CD con freeDOS en modo comando. Desde allí se ejecuta el DLGdiag en modo comando.

este es un inversor (o "inverter" en ingles) y un banco de baterias:

[IMG]http://www.ratechsolar.com/galery/los_gatos/1.jpg[/IMG]

bueno en realidad son 3 o 4 inversores en esa foto.

en mi hogar solo tenemos 1 y un cuarto de las baterias que ves.

las baterias se pueden cargar con energia solar, aeolica o con la energia de la "calle".

no es muy distinto a tener por ejemplo un vehiculo electrico, pero en este caso para el hogar.


> Lo que no entiendo es lo de las BATERIAS... ¿Porqué no usan generadores portátiles???
Saludos

yo tambien tengo uno pero no lo uso al menos que sea una emergencia (como huracanes), porque es anti-economico y has visto **el precio de los combustibles ultimamente** !!! uiii!! :p

y si aveces nos volvemos un poco locos, en especial al tener que cambiar esas baterias cada tantos años que no salen nada baratas :/


@alfplayer

ok te entiendo y gracias por el enlace, esta muy interesante y completa esa pagina.

---

### Post by guillermolisi on 2011-09-17
> **marcelo_bur said:**
> Hola a todos.

He aprendido unas cuantas cosas a partir de este tema, pero sigo sin poder restaurar mi sistema,
Estoy haciendo los últimos intentos antes de formatear y reinstalar.
Buscando y buscando encontre esto: [http://ubuntuforums.org/showthread.php?t=1555031](http://ubuntuforums.org/showthread.php?t=1555031) , que es lo más parecido a lo que me ocurrió a mi. 
De todas formas, y aunque figure como SOLVED, con lo que lei ahí no pude lograr nada, a no ser que mi relativo dominio del inglés haya hecho que pase algo por alto.


Cambiado a UNSOLVED hasta ver a que definicion se llega con el tema.

---

### Post by marcelo_bur on 2011-09-20
> **guillermolisi said:**
> Cambiado a UNSOLVED hasta ver a que definicion se llega con el tema.


Hola. Me parece bien.
Por el momento todo está igual. Desde hace algunos días ando con muchisimo trabajo y con algunos problemas personales, lo cual hace que este asunto quede en segundo plano hasta tanto todo este en orden en mi vida.
Con esto quiero decir que, por el momento, sigo usando XP aunque en realida poco uso le estoy dando a la PC (mi trabajo no tiene nada que ver con la informática, ni mis problemas...). No he tenido ánimo para hacer nuevos intentos de reparar el SO ni de reinstalar.
Espero en breve pueda ocuparme de este asunto.
Saludos

---

### Post by marcelo_bur on 2011-09-23
Hola. Me tome un rato e hice mis últimos intentos por recuperar el sistema. Ya lo doy por perdido.
Espero tener tiempo el domingo para ponerme tranquilo a formatear la partición y reinstalar.
Saludos

---

### Post by marcelo_bur on 2011-11-28
Hola. Cada tanto entro a leer un poco y, en esta ocasión, quise dejarles un saludo.
En los últimos meses he estado muy ocupado. Los domingos, unico día que me tomo libre, tengo mil cosas que hacer en la casa y, ahora, también en el jardín.
Por lo tanto, y hasta que reviente, sigo usando XP. Claro que habiéndome acostumbrado a los programas de Ubuntu he ido reemplazando los de Windows por otros. Por ejemplo: uso Open Office, Gimp, Pidgin, VLC Media Player, y en lugar del bloc de notas uso Akel Pad. Armado de estos programas no se me hace tan extraño usar Windows, lo cual seguramente seguirá así hasta que baje el trabajo, como es normal, durante el verano.
Hasta cualquier momento.

---

### Post by juancarlospaco on 2011-11-29
...y bueno, siendo Trabajo, mejor que sobre y no que falte :P

suerte.

---

### Post by marcelo_bur on 2012-02-18
Hola. Espero que todos estén bien y pasando un excelente verano. Mi PC sigue en las mismas condiciones, cada tanto intento algo pero no pasa nada. No he podido siquiera reinstalar Ubuntu (intenté hacer una instalación nueva asignandole la partición que no me funciona para que la formatee y listo, pero el programa de instalación se queda, no colgado, pero no avanza).
Encontré por ahí un cd con algunas herramientas que no se muy bien como usar, por lo que las dejo para cuando XP me comience a dar problemas.
Saludos a todos y hasta cualquier momento.

---

