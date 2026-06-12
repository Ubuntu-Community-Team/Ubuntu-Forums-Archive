---
title: "Jaunty Jackalope BETA"
date: 2009-04-11
forum: Comunidad
---

### Post by xsergei on 2009-04-11
Hola amigos, alguien no pudo esperar y actualizó a la versión 9.04? cambios notables?
Yo soy algo impaciente, pero no puedo hacer la prueba en mi Pc ya que no tengo disco ni espacio extra y la uso para trabajar.
saludos a los ubuntureros

Sergei

---

### Post by Hei Ku on 2009-04-11
En el foro de software un par comentaron sobre la beta.
Yo instale la beta de Xubuntu y esta linda, y me llamo la atencion la velocidad de booteo. El tiempo hasta que aparece el X y pide la contraseña es mucho mas corto, y la pantalla de login para Xubuntu esta muy copada.

---

### Post by Hernán-Amaya on 2009-04-11
yo formatié a ext4 y anda mas rápido en la copia y búsqueda de archivos y el booteo es mucho mas rápido en el manejo cotidiano la verdad que no note mucha diferencia.

---

### Post by pablo.s on 2009-04-11
> **xsergei said:**
> Hola amigos, alguien no pudo esperar y actualizó a la versión 9.04? cambios notables?

Depende mucho de qué versión vengas:
Si actualizás desde Dapper la diferencia es
enorme y se va reduciendo el asombro si
actualizás desde Intrepid.
Jaunty viene con muchas pero pequeñas
mejoras, la más sobresaliente es, como han
mencionado, el tiempo de booteo que según
el hardware puede llegar a ser la mitad del
tiempo que usa Intrepid.
Saludos.

---

### Post by rojojuan on 2009-04-11
La corrí desde un live CD. Me reconoció todo el hardware. (Escaner Canon lide, pen drive usb). En cuanto a los drivers de video de Nvidia, veo que se puede instalar directamente el nuevo desde Sistema, Controladores de Hardware. Este driver 180 de nvidia me interesa porque trae bastante mejoras para ver películas (pure video,etc).
Espero la nueva versión definitiva para instalar

---

### Post by pablo.s on 2009-04-11
> **rojojuan said:**
> En cuanto a los drivers de video de Nvidia, veo que se puede instalar directamente el nuevo desde Sistema, Controladores de Hardware. Este driver 180 de nvidia me interesa porque trae bastante mejoras para ver películas (pure video,etc).

Lo que mencionas de Pure Video en nuestro
mundo se llama VDPAU (Video Decode and
Presentation API for Unix) y si bien es cierto
que viene habilitado en los drivers, tambien
hay que habilitarlo en los programas que uno
usa habitualmente para reproducir video.

Yo hace unos meses que estoy utilizando los
paquetes experimentales de VLC y MPlayer
con VDPAU habilitado y para reproducir
video 720p/1080p vale la pena, aunque como
todo lo experimental tiene sus falencias y
se cuelga muy muy seguido.

Si te interesa el tema te puedo pasar los
repositorios de donde bajé las versiones
de VLC y MPlayer. Saludos.

---

### Post by rojojuan on 2009-04-11
> **pablo.s said:**
> Lo que mencionas de Pure Video en nuestro
mundo se llama VDPAU (Video Decode and
Presentation API for Unix) y si bien es cierto
que viene habilitado en los drivers, tambien
hay que habilitarlo en los programas que uno
usa habitualmente para reproducir video.

Yo hace unos meses que estoy utilizando los
paquetes experimentales de VLC y MPlayer
con VDPAU habilitado y para reproducir
video 720p/1080p vale la pena, aunque como
todo lo experimental tiene sus falencias y
se cuelga muy muy seguido.

Si te interesa el tema te puedo pasar los
repositorios de donde bajé las versiones
de VLC y MPlayer. Saludos.

Gracias por tu post, especialmente por la aclaración respecto de VDPAU.
Pienso actualizar a Jaunty y con esa versión podré instalar el driver 180 de Nvidia.
Me parece mejor esperar y actualizar a Jaunty, que supongo haga correr todo bien.
Será así?

---

### Post by pablo.s on 2009-04-11
> **rojojuan said:**
> Me parece mejor esperar y actualizar a Jaunty, que supongo haga correr todo bien.
Será así?

Si, según mi experiencia a través
de las alphas, se van arreglando
muchisimos bugs y agregando a la
base de compatibilidad muchos
perifericos. Es notable la cantidad
de trabajo que la comunidad hace
cada dia para cubrir los huecos de
drivers. Incluso la documentación y
el soporte ahora mismo están muy
accesibles. Asombra ver cómo de
un lanzamiento de versión a otro
hay asuntos que automagicamente
se incorporan, ahorrando al usuario
final un montón de tiempo.

---

### Post by rojojuan on 2009-04-12
> **pablo.s said:**
> Si, según mi experiencia a través
de las alphas, se van arreglando
muchisimos bugs y agregando a la
base de compatibilidad muchos
perifericos. Es notable la cantidad
de trabajo que la comunidad hace
cada dia para cubrir los huecos de
drivers. Incluso la documentación y
el soporte ahora mismo están muy
accesibles. Asombra ver cómo de
un lanzamiento de versión a otro
hay asuntos que automagicamente
se incorporan, ahorrando al usuario
final un montón de tiempo.

Gracias por la respuesta. A esperar el 25...

---

### Post by pablo.s on 2009-04-12
> **rojojuan said:**
> Gracias por la respuesta. A esperar el 25...

El 23 ya va a estar.

---

### Post by c4d0rn4 on 2009-04-15
yo me pienso instalar la Release candiate que sale mañana segun. El 23 estoy hasta las manijas con muchas cosas, mañana voy a estar medio tranca.

Más que nada lo pienso hacer porque hay varias cosas que pienso corregir, entre ellas poner el boot en partición aparte, estoy bastante molesto con lo que tarda en bootear el grub.

---

### Post by lega on 2009-04-17
Probé el otro día la beta de Jaunty desde el LiveCD y también reconoció todo el hardware de la notebook de mi esposa, (compaq F755la) incluso la placa wireless que en hardy tenia funcionando con los drivers de madwifi, así que ya tengo autorización de mi esposa para hacer una instalación limpia cuando salga la versión final :)

---

### Post by rojojuan on 2009-04-17
> **Hernán-Amaya said:**
> yo formatié a ext4 y anda mas rápido en la copia y búsqueda de archivos y el booteo es mucho mas rápido en el manejo cotidiano la verdad que no note mucha diferencia.

Tenés noticias sobre el funcionamiento del Grub con esta nueva versión? 
Algunos dicen que no funciona, que se necesita otro Grub o Grub 2, etc.

---

### Post by pablo.s on 2009-04-17
> **rojojuan said:**
> Algunos dicen que no funciona, que se necesita otro Grub o Grub 2, etc.

Lo preguntás en serio?
Cuando el tema candente es la
arbitrariedad de imponer EFi y
derivados en motherboards, me
parece raro que alguien esté
manipulando con datos equivocos.
Sinceramente.
Donde lo leiste?

---

### Post by rojojuan on 2009-04-18
> **pablo.s said:**
> Lo preguntás en serio?
Cuando el tema candente es la
arbitrariedad de imponer EFi y
derivados en motherboards, me
parece raro que alguien esté
manipulando con datos equivocos.
Sinceramente.
Donde lo leiste?

Colocá en google grub2 y vas a ver variada información.
Mis conocimientos son más que limitados, no se que es EFi.
Uno de los sitios:
[http://www.ubuntu-es.org/index.php?q=node/110683](http://www.ubuntu-es.org/index.php?q=node/110683)

---

### Post by Hei Ku on 2009-04-18
El mismo link te responde la duda. Otro descolgado que pregunta sobre Grub2, y la misma respuesta que no, que es solo un paquete mas.

---

### Post by rojojuan on 2009-04-18
> **Hei Ku said:**
> El mismo link te responde la duda. Otro descolgado que pregunta sobre Grub2, y la misma respuesta que no, que es solo un paquete mas.

Gracias por lo descolgado

---

### Post by xsergei on 2009-04-20
Hola amigos, les cuento que bajé y corrí en vivo la V9.04 RC pero por primera vez Kubuntu en lugar de Ubuntu en 64B
Quedé asombrado ya que reinicié la PC con el cd fui a poner la pava cuando volví tenía en escritorio listo para usar, con una facha de aquellas, nunca había visto la versión 4 de KDE nada librado al azar, muy cuidado y unos efectos impresionantes!!!
Ojo no es para entrar el la famosa polémica que escritorio es mejor, hablo de lo que experimenté y me pareció fabuloso ahora cuando salga la versión final no se que hacer... alguien puede contarme alguna ventaja de un escritorio sobre el otro o es simplemente una cuestión de gusto?

---

### Post by pablo.s on 2009-04-20
> **xsergei said:**
> Ojo no es para entrar el la famosa polémica que escritorio es mejor, hablo de lo que experimenté y me pareció fabuloso ahora cuando salga la versión final no se que hacer... alguien puede contarme alguna ventaja de un escritorio sobre el otro o es simplemente una cuestión de gusto?

Si te gustó tanto KDE, usá KDE.
Si no te gustó KDE no lo uses.
Si te gusta armar bardo, tenés un
foro que se llama Taringa.
Si no te gusta armar bardo, podés
contribuir pacificamente acá.
Si dudás de tus gustos y te
parece que otros pueden modificarlos,
ya estás en un gran problema.

Todo esto porque te cuento que
esta pelicula ya la vi muchas veces,
y la verdad no da para verla otra
vez. Saludos.

---

### Post by pol666 on 2009-04-20
> **pablo.s said:**
> Si te gustó tanto KDE, usá KDE.
Si no te gustó KDE no lo uses.
Si te gusta armar bardo, tenés un
foro que se llama Taringa.
Si no te gusta armar bardo, podés
contribuir pacificamente acá.
Si dudás de tus gustos y te
parece que otros pueden modificarlos,
ya estás en un gran problema.

Todo esto porque te cuento que
esta pelicula ya la vi muchas veces,
y la verdad no da para verla otra
vez. Saludos.

Eso de mandar a otra página a "hacer bardo" es infantil, sorry ;)
Es más facil decirle un:

"Usa el que más te guste, entre KUbuntu y Ubuntu solo cambia el escritorio, si tenes una duda específica abri un tema a parte, chau"

---

### Post by xsergei on 2009-04-20
Fui muy claro al expresarme, no se porqué la agresión. 
Mi idea era si por ejemplo uno consumía mas recursos que otro, o bien si hay alguna aplicación que es mas compatible bajo cierto entorno.
Nadie decide por mi, pero los comentarios al respecto ayudan a sacar dudas, claro, no precisamente de los tuyos.
saludos

---

### Post by pablo.s on 2009-04-20
Son dos gestores de ventanas distintos,
con sus defectos y virtudes.
Tu pregunta me sonó a inicio de [flame war]("http://es.wikipedia.org/wiki/Flame_war") 
y no sería ni la primera ni la última, sino
que hace diez años que veo como la gente
gasta energia en polemizar si KDE esto, si
GNOME aquello, si es mas lindo, si es mas
feo. La verdad no da.

Bien dice [pol]("http://www.taringa.net/perfil/129793") que es infantil mandar a otro
sitio a hacer bardo. Lo reconozco. Mis
disculpas.

Espero que mi punto se haya comprendido.
Saludos.

---

### Post by josecuervo86 on 2009-04-20
> **pablo.s said:**
> 
Tu pregunta me sonó a inicio de [flame war]("http://es.wikipedia.org/wiki/Flame_war") 

Espero que mi punto se haya comprendido.
Saludos.

Y... si, sono a flame war. Es bastante feo tener que ver como se rasgan las vestiduras los respectivos defensores de cada gestor. Asi que lo que podes hacer es bajarte la iso de Ubuntu y de Kubuntu, probarlas y ver cual te gusta mas.

---

### Post by xsergei on 2009-04-20
Ok, disculpas aceptadas, pero para que no haya otro mini al entendido no era desde un principio generar una discusión absurda, porque ya he visto esas peleas de nunca acabar y no solo del los escritorios sinó entre SO.
Como bien comenté al principio no puedo hacer pruebas en mi PC porque la uso para trabajar y si bien hago backups periódicos no puedo estar mucho tiempo sin la misma, es por eso mi pregunta, ya que probar las diferentes distros en modo vivo no me va a dar una respuesta respecto a como se desempeñe el sistema instalado en el disco.
gracias a todos.
Sergei

---

### Post by sajnox on 2009-04-20
> **pablo.s said:**
> Son dos gestores de ventanas distintos,
con sus defectos y virtudes.
Tu pregunta me sonó a inicio de [flame war]("http://es.wikipedia.org/wiki/Flame_war") 
y no sería ni la primera ni la última, sino
que hace diez años que veo como la gente
gasta energia en polemizar si KDE esto, si
GNOME aquello, si es mas lindo, si es mas
feo. La verdad no da.

Bien dice [pol]("http://www.taringa.net/perfil/129793") que es infantil mandar a otro
sitio a hacer bardo. Lo reconozco. Mis
disculpas.

Espero que mi punto se haya comprendido.
Saludos.

Che, Primo!!

Deja que los moderadores moderen que para algo estan!!!

---

### Post by pablo.s on 2009-04-21
> **sajnox said:**
> Che, Primo!!

Deja que los moderadores moderen que para algo estan!!!

Fue sin querer queriendo...
Pero no hubo flame war al final.

---

### Post by pablo.s on 2009-04-21
Inexplicablemente este thread sigue
siendo leido...

---

