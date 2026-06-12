---
title: "Problemas de Speedy con Linux &amp; Mac..."
date: 2010-09-17
forum: Comunidad
---

### Post by N3RI on 2010-09-17
Les traigo un caso muy bizarro. A ver:

hace un par de semanas empecé a tener un problema de conexión que consiste en que cuando abro páginas web... no cargan. Tengo que refrescar y ahí cargan, o no cargan las imágenes. No es el típico error de "cargan lentas las páginas", porque no cargan, y cuando cargan, cargan rápido. Espero que se haya entendido la explicación, ahora, para complicarla:

1. tengo 3 computadoras, una con windows 7 y ubuntu, otra con ubuntu netbook edition y otra con windows xp y xubuntu. El problema me pasa en todas las computadoras y todos los SO... pero en el windows 7 es evidentemente menor el problema, pues sólo ocurre de vez en cuando; en cambio en el ubuntu pasa todo el tiempo.

Y lo que es peor, un par de días me levanté temprano y oh sorpresa, andaba perfecta la conexión, pero 9 am en punto, empezó el problema de nuevo.

Pensé que algún vecino me estaba usando el wifi, pero está con WPA2 una contraseña larga. La descarga P2P anda perfecto.

Ah, y vino el técnico de speedy, no pudo encontrarle explicación, dijo "ya vengo ahora a la tarde" y no apareció más ¬¬

Les traigo el problema a UDs porque me llama la atención que con Ubuntu sea mucho más notorio el problema que con windows 7.

Bueno, cualquier consejo que puedan darme, será agradecido.

---

### Post by alfplayer on 2010-09-17
Ya probaste cambiando el servidor DNS?

---

### Post by N3RI on 2010-09-17
sí, de hecho ahora tengo los de OpenDNS. 

También probé:
hacer ping (cada 6 o 7 paquetes, pierde uno)
probé con un livecd (x si era algo raro en mis 2 ubuntus y el xubuntu) y mismo problema
probé todo lo que te hacen hacer los de speedy cuando los llamás

lo único que me queda es instalar windows en la notebook y ver qué tal anda, pero supongo que también va a andar mal.

lo que más me llama la atención es que de noche anda aparentemente bien

---

### Post by alfplayer on 2010-09-18
Si tenés router probá hacer ping desde la interfaz web del router.

---

### Post by atari130xe on 2010-09-18
MMm si tenés Speedy llamalos y que te tomen el reclamo, tengo exactamente el mismo problema y verificaron que hay un bloqueo de puerto, en realid tiene problemas con una parte del hard del equipamiento que tienen, y eso hace que para poder navegar como se debe debas darle a "actualizar" o recargar el navegador a cada momento, esta mañana vino a mi casa el empleado de Speedy y verificó eso con el servidor y le dijeron que mas o menos en el plazo de entre 7 y 10 dias deberia estar solucionado, asi que paciencia!!!

---

### Post by N3RI on 2010-09-18
gracias, ya hice el reclamo... vino el técnico, no pudo solucionarlo y dijo "ahora vuelvo" y no volvió más ¬¬ hice el reclamo de nuevo y ahora estoy esperando. gracias por las respuestas.

---

### Post by alfplayer on 2010-09-18
Primero chequeá que no sea problema con tus cosas. Te recomiendo probar lo que te dije. Speedy arregla los problemas de Speedy, no los de los usuarios.

---

### Post by atari130xe on 2010-09-18
> **N3RI said:**
> gracias, ya hice el reclamo... vino el técnico, no pudo solucionarlo y dijo "ahora vuelvo" y no volvió más ¬¬ hice el reclamo de nuevo y ahora estoy esperando. gracias por las respuestas.

En mi caso no es un problema mio, ni de configuración ni nada de eso, tengo el modem Router ZTE831 que dá Telefónica, ruteado como corresponde, etc etc y me confirmó el técnico que no es un problema mio ni de hard ni de configuración, me dijo que hay mucha gente con la misma situación por el problema con equipos de la empresa y que están tratando de solucionarlo en cuanto puedan. Te cuento que probé con Win 7, con 8 Live cd's de otras distros y con todas pasa lo mismo. Este problema apareció en mi conexión desde el Miércoles pasado (antes andaba muy bién estoy solo a 5 cuadras de la central tengo 3MB contratados y a veces llega a casi 5MB la velocidad de download), asi que al menos yo hice el reclamo y aparentemente se están moviendo porque vino el técnico hoy llamo hablo con la gente del servidor y me confirmó eso, un problema técnico de ellos no mio.

---

### Post by N3RI on 2010-09-18
> **alfplayer said:**
> Si tenés router probá hacer ping desde la interfaz web del router.

el DNS lo he cambiado a los de OpenDNS. Y haciendo ping desde la interfaz web del modem routeado zyxel que da speedy... hace ping correctamente.

EDIT: al momento de escribir esto, anda todo perfecto, la conexión anda bien en todas las computadoras (sin que yo haya hecho ningún cambio)

Ya pasó la semana pasada, el domingo anduvo todo bien, hasta las 9 am del lunes... es como si el problema no fuera "algo", sino "alguien". ¿Alguna posibilidad de que venga por ese lado el asunto?

EDIT: jajaja falsa alarma, sigue andando mal =(

---

### Post by alfplayer on 2010-09-18
Leí de algunos Zyxel que tiene problemas de temperatura. Puede ser eso, la noche es generalmente más fría. Qué modelo es?

---

### Post by N3RI on 2010-09-18
mmm, no veo qué modelo es, es el que viene con wifi. Creo recordar que cuando vino el técnico, cambió el modem por otro y el problema continuaba (x ej, hizo ping y perdía un paquete cada 6 o 7) y lo hizo todo desde windows, y andaba mal igual. Pero en estos días pareciera que en windows 7 el problema, si bien existe, se nota mucho menos que en ubuntu y windows xp.

Por cierto, no sé si ya comenté, pero probé también con un LiveCD 9.10 y pasaba lo mismo.

Bueno, ahora voy a probar pagarlo un buen rato, que "se enfríe" y veremos qué pasa.

---

### Post by alfplayer on 2010-09-18
Estoy viendo un foro argentino, hay mucha gente con exactamente el mismo problema. Parece que es un problema muy grande.

---

### Post by N3RI on 2010-09-18
qué foro? me pasás el link?

---

### Post by alfplayer on 2010-09-18
> **N3RI said:**
> qué foro? me pasás el link?

Sí. Por el tamaño del problema seguro que hay más casos que aparecen en Google.

[http://foros.3dgames.com.ar/internet-y-redes.191/442022.speedy-problemas-conexion-thread-oficial.177.html]("http://foros.3dgames.com.ar/internet-y-redes.191/442022.speedy-problemas-conexion-thread-oficial.177.html")

---

### Post by javier-2714 on 2010-09-18
Tengo exactamente el mismo problema hace un mes estoy reclamando y no me lo solucionan ya me tienen cansado es un desastre sppedy no se puede navegar vinieron 3 supuestos técnicos que saben menos que yo y no tienen idea cual es el problema por lo que encontré en google el tema pasa por el nivel de ruido en la linea tengo un 80 % y lo máximo es el 70 % " [http://wiki.bandaancha.st/Todo_sobre_ruido-atenuaci%C3%B3n_de_tu_l%C3%ADnea](http://wiki.bandaancha.st/Todo_sobre_ruido-atenuaci%C3%B3n_de_tu_l%C3%ADnea) " lo único a favor de sppedy es que agregaron soporte para linux, cuando me pasaron con la parte de linux fue el único que mazo menos sabe algo y se puede hablar decentemente pero igual no hay solución por ahora.

---

### Post by alfplayer on 2010-09-18
Esto puede ser por ruido en la línea... o no.

---

### Post by javier-2714 on 2010-09-18
Si el nivel de ocupación  a la conclusión que estoy llegando es que speedy no da abasto ofrece velocidades que no soporta en las instalaciones que tienen tengo contratado 3 mb por lo que encontré a mayor velocidad aumenta la ocupación voy a probar llamando y pidiendo que me bajen a 1 mb y vamos a ver que pasa.

---

### Post by N3RI on 2010-09-18
qué tan "exactamente el mismo problema" tenés? en qué se parecen tus síntomas? (pregunto así el lunes si viene el técnico, tengo para decirle.

---

### Post by alfplayer on 2010-09-18
> **javier-2714 said:**
> Si el nivel de ocupación  a la conclusión que estoy llegando es que speedy no da abasto ofrece velocidades que no soporta en las instalaciones que tienen tengo contratado 3 mb por lo que encontré a mayor velocidad aumenta la ocupación voy a probar llamando y pidiendo que me bajen a 1 mb y vamos a ver que pasa.

No entiendo cómo llegás a esa conclusión y cómo se relaciona con este tema.

Igualmente, no te recomiendo hacer eso, no creo que así mejore. Si a Speedy se le satura una conexión tu velocidad real probablemente siga limitada de la misma manera, hasta puede ser más por tener menor velocidad máxima contratada. La diferencia sería solamente del costo.

---

### Post by alfplayer on 2010-09-18
Si es un problema generalizado como parece, muy probablemente lo único que se puede hacer para que se normalize es esperar.

---

### Post by javier-2714 on 2010-09-18
Es imposible navegar decentemente abrís cualquier pagina no la abre te dice servidor no encontrado le das a recargar y la abre y con el correo es un dolor de cabeza te sierra la sesión por ahí abre bien vas algún enlace y otra vez en youtube ver un video estas 1 hora

---

### Post by N3RI on 2010-09-18
> **javier-2714 said:**
> Es imposible navegar decentemente abrís cualquier pagina no la abre te dice servidor no encontrado le das a recargar y la abre y con el correo es un dolor de cabeza te sierra la sesión por ahí abre bien vas algún enlace y otra vez en youtube ver un video estas 1 hora

si, es exactamente el mismo problema, hace cuánto te está pasando?

---

### Post by javier-2714 on 2010-09-18
Hace un mes venden demasiado y no invierten en infraestructura y por lo que leí por varios lados a mayor velocidad aumenta el nivel de ruido y no creo que speedy invierta por ahora no creo que lo soluciones ya que encontré abundantes casos sin solución sobre este tema que pasa en ciertas zonas del conurbano yo soy de Merlo.

---

### Post by biale on 2010-09-19
De un tiempo a esta parte, yo tengo el mismo problema con Speedy. No es la primera vez que ocurre, cada tanto vuelve a aparecer.

En mi caso el problema se nota mucho mas en las horas pico, y con la combinación WIFI + Web + Firefox.

No se nota en la transferencia de archivos grandes, si con la navegación Web. Pareciera que los DNS (200.51.211.7) tienen mucho que ver: un tiempo de respuesta de 170 mseg (obtenido con namebench) es una barbaridad, solo un poquito menos que los DNS de google y que no estan en las red del ISP.

El problema usando chromium se nota mucho menos, que parece ser menos sencible a las redes lentas. Chromium Mantiene la conexión mientras que FFox directamente la corta y entonces se necesita  repetir el pedido. IE parece funcionar de una manera parecida a Chromium.

Yo descartaría los problemas de ruido propios de la línea ADSL. Esos problemas arrancan fuerte a partir de los 5 o 7 Mbps y terminarían limitando la velocidad de señalización. Mi lema es que si alguna vez anduvo, y si repentinamente no se degradó la última milla, todo debería seguir andando como siempre. De todas maneras el análisis del enlace se realiza fácilmente.

¿Por ahí se mencionó un port bloqueado? En fin...

Para mi gusto el problema pasa substancialmente por la saturación de los enlaces, por el funcionamiento de los DNS y no descarto algún perfilado. Si un enlace no puede "picar" a unos 30/ 50 MBps la visualización Web puede terminar siendo un karma.  

Un saludo a todos.

---

### Post by atari130xe on 2010-09-19
> **biale said:**
> De un tiempo a esta parte, yo tengo el mismo problema con Speedy. No es la primera vez que ocurre, cada tanto vuelve a aparecer.

En mi caso el problema se nota mucho mas en las horas pico, y con la combinación WIFI + Web + Firefox.

No se nota en la transferencia de archivos grandes, si con la navegación Web. Pareciera que los DNS (200.51.211.7) tienen mucho que ver: un tiempo de respuesta de 170 mseg (obtenido con namebench) es una barbaridad, solo un poquito menos que los DNS de google y que no estan en las red del ISP.

El problema usando chromium se nota mucho menos, que parece ser menos sencible a las redes lentas. Chromium Mantiene la conexión mientras que FFox directamente la corta y entonces se necesita  repetir el pedido. IE parece funcionar de una manera parecida a Chromium.

Yo descartaría los problemas de ruido propios de la línea ADSL. Esos problemas arrancan fuerte a partir de los 5 o 7 Mbps y terminarían limitando la velocidad de señalización. Mi lema es que si alguna vez anduvo, y si repentinamente no se degradó la última milla, todo debería seguir andando como siempre. De todas maneras el análisis del enlace se realiza fácilmente.

¿Por ahí se mencionó un port bloqueado? En fin...

Para mi gusto el problema pasa substancialmente por la saturación de los enlaces, por el funcionamiento de los DNS y no descarto algún perfilado. Si un enlace no puede "picar" a unos 30/ 50 MBps la visualización Web puede terminar siendo un karma.  

Un saludo a todos.

Jejejej me quedo tranquilo con el "problema" dicen que mal de mucho consuelo de tontos :P, Googleando y buscando "Speedy NetCache" te encontrás con muchísima gente en el mismo estado que nosotros... Nunca me había pasado empecé con este tema el Miércoles pasado de repente tener que darle a todos los sitios "reintentar" es un garrón y mucho más cuando tengo que recargar los repos, simplemente dán error, porque no los encuentra "habilitados o aparecen "sin conexion", espero lo solucionen realmente cuanto antes, me extraña que a pesar de tantos reclamos eso siga ocurriendo, lamentable.

---

### Post by atari130xe on 2010-09-19
Por cierto acá les dejo material de lectura para entretenerse sobre el problemita en cuestión:

[http://www.sabermenos.com.ar/%C2%BF-que-pasa-con-speedy-en-argentina/]("http://www.sabermenos.com.ar/%C2%BF-que-pasa-con-speedy-en-argentina/")

[http://blogs.buanzo.com.ar/2009/08/netcache-url-dos-speedy-argentina-advisory.html]("http://blogs.buanzo.com.ar/2009/08/netcache-url-dos-speedy-argentina-advisory.html")

---

### Post by alfplayer on 2010-09-19
> **atari130xe said:**
> Por cierto acá les dejo material de lectura para entretenerse sobre el problemita en cuestión:

[http://www.sabermenos.com.ar/%C2%BF-que-pasa-con-speedy-en-argentina/]("http://www.sabermenos.com.ar/%C2%BF-que-pasa-con-speedy-en-argentina/")

[http://blogs.buanzo.com.ar/2009/08/netcache-url-dos-speedy-argentina-advisory.html]("http://blogs.buanzo.com.ar/2009/08/netcache-url-dos-speedy-argentina-advisory.html")

No sabemos si algo de esto está relacionado con el problema de estos días.

---

### Post by juancarlospaco on 2010-09-19
*Un proxy trasparente.*
:)

---

### Post by alfplayer on 2010-09-19
> **juancarlospaco said:**
> *Un proxy trasparente.*
:)

Si es eso, ahora no es transparente :)

---

### Post by N3RI on 2010-09-19
buenísimo entonces, es el momento ideal para pasarme a... ah.. oh wait!

---

### Post by atari130xe on 2010-09-19
> **alfplayer said:**
> No sabemos si algo de esto está relacionado con el problema de estos días.

yo creo que sí los síntomas son exactamente iguales a los descriptos en esas notas...

---

### Post by alfplayer on 2010-09-19
En el primer link las páginas dejan de funcionar por un tiempo, por ejemplo durante minutos. El segundo link es de un problema de seguridad, un DoS, no un problema generalizado.

Lo que están diciendo ahora es que hay que hacer reintentos para entrar a páginas, que actualizando varias veces la página se puede entrar.

No parece que es un problema con un (web) proxy, sino que fallan los pings.

---

### Post by biale on 2010-09-19
La unica prueba que encontré rápido no muestra la presencia de un proxy. Y es razonable que fallen los pings: la mayoría de los equipos estan configurados para no responder al ping o solo responder a una parte de ellos.

Lo que no logro cerrar es que impacte tanto la presencia de WIFI.

---

### Post by alfplayer on 2010-09-19
> **biale said:**
> La unica prueba que encontré rápido no muestra la presencia de un proxy. Y es razonable que fallen los pings: la mayoría de los equipos estan configurados para no responder al ping o solo responder a una parte de ellos.

Lo que no logro cerrar es que impacte tanto la presencia de WIFI.

Lo razonable es que los hosts que lo tienen habilitado respondan a todos los pings. Se puede probar por ejemplo hacer ping a 8.8.8.8, que responde siempre (todos los pedidos, como debe ser).

Con o sin wifi, el problema está, aunque no probé en las últimas horas.

---

### Post by guillermolisi on 2010-09-19
La prueba mas categorica que el simple ping es el traceroute. No tenes problemas con la respuesta ante los ping (y el posible DoS) y te da mucha mas informacion.

---

### Post by atari130xe on 2010-09-19
Guillermo este es un ejemplo de traceroute echo a [www.google.com.ar](www.google.com.ar) con el problema con estoy teniendo con Speedy (no cargan los sitios) aclaro que le puse los DNS de Google.

```
jose@jose-desktop:~$ traceroute www.google.com.ar
traceroute to www.google.com.ar (72.14.253.104), 30 hops max, 60 byte packets
 1  192.168.1.1 (192.168.1.1)  1.176 ms  1.866 ms  2.545 ms
 2  * * *
 3  200.51.233.122 (200.51.233.122)  50.167 ms  51.967 ms  53.891 ms
 4  200.51.233.73 (200.51.233.73)  56.387 ms  58.517 ms  60.427 ms
 5  So7-0-0-0-grtbuecu1.red.telefonica-wholesale.net (84.16.9.233)  64.502 ms  66.339 ms  68.259 ms
 6  Xe6-1-2-0-grtmiabr8.red.telefonica-wholesale.net.121.142.94.in-addr.arpa (94.142.121.234)  203.360 ms Xe-7-1-0-0-grtmiabr7.red.telefonica-wholesale.net.121.142.94.in-addr.arpa (94.142.121.210)  266.605 ms  175.804 ms
 7  Xe2-0-2-0-grtmiana3.red.telefonica-wholesale.net.121.142.94.in-addr.arpa (94.142.121.149)  180.143 ms  180.859 ms  182.783 ms
 8  GOOGLE-xe-7-1-0-0-grtmiana3.red.telefonica-wholesale.net (84.16.6.114)  202.638 ms GOOGLE-xe-6-1-0-0-grtmiana3.red.telefonica-wholesale.net (84.16.6.118)  208.067 ms GOOGLE-xe-7-1-0-0-grtmiana3.red.telefonica-wholesale.net (84.16.6.114)  209.206 ms
 9  209.85.253.74 (209.85.253.74)  209.605 ms  209.862 ms  210.082 ms
10  209.85.254.50 (209.85.254.50)  210.401 ms  210.652 ms  210.879 ms
11  mia04s03-in-f104.1e100.net (72.14.253.104)  211.117 ms  211.543 ms  183.698 ms
jose@jose-desktop:~$ 

```

---

### Post by alfplayer on 2010-09-27
Hay un hilo aparentemente del mismo problema en [http://www.bandangosta.com.ar/index.php/topic,5194.0.html](http://www.bandangosta.com.ar/index.php/topic,5194.0.html) y en otros hilos del mismo foro.

---

### Post by biale on 2010-09-27
Ahora si que anda mal en serio la navegación "speedy F5.0"...

---

### Post by biale on 2010-09-27
alfplayer: agradezco la data...

En la misma computadora, ahora escribo este post desde Virtualbox/WXP/Firefox-3.6.3 y anda mucho mejor. No se imaginan lo que me costo enviar lo anterior.

---

### Post by josecuervo86 on 2010-09-27
No me puede andar peor Speedy! 6 o 7 veces tengo que "refrescar" la pagina para que cargue, y agradece si no te tira el html "crudo" o te faltan imagenes. Llame recien y la verdad es que no tienen ni idea de como solucionarlo, me paseo por todos lados el de "soporte".

Speedy F5.0!! No podria estar mas de acuerdo con eso!!

---

### Post by biale on 2010-09-27
Fijate lo que estoy usando para nevegar ahora: doblemente preocupante.

---

### Post by alfplayer on 2010-09-27
Se puede probar si mejora navegando con un web proxy.

---

### Post by atari130xe on 2010-09-28
Bueno gente hace unos días hice un post sobre los problemas que tengo para nevegar (Continuamente debo darle a F5 porque las páginas NO cargan como se debe). LLamé a Sppedy y me enviaron en 10 días a 3 Técnicos: el 1ro vino, miró todo probó linea, etc. y me dijo (previo llamado al server de Speedy) que en unos 10 días lo iban a solucionar y que era un problema del servidor), el 2do vino a los 2 días y luego de andar por el techo del edificio y decirme que mi par estaba mal conectado cortó un par de cables (dejandome a mí con el número de mi vecina de arriba, a ella sin tono y al de otro Dto, también sin tono, un joyita, al menos con el número de mi vecina andaba más lento pero andaba BIÉN en cuanto a cargar los sitios), el 3ro llegó y luego de revisar cables, volvi a tener mi par (con mi nro.), el último me salío con que el modem no servia porque era simple y necesitaba un modem sarasa sarasa), resultado de esto y de MUCHAS llamadas al 0800 333 7733 opción 0: Nada sigue funcionando MUY mal (ni hablar de las actualizaciones de Ubuntu que no llegan a resolver la conexión y quedan en ese estado). Ahora pasa algo extraño, tengo Dual boot con Windows 7 y extrañamente ahi no ocurre lo mismo, funciona bien, salvo que más lento. No sé cuál será el problema, no soy técnico ni ingeniero en comunicaciones ni en informática pero creo yó que tocaron algo en el servidor o la central porque casualmente encontré a infinidad de personas (básicamente usuarios de GNU/Linux & Mac) con el mismo problema y algunos con Windows. Entre otras cosas mencionan el tema de Fibertel y la ampliación de la capacidad de Speedy para recibir a los usuarios que dejen Fibertel (Uff). En fín me gustaria saber si a los usuarios de Ubuntu como yo, o de otras distros e inclusive de Mac y Win les ocurre lo mismo con su conexión de Speedy.

Posteo los links de foros con el mismo problema:

[http://www.bandangosta.com.ar/index.php/topic,5194.0.html](http://www.bandangosta.com.ar/index.php/topic,5194.0.html)

[http://old.nabble.com/-ubuntu-ar--extra%C3%B1o-problema-con-la-navegaci%C3%B3n-en-internet-td29802461.html](http://old.nabble.com/-ubuntu-ar--extra%C3%B1o-problema-con-la-navegaci%C3%B3n-en-internet-td29802461.html)

[http://www.macusergroup.com.ar/foro/showthread.php?t=28834]("http://www.macusergroup.com.ar/foro/showthread.php?t=28834")

PD: Este problema comenzó en mi caso a partir del 15 de Setiembre pasado.

---

### Post by hectorivand on 2010-09-28
Es raro lo que comentas, probaste cambiando los servidores DNS? proba con estos: 200.47.82.3 y 200.47.82.4.

Tal vez esta sucediendo que no esta resolviendo bien, solamente lo hace hasta el proxy cache de ellos y te muestra lo que tiene cacheado Speedy.

No me suena a filtrado por parte de ellos a usuarios de Linux o cualquier otro sistema operativo, técnicamente es al divino boton y sobre todo complicado.

Proba con lo de los DNS, es fija de telefónica que cada tanto fallen los servidores.

Contanos después como lo viste.

Saludos
Nacho

---

### Post by atari130xe on 2010-09-28
> **hectorivand said:**
> Es raro lo que comentas, probaste cambiando los servidores DNS? proba con estos: 200.47.82.3 y 200.47.82.4.

Tal vez esta sucediendo que no esta resolviendo bien, solamente lo hace hasta el proxy cache de ellos y te muestra lo que tiene cacheado Speedy.

No me suena a filtrado por parte de ellos a usuarios de Linux o cualquier otro sistema operativo, técnicamente es al divino boton y sobre todo complicado.

Proba con lo de los DNS, es fija de telefónica que cada tanto fallen los servidores.

Contanos después como lo viste.

Saludos
Nacho

Hola Nacho gracias por la sugerencia de los DNS pero no sirvieron, en realidad ya probé con un par y es lo mismo:
OpenDNS, Google DNS y los que vos posteaste, en realidad debe ser un tema del hard of soft del servidor, que será lo desconozco, pero curiosamente todo empezó a andar mal a partir del día 15 de Septiembre como a la gran mayoría, es algo muy curioso.

---

### Post by hectorivand on 2010-09-28
> **atari130xe said:**
> Hola Nacho gracias por la sugerencia de los DNS pero no sirvieron, en realidad ya probé con un par y es lo mismo:
OpenDNS, Google DNS y los que vos posteaste, en realidad debe ser un tema del hard of soft del servidor, que será lo desconozco, pero curiosamente todo empezó a andar mal a partir del día 15 de Septiembre como a la gran mayoría, es algo muy curioso.

Ok, tal vez estan haciendo cambios en el Dslam, con lo cual, debe ser un problema general y no que afecte a usuarios/equipos con GNU especificamente, le debe afectar a todos. A algunos más, otros menos, dependiendo de la distancia con la central y la calidad de los pares, hay muchos factores a tener en cuenta.

Por lo pronto, Paciencia.

Saludos
Nacho

---

### Post by atari130xe on 2010-09-28
> **hectorivand said:**
> Ok, tal vez estan haciendo cambios en el Dslam, con lo cual, debe ser un problema general y no que afecte a usuarios/equipos con GNU especificamente, le debe afectar a todos. A algunos más, otros menos, dependiendo de la distancia con la central y la calidad de los pares, hay muchos factores a tener en cuenta.

Por lo pronto, Paciencia.

Saludos
Nacho

Asi es Nacho, acabo de hablar con el soporte técnico y me dijeron que están tratando de ver cuál es el problema (no lo saben aún) me transfirieron con la parte comercial para que me descuenten los días con mal servicio, yo tmb creo que es un problema de cambio de hardware (DSLAM parecer ser el tema) me reconocieron que el problema existe pero que todavía no pueden saber que lo ocasiona.
MI casa se encuentra a menos de 500Mts de la central.
Saludos!

---

### Post by alfplayer on 2010-09-28
Algunos usuarios dicen que mejora con un web proxy, así estarían salteando el proxy de Speedy.

---

### Post by biale on 2010-09-28
Desde el thread análogo... 
[http://ubuntuforums.org/showthread.php?t=1576584]("http://ubuntuforums.org/showthread.php?t=1576584")

> ...así estarían salteando el proxy de Speedy.

Tiene sentido que Speedy pueda tener instalado un proxy? 

Estoy esperando contar con un poco de tiempo para probar instalando un squid, algo que no hice nunca.

Curiosamente esta vez llegó la factura de speedy (correspondiente a octubre) hace unos días, con una anticipación extraordinaria.

---

### Post by ioargento on 2010-09-28
Qué bueno que finalmente encontré a alguien más con estos problemas, comenzaba a pensar que la cantidad de veces que llamé al 08003377333 eran en vano y el que tenia un problema era yo, en la cabeza!

Les cuento mi situación, tengo el mismo problema que ustedes plantean con Speedy 5 megas, me han cambiado el modem, he navegado a través de servidores proxy con el mismo problema, cambié 20 dns's incluyendo los de speedy y todo ofrece el mismo resultado: una conexion intermitente. 

Lo verdaderamente raro es que si en Ubuntu, cualquier version, tengo 20% de navegación satisfactoria (o sea que si pongo una dir solo el 20% de las veces la carga bien), en Windows Vista tengo un 99% o sea, por alguna extraña razón (y con esto es que siempre el tecnico que viene a casa me hecha fly y pone como resuelto el ticket de servicio tecnico) en Windows Vista el problema no se me manifiesta.

Hay un thread en inglés [http://ubuntuforums.org/showthread.php?t=1526664]("http://ubuntuforums.org/showthread.php?t=1526664") donde estaba intentando encontrar alguna info, pero se ve que sólo a nosotros en castellano nos maltrata Speedy.

El técnico vino 2 veces ya, y obviamente no sabe qué hacer, pero el problema es que para no perjudicarse, pone como resuelto el asunto... y no lo está! Por esta razón es importante que sigamos quejándonos, esto no lo van a resolver con el pasar del tiempo a menos que hagamos suficiente presion.

Espero respuestas, quizás podamos encontrar alguna solución temporal...

---

### Post by N3RI on 2010-09-28
yo lamentablemente decidí cambiarme de proveedor, cansado de que me cancelen las venidas del técnico (evidencia clara de que saben que el problema es de ellos y al pedo te mandan el técnico)

Como nota de color, un par de días estuve sin internet y les usé el wifi a mis vecinos :) en el que tiene Telecentro me conectaba todo perfecto, y el que tiene speedy 3play me da el mismo problema (que seguramente él sufre, pero mucho menos, al tener windows)

---

### Post by atari130xe on 2010-09-28
> **biale said:**
> Desde el thread análogo... 
[http://ubuntuforums.org/showthread.php?t=1576584]("http://ubuntuforums.org/showthread.php?t=1576584")



Tiene sentido que Speedy pueda tener instalado un proxy? 

Estoy esperando contar con un poco de tiempo para probar instalando un squid, algo que no hice nunca.

Curiosamente esta vez llegó la factura de speedy (correspondiente a octubre) hace unos días, con una anticipación extraordinaria.

En el link de Mac users aparece el problema también con squid

Que casualidad que la factura de Duo tmb me llegó muchísimo antes que de costumbre (el 14 de set y vence el 6 de Octubre) mmmm

---

### Post by ioargento on 2010-09-28
Efectivamente reconozco que es un tema de Speedy porque llevando la notebook a otros lugares con Telecentro o Fibertel, la conexion es normal. En mi casa con Speedy sin modificación alguna es insufrible y con la conexion de mis vecinos que tmb tienen Speedy sucede lo mismo. 

Igual creo que hay que presionar, porque sino no se solucionan los problemas y los que nos perjudicamos somos nosotros a la larga. Siempre hay alguna forma de obligarlos a recibir una compensación por el servicio deficiente, es lo justo.

---

### Post by alfplayer on 2010-09-28
> **atari130xe said:**
> En el link de Mac users aparece el problema también con squid

Sí, pero con Squid usando la conexión de Speedy, no para saltear el proxy de Speedy.

---

### Post by biale on 2010-09-28
> con Squid usando la conexión de Speedy, no para saltear el proxy de Speedy. 

No entendí la diferencia. Sockets?

---

### Post by alfplayer on 2010-09-28
ioargento: Si tenés el problema del F5 mejor aclará que es problema del ISP en el thread en inglés que estás participando.

---

### Post by alfplayer on 2010-09-28
La diferencia es que si el proxy se conecta a los servidores web con la conexión de otros ISP se saltea el proxy trasparente.

---

### Post by ioargento on 2010-09-29
alfplayer, mirá de todas formas no es casual que funcione bien en windows y mal en ubuntu, alguna variable entre dichos sistemas debe existir en torno a la conexion. 

Es por esto que yo buscaba una solución técnica y creo que debe haberla, más allá de si en Speedy hacen bien o mal las cosas, o aplican algun tipo de restriccion, o simplemente desidia...

---

### Post by atari130xe on 2010-09-29
Casualmente hice un post en "comunidad" en este foro sobre el mismo problema que vengo teniendo desde el 15 de setiembre y resulta que uno de los operadores entre tanta sanata que me dijeron luego de llamar no menos de 12 veces al 0800 333 7733 opción 0 me dijo que ellos con "Dr Speedy" previo pago de $ 20.- (hay que contratarlo, ellos estaban brindando un servicio que funcionaba bien hasta el 15/09/2010 y de repente por un problema que no tiene que ver con el usuario sino con ellos mismos -llámese de hard o soft y la configuración de los mismos- te enchufan un cargo "extra" por "solucionarte" un problema que originan ELLOS mismos), lo más extraño de todo esto es que por ej. en Windows 7 funciona relativamente bíen, no hay micro cortes o fallas de conexión, no será alguna movida de Microsoft? la verdad que uno puede "desvariar" con estas cosas, pero sabiendo lo que son como empresa y sus estrategias para conseguir lo que quieren no seria tan loco pensar algo así (cabe aclarar que el mismo problema lo tienen los usuarios de Mac). Para pensar...

---

### Post by N3RI on 2010-09-29
No sé si realmente sea oportuno a llegar a pensar que es una movida sucia tercermundista de Microsoft. En mi caso por ejemplo, en una de las compus tengo xubuntu y windows xp, y anda mal en ambos SO. En la otra tengo ubuntu y windows 7, y en w7 anda considerablemente mejor (pero también tiene problemas)

Y tengo un amigo con el mismo problema (que "ya se acostumbró" según me dijo) y tengo entendido que él tiene windows 7 (no estoy seguro, pero que es windows, es windows)

Lo más probable es que sea algo en lo que windows sea menos quisquilloso que linux y el resultado sea ese. Hasta ahora nadie encontró la causa, ni yo (ya se me acabaron todos los trucos que sé) ni los técnicos que te mandan a tu casa, ni los que te atienden el teléfono ni nadie de varios foros que consulté sobre el tema.

---

### Post by atari130xe on 2010-09-29
Si fué una locura que se me cruzó jejeje pero bueno el gran problema es que ellos no reconozcan de manera pública que es un problema de ellos y no de los sistemas Unix like (GNU/Linux y Mac) porque yo tmb sé de casos de Windows, que estarán haciendo solo ellos lo saben...

---

### Post by alfplayer on 2010-09-29
Windows parece afectado pero menos, si win tuviera los problemas de linux esto sería un "desastre" nacional.

---

### Post by guillermolisi on 2010-09-29
Si se pudiera verificar esto de que con Windows funciona "menos mal" que con Linux entonces iria por el lado del tamaño de paquete TCP/IP que normalmente utilizan por defecto.

Si los tamaños difieren, entonces el tema podria pasar por paquetes TCP fuera de medida (respecto de lo que espera algun equipo en el NOC de TASA) y que obligan a retransmisiones hasta que se completan, con la sobrecarga que implica en las conexiones.

---

### Post by biale on 2010-09-29
Guillermo: Mantengo la tesitura de mi post anterior, en este mismo thread. Te cuento:

Arranque Wireshark (ethereal) y confirme la presencia de paquetes TCP/RST. O sea que la conexión se corta abruptamente. Ahora bien, cuando uso "Virtualbox/WXP/Firefox-3.6.3" esos paquetes no aparecen. Y ese es mi workaround provisorio...

Los MTUs para WXP en principio son los mismos o muy parecidos. Pero es cierto que si a Ubuntu le bajo el MTU a 1462 la cosa mejora "un poco".

Tambien es cierto que si utilizo un FFox "null" la cosa mejora, en este caso bastante mas. Para eso directamente usé en la misma compu un usuario distnto, un usuario de pruebas. 

Parece que las situaciones difieren según los lugares que se quieran considerar. Hay gente que si tiene problemas con W$, pero se mezclan con todo lo que siempre anduvo dando vueltas. Al menos en mi situación es un problema Speedy-Linux

Otro si, conectándose en horarios de baja el funcionamiento mejora muchísimo, algo que también debería ser tomado en cuenta.

---

### Post by mama21mama on 2010-09-29
Hola, fibertel anda para atrás también aquí en Lincoln.
La verdad no se de que nodo se conectan speedy y fibertel pero da la sensación que aveces se ponen de acuerdo (chupan internet del mismo lado) o por casualidad se caen al mismo tiempo.

:s

me pasa lo mismo con fibertel se corta esto che

---

### Post by biale on 2010-09-29
En algún punto se unen y es posible que esten intercambiando picardías...

---

### Post by atari130xe on 2010-09-29
> **guillermolisi said:**
> Si se pudiera verificar esto de que con Windows funciona "menos mal" que con Linux entonces iria por el lado del tamaño de paquete TCP/IP que normalmente utilizan por defecto.

Si los tamaños difieren, entonces el tema podria pasar por paquetes TCP fuera de medida (respecto de lo que espera algun equipo en el NOC de TASA) y que obligan a retransmisiones hasta que se completan, con la sobrecarga que implica en las conexiones.

Sería cuestión de probar Guillermo, si querés pasame como hacerlo y lo pruebo en ambos (Ubuntu y Win 7) gracias!

---

### Post by omniwired on 2010-09-30
Tengo el mismo problema, cambiar el MTU se hace o desde el modem/router (ejemplo 192.168.0.1) ir a "Basic -> WAN" si tienen el huawei.


y/o 

desde la consola con

sudo ifconfig (interfase de red) mtu (numero que queramos)

A modo de ejemplo
```

sudo ifconfig eth0 mtu 1460

```

No se podria hacer algo loco con un squid proxy?

---

### Post by atari130xe on 2010-09-30
Extractado de uno de los links que posteé más atrás, si alguien que es Licenciado en sistemas usa Ubuntu y le viene pasando lo mismo desde hace 1 mes y probó muchas cosas, es evidente que es algo pura y exclusivamente de Speedy & Telefónica:

> Re: [ubuntu-ar] extraño problema con la navegación en internet
Click to flag this post

by Marcelo Fernandez Sep 28, 2010; 11:47am :: Rate this Message: - Use ratings to moderate (?)

Reply | Print | View Threaded | Show Only this Message
El día 28 de septiembre de 2010 02:20, leo fishman
<leofishman@...> escribió:
> Hoy hable nuevamente a soporte de speedy por otro tema, pero milagrosamente,
> intentaron darme soporte sobre ubuntu!
> No lo lograron del todo, pero valoro la intencion.
> Segun ellos, el problema esta en el preload del dns, primero me indicaron
> que suba el mtu a 1492, cuando le dije que ya lo tenia en 1500, me pasaron
> un comando que aparentemente funciona en mac:
> sudo defaults write com.apple.safari WebKitDNSPrefetchingEnabled -boolean
> false

A ver, nunca escuché acerca de un parámetro "preload del caché DNS"; a
lo sumo encuentro esto [1], que es similar a tocar a mano el
/etc/hosts de Linux y no tiene nada que ver con el problema, y esto
[2][3], que sugiere un problema del módem/router respondiendo
peticiones DNS (asumo que uno tendría que tener configurado como DNS
el modem/router en su PC).

Intentando darle un contexto, entiendo que el browser hace un caché de
la IP del servidor para evitar preguntar repetidamente al DNS por
nombres de dominio ya resueltos o que si el usuario va a un link, el
browser va a necesitar (sería un "query optimista"). Así y todo, no
entiendo que eso tenga que ver con el problema, porque:

- Les pasa a muchos usuarios a la vez, en regiones geográficas
totalmente diferentes y con modems/estructuras de red diferentes.
- Pasó de un día a otro.
- Cambio los DNSs a Google, OpenDNS, Speedy, etc. y el problema persiste.
- En mi trabajo o en cualquier otro lado que no haya Speedy, la misma
PC con el mismo navegador, configuraciones y demás, *funciona
perfecto*.
- Hice sniffing de tráfico, y muy claramente, al SYN del navegador, el
destino (que no es el destino real, es el proxy transparente de
Speedy), devuelve RST. Con lo cual *no es problema de DNS*.
- Esto más allá de que cuando logra establecer una conexión anda *muy
lento* (tasas de transferencias de no más de 20 KB/seg).

> Probe ejecutarlo, pero seguian los microcortes. Entonces me ofrecieron
> cambiar el modem zyxel.

Ojalá me equivoque, pero me parece que te están peloteando... Lo que
te dijeron hasta acá tiene más que ver conque han buscando en Google
por "páginas rotas navegador cómo arreglar no tengo idea de redes" que
por preguntarle a sus "técnicos" dónde está el problema.

> Lo raro es que por ahora viene andando bien, quizas sea por la hora, son mas
> de las 2 am, tuve que usar un rato el windows y pude comprobar que tambien
> tiene el mismo problema, aunque menos frecuente que en ubuntu.

Mi humilde diagnóstico es que tienen problemas en el proxy
transparente o sus firewalls (SYN cookies desactivados por ejemplo) o
no aguantan la carga y te devuelve un RST como si los usuarios le
estuviéramos haciendo un DoS [4] a sus proxies. Esta teoría se adecúa
a lo que vos observaste (y yo también), que tiene que ver con el
horario en que uno usa la conexión.

Que tengan problemas, uno, dos días, una semana... pero ya va más de
un mes en mi caso.

[1] [http://technet.microsoft.com/en-us/library/cc787573(WS.10).aspx](http://technet.microsoft.com/en-us/library/cc787573(WS.10).aspx)
[2] [http://support.apple.com/kb/TS3408?viewlocale=es_ES&locale=es_ES](http://support.apple.com/kb/TS3408?viewlocale=es_ES&locale=es_ES)
[3] [http://www.faq-mac.com/40643/problemas-navegacion-safari-5-desactiva-prefetching-dns](http://www.faq-mac.com/40643/problemas-navegacion-safari-5-desactiva-prefetching-dns)
[4] [http://en.wikipedia.org/wiki/Denial_of_service](http://en.wikipedia.org/wiki/Denial_of_service)

Saludos
PD: Ojo con el Top-Posting.
-- 
Marcelo F. Fernández
Buenos Aires, Argentina
Licenciado en Sistemas - CCNA

E-Mail: marcelo.fidel.fernandez@...
Blog: [http://blog.marcelofernandez.info](http://blog.marcelofernandez.info)
Twitter: [http://twitter.com/fidelfernandez](http://twitter.com/fidelfernandez)

-- 
Ubuntu-ar lista de correo
Ubuntu-ar@...
Modifica tus opciones o desuscribite en: [https://lists.ubuntu.com/mailman/listinfo/ubuntu-ar](https://lists.ubuntu.com/mailman/listinfo/ubuntu-ar)
Siempre leer, comprender y aplicar nuestra etiqueta: [https://wiki.ubuntu.com/ArgentinaTeam/EtiquetaML](https://wiki.ubuntu.com/ArgentinaTeam/EtiquetaML)


Otro link del año apsado con un caso identico al que padecemos todos en estos momentos:

[http://www.sabermenos.com.ar/%C2%BF-que-pasa-con-speedy-en-argentina/]("http://www.sabermenos.com.ar/%C2%BF-que-pasa-con-speedy-en-argentina/")

---

### Post by atari130xe on 2010-09-30
> **omniwired said:**
> Tengo el mismo problema, cambiar el MTU se hace o desde el modem/router (ejemplo 192.168.0.1) ir a "Basic -> WAN" si tienen el huawei.


y/o 

desde la consola con

sudo ifconfig (interfase de red) mtu (numero que queramos)

A modo de ejemplo
```

sudo ifconfig eth0 mtu 1460

```

No se podria hacer algo loco con un squid proxy?

Tengo un Modem ZTE 831 II en modo router... sabés como modificarlo? ya entré al setup del modem pero no encuentro la opción de cambio del MTU

---

### Post by alfplayer on 2010-09-30
> **atari130xe said:**
> Tengo un Modem ZTE 831 II en modo router... sabés como modificarlo? ya entré al setup del modem pero no encuentro la opción de cambio del MTU

Por qué no probás cambiarlo en linux?

---

### Post by adank92 on 2010-09-30
Muchachos, ami me esta pasando lo mismo, ya llame a speedy y me dijeron que es un problema interno de ellos con los usuarios de Linux & Mac.

Pase 2 dias enteros cambiando de NiC y pasaba lo mismo hasta que me resigne y los llame.

Me dijeron que llame mañana para ver lo que pasó, igual ya se que me van a b******r denuevo, pero voy a hacer lo posible por romperle las b***s a ellos.


Saludos!:popcorn:

---

### Post by mama21mama on 2010-10-01
> <mama21mama> se me corta el Internet por que en Lincoln, fibertel paga la fibra óptica a telefónica de argentina. recién me dijo eso los de soporte que vinieron a mi casa.
<mama21mama> o sea, fibertel y telefónica chupan Internet del mismo lado en Lincoln.
<mama21mama> hasta fin de año que fiber tenga su propia fibra.

[como dije en irc.]("http://logs.ubuntu-eu.org/free/2010/10/01/%23ubuntu-ar.html")
fibertel le compra en Lincoln el uso de fibra óptica, y anda saber en donde mas pasara lo mismo.

Me siento afectado yo también al andar mal speedy, por que uso fibertel.
Solo me queda la esperanza que me dijeron los muchachos de soporte de fibertel que a fin de años tendrán en esta zona su propia fibra óptica.

posible sabotaje:
Seguramente por el q******o de fibertel, los de speedy tenían orden de cierto rango de conexiones ajenas a speedy hacerlas andar mal. (opinión personal miá, una teoría)

---

### Post by marcelo_bur on 2010-10-02
Hola,estoy navegando para ver si me puedo enterar de que está pasando con Speedy. Lo he tenido por muchisimos años y nunca había tenido tantos problemas. Las páginas cargan mal, hoy incluso las descargas de archivos desde sitios como Hotfile, Megaupload, etc, que antes andaban rapidisimo, tampoco funcionan bien.
No creo que sea un problema con Linux, uso muy poco Windows pero también me sucede casi lo mismo, quizás un poco menos, o quizás me parece menos por el poco uso que le doy. Por ahí lei algo de cambair el valor del MTU en el router, voy a ver que pasa, dicen que bajandolo un poco anda mejor.
No he hecho reclamos a Speedy porque se que no dan bolilla. Si con suerte te dan algo de razón, como he leido en este post, a la larga no pasan de eso, dificilmente te descuentes los días con mal servicio y, si no sabes lo suficiente, o al menos algo (o sea si sos muy nuevito en internet), te enroscan la víbora de tal forma que te dejan creyendo que la culpa de todo es pura y exclusivamente tuya.
Bueno, por ahora voy a seguir navegando (dentro de lo que se pueda) y haciendo pruebas, tambien me comentaron sobre usar un proxi virtual, en un rato voy a probar con este: [http://www.tuvpn.com/proxy/index.php?ln=es]("http://www.tuvpn.com/proxy/index.php?ln=es"), también tengo la opción de instalar un proxi en mi servidor, no se, si algo de todo esto funciona lo publico.
saludos.

Marcelo

---

### Post by marcelo_bur on 2010-10-02
No estoy muy seguro pero parece que bajar el MTU de 1492 a 1476 mejoró un poco las cosas. Lo del proxi virtual no hizo diferencia.
Da bronca y uno piensa en cambiar de proveedor, sin embargo he leido por ahí que el mismo problema se está dando en casi todos los ISP de Argentina.
La verdad no se que pasa, muchos comentarios en la red dicen que todo esto comenzó el 15 de septiembre pasado, yo no recuerdo con exactitud la fecha, sin embargo asocio el comienzo de estos problemas con el lio que se armó con Fibertel.
Saludos.

---

### Post by atari130xe on 2010-10-02
> **marcelo_bur said:**
> Hola,estoy navegando para ver si me puedo enterar de que está pasando con Speedy. Lo he tenido por muchisimos años y nunca había tenido tantos problemas. Las páginas cargan mal, hoy incluso las descargas de archivos desde sitios como Hotfile, Megaupload, etc, que antes andaban rapidisimo, tampoco funcionan bien.
No creo que sea un problema con Linux, uso muy poco Windows pero también me sucede casi lo mismo, quizás un poco menos, o quizás me parece menos por el poco uso que le doy. Por ahí lei algo de cambair el valor del MTU en el router, voy a ver que pasa, dicen que bajandolo un poco anda mejor.
No he hecho reclamos a Speedy porque se que no dan bolilla. Si con suerte te dan algo de razón, como he leido en este post, a la larga no pasan de eso, dificilmente te descuentes los días con mal servicio y, si no sabes lo suficiente, o al menos algo (o sea si sos muy nuevito en internet), te enroscan la víbora de tal forma que te dejan creyendo que la culpa de todo es pura y exclusivamente tuya.
Bueno, por ahora voy a seguir navegando (dentro de lo que se pueda) y haciendo pruebas, tambien me comentaron sobre usar un proxi virtual, en un rato voy a probar con este: [http://www.tuvpn.com/proxy/index.php?ln=es]("http://www.tuvpn.com/proxy/index.php?ln=es"), también tengo la opción de instalar un proxi en mi servidor, no se, si algo de todo esto funciona lo publico.
saludos.

Marcelo

Jejeje acá hay años de dial up con Arnet, Ciudad Internet y con Advance, bastante tiempo con Speedy en lineas diferentes de tel, yo reclamo y como ya tengo bastante experiencia en esto de las compensaciones por malas prestaciones, espero lograr lo que corresponde, que me descuenten todos estos días de mal servicio. De echo uno de los operadores que supuestamente dan "soporte a Linux" me dijo haciendose el "gallito": Ud contrate Dr. Speedy y van a su casa le instalan "el parche" (ni que fuera bicicleta) que deja su pc en "condiciones" para navegar, un papanatas a la enésima potencia. Me "amenazó" con que Speedy no tiene problemas brindandome el servicio, que en Windows "anda bién" y ya con eso "estamos cubiertos" (para no descontar los dias sin servicio) "pero ud. por favor no le comente esto a nadie su vuelve a comunicarse con nosotros" :confused: Por lo visto, la capacitación de estos operadores es pobrísima, yo trabajé unos meses en un call center para un proveedor de Triple play de USA (Time Warner Cable) y sé todo lo que es asimilar mucha info para dar un mínimo y aceptable soporte técnico para Telefonía, TV digital e Internet de hasta 20MB. hay que insistir y llamar todas las veces necesarias que total es un 0800 solo perdemos un poco de tiempo, pero al menos no van a pensar que los usuarios de GNU/Linux & Mac somos clientes de 2da.

---

### Post by biale on 2010-10-02
No creo que esten totalmente "cubiertos". Si funcionaba y dejó de funcionar, queda claro que no estan pudiendo dar servicio a Linux/Mac. A mi manera de ver, no dar servicio no es lo mismo que no dar soporte.

Por ejemplo, tendrían que aclarar de donde obtener el supuesto el parche, quien lo hizo y "que altera". Las reglas básicas se aplican a todos...

También implica aceptar que es una modificación del status quo que llegó para quedarse, o sea que potencialmente es una posición tomada por la compañía. 

Incluso hay que tener muy en cuenta que la navegación funciona casi bien en las horas de baja.

Mi sugerencia: "aunque sea anoten el número de reclamo"

---

### Post by heliotropo on 2010-10-02
Después de dos semanas y sospechando que podía ser mi Ubuntu ya que le pasaba a un amigo que también tiene Ubuntu. Hoy instale Debían y también me pasaba lo mismo, cambie de módem uno que me quedo por ahí y también seguía igual, con paginas que hay que recargar hasta que las toma o que cargan sin formato. Por lo cual después de hacer todo esto me digne o resigne a llamar a el servicio técnico de speedy, aquí me comentaron que el problema es de los servidores de ellos que no se que tocaron con la petición de paquetes y sarasa, alegando que los sistemas operativos basados en Unix tipo Linux y Mac negociaban con paquetes mas grades y que la nueva configuración no lo soportaba. Por lo cual están resolviendo el problema a los usuarios usan estos sistemas y hacen el reclamo en las 24 horas luego de realizado el reclamo...
Apenas pasaron unas horas y nada. Así que esperare las 24 horas y comento si se soluciono.

---

### Post by dirty fingers on 2010-10-03
me anda horrible ! odio a todos los servicio de comunicaciones de la argentina ! ya probe con 3 modem. Falla la conexión solo en conexiones http.

---

### Post by atari130xe on 2010-10-04
> **heliotropo said:**
> Después de dos semanas y sospechando que podía ser mi Ubuntu ya que le pasaba a un amigo que también tiene Ubuntu. Hoy instale Debían y también me pasaba lo mismo, cambie de módem uno que me quedo por ahí y también seguía igual, con paginas que hay que recargar hasta que las toma o que cargan sin formato. Por lo cual después de hacer todo esto me digne o resigne a llamar a el servicio técnico de speedy, aquí me comentaron que el problema es de los servidores de ellos que no se que tocaron con la petición de paquetes y sarasa, alegando que los sistemas operativos basados en Unix tipo Linux y Mac negociaban con paquetes mas grades y que la nueva configuración no lo soportaba. Por lo cual están resolviendo el problema a los usuarios usan estos sistemas y hacen el reclamo en las 24 horas luego de realizado el reclamo...
Apenas pasaron unas horas y nada. Así que esperare las 24 horas y comento si se soluciono.


La última operadora que me atendió me dijo el Viernes pasado que en 48/72hs. habría novedades... mmm hoy ya es Lunes y la cosa sigue tan mal como el 15 de Setiembre...

---

### Post by KAYAMAN0 on 2010-10-04
Hola todos, les comparto un poco de info como lo hice en el foro de bandaangosta.

Antes que nada, quiero decir que hasta hace 15 dias era uno de los pocos afortunados usuarios de speedy que no habia tenido problemas con el servicio. Mas alla de algun limite de descarga por connecion internacional(50 KB/s aprox.), nada de mayores complicaciones.

A mediados de septiembre empezaron los problemas de navegacion. En un comienzo pense que se trataba de un problema con el modem, ya sea de hard o configuracion. Primero probe el speedtouch 330(usb) que me dio tasa hace unos 5 anos cuando instale el servicio. Le siguio un Edimax 7084 modem/router, y por ultimo, mi configuracion actual, un Cisco 1801 con modem POTS Alcatel integrado. Pero **el problema se presenta con todos los equipos.**

Ademas, por la cantidad de usuarios afectados, claramente no es un problema de las lineas. Mis valores el modem:

> Capacity Used:   51%                           
Noise Margin:    23.5 dB                         
Output Power:    16.5 dBm                       
Attenuation:     30.0 dB                      

Descartado eso, necesariamente el problema estaba en la red de tasa o alguno de sus upstream. Aunque tambien tenia problemas cuando navegaba sitios dentro del mismo AS, por lo que evidentemente es un quilombo de la red de telefonica.

Luego analizar un poco el trafico con un packet sniffer, saque estas conclusiones:
1-**No **es un problema con los DNS.
2-Solo se afecta el trafico TCP, puerto 80(HTTP).
3-No afecta a trafico HTTPS, ej : webmail, homebanking, etc.
4-No afecta P2P.
5-LOS PROXIES DE SPEEDY ANDAN COMO EL O**O!!

El proxy que esta afectando a mi zona es un **Blue Coat, IP:200.63.157.190**

Resumiendo un poco, el problema esta cuando se intenta establecer una conexion TCP con algun sitio HTTP, se recibe un RESET de la conexion, provocando la caida de las misma y que el navegador nos muestre " Imposible mostrar la pagina" o "Unable to connect". Aparentemente, el problema es mas apreciable en sistemas del tipo UNIX; ej:linux,mac,BSD,etc, que con Windows debido a la forma que manejan el protocolo.

Para mas detalle, les pongo 2 TCP-traceroutes que muestra la diferencia de camino entre HTTP y HTTPS:

#tcptraceroute speedy.com.ar -p 80
traceroute to speedy.com.ar (209.13.119.32), 30 hops max, 60 byte packets
 1  192.168.0.1 (192.168.0.1)  1.437 ms  1.337 ms  1.286 ms
 2  200.51.241.185 (200.51.241.185)  11.417 ms  11.059 ms  11.809 ms
 3  200.51.234.100 (200.51.234.100)  11.540 ms  24.798 ms *
** 4  200-63-157-190.speedy.com.ar (200.63.157.190)  14.431 ms  11.227 ms  11.905 ms**
 5  * speedy.com.ar (209.13.119.32)  974.424 ms *

# tcptraceroute speedy.com.ar -p 443
traceroute to speedy.com.ar (209.13.119.32), 30 hops max, 60 byte packets
 1  192.168.0.1 (192.168.0.1)  1.461 ms  1.282 ms  1.245 ms
 2  200.51.241.185 (200.51.241.185)  11.196 ms  11.450 ms  11.670 ms
 3  * * 200.51.234.100 (200.51.234.100)  12.114 ms
 4  speedy.com.ar (209.13.119.32)  12.187 ms  13.426 ms  14.466 ms


Espero que la data le sea de ayuda para entender un poco mejor lo que pasa, y sobre todo que telefonica arregle esta c****a que se mandaron.
Saludos a todos!

---

### Post by heliotropo on 2010-10-04
> **atari130xe said:**
> La última operadora que me atendió me dijo el Viernes pasado que en 48/72hs. habría novedades... mmm hoy ya es Lunes y la cosa sigue tan mal como el 15 de Setiembre...

Así es estamos a lunes y todo sigue igual. Al fin del día vuelvo a insistir....
Si el problema no tiene solución tendre que ver a que empresa migrar.

---

### Post by marcelo_bur on 2010-10-04
Hola. Yo insisto en que esto no tiene nada que ver con Linux en particular. Todo lo que dicen los de soporte técnico sobre parches y cosas por el estilo son estupideces, simples "parches" con los cuales intentan cubrir su ignorancia. De acuerdo a lo que he leido ayer en montones de foros y blogs el problema afecta tanto a usuarios de Windows como a cualquier otro. Lo que si es cierto, y que yo reclamé en su momento a Speedy, es que Terabox está diseñado especialmente para Windows y este dato figura en la letra chica de los términos y condiciones del servicio, y que muchas veces tenemos la mala costumbre de no leer. Sin embargo incluso el problema con Terabox está solucionado en Ubuntu 10.04 (tengo que cambiar mi versión en el perfil...). Desde ayer tarde las descargas nuevamente funcionan bien y Terabox vuela. Antes que comenzara el famoso síndrome F5 mi velocidad de descarga desde sitios como Neload rara vez superaba los 50 kb/s, sin embargo, como se ve en este captura, estoy descargando a 108 kb/s.

[http://img683.imageshack.us/img683/280/pantallazo27.png](http://img683.imageshack.us/img683/280/pantallazo27.png) - Abran la imagen aparte porque me quedó muy grande y deformaba las tablas del foro.

Alguna macana se mandaron los de Speedy y afecta a todos los usuarios, cual sea el sistema operativo que utilizen.

Saludos

---

### Post by malatesta on 2010-10-04
Mismo problema con speedy. En windows xp no hay mayores dramas. Tenía el mtu bajo 1392, lo pase a 1492 y *parece mejorar*.

Espero tiren una solución los de timofónica.

Slds

corrección, no mejoró...
pruebo con mtu=1462 y les cuento...pinta mejor.

---

### Post by biale on 2010-10-04
aqui el traceroute da distinto...

$ tcptraceroute speedy.com.ar -p 80
traceroute to speedy.com.ar (209.13.119.32), 30 hops max, 60 byte packets
 1  192.168.1.1 (192.168.1.1)  1,219 ms  1,234 ms  1,122 ms
 2  * * *
 3  200.51.233.144 (200.51.233.144)  9,409 ms  9,489 ms  9,005 ms
 4  200-63-158-134.speedy.com.ar (200.63.158.134)  9,161 ms  9,618 ms  10,665 ms
 5  200.51.233.135 (200.51.233.135)  10,587 ms  9,794 ms  11,121 ms
 6  209.13.133.57 (209.13.133.57)  14,104 ms *  12,153 ms
 7  200.5.87.82 (200.5.87.82)  13,761 ms * *
 8  * * *
 9  * * *
10  * * *
11  * * *
12  * * *
13  *      "olvidalo"

$ tcptraceroute speedy.com.ar -p 443
traceroute to speedy.com.ar (209.13.119.32), 30 hops max, 60 byte packets
 1  192.168.1.1 (192.168.1.1)  1,106 ms  1,265 ms  1,105 ms
 2  * * *
 3  200.51.233.144 (200.51.233.144)  8,824 ms  10,410 ms  49,373 ms
 4  200-63-158-134.speedy.com.ar (200.63.158.134)  11,595 ms  10,981 ms  11,868 ms
 5  200.51.233.135 (200.51.233.135)  11,761 ms 209.13.119.32 (209.13.119.32)  11,119 ms  11,286 ms
(OK)

---

### Post by atari130xe on 2010-10-04
En Mi caso no toco más nada porque como el problema no es mío solo espero que los responsables le dén solución.

---

### Post by Sergius14 on 2010-10-04
Veo que mi problema, desde mediados de Septiembre, es mucho más masivo de lo que pensaba. Pensaba que era un pobre tipo pero somos muchos los infelices.

Será cuestión de esperar (reclamando, por supuesto) a que se arregle. No hay que dejar de reclamar.

El problema en cuestión no lo van a ver haciendo pings o traceroutes.

Primero, porque ping solo prueba una parte de ICMP y el problema está en el protocolo TCP (quizás UDP, pero no lo probé).

Tampoco traceroute, que solo prueba mediante ICMP y el TTL modificado para ver los soltos hasta el destino.


En este caso, la prueba fehasiente es analizando el tráfico con Wireshark y ver en detalle que está pasando.


Deberían notar algo así como:

Inciar la captura (sin hacer uso de internet, para que el trafico sea poco y se pueda analizar rapidamente)

Poner en el browser la IP de una página (la IP de google por ej.)

Si la pagina abre bien, van a ver trafico normal.

Si la página falla van a darse cuenta que:

A) Sale el paquete TCP con el SYN flag activado hacia google. Lo normal. Nuestros sistemas andan bien.

B) En lugar de retornar un ACK, retornan un RST ACK!.


RST ACK significa: Reset + Acknowledge. Eso es nada más ni nada menos que "puerto cerrado". Los firewalls suele evitar este tipo de respuesta para despistar a los atacantes que buscan puertos abiertos (algunos le llaman "stealth").

Este error debe pasar en Linux con más fuerza que Windows porque las cosas deben funcionar mejor que en Windows !

El Firefox/Chromium al recibir el paquete RST automáticamente cierran la conexión ya que el puerto "esta cerrado". Si no hubiera respuesta, reintentarían. Realmente habría que analizar en Windows porque este comportamiento se hace con menos frecuencia, aunque también sucede.



Pude comprobar que el problema es ese. Al intentar iniciar una conexión con una web X, Speedy nos responde que el puerto 80/443 de esa dirección IP está cerrado. Y si volvés a intentar (generalmente) accedés lo más bien.



Saludos,

---

### Post by KAYAMAN0 on 2010-10-05
> Primero, porque ping solo prueba una parte de ICMP y el problema está en el protocolo TCP (quizás UDP, pero no lo probé).
**tcptraceroute!!!**

Hay que leer un poco mejor:P

---

### Post by atari130xe on 2010-10-05
Acá va uno mío echo hace un momento:

```
-desktop:~$ sudo tcptraceroute speedy.com.ar -p 80
traceroute to speedy.com.ar (209.13.119.32), 30 hops max, 60 byte packets
 1  192.168.1.1 (192.168.1.1)  0.879 ms  0.720 ms  0.660 ms
 2  * * *
 3  200.51.233.30 (200.51.233.30)  42.909 ms  42.163 ms  42.648 ms
 4  200-63-158-182.speedy.com.ar (200.63.158.182)  43.181 ms  42.014 ms  41.737 ms
 5  200.51.233.7 (200.51.233.7)  42.102 ms  42.137 ms  42.006 ms
 6  209.13.133.57 (209.13.133.57)  43.850 ms 209.13.119.32 (209.13.119.32)  -3576.347 ms  -5020.510 ms
-desktop:~$ 

-desktop:~$ sudo tcptraceroute speedy.com.ar -p 443
traceroute to speedy.com.ar (209.13.119.32), 30 hops max, 60 byte packets
 1  192.168.1.1 (192.168.1.1)  0.803 ms  0.743 ms  0.670 ms
 2  * * *
 3  200.51.233.30 (200.51.233.30)  41.841 ms  41.692 ms  41.928 ms
 4  200-63-158-182.speedy.com.ar (200.63.158.182)  43.765 ms  42.707 ms  41.976 ms
 5  200.51.233.7 (200.51.233.7)  41.763 ms  41.678 ms  41.708 ms
 6  209.13.133.57 (209.13.133.57)  44.013 ms 209.13.119.32 (209.13.119.32)  -2525.342 ms 209.13.133.57 (209.13.133.57)  -5027.171 ms
-desktop:~$ 


```

Agrego también que cada vez que recargo las páginas (F5 o reload en el navegador) -por ejemplo al postear esto- demora en cargar y una vez recibida la petición, me envia un archivo .php para descargar... (?)

Acá va el test de la Universidad de Berkeley sobre mi conexión:
> The ICSI Netalyzr
Introduction » Analysis » Results
Result Summary
+/&#8211; (help)
190-50-218-232.speedy.com.ar / 190.50.218.232
Recorded at 10:43 EDT (14:43 UTC), Oct 05 2010. Permalink. Client/server transcript.
Summary of Noteworthy Events &#8211;
[B][COLOR="Red"]Minor Aberrations

    * There appears to be a path MTU hole
    * The network path does not reply when it needs to fragment traffic
    * Network bandwidth may be low
    * An HTTP proxy was detected based on added or changed HTTP traffic [/COLOR][/B]

Minor Aberrations
Address-based Tests +
NAT detection (?): NAT Detected

Your global IP address is xxx.50.xxx.232 while your local one is xxx.xxx.1.2. You are behind a NAT. Your local address is in unroutable address space.

Your machine numbers TCP source ports sequentially. The following graph shows connection attempts on the X-axis and their corresponding source ports used by your computer on the Y-axis.

port sequence plot

TCP ports are not renumbered by the network.
DNS-based host information (?): OK
You are not a Tor exit node for HTTP traffic.
You are listed on the Spamhaus Policy Based Blacklist, meaning that your provider has designated your address block as one that should only be sending authenticated email, email through the ISP's mail server, or using webmail.
The SORBS DUHL believes you are using a statically assigned IP address.
NAT detection (?): NAT Detected
DNS-based host information (?): OK
Reachability Tests &#8211;
TCP connectivity (?): OK
Direct TCP access to remote FTP servers (port xx) is allowed.
Direct TCP access to remote SSH servers (port xx) is allowed.
Direct TCP access to remote SMTP servers (port xx) is allowed.
Direct TCP access to remote DNS servers (port xx) is allowed.
Direct TCP access to remote HTTP servers (port xx) is allowed.
Direct TCP access to remote POP3 servers (port xxx) is allowed.
Direct TCP access to remote RPC servers (port xxx) is allowed.
Direct TCP access to remote NetBIOS servers (port xxx) is allowed.
Direct TCP access to remote IMAP servers (port xxx) is allowed.
Direct TCP access to remote SNMP servers (port xxx) is allowed.
Direct TCP access to remote HTTPS servers (port xxx) is allowed.
Direct TCP access to remote SMB servers (port xxx) is allowed.
Direct TCP access to remote SMTP/SSL servers (port xxx) is allowed.
Direct TCP access to remote secure IMAP servers (port xxx) is allowed.
Direct TCP access to remote authenticated SMTP servers (port xxx) is allowed.
Direct TCP access to remote IMAP/SSL servers (port xxx) is allowed.
Direct TCP access to remote POP/SSL servers (port xxx) is allowed.
Direct TCP access to remote OpenVPN servers (port xxxx) is allowed.
Direct TCP access to remote PPTP Control servers (port xxxx) is allowed.
Direct TCP access to remote SIP servers (port xxxx) is allowed.
Direct TCP access to remote BitTorrent servers (port xxxx) is allowed.
Direct TCP access to remote TOR servers (port xxxx) is allowed.
UDP connectivity (?): Note
(Todos los puertos "permitidos")

Basic UDP access is available.

The applet was unable to send packets of 1471 bytes of payload (1499 bytes total), which suggests a problem on the path between your system and our server.

The applet was able to receive fragmented UDP traffic.
Direct UDP access to remote DNS servers (port xx) is allowed.
Direct UDP access to remote OpenVPN servers (port xxxx) is allowed.
Direct UDP access to remote MSSQL servers (port xxxx) is allowed.
**[COLOR="Red"]Path MTU (?): Warning[/COLOR]**

The path between your network and our system supports an MTU of at least 1500 bytes, and the path between our system and your network has an MTU of 1492 bytes.

The path between our system and your network does not appear to properly report when it needs to fragment traffic.
TCP connectivity (?): OK
UDP connectivity (?): Note
Path MTU (?): Warning
Network Access Link Properties &#8211;
Network latency measurements (?): Latency: 200ms Loss: 0.0%
The round-trip time (RTT) between your computer and our server is 200 msec, which is good.
We recorded no packet loss between your system and our server.
TCP connection setup latency (?): 210ms
The time it takes your computer to set up a TCP connection with our server is 210 msec, which is good.
Network background health measurement (?): no transient outages
During most of Netalyzr's execution, the applet continuously measures the state of the network in the background, looking for short outages. During testing, the applet observed no such outages.
Network bandwidth measurements (?): Upload 520 Kbit/sec, Download 180 Kbit/sec
Your Uplink: We measured your uplink's sending bandwidth at 520 Kbit/sec. This level of bandwidth works well for many users.
Your Downlink: We measured your downlink's receiving bandwidth at 180 Kbit/sec. This rate could be considered quite slow, and will affect your user experience if you perform large transfers.
Network buffer measurements (?): Uplink 350 ms, Downlink 280 ms
We estimate your uplink as having 350 msec of buffering. This level may serve well for maximizing speed while minimizing the impact of large transfers on other traffic.
We estimate your downlink as having 280 msec of buffering. This level may serve well for maximizing speed while minimizing the impact of large transfers on other traffic.
Network latency measurements (?): Latency: 200ms Loss: 0.0%
TCP connection setup latency (?): 210ms
Network background health measurement (?): no transient outages
Network bandwidth measurements (?): Upload 520 Kbit/sec, Download 180 Kbit/sec
Network buffer measurements (?): Uplink 350 ms, Downlink 280 ms
HTTP Tests &#8211;
Address-based HTTP proxy detection (?): OK
There is no explicit sign of HTTP proxy use based on IP address.
Header-based HTTP proxy detection (?): Warning

Changes to headers or contents sent between the applet and our HTTP server show the presence of an otherwise unadvertised HTTP proxy.

The following headers had their capitalization modified by the proxy:

    * Content-Length: 684
    * Content-Type: text/html

The detected proxy reordered the headers sent from the server.

The detected HTTP proxy changed either the headers the applet sent or the HTTP response from the server. We have captured the changes for further analysis.
HTTP proxy detection via malformed requests (?): OK
Deliberately malformed HTTP requests arrive at our server unchanged. Thus, the proxies along your path are able to transparently forward invalid HTTP traffic.
Filetype-based filtering (?): OK
We did not detect file-content filtering.
HTTP caching behavior (?): OK
An I/O error occurred during the test. The test result code is 34.
JavaScript-based tests (?): OK
The applet was not run from within a frame.
Your web browser reports the following cookies for our web page:

    * netAlizEd = BaR (set by our server)
    * netalyzrStatus = running (set by our server)

Your web browser was unable to fetch an image using IPv6.
Address-based HTTP proxy detection (?): OK
Header-based HTTP proxy detection (?): Warning
HTTP proxy detection via malformed requests (?): OK
Filetype-based filtering (?): OK
HTTP caching behavior (?): OK
JavaScript-based tests (?): OK
DNS Tests +
Restricted domain DNS lookup (?): OK
We are able to successfully lookup a name which resolves to the same IP address as our webserver. This means we are able to conduct many of the tests on your DNS server.
Unrestricted domain DNS lookup (?): OK
We are able to successfully lookup arbitrary names from within the Java applet. This means we are able to conduct all test on your DNS server.
Direct EDNS support (?): OK
EDNS-enabled requests for small responses are answered successfully.
EDNS-enabled requests for medium-sized responses are answered successfully.
EDNS-enabled requests for large responses are answered successfully.
DNS resolver address (?): OK
The IP address of your ISP's DNS Resolver is 200.47.82.1, which resolves to pop3.equal.com.ar.
DNS resolver properties (?): Lookup latency: 680ms
Your ISP's DNS resolver requires 680 msec to conduct an external lookup, and 430 msec to lookup an item in the cache. It takes 229 msec for your ISP's DNS resolver to lookup a name on our server.
Your resolver correctly uses TCP requests when necessary.
Your resolver is using QTYPE=A for default queries.
Your host or resolver also performs IPv6 queries in addition to IPv4 queries.
Your DNS resolver does not use EDNS.
Your DNS resolver accepts DNS responses of up to 1280 bytes.
Your resolver does not use 0x20 randomization, but will pass names in a case-sensitive manner.
Your ISP's DNS resolver respects a TTL of 0 seconds.
Your ISP's DNS resolver respects a TTL of 1 seconds.
Your NAT has a built in DNS proxy. The DNS request was received from 200.47.82.1
No transport issues were discovered which could affect the deployment of DNSSEC
DNS glue policy (?): OK
Your ISP's DNS resolver accepts generic glue records located in subdomains of the queried domain.
Your ISP's DNS resolver accepts additional (glue) records for nameservers located in subdomains of the queried domain.
Your ISP's DNS resolver follows CNAMEs when it is in a subdomain of the queried domain.
DNS resolver port randomization (?): OK
Your ISP's DNS resolver properly randomizes its local port number.
The following graph shows DNS requests on the x-axis and the detected source ports on the y-axis.

port sequence plot
DNS lookups of popular domains (?): OK
77 of 77 popular names were resolved successfully. Show all names.
In the following table reverse lookups that failed but for which a Start Of Authority (SOA) entry indicated correct name associations are shown using an "X", followed by the SOA entry. Absence of both IP address and reverse name indicates failed forward lookups.
Name     IP Address     Reverse Name/SOA
[www.abbey.co.uk](www.abbey.co.uk)     165.160.13.20     X (pdns1.cscdns.net)
ad.doubleclick.net     72.14.253.148     mia04s03-in-f148.1e100.net
[www.alliance-leicester.co.uk](www.alliance-leicester.co.uk)     194.130.105.121     X (alice.ioko365.com)
[www.amazon.com](www.amazon.com)     207.171.166.252     166-252.amazon.com
[www.ameritrade.com](www.ameritrade.com)     216.105.251.204     X (mike.lynn.tdameritrade.com)
[www.bankofamerica.com](www.bankofamerica.com)     171.161.148.100     X (primarydmz.bankofamerica.com)
[www.bankofscotland.co.uk](www.bankofscotland.co.uk)     195.171.171.21     X (ns0.bt.net)
bit.ly     128.121.254.205     X (ns1.dn.net)
[www.capitalone.com](www.capitalone.com)     208.80.48.112     X (chia.arin.net)
[www.careerbuilder.com](www.careerbuilder.com)     208.82.7.22     X (smokey.careerbuilder.com)
[www.chase.com](www.chase.com)     159.53.64.105     X (ns1.jpmorganchase.com)
chaseonline.chase.com     159.53.52.105     X (ns1.jpmorganchase.com)
[www.citi.com](www.citi.com)     192.193.103.222     citibank.com
[www.citibank.com](www.citibank.com)     192.193.103.222     citibank.com
[www.citimortgage.com](www.citimortgage.com)     192.193.218.222     citimortgage.com
[www.desjardins.com](www.desjardins.com)     142.195.132.100     [www.desjardins.com](www.desjardins.com)
[www.e-gold.com](www.e-gold.com)     209.200.169.10     unknown.prolexic.com
[www.ebay.com](www.ebay.com)     66.135.200.145     hp-core.ebay.com
[www.etrade.com](www.etrade.com)     12.153.224.22     [www.etrade.com](www.etrade.com)
[www.facebook.com](www.facebook.com)     66.220.156.25     www-12-04-ash2.facebook.com
[www.fdic.gov](www.fdic.gov)     167.176.17.84     [www.fdic.gov](www.fdic.gov)
[www.friendfinder.com](www.friendfinder.com)     208.88.180.81     X (ii53-30.friendfinderinc.com)
[www.google.com](www.google.com)     72.14.253.104     mia04s03-in-f104.1e100.net
[www.halifax.co.uk](www.halifax.co.uk)     62.172.43.225     halifax.co.uk
[www.hsbc.co.uk](www.hsbc.co.uk)     193.108.74.126     X (ns3.hsbc.com)
[www.jpmorganchase.com](www.jpmorganchase.com)     159.53.64.105     X (ns1.jpmorganchase.com)
mail.google.com     74.125.157.83     gy-in-f83.1e100.net
mail.live.com     64.4.20.169     dp2.mail.live.com
mail.yahoo.com     209.191.92.114     l2.login.vip.mud.yahoo.com
[www.mbna.com](www.mbna.com)     209.135.59.10     X (ns1.usi.net)
[www.mbna.net](www.mbna.net)     209.135.59.10     X (ns1.usi.net)
[www.meebo.com](www.meebo.com)     74.114.28.110     X (ns1.meebo.com)
messenger.yahoo.com     68.142.230.204     myc1.msg.vip.re2.yahoo.com
[www.microsoft.com](www.microsoft.com)     65.55.21.250     wwwco1vip.microsoft.com
[www.nationwide.co.uk](www.nationwide.co.uk)     155.131.31.81     [www.nationwide.co.uk](www.nationwide.co.uk)
[www.networksolutions.com](www.networksolutions.com)     205.178.187.13     [www.networksolutions.com](www.networksolutions.com)
[www.newegg.com](www.newegg.com)     204.14.213.185     X (pdns1.ultradns.net)
online.citibank.com     199.67.181.11     citibankonline.com
online.wellsfargo.com     151.151.13.132     psaltery-on.wellsfargo.com
[www.orange.fr](www.orange.fr)     193.252.122.103     [www.orange.fr.b2.fti.net](www.orange.fr.b2.fti.net)
partner.googleadservices.com     72.14.253.164     mia04s03-in-f164.1e100.net
[www.paypal.com](www.paypal.com)     64.4.241.49     node-64-4-241-4[...]orks.paypal.com
[www.postbank.de](www.postbank.de)     62.153.105.37     X (ns1.postbank.de)
[www.rbs.co.uk](www.rbs.co.uk)     155.136.80.222     X (ns0-08.dns.pipex.net)
[www.schwab.com](www.schwab.com)     162.93.206.80     wwwschwab-vip.schwab.com
search.yahoo.com     74.6.238.254     syc.search.vip.ac2.yahoo.com
[www.sears.com](www.sears.com)     96.16.249.99     a96-16-249-99.d[...]echnologies.com
[www.secureworks.com](www.secureworks.com)     67.107.53.168     67.107.53.168.ptr.us.xo.net
smartzone.comcast.net     76.96.58.12     webmail3.westch[...]ail.comcast.net
[www.smithbarney.com](www.smithbarney.com)     192.193.20.126     X (ns.citicorp.com)
[www.sterlingsavingsbank.com](www.sterlingsavingsbank.com)     12.19.55.215     sterlingsavingsbank.com
[www.tdameritrade.com](www.tdameritrade.com)     216.105.251.204     X (mike.lynn.tdameritrade.com)
[www.ticketmaster.com](www.ticketmaster.com)     184.50.164.199     a184-50-164-199[...]echnologies.com
tinyurl.com     195.66.135.139     b2.tinyurl.com
[www.torproject.org](www.torproject.org)     38.229.70.16     vescum.torproject.org
us.etrade.com     198.93.34.50     us.etrade.com
[www.verisign.com](www.verisign.com)     69.58.181.89     www-ilg.verisign.net
[www.wachovia.com](www.wachovia.com)     169.200.183.139     X (sls-ns1.wachovia.com)
[www.wamu.com](www.wamu.com)     159.53.62.63     X (ns1.jpmorganchase.com)
[www.wellsfargo.com](www.wellsfargo.com)     151.151.13.133     [www.wellsfargo.com](www.wellsfargo.com)
westernunion.com     206.201.227.250     wumt1.westernunion.com
windowsupdate.microsoft.com     65.54.221.118     X (msnhst.microsoft.com)
wireless.att.com     135.209.168.22     origin-b2b-al[...]eless.att.com
[www.yahoo.com](www.yahoo.com)     209.191.122.70     ir1.fp.vip.mud.yahoo.com
12 popular names have a mild anomaly. The ownership suggested by the reverse name lookup does not match our understanding of the original name. The most likely cause is the site's use of a Content Delivery Network. Show all names.
Name     IP Address     Reverse Name/SOA
[www.barclays.co.uk](www.barclays.co.uk)     212.140.250.32     X (ns0.bt.net)
[www.bing.com](www.bing.com)     200.47.133.38     line38.comsat.net.ar
[www.cnn.com](www.cnn.com)     157.166.255.19     X (ns1.timewarner.net)
[www.deutsche-bank.de](www.deutsche-bank.de)     160.83.8.24     X (ns2.db.com)
[www.f-secure.com](www.f-secure.com)     200.47.133.38     line38.comsat.net.ar
[www.irs.gov](www.irs.gov)     200.47.133.39     line39.comsat.net.ar
[www.lloydstsb.com](www.lloydstsb.com)     141.92.130.226     X (ns0.bt.net)
[www.nordea.fi](www.nordea.fi)     193.88.186.178     X (ns01.tdchosting.dk)
[www.sparkasse.de](www.sparkasse.de)     212.34.69.3     rev-212.34.69.3.rev.izb.net
[www.trendmicro.com](www.trendmicro.com)     173.223.109.214     a173-223-109-21[...]echnologies.com
[www.usbank.com](www.usbank.com)     170.135.216.181     [www.firstar-mfs.com](www.firstar-mfs.com), [www.firstar401k.com](www.firstar401k.com), [www.firstarfunds.com](www.firstarfunds.com), [www.grabcashfast.com](www.grabcashfast.com), [www.gymboreevisa.com](www.gymboreevisa.com), [www.porticofunds.com](www.porticofunds.com), [www.vailbanksinc.com](www.vailbanksinc.com), [www.weststarbank.com](www.weststarbank.com), [www.cpssalestools.com](www.cpssalestools.com), [www.uconnectonline.com](www.uconnectonline.com), [www.heritagemontana.com](www.heritagemontana.com), [www.firstarinsurance.com](www.firstarinsurance.com), [www.firstarcommercial.com](www.firstarcommercial.com), [www.weststar-mortgage.com](www.weststar-mortgage.com)
[www.visa.com](www.visa.com)     200.47.133.40     line40.comsat.net.ar
1 popular name has a mild anomaly: we are unable to find a reverse name associated with the IP address provided by your ISP's DNS server. This is most likely due to a slow responding DNS server or misconfiguration on the part of the domain owner. Show all names.
Name     IP Address     Reverse Name/SOA
[www.bankofthewest.com](www.bankofthewest.com)     204.44.12.103     X
DNS external proxy (?): OK
Your host ignores external DNS requests.
DNS results wildcarding (?): OK
Your ISP correctly leaves non-resolving names untouched.
Restricted domain DNS lookup (?): OK
Unrestricted domain DNS lookup (?): OK
Direct EDNS support (?): OK
DNS resolver address (?): OK
DNS resolver properties (?): Lookup latency: 680ms
DNS glue policy (?): OK
DNS resolver port randomization (?): OK
DNS lookups of popular domains (?): OK
DNS external proxy (?): OK
DNS results wildcarding (?): OK
Host Properties +
System clock accuracy (?): OK
Your computer's clock agrees with our server's clock.
Browser properties (?): OK
The following parameters are sent by your web browser to all web sites you visit:

    * User Agent: Mozilla/5.0 (X11; U; Linux i686; es-AR; rv:1.9.2.10) Gecko/20100922 Ubuntu/10.10 (maverick) Firefox/3.6.10
    * Accept: text/html,application/xhtml+xml,application/xml; q=0.9,*/*; q=0.8
    * Accept Language: es-ar,es;q=0.8,en-us;q=0.5,en;q=0.3
    * Accept Encoding: gzip,deflate
    * Accept Charset: ISO-8859-1,utf-8;q=0.7,*;q=0.7

Java identifies your operating system as Linux.
Uploaded Data (?): OK
The applet uploaded no additional data
System clock accuracy (?): OK
Browser properties (?): OK
Uploaded Data (?): OK


---

### Post by heliotropo on 2010-10-05
Hoy el problema no es tan persistente. Pero sigue aparece muchísimas menos veces que no puede cargar la pagina o paginas sin formatos... pero esta todavía el problema.

Otra cosa.
Hago tcptraceroute y me da esto.


sudo tcptraceroute speedy.com.ar -p 80
traceroute to speedy.com.ar (209.13.119.32), 30 hops max, 60 byte packets
bind: Dirección ya está en uso

---

### Post by anarko on 2010-10-05
Hola, no puedo creerlo, aunque debería haberme parecido, creí que era el único que estaba gastando el F5 por culpa de speedy. Yo estoy con este problema hace no menos de 2 meses. 

¿Porque no nos juntamos como comunidad y presentamos un reclamo en la CNC?
Por ahí algunos podríamos ir a los headquartes de speedy y ver cual es el proxy o los proxy http que tienen mal configurados y darles una mano :p
No seria la primera vez que tengo que ir a la empresa que me presta un servicio a explicarles como se configura ese servicio.

---

### Post by heliotropo on 2010-10-05
> **anarko said:**
> Hola, no puedo creerlo, aunque debería haberme parecido, creí que era el único que estaba gastando el F5 por culpa de speedy. Yo estoy con este problema hace no menos de 2 meses. 

¿Porque no nos juntamos como comunidad y presentamos un reclamo en la CNC?
Por ahí algunos podríamos ir a los headquartes de speedy y ver cual es el proxy o los proxy http que tienen mal configurados y darles una mano :p
No seria la primera vez que tengo que ir a la empresa que me presta un servicio a explicarles como se configura ese servicio.

Yo hasta ahora estoy dale reclamar al centro de atención al cliente...
Estaría bueno presentar un reclamo a DC.
Lo de y a ayudar estaría bueno también. Por supuesto cobrando honorarios... XD

---

### Post by TECSD on 2010-10-05
Estimados: Es cierto, con SO de Macintosh pasa lo mismo. He realizado pruebas con 4 MAC con el mismo resultado. En mi caso, el inconveniente comenzó hace 2 semanas. Ya vinieron los técnicos de Speedy a cambiar el modem, probar, etc, etc, sin soluciones a la vista!
Los técnicos del 0-800, ya reconocen que es un problema que tienen ellos con estos SO.
Saludos cordiales,

---

### Post by marcelo_bur on 2010-10-06
Hola. Hoy anda un poco mejor, al menos eso parece. Ayer usé window$ y también tuve problemas, aunque debo reconocer que menos. Sin embargo no creo que Speedy pretenda brindar servicio solo a usuarios de Window$, no tiene lógica.
Yo todavía no hice ningún reclamo al 0800, ocurre que tengo muy poca paciencia para eso. Me ha sucedido de llamar, por otros motivos que ni siquiera tienen nada que ver con internet ni Telefónica, y pasarme casi una hora entre el tiempo que te hacen esperar, después se corta, volvés a llamar, de nuevo a esperar, suele ser demasiado estresante, mis nervios no lo soportan. Es por ello que, a pesar de que reconozco la razón de quienes dicen que tenemos que reclamar, no lo he hecho en este caso aún. De todas formas es sólo para que quede asentado un reclamo más, y no olvidar que para que la pérdida de tiempo haya valido mínimamente la pena tenés que insistir en que lo que queres no es "soporte" sino ingresar un reclamo por mal servicio, tomar el nombre de la operadora, pedir el número de reclamo, anotar la hora exacta en la que fuiste atendido, etc. Y se que en difinitiva no me van a solucinar nada, aunque supongo que están buscando la solución porque a ello no les conviene una falla tan masiva en el servicio. Y por supuesto que no voy a permitir que un "técnico" de Speedy meta mano en mi router o pc... después seguro que no iba a funcionar nada y, menos aún, si se encuentran con que la pc tiene Ubuntu, no estoy seguro de que sepan por donde iniciar el sistema... LOL.
Saludos

---

### Post by atari130xe on 2010-10-06
Por este lado la cosa sigue tan mal como a partir del 15 de Setiembre, es probable que vuelva a llamar al 0800 333 7733 opción 0 para seguirle los pasos al reclamo...

---

### Post by emiliano_raso on 2010-10-07
Tengo el mismo problema con Speedy.
Ya llamé al fukin numero ese como 4 veces y me dijeron que me van a mandar un tecnico pero todavía nada.

Empezó a andar mal de un dia para el otro, hace 2 semanas mas o menos.

---

### Post by emiliano_raso on 2010-10-07
Estaría bueno lo de juntarnos todos y hacer un reclamo juntos. Podriamos empezar a organizarlo.

---

### Post by atari130xe on 2010-10-07
Hay una cosa que no me cierra (entre otras) de Telefónica: ¿Cual o cuales son los motivos por los que Speedy (Telefónica) no admite que es un problema general y que están trabajando en solucionarlo siendo que somos miles con el mismo problema? Insiste con enviarnos técnicos cuando claramente ya saben que es un problema de los servidores, (pasaron 3 técnicos por casa) y por más que toque y re contra toquen cables, modem, router, configuración de los DNS, etc, etc. no van a solucionar nada, si me admitieron luego de más de 10 reclamos que es un problema de ellos, porque no se lo dicen a los que llaman por 1ra vez?, un manoseo sin sentido...

---

### Post by marcelo_bur on 2010-10-07
> **emiliano_raso said:**
> Tengo el mismo problema con Speedy.
Ya llamé al fukin numero ese como 4 veces y me dijeron que me van a mandar un tecnico pero todavía nada.

Empezó a andar mal de un dia para el otro, hace 2 semanas mas o menos.

HOla. Mejor no dejes que te toquen nada, no hay modo de que te soluciones este problema en particular. Ahora bien, si crees que podes tener algún problema adicional bien. Pero en general los técnicos solo sirven para mirar modems, cables, fichas y, a veces, meter mano en la pc y hacer macanas.

Saludos

---

### Post by marcelo_bur on 2010-10-07
> **emiliano_raso said:**
> Estaría bueno lo de juntarnos todos y hacer un reclamo juntos. Podriamos empezar a organizarlo.

Es realmente una buena idea, aunque a mi no se me ocurre como implementarla. Tendría que ser un reclamo presentado en mano, en algúna oficna de Telefónica o Speedy, algo firmado por todos, con todos los datos. Si a alguien se le ocurre una manera viable de hacerlo y sabe donde presentar la queja me sumo. Quizas se debería presentar ante el Ente Regulador.
Saludos

---

### Post by marcelo_bur on 2010-10-07
> **emiliano_raso said:**
> Estaría bueno lo de juntarnos todos y hacer un reclamo juntos. Podriamos empezar a organizarlo.

Es realmente una buena idea, aunque a mi no se me ocurre como implementarla. Tendría que ser un reclamo presentado en mano, en algúna oficna de Telefónica o Speedy, algo firmado por todos, con todos los datos. Si a alguien se le ocurre una manera viable de hacerlo y sabe donde presentar la queja me sumo. Quizas se debería presentar ante el Ente Regulador.
Saludos

---

### Post by marcelo_bur on 2010-10-07
Disculpen el mensaje posteado dos veces, pero lo mal que anda la conección no te permite estar seguro de lo que proceso o no el sistema, reenvias la petición y a veces sale bien, a veces nada y a veces doble... jajaja

---

### Post by marcelo_bur on 2010-10-07
> **atari130xe said:**
> Hay una cosa que no me cierra (entre otras) de Telefónica: ¿Cual o cuales son los motivos por los que Speedy (Telefónica) no admite que es un problema general y que están trabajando en solucionarlo siendo que somos miles con el mismo problema? Insiste con enviarnos técnicos cuando claramente ya saben que es un problema de los servidores, (pasaron 3 técnicos por casa) y por más que toque y re contra toquen cables, modem, router, configuración de los DNS, etc, etc. no van a solucionar nada, si me admitieron luego de más de 10 reclamos que es un problema de ellos, porque no se lo dicen a los que llaman por 1ra vez?, un manoseo sin sentido...

Hola. Los operadores, así como los técnicos, estan entrenados para buscar siempre la forma de decirte que la culpa es de tu linea, de tu ficha, de tu pc, lo que sea, menos culpa de ellos. Si alguno te lo reconoció tuviste mucha suerte, y si el supervisor lo pesco (graban todo), hasta tal vez lo hayan echado.
Saludos

---

### Post by emiliano_raso on 2010-10-07
Acaba de irse el tecnico de Speedy de mi casa. El tipo no sabía un joraca.

Me levantó mi vieja (yo estaba durmiendo) y el tipo ya estaba sentado en la PC de escritorio, chusmeando el modem, con otro modem en la mano.
Lo freno, le explico todo ("Hace dos semanas que anda mal en Linux, y hace 1 semana está andando mal tambien en Windows, ya probé conectar y desconectar, no es problema de red local, ni de hardware, es problema de la conexion que me están mandando").
Cuestion, para estoy llevé la notebook de mi pieza a la cocina que tiene instalado Ubuntu Lucid y le comento que tuve el mismo problema con Ubuntu 10.04, Debian Lenny y Cent OS.
El tipo me mira y me dice "Pero en Windows anda bien? Entonces yo mas no puedo hacer". A lo cual, como recien me levantaba no advertí que el tipo no entendía nada de lo que yo le estaba diciendo y que me empezaba a tener miedo tecnico.
Le volví a explicar que la ultima semana tambien empezó a andar mal Windows. Acto seguido, el tipo se pone a revisar la configuración de IP y DNS en el protocolo TCP/IP en Windows, a lo cual le respondo "Si se soluciona con eso, solo se solucionaría en Windows, y no en Linux" a lo cual el tipo me dice "Por Qué tenés tantos sistemas operativos?"
Ahí me desperté, me maté de risa, la miré a mi vieja, mi vieja se tapaba la cara con una revista, lo miro al tipo y le respondo "Por estudio, trabajo y por gusto".
Acto seguido a esta respuesta mia, lo BOMBARDEÉ a indiscreción con todas las palabras tecnicas que se me pudieron ocurrir.
El tipo se levantó de la silla, y empezó a caminar hacia subiendo los hombros y mirando hacia abajo, llendo para la puerta, dispuesto a escaparse ante tanto despliegue de conocimiento informatico :P
Antes de irse me dice "Definitivamente es un problema de software, no de la red entonces." a lo que le respondo "No! Acabamos de comprobar que no! Que es un problema de la conexión que me están enviando. Es mas, no soy el unico(...)" y le mostré este thread, y le conté que un montón de gente está teniendo problemas de la misma forma.

Fue muy comico y triste al mismo tiempo.
Se fué diciendo que iba a comentarle a sus superiores.

Cuestión: No me solucionó nada. Hoy a la tarde voy a llamar y pedir que me manden un tecnico que tenga conocimientos de GNU/Linux.

---

### Post by emiliano_raso on 2010-10-07
> **marcelo_bur said:**
> Es realmente una buena idea, aunque a mi no se me ocurre como implementarla. Tendría que ser un reclamo presentado en mano, en algúna oficna de Telefónica o Speedy, algo firmado por todos, con todos los datos. Si a alguien se le ocurre una manera viable de hacerlo y sabe donde presentar la queja me sumo. Quizas se debería presentar ante el Ente Regulador.
Saludos

Lo que hay que hacer es, anotar todos los numeros de nuestros reclamos (hay que pedirlos cuando llamas), y hablár con el ente regulador de Speedy, y darle todos los datos de nuestros reclamos:
- Numero de reclamo, fecha y hora.
- Tiempo de espera que nos dieron (clasico 72hs)
- Tiempo que tardó el tecnico en venir en realidad
- Cuanto hace que tenemos el problema.
- etc.

Vayamos juntando esa información. Yo tengo la información de mi reclamo de ayer.
Un amigo tenia problemas con EDELAP, llamó y dijo "Si no me solucionan el problema para mañana, hablo con el ente regulador y les hago un juicio. Hace 1 mes que no tengo luz." Al dia siguiente se lo arreglaron.

---

### Post by atari130xe on 2010-10-07
Gente si van a organizar la entrega de un reclamo masivo y simultaneo, me anoto, es importante saber que (en mi caso tengo el plan "Duo") hay que reclamar no solo por un mal servicio sino por el descuento de todos los días sin contar con el servicio en condiciones, tomen en cuenta que para ello hay que llamar al 112 y reclamar. Yo lo hice y me contestaron que una vez notificados los del area comercial que el problema está solucionado ellos aplicarán el descuento de los días sin servicio. Nos corresponde, creo que si ellos por atrasos del abonado cobran intereses punitorios y hay una fecha a cumplir con la facturación, lo mismo debe aplicarse para ellos como empresa y exigirles nos descuenten lo que corresponde.

---

### Post by coskibukowski on 2010-10-07
> **emiliano_raso said:**
> Tengo el mismo problema con Speedy.
Ya llamé al fukin numero ese como 4 veces y me dijeron que me van a mandar un tecnico pero todavía nada.

Empezó a andar mal de un dia para el otro, hace 2 semanas mas o menos.

Lo mismo en mi caso.

Saludos

PD: hola emi :P

---

### Post by heliotropo on 2010-10-07
El problema se me presenta en mi lugar de trabajo...
Estoy en la zona sur del gran Buenos Aires a 42 km de capital.
Estamos migrando a linux y este problema se presenta en las maquinas con linux. Llamo al servicio tecnico de empresas y me dicen que no hay problemas y que ellos no dan soporte para linux.
Lamentablemente aca no tenemos opcoçión de elegir otra empresa para que nos brinde el servicio....

---

### Post by marcelo_bur on 2010-10-07
> **heliotropo said:**
> El problema se me presenta en mi lugar de trabajo...
Estoy en la zona sur del gran Buenos Aires a 42 km de capital.
Estamos migrando a linux y este problema se presenta en las maquinas con linux. Llamo al servicio tecnico de empresas y me dicen que no hay problemas y que ellos no dan soporte para linux.
Lamentablemente aca no tenemos opcoçión de elegir otra empresa para que nos brinde el servicio....

Tal vez esté divagando, pero se me ocurre que nuestro amigo Bill le debe haber tirado algunos millones a Telefónica para que haga funcionar mal nuestros equipos con Linux. Imaginense que al ritmo que los usuarios están comenzando a conocer y utilizar el sofware libre en breve la cosa se le va a poner fea...

---

### Post by emiliano_raso on 2010-10-07
Bueno gente. Empezemos a organizarnos. Comencemos por reunir toda la información referente a los reclamos. Anoten los siguientes datos de los reclamos que ya hicieron y de los que vayan a hacer:

- Numero de reclamo, fecha y hora.
- Tiempo de espera que nos dieron (clasico 72hs)
- Tiempo que tardó el tecnico en venir en realidad
- Cuanto hace que tenemos el problema.
- etc.

Tambien hay que averiguar:
- Cual es el ente regulador encargado de Speedy
- Que datos son necesarios para levantar un reclamo ante el ente regulador

Otra alternativa podria ser elevar una carta documento en nombre de la comunidad Linuxera al ente regulador.

---

### Post by hectorivand on 2010-10-07
> **emiliano_raso said:**
> Bueno gente. Empezemos a organizarnos. Comencemos por reunir toda la información referente a los reclamos. Anoten los siguientes datos de los reclamos que ya hicieron y de los que vayan a hacer:

- Numero de reclamo, fecha y hora.
- Tiempo de espera que nos dieron (clasico 72hs)
- Tiempo que tardó el tecnico en venir en realidad
- Cuanto hace que tenemos el problema.
- etc.

Tambien hay que averiguar:
- Cual es el ente regulador encargado de Speedy
- Que datos son necesarios para levantar un reclamo ante el ente regulador

Otra alternativa podria ser elevar una carta documento en nombre de la comunidad Linuxera al ente regulador.

El ente regulador es la [CNC]("http://www.cnc.gov.ar/") (Comisión Nacional de Comunicaciones)

[Estos son los pasos para hacer el reclamo.]("http://www.cnc.gov.ar/tramites/tramitedetalle.asp?codigo_tramite=1799#1")

No es la intención trollear, pero es medio flojo no saber quien regula las comunicaciones :S

Otra sugerencia.:

Nota a Defensa del consumidor, se pueden hacer presentaciones "en grupo".

Otra, se juntan entre todos y un buen abogado. Puedo recomendarles.

Saludos
Nacho

---

### Post by biale on 2010-10-07
Tratando de aportar algo, comento que encontre que los tests de la Univ de Berkeley son útiles como un diagnóstico independiente y muy completo de la situación de la red.

Luego de ejecutarlos quedan almacenados en el servidor y la URL puede servir para fundamentar un poco mas el posible reclamo.

Hay un ejemplo en este mismo thread, pero si interesa puedo postear mis resultados. 

Los tests se realizan desde: [http://netalyzr.icsi.berkeley.edu/](http://netalyzr.icsi.berkeley.edu/)

Aunque supongo que la mayoría lo debe saber, comento que desgraciadamente hay un ruido de fondo que enturbia la cuestión. 

Concretamente, los directivos de Telefónica declararon al Gobierno que "estaban en condiciones de absorber a los abonados de Fibertel". Y la realidad muestra problemas varios ya con los abonados existentes. Moraleja: dificilmente reconozcan oficialmente un problema que de alguna manera es general.

---

### Post by emiliano_raso on 2010-10-07
> **hectorivand said:**
> No es la intención trollear, pero es medio flojo no saber quien regula las comunicaciones :S

Jaja, es que nunca en mi vida tuve un problema semejante. Nunca tuve que recurrir a un ente regulador :P
Y los demas usuarios, no se xD


> **biale said:**
> Tratando de aportar algo, comento que encontre que los tests de la Univ de Berkeley son útiles como un diagnóstico independiente y muy completo de la situación de la red.

Luego de ejecutarlos quedan almacenados en el servidor y la URL puede servir para fundamentar un poco mas el posible reclamo.

Hay un ejemplo en este mismo thread, pero si interesa puedo postear mis resultados. 

Los tests se realizan desde: [http://netalyzr.icsi.berkeley.edu/](http://netalyzr.icsi.berkeley.edu/)

Aunque supongo que la mayoría lo debe saber, comento que desgraciadamente hay un ruido de fondo que enturbia la cuestión. 

Concretamente, los directivos de Telefónica declararon al Gobierno que "estaban en condiciones de absorber a los abonados de Fibertel". Y la realidad muestra problemas varios ya con los abonados existentes. Moraleja: dificilmente reconozcan oficialmente un problema que de alguna manera es general.
Gracias por la info!

---

### Post by josecuervo86 on 2010-10-07
Che, soy solo yo, o particularmente hoy anda malisimamente MAL??

Me sumo a lo de juntar fuerzas y tratar de que se solucione. Mañana llamo a Speedy y hago el reclamo!

Saludos!

---

### Post by emiliano_raso on 2010-10-07
> **josecuervo86 said:**
> Che, soy solo yo, o particularmente hoy anda malisimamente MAL??

Me sumo a lo de juntar fuerzas y tratar de que se solucione. Mañana llamo a Speedy y hago el reclamo!

Saludos!

Hoy anduvo peor que nunca.
Creo que para abrir este thread apreté F5 mas de 10 veces

EDIT: Estoy en XP viendo si definitivamente es que anda peor o que, pero anda impecable en XP.
Igual, prefiero comerme el garron de apretar F5 antes que estár en Windows.

---

### Post by josecuervo86 on 2010-10-07
> **emiliano_raso said:**
> Hoy anduvo peor que nunca.
Creo que para abrir este thread apreté F5 mas de 10 veces

Speedy F5.0

> Igual, prefiero comerme el garron de apretar F5 antes que estár en Windows.
Ni hablar de eso! Igualmente, desde un xp virtualizado me anda igual de MAL, un poquito menos quiza, pero no se muy bien por que lo use para testear la conexion nomas =P

---

### Post by marcelo_bur on 2010-10-08
> **josecuervo86 said:**
> Speedy F5.0


Ni hablar de eso! Igualmente, desde un xp virtualizado me anda igual de MAL, un poquito menos quiza, pero no se muy bien por que lo use para testear la conexion nomas =P


Hola. A mi por las mañanas temprano me anda bastante bien, ya por la tarde todo se complica. Sigo sin entender porque anda peor en Linux, use esta conección durante dos años con Ubuntu (que es el tiempo que llevo en Linux, mas o menos) con las dificultades comunes en alguien que recién se inicia y tiene que aprender algunas cosas, pero nada grave. Por el contrario, muchas veces me senti sorprendido de que algunas cosas fuesen más simples y más seguras que en Window$.
Yo todavía no hice ningún reclamo. Primero voy a ver si uso durante unos dos dias Window$ para ver que pasa (tengo un viejo XP isntalado por ahí) y poder replicar con más conocimiento en caso de que me toque algún "operador combativo". Ya me bajé los formularios para iniciar el reclamo ante el Ente. Supongo que luego coordinaremos la forma de presentar esto en mano todos juntos.
Saludos

---

### Post by emiliano_raso on 2010-10-08
Estoy haciendo una hoja de calculo en Open Office con los dias de la semana y las 24 horas, poniendo en que momentos anda bien y mal.
Ahora anda mal por ejemplo.

---

### Post by emiliano_raso on 2010-10-08
Estoy haciendo una hoja de calculo en Open Office con los dias de la semana y las 24 horas, poniendo en que momentos anda bien y mal.
Ahora anda mal por ejemplo.

---

### Post by ioargento on 2010-10-08
Si bien en mi caso no tengo un horario en particular (siempre funciona mal y sólo a veces muy mal como ahora) quizás resulte algo de estudiar esos datos.

Más allá de eso, propongo que cada uno que vaya posteando sus inconvenientes agregue datos como ser

Velocidad de conexion, zona o barrio, version de sistema operativo(s), si usa router o modem, horarios en los que le funciona mejor y peor (si los hay).

Creo que con est información quizás podríamos ir organizando un reclamo con información puntual. Lamentablemente como sabemos ellos no sólo no están enterados sino que además tampoco se van a dar por enterados.

Si les parece, comienzo yo brindando esos datos... el que quiera aportar alguno otro que crea relevante, agregue!

[B]5megas (speedy duo)
Caballito - Capital federal
Ubuntu 10.04 (2 máquinas con idéntico problema aunque en Vista funciona OK)
Huawei HG520c (por wifi y lan)
Totalmente aleatorio, funciona mal todo el tiempo.[/B]


Saludos!

---

### Post by marcelo_bur on 2010-10-08
Yo tengo Speedy 1 mega, un modem Huavei (el que me trajo el kit) conectado a un router Kozumi que compre yo. Dos maquinas con Linux, una con Ubuntu 8.04 (la usa mi hija), la mia con Ubuntu 10.04, ambas conectadas al router por cable. Además una note con Vista que usa otra hija mia que vive al lado de casa, conectada por Wi-Fi al router, pero ella casi no la usa y no me hizo ningún comentario de que le funcione mal. Mi zona esta en el perfil, Burzaco, a 25 km al Sur de la Ciudad Autónoma de Buenos Aires. Me funciona bastante bien por la mañana y el resto del día es variable pero no funciona como debería. Los modelos del modem y router no los veo por el polvo que se les junto... jajaja. Creo que, como a todos, el problema se presenta únicamente en el protocolo http mientras que los protocolos que usan otros puertos diferentes al 80 funcionan con más velocidad que antes. No tengo problemas con https ni con el programa de correo ni con conecciones ftp (que uso mucho por mi dominio), ni con programas de mensajeria ni descargas de archivos.
Saludos

---

### Post by atari130xe on 2010-10-08
Bueno a partir del 15 de Setiembre tengo este problema, antes funcionaba muy bien, y con un perfil de 3 Megas llegaba a 4 megas tranquilamente.

[B]Barrio: Floresta (Capital federal) (no vale el chiste fácil) :lolflag:
Plan: Duo 3 Megas (Ethernet) Modem ZTE 831 II (modo router + un switch TP Link conectado a 2 PC's)
Distancia de la central en linea recta: menos de 500 metros.
Ambas Maquinas con Ubuntu 10.04.1
Funciona mal en cualquier horario, no cargan las páginas como corresponde y en el caso de Ubuntuforums si no carga, al darle reload recibo un archivo .php para descargar y/o abrir en lugar que la página se abra en Firefox como corresponde)[/B]

---

### Post by marcelo_bur on 2010-10-08
> Funciona mal en cualquier horario, no cargan las páginas como corresponde y en el caso de Ubuntuforums si no carga, al darle reload recibo un archivo .php para descargar y/o abrir en lugar que la página se abra en Firefox como corresponde)

HOla, yo usé Firefox por muchos años, pero ahora me funciona algo mejor con el Google Chrome.
De la central de Telfónica en Burzaco debo estar a unos 1500 mts.
Saludos

---

### Post by josecuervo86 on 2010-10-08
Aca van mis datos:

Zona: La Plata
Plan: Duo F5.0 Megas con un modem huawei que me vino, conectado a un router tp link.
SO: Ubuntu 10.04
Cuando anda mal? A la mañana anda "considerablemente" bien, pero ni pienses en navegar correctamente en horas de la tarde/noche por que NO SE PUEDE!

---

### Post by biale on 2010-10-08
No le daría muchas vueltas: todo indica que la red esta al límite o sobrecargada. O sea que en las horas "de baja", funciona mejor. 

Ya que estamos...

Zona: La Plata
Plan: Duo F5.0 Megas. Viejo Zytel 600 enrutando a un nodo WIFI. 
Una de las dos PCs opera con conexión directa, con lo cual descarto problemas en al WIFI.
SO: Ubuntu 10.04, Ununtu 9.10, WXP real, WXP virtual.
Funciona casi bien a 6:30 de la mañana. Y si es un sabado o domingo, mejor!
En horas de la tarde oscila entre muy-regular e imposible sugún los días.

---

### Post by marcelo_bur on 2010-10-08
Hola. Desde hace un rato estoy con Windows Xp, abriendo páginas al voleo. Con Ubuntu andaba entre regular y mal, sin embargo con XP estuvo casi normal, dos páginas no cargaron de una, tal vez porque como quiero hacer otras cosas apuré mucho la máquina. Estoy de acuerdo en que el problema esta en una saturación de las redes, sin embargo hay alguna cosita por ahi que hace que se note más en los sistemas operativos Linux y, por lo que lei, en Mac.
Saludos

---

### Post by atari130xe on 2010-10-08
Navegando (a la deriva) encontré este blog donde explica lo que está pasando con telefónica...

[http://blog.salinas.com.ar/2010/10/07/telefonica-y-el-proxy-de-los-misterios/#comment-22714]("http://blog.salinas.com.ar/2010/10/07/telefonica-y-el-proxy-de-los-misterios/#comment-22714")

---

### Post by biale on 2010-10-08
> Estoy de acuerdo en que el problema esta en una saturación de las redes, sin embargo hay alguna cosita por ahi que hace que se note más en los sistemas operativos Linux y, por lo que lei, en Mac.

En lo general, WNT (y sus etc) fué pensado para funcionar en redes lentas y es muy tolerante. Linux proviene de la filosofía Unix y fué mas bien pensado para operar en redes locales, redes de calidad razonable. 

De cualquier manera se trata de una deducción "a sentimiento" y no explica muy bien porque los paquetes "RST" bajo WXP, hablando en general, casi desaparecen. Tengo algunas otras ideas, pero a los efectos prácticos...

---

### Post by marcelo_bur on 2010-10-09
> **biale said:**
> En lo general, WNT (y sus etc) fué pensado para funcionar en redes lentas y es muy tolerante. Linux proviene de la filosofía Unix y fué mas bien pensado para operar en redes locales, redes de calidad razonable. 

De cualquier manera se trata de una deducción "a sentimiento" y no explica muy bien porque los paquetes "RST" bajo WXP, hablando en general, casi desaparecen. Tengo algunas otras ideas, pero a los efectos prácticos...

Hola. Yo no soy ningún experto en redes ni sistemas, apenas se lo suficiente como para no arruinar mi pc con frecuencia. Sin embargo a pesar de que las exigencias de WXP y Linux sean distintas, no cabe duda que hace más o menos un mes alguien modificó algo en la red de Speedy, porque antes no existia este problema y se navegaba muy bien o al menos, en mi caso, razonablemente bien para una conección de 1 mega como la mia.

---

### Post by atari130xe on 2010-10-09
> **marcelo_bur said:**
> Hola. Yo no soy ningún experto en redes ni sistemas, apenas se lo suficiente como para no arruinar mi pc con frecuencia. Sin embargo a pesar de que las exigencias de WXP y Linux sean distintas, no cabe duda que hace más o menos un mes alguien modificó algo en la red de Speedy, porque antes no existia este problema y se navegaba muy bien o al menos, en mi caso, razonablemente bien para una conección de 1 mega como la mia.

Coincido con vos Marcelo, yo antes del 15 de Setiembre, tenía un buen servicio, con un perfil de 3MB llegué a 4MB sin problemas, y tuve solo un par de interrupciones que duraron poco y fueron caidas generales de la zona, luego del 15 simplemente es una molestia navegar e inclusíve actualizar el sistema.

---

### Post by edboy on 2010-10-09
Buenas gente, me uní al foro después de leer este thread jajajaja, de igual manera después voy a empezar a ayudar correctamente xD.
Con respecto al tema de Speedy yo tambièn tengo los mismos síntomas y pasan exactamente en la misma franja horaria que ustedes detallaron, al llamar a telefónica me dijeron "Usted tiene virus en la PC", pero mirá que yo laburo en redes (esto es más o menos verdad xD) y el sniffer me tira esto y lo otro... TU TU TU TU TU TU...
En mi caso voy a llamar una vez más, si el problema persiste voy a levantar una queja en defensa del consumidor.

---

### Post by edboy on 2010-10-10
Gente, consulta, según anduve investigando formas de evadir estos cache proxy, una de las maneras podría ser agreando un Header al browser para hacer que el proxy consulte al sitio remoto en vez de resolverlo por sus DNS o mostrar una copia cacheada.

Encontré un programita ffproxy que según la documentación serviría para agregar headers pero no encontré la manera, también hay un add-on de Mozilla que se llama "Modify Headers" con el mismo probé forzando que firefox le agregue a todas las páginas http:// que había leido por ahí que podría llegar a andar.

Si alguién probó con esto avise así busco por otro lado xD.

---

### Post by marcelo_bur on 2010-10-11
> **edboy said:**
> Buenas gente, me uní al foro después de leer este thread jajajaja, de igual manera después voy a empezar a ayudar correctamente xD.
Con respecto al tema de Speedy yo tambièn tengo los mismos síntomas y pasan exactamente en la misma franja horaria que ustedes detallaron, al llamar a telefónica me dijeron **[COLOR="Red"]"Usted tiene virus en la PC"[/COLOR]**, pero mirá que yo laburo en redes (esto es más o menos verdad xD) y el sniffer me tira esto y lo otro... TU TU TU TU TU TU...
En mi caso voy a llamar una vez más, si el problema persiste voy a levantar una queja en defensa del consumidor.

Deciles que si,que se trata del [COLOR="red"]**"Speedy Chupasangre.deb"**[/COLOR]

---

### Post by marcelo_bur on 2010-10-11
> **edboy said:**
> Gente, consulta, según anduve investigando formas de evadir estos cache proxy, una de las maneras podría ser agreando un Header al browser para hacer que el proxy consulte al sitio remoto en vez de resolverlo por sus DNS o mostrar una copia cacheada.

Encontré un programita ffproxy que según la documentación serviría para agregar headers pero no encontré la manera, también hay un add-on de Mozilla que se llama "Modify Headers" con el mismo probé forzando que firefox le agregue a todas las páginas http:// que había leido por ahí que podría llegar a andar.

Si alguién probó con esto avise así busco por otro lado xD.

Instale el complemento de Firefox, aunque no creo que con eso se solucione, lo voy a dejar unos días a ver que pasa. En cuanto a ffproxi, la cosa es mucho más compleja y, la verdad, quienes tienen que arreglar las cosas son los de Speedy, no nosotros buscar como adaptar nuestras máquinas a sus quilombetes.
Saludos

---

### Post by edboy on 2010-10-11
> **marcelo_bur said:**
> Instale el complemento de Firefox, aunque no creo que con eso se solucione, lo voy a dejar unos días a ver que pasa. En cuanto a ffproxi, la cosa es mucho más compleja y, la verdad, quienes tienen que arreglar las cosas son los de Speedy, no nosotros buscar como adaptar nuestras máquinas a sus quilombetes.
Saludos

Tenés absolutamente toda la razón, pero bueno como me gusta meterme en esas cosas me fijé que onda y bueno eso es lo que encontré.

Lo más triste de esto es que en otras partes del mundo nuncá pasó esto a nivel popular, esto en Europa no se consigue xD.

Un abrazo.

---

### Post by marcelo_bur on 2010-10-11
Hay muchas cosas argentinas que en Europa no se consiguen, buenas y malas. Y hablando de cosas que "no se consiguen"... ¿Alguien sabe si se vende la tecla F5 suelta o es necesario cambiar todo el teclado cada vez que se gasta???

---

### Post by atari130xe on 2010-10-11
> **marcelo_bur said:**
> Hay muchas cosas argentinas que en Europa no se consiguen, buenas y malas. Y hablando de cosas que "no se consiguen"... ¿Alguien sabe si se vende la tecla F5 suelta o es necesario cambiar todo el teclado cada vez que se gasta???

Jajaja me hiciste reir con lo del F5 :lolflag:

---

### Post by teotihuacano on 2010-10-12
Buenas...
Yo tengo el problema hace meses. Hablé con no menos de 5 técnicos. Una de ellas con un Ubuntu al frente me guió para hacer una hora de pruebas. Al final me dijo "es cierto, hay un problema en la línea". Esto no impidió que dieran por resuelto el problema, tal como me dijeron en mis siguientes llamado. Por supuesto los siguientes no tuvieron problema en decirme que el problema era Linux hasta que uno me reconoció que no podían detectar el problema y no pueden hacer nada. En fin.
Tengo problemas hace al menos dos meses. Tal vez dos y medio.
Estoy en Almagro. Dell Inspiron 1420 y Del Inspiron 1500, ambas con Lucid. Mi vecina, con Window$ tiene el mismo problema, aunque no sé la frecuencia (usa mi conexión).
Por las mañanas trabajo a las 7am y no suelo tener problemas hasta las 10:30.Por las tardes es imposible (de hecho hoy se cayó del todo). 
Estuve a punto de contratar Telecentro, pero como llevo más de 4 años sin problemas, me cuesta romper una pared para pasar otro cable cuando todo andaba tan bien... Y ahora, al vez que no soy el único se renuevan mis esperanzas de que hagan algo...
Ya no tengo más propuestas.
Saludos

---

### Post by teotihuacano on 2010-10-12
Ultimo momento: llamé de nuevo con la info del foro de que no soy el único en el planeta  con este problema. Me pasaron con el sector "linux". El que me atendió me dijo que estaban al tanto del problema y que necesitaba mis datos (distro y si uso "mozilla o explorer" ¿?). Le pregunté si le estaban dando solución al tema, pero se puso el cassette de que en 72 horas tenía que estar resuelto. Le pregunté si me cambiarían de proxy o lo que sea, y se puso el cassette de nuevo. Tal vez estén ganando tiempo como siempre, pero recuperé las esperanzas.
Si funciona chiflo...

---

### Post by mama21mama on 2010-10-12
Ando probando esto [" hammerofthor - Hammer of Thor Proxy"]("http://mamalibre.eshost.com.ar/?q=comment/reply/525#comment-form").

Y dicen que funciona para el problema.

---

### Post by Tosh78 on 2010-10-13
Gente, yo no tengo el problema, pero vi este post en Taringa y me parecio bueno compartirlo con ustedes a ver si les sirve:
[http://www.taringa.net/posts/linux/7433868/Arreglar-Speedy-en-Linux.html]("http://www.taringa.net/posts/linux/7433868/Arreglar-Speedy-en-Linux.html")

Ojala les sirva!

---

### Post by marcelo_bur on 2010-10-13
Comencé a hacer reclamos.

Primer llamada:

13/10/2010 - 12:27 hs
Operador: Maruricio
Resultado de la gestión: Me cortó la comunicación.

Segunda llamada:

13/10/2010 - 12:30 hs

Operador: Lucas

Resultado de la gestión: Me toman un reclamo por problemas en la navegación. El número de reclamo es 404019650. Afirma que para el viernes 15/10 el problema debería estar solucionado.

Saludos

---

### Post by edboy on 2010-10-13
> **marcelo_bur said:**
> Comencé a hacer reclamos.
 
Primer llamada:
 
13/10/2010 - 12:27 hs
Operador: Maruricio
Resultado de la gestión: Me cortó la comunicación.
 
Segunda llamada:
 
13/10/2010 - 12:30 hs
 
Operador: Lucas
 
Resultado de la gestión: Me toman un reclamo por problemas en la navegación. El número de reclamo es 404019650. Afirma que para el viernes 15/10 el problema debería estar solucionado.
 
Saludos
 
Debería porque se deben cumplir los SLAs, es una mentira enorme, voy a fichar el post de T!
 
Además instalé el hammerthor pero no me funcionó muy buen, tendría que ver bien que hosts tengo que restringir, apenas sepa algo lo posteo.
 
Un saludo.

---

### Post by marcelo_bur on 2010-10-13
> **edboy said:**
> Debería porque se deben cumplir los SLAs, es una mentira enorme, voy a fichar el post de T!
 
Además instalé el hammerthor pero no me funcionó muy buen, tendría que ver bien que hosts tengo que restringir, apenas sepa algo lo posteo.
 
Un saludo.

Hola. Por supuesto que se que es puro verso y que el viernes va a seguir igual que ahora. Pero quiero al menos sumar reclamos, cosa que no venía haciendo porque se como viene la mano, al final perdes montones de tiempo, y eso que hoy tuve suerte y me comuniqué rápido. Voy a tratar de invertir algo de tiempo en seguir reclamandoles, no se me ocurre nada mejor. Ahora está por pasar en esta zona Telecentro, pero si vos buscar en la web tambien hay montones de quejas. Y para ser sincero con Speedy es la primer vez en muchos años que tengo problemas realmente serios con el servicio.
En cuanto a seguir instalando cosas, repito lo que escribi en un post anterior, le corresponde a Speedy normalizar el servicio, no a nosotros adaptar nuestras máquinas para que funcionen aunque sea un poco mejor. Y, aunque Ubuntu sea un sistema seguro, siempre se corre el riesgo de que instalando tantas cosas tengamos un disgusto, lo cual me consta proque cuando comencé con Ubuntu quería ver todo, instalar todo, aprender todo y eso me trajo algunos dolores de cabeza.
Saludos

---

### Post by marcelo_bur on 2010-10-13
> **edboy said:**
> Debería porque se deben cumplir los SLAs, es una mentira enorme, voy a fichar el post de T!
 
Además instalé el hammerthor pero no me funcionó muy buen, tendría que ver bien que hosts tengo que restringir, apenas sepa algo lo posteo.
 
Un saludo.

Hola. Por supuesto que se que es puro verso y que el viernes va a seguir igual que ahora. Pero quiero al menos sumar reclamos, cosa que no venía haciendo porque se como viene la mano, al final perdes montones de tiempo, y eso que hoy tuve suerte y me comuniqué rápido. Voy a tratar de invertir algo de tiempo en seguir reclamandoles, no se me ocurre nada mejor. Ahora está por pasar en esta zona Telecentro, pero si vos buscar en la web tambien hay montones de quejas. Y para ser sincero con Speedy es la primer vez en muchos años que tengo problemas realmente serios con el servicio.
En cuanto a seguir instalando cosas, repito lo que escribi en un post anterior, le corresponde a Speedy normalizar el servicio, no a nosotros adaptar nuestras máquinas para que funcionen aunque sea un poco mejor. Y, aunque Ubuntu sea un sistema seguro, siempre se corre el riesgo de que instalando tantas cosas tengamos un disgusto, lo cual me consta proque cuando comencé con Ubuntu quería ver todo, instalar todo, aprender todo y eso me trajo algunos dolores de cabeza.
Saludos

---

### Post by biale on 2010-10-13
Marcelo:

En este caso se trata de un programita python muy sencillo, que ni siquiera se instala, solo los 3,5 Mb de prerrequisitos. Si no te gusta no lo ejecutas y lo borras. Y si, tambien volves atras el toque a FFox.

En lo demás estoy 99% de acuerdo: concretamente estoy estudiando el cambio de ISP, aunque aquí no exista Telecentro. Yo voy por el segundo reclamo y en breve haré el tercero.

Edito: y parece que esta funcionando, solo una pérdida de velocidad.

---

### Post by Sarumannet on 2010-10-13
Hola gente!!!

Estoy probando el "hammerofthor", y *FUNCIONA*\\:D/
Lo que hace, es lo que no hace por default los navegadores cuando 
reciben un connection reset como respuesta del proxydelORT de Speedy:
REINTENTA hasta lograr la conexión, lo cual es mucho mejor que
recibir un "no se puede mostrar la página" o que falten elementos en
la misma.

Entra dentro de la categoría Argentina, frente a algo que no funciona
"lo atamos con alambre". Por lo menos torna el sistema en "navegable".

Brillante parche-solución y todos los créditos para el autor:

=D>Alejandro Santos=D>

Página oficial del proyecto:
[http://code.google.com/p/hammerofthor/](http://code.google.com/p/hammerofthor/)

Les mando un Output del Script hammerofthor.py para que vean los 
reintentos que tuvo que hacer en una navegación al azar
(sucede cuando aparece "Thor esta esperando")

[I]Thor esta a la escucha.
Intento de conexion a:  91.189.90.40:80
Intento de conexion a:  69.147.125.65:80
Intento de conexion a:  190.210.62.10:80
Intento de conexion a:  190.210.62.10:80
Thor esta esperando
Intento de conexion a:  190.210.62.10:80
Thor esta esperando
Intento de conexion a:  190.210.62.10:80
Intento de conexion a:  190.210.62.10:80
Intento de conexion a:  190.210.62.10:80
Intento de conexion a:  69.147.76.120:80
Intento de conexion a:  69.147.76.120:80
Intento de conexion a:  69.147.76.120:80
Intento de conexion a:  190.210.62.10:80
Intento de conexion a:  76.13.6.31:80
Intento de conexion a:  205.128.71.126:80
Intento de conexion a:  69.147.125.65:80
Intento de conexion a:  74.6.239.84:80
Intento de conexion a:  69.147.76.120:80
Intento de conexion a:  190.210.62.10:80
Intento de conexion a:  190.210.62.10:80
Intento de conexion a:  76.13.6.31:80
Intento de conexion a:  190.210.62.10:80
Intento de conexion a:  190.210.62.17:80
Intento de conexion a:  190.210.62.10:80
Thor esta esperando
Thor esta esperando
Intento de conexion a:  190.210.62.10:80
Thor esta esperando
Intento de conexion a:  98.137.80.75:80
Intento de conexion a:  69.147.79.51:80
Intento de conexion a:  200.42.136.212:80
Thor esta esperando
Thor esta esperando
Intento de conexion a:  200.42.136.212:80
Thor esta esperando
Thor esta esperando
Thor esta esperando
Thor esta esperando
Intento de conexion a:  200.42.136.212:80
Intento de conexion a:  200.42.136.212:80
Intento de conexion a:  200.42.136.212:80
Intento de conexion a:  200.42.136.212:80
Thor esta esperando[/I]
...

En la página oficial está cómo configurarlo.
Lo estoy usando con FireFox en Ubuntu 10.04

Saludos!

---

### Post by alfplayer on 2010-10-13
Y los pasos básicamente son... ejecutarlo y configurar el navegador con el proxy SOCKS v5 en puerto 8081.

---

### Post by marcelo_bur on 2010-10-13
Hola. Lo instalé y parece que funciona. Pero insisto en que no es nuestro problema, el servicio tiene que funcionar sin todo esto. Además piensen algo, aqui hay gente que sabe mucho, yo algo me defiendo, ¿pero que pasa con los que recién se inician en Linux y tienen que pasar por esto? ¿no creen que se les va a hacer un bodrio en la cabeza y van a volver mansitos a Windows? Yo creo que si, y no podemos quedarnos tranquilos simplemente porque quienes ya más o menos manejan el tema encontremos la forma, o lo atemos con alambre a la argentina, como lei por ahi.
Bue, lástima que no se puede configurar en Google, voy a tener que pasar todos los favoritos a Firefox, no encontre como configurar "SOCKS v5" en Google. Y algo más, esto este en el README del programita:

[B]"El proxy fue diseñado para correr en la PC del usuario afectado. No esta 
pensado para ser usado abiertamente en Internet ya que no tiene restricciones
de seguridad.

Repito: El proxy no tiene ninguna restriccion de seguridad, por lo que deberan
configurar correctamente el firewall de su PC.

Es un patch para no tener que sufrir la incorrecta configuracion del ISP. 

Lamentablemente este software es una solucion de compromiso, y como desventaja
tiene que la navegacion de los sitios web puede ser mucho mas lenta de lo
normal.

Eso se debe a que la deteccion del flag RST se hace disparando un timer que 
espera una determina cantidad de tiempo, calibrado sin ninguna clase de metodo
cientifico.

Repito: este proxy no es una solucion permanente sino una forma de salir del
paso."[/B]

Saludos

---

### Post by LolaMora on 2010-10-13
Tengo el mismo problema. Maldito speedy  @&#@~....:mad:

En mi caso fue cuando me calenté hace unas semanas porque me cobraban por un servicio de 3 megas y la transferencia venía a pata. Los llamé para cambiar de 3 Mb a 1 Mb y para reclamarles que cobran un servicio que no dan.
A partir ahi, solo tengo cortes permanentes. ¬¬

Mi nro. de reclamo  404076778
Fecha     13/10/2010 19:20 hs

Disculpas por la bronca. :|



PD: en mi zona, telefónica es monopolio, no hay otro.

---

### Post by Sarumannet on 2010-10-13
Marcelo, creo que todos te damos la razón en que el problema es de Speedy. También es cierto que más que atar con alambre otra cosa no nos queda, salvo que dejar reverendas pu..adas al soporte inexistente del ISP.
 
El script, de por sí, no crea ninguna inseguridad, sólo reintenta la conexión cuando no se podría normalmente por el quil...mbo de Speedy. No genera más demoras que las existentes por el ISP.
 
No le pasa por arriba a nada más de lo que estás haciendo con tu navegador, que si lo hacés desde Linux, tenés MUCHAS menos chances de que te embiches.
 
Por otro lado, lo más terrible de la situación es que no se pueden usar los servicios de OpenDNS, o peor aún, que si usás otros DNS que no sean de Speedy, como por ejemplo los de google, Speedy los ignora.
 
Esto significa que si alguien hackea los DNS de $peedy, vamos a conectarnos en lugar de banconación.com a cualquierverdura.com 
 
Estoy de acuerdo a que hay que seguir r******o los h****s a $peedy, porque esta no es una solución definitiva, pero es por lo menos una solución de TRANSICIÓN hasta que, por lo menos aquellos que no podemos contar con más de una oferta de ISP, sino que dependemos de un p******o monopolio (cosa que nuestra presidenta evidentemente quiere romper, borrando una alternativa como la de Fibertel) podamos seguir navegando "aceptablemente" ya que no nos queda otra.
 
Saludos!

---

### Post by guillermolisi on 2010-10-13
Sarumannet, por favor cuida tus expresiones idiomaticas ya que este foro es publico, internacional, es auditado y rigen pautas de uso y convivencia (Codigo de Conducta). Gracias.

---

### Post by Sarumannet on 2010-10-13
Para las víctimas de Windows, y de $peedy con el problema de los proxys transparentes, pueden hacer las siguiente prueba para comprobar que lo que les digo de los DNS es tal-cual.

1) inicio->ejecutar->cmd.exe [enter]
2) notepad C:\WINODWS\System32\drivers\etc\hosts
3) agregar una linea que diga:
   127.0.0.1       [www.google.com.ar](www.google.com.ar)
4) archivo->guardar
5) abran cualquier navegador y en la barra de direcciones pongan: 
   [http://www.google.com.ar](http://www.google.com.ar)
=> El resultado debería ser "no se puede conectar con el servidor"

¿Por qué? -> Porque el archivo hosts modificado tiene prioridad a cualquier búsqueda por DNS; [www.google.com.ar](www.google.com.ar) apunta a 127.0.0.1 que es nuestra máquina, y por supuesto nosotros no somos Google :mrgreen:

6) Modifiquen la línea agregada a la dirección 127.0.0.1 a la dirección 1.1.2.1 (que es cualquier verdura, ni nosotros, menos Google)
7) archivo->guardar
8) abran cualquier navegador y en la barra de direcciones pongan: [http://www.google.com.ar](http://www.google.com.ar)
=> El resultado debería ser "no se puede ..." UN MOMENTO, ¿QUÉ PASÓ? Abrió Google ????? ¡Chispas Batman! ¡Santas trampillas de $peedy! :confused:

Eso significa que no importa lo que nos resuelvan nuestros DNS (que son nuestras guías telefónicas) no importa el número que marquen, siempre tendremos a un intermediario irrespetuoso $peedy :(

¡CÁSPITA! :confused:

---

### Post by Sarumannet on 2010-10-13
> **guillermolisi said:**
> Sarumannet, por favor cuida tus expresiones idiomaticas ya que este foro es publico, internacional, es auditado y rigen pautas de uso y convivencia (Codigo de Conducta). Gracias.

Perdón por los vocablos impropios, trataré de usar sinónomos infantiles.
Gracias por la comprensión
Saludos!!!

---

### Post by edboy on 2010-10-13
> **Sarumannet said:**
> Para las víctimas de Windows, y de $peedy con el problema de los proxys transparentes, pueden hacer las siguiente prueba para comprobar que lo que les digo de los DNS es tal-cual.

1) inicio->ejecutar->cmd.exe [enter]
2) notepad C:\WINODWS\System32\drivers\etc\hosts
3) agregar una linea que diga:
   127.0.0.1       [www.google.com.ar]("http://www.google.com.ar")
4) archivo->guardar
5) abran cualquier navegador y en la barra de direcciones pongan: 
   [http://www.google.com.ar](http://www.google.com.ar)
=> El resultado debería ser "no se puede conectar con el servidor"

¿Por qué? -> Porque el archivo hosts modificado tiene prioridad a cualquier búsqueda por DNS; [www.google.com.ar]("http://www.google.com.ar") apunta a 127.0.0.1 que es nuestra máquina, y por supuesto nosotros no somos Google :mrgreen:

6) Modifiquen la línea agregada a la dirección 127.0.0.1 a la dirección 1.1.2.1 (que es cualquier verdura, ni nosotros, menos Google)
7) archivo->guardar
8) abran cualquier navegador y en la barra de direcciones pongan: [http://www.google.com.ar](http://www.google.com.ar)
=> El resultado debería ser "no se puede ..." UN MOMENTO, ¿QUÉ PASÓ? Abrió Google ????? ¡Chispas Batman! ¡Santas trampillas de $peedy! :confused:

Eso significa que no importa lo que nos resuelvan nuestros DNS (que son nuestras guías telefónicas) no importa el número que marquen, siempre tendremos a un intermediario irrespetuoso $peedy :(

¡CÁSPITA! :confused:

Interesantísimo tu comentario, al menos aprendí un poco más de que era el archivo hosts, un capo la verdad ;)

Voy a probar lo del Hammerthor a ver que onda, había hecho un par de pruebas locas pero no había funcionado, de igual manera voy a seguir intentando.

Saludos,

---

### Post by edboy on 2010-10-13
Ya lo probé y vi la salida en la terminal. ¡Funciona!, Es una excelente solución temporaria pero igualmente los reclamos a Speedy no deben cesar.  

Con respecto a la seguridad yo les recomiendo que instalen Firestarter, el firewall ese anda bastante bien, ojo no tiene protección muy buena contra Buffer Overflow, pero algo es algo al menos para estar un poquito más seguro en Inet.  Saludos!!!

---

### Post by guillermolisi on 2010-10-14
> **edboy said:**
> Ya lo probé y vi la salida en la terminal. ¡Funciona!, Es una excelente solución temporaria pero igualmente los reclamos a Speedy no deben cesar.  

Con respecto a la seguridad yo les recomiendo que instalen Firestarter, el firewall ese anda bastante bien, ojo no tiene protección muy buena contra Buffer Overflow, pero algo es algo al menos para estar un poquito más seguro en Inet.  Saludos!!!
Firestarter es una interface grafica para administrar las reglas de iptables del firewall de Linux, que se encuentra como parte del kernel. Es decir, Firestarter no es el firewall, solo una aplicacion grafica (que ya tiene sus años y que para entornos personales y domesticos esta muy buena. Para entornos mas exigentes hay otras como Shorewall, Zentyal -ex eBox-, FirewallBuilder, etc.)

---

### Post by marcelo_bur on 2010-10-14
> **guillermolisi said:**
> Firestarter es una interface grafica para administrar las reglas de iptables del firewall de Linux, que se encuentra como parte del kernel. Es decir, Firestarter no es el firewall, solo una aplicacion grafica (que ya tiene sus años y que para entornos personales y domesticos esta muy buena. Para entornos mas exigentes hay otras como Shorewall, Zentyal -ex eBox-, FirewallBuilder, etc.)

Hola. Desde que uso Linux he dejado de preocuparme por antivirus y firewalls. Y, si entiendo bien el mensaje anterior, el firewall ya existe y corre en nuestros sistemas operativos por default. Y estas aplicaciones solo sirven para personalizarlo. ¿Estoy en lo cierto?
Saludos

PD: A esta hora no se notan los problemas a los que nos venimos refiriendo en este thread.

---

### Post by biale on 2010-10-14
Sigo pensando que en realidad, lo que aparenta ser un problema de "soporte técnico" debería considerarse un problema "del servicio" y lo único que hace Linux/ Mac es mostrarlos de una manera mas taxativa que Windows. Les gusta si digo "QoS"?

Por ejemplo, de acuerdo con los tests de Berkeley, el proxy entrega desde cache incluso datos variables y que no deberían obtenerse desde allí, grandes retardos de buffering, etc

Aún antes de saber todo esto, mi primer reclamo fue por los DNS, con retardos cercanos a los 200 mseg (y encima ahora sabemos que además estan forzados).

Desgraciadamente todas estas cosas son compatibles con los pensamientos expresados a nivel internacional por parte de Telefónica, basta Googlear para corroborarlo.

> borrando una alternativa como la de Fibertel 

Todavía no esta dicha la última palabra...

> el firewall ya existe y corre en nuestros sistemas operativos por default.

Los puertos no se abren por casualidad. Hace falta una aplicación que los abra.

---

### Post by marcelo_bur on 2010-10-14
Yo no soy de los que más saben en este foro, pero recuerdo que mucho antes de iniciarse este problema (a fines del 2009 o principios del 2010) quien brinda webhosting a mi dominio mudo de datacenter, de Holanda a Houston creo, y me envió los nuevos DNS para que verifique elfuncionamiento en el nuevo servidor. Cambie los DNS para mi dominio en el archivo /etc/hosts y sin embargo siempre obtenía la página en su alojamiento aún oficial. Esto le llamo mucho la atención al soporte de mi host y muestra que evidentemente Speedy ignora completamente los datos que nuestras máquinas puedan enviar desde hace mucho tiempo.

---

### Post by Sarumannet on 2010-10-14
> **marcelo_bur said:**
> Yo no soy de los que más saben en este foro, pero recuerdo que mucho antes de iniciarse este problema (a fines del 2009 o principios del 2010) quien brinda webhosting a mi dominio mudo de datacenter, de Holanda a Houston creo, y me envió los nuevos DNS para que verifique elfuncionamiento en el nuevo servidor. Cambie los DNS para mi dominio en el archivo /etc/hosts y sin embargo siempre obtenía la página en su alojamiento aún oficial. Esto le llamo mucho la atención al soporte de mi host y muestra que evidentemente Speedy ignora completamente los datos que nuestras máquinas puedan enviar desde hace mucho tiempo.
 
Totalmente de acuerdo. Esto pasa desde el 2007, como lo denuncia Javier en su blog:
[http://blog.salinas.com.ar/2007/10/15/el-proxy-de-peedy/](http://blog.salinas.com.ar/2007/10/15/el-proxy-de-peedy/)

---

### Post by teotihuacano on 2010-10-14
Ayer me andaba el hammer of thor y hoy me dice  "la conexión al servidor fue reiniciada mientras la página se cargaba". Ayer era lento, pero al menos andaba. Hoy ni eso.
¿A alguien más le pasa?

---

### Post by marcelo_bur on 2010-10-14
Hola. Ayer me pasó una vez durante el tiempo que lo use, y también una vez en lugar de abrir la página me ofreció guardar un archivo .php.
Hoy todavía no active el script porque durante las mañanas a mi me funciona bastante bien y prefiero usar Chromium, recién ahora se esta poniendo pesada la cosa. En estoy momentos con Firefox estoy cargando archivos a Terabox que, como usa HTTPS, no tiene problemas. Apenas termine la carga pruebo y comento algo.
Saludos

---

### Post by marcelo_bur on 2010-10-14
> **teotihuacano said:**
> Ayer me andaba el hammer of thor y hoy me dice  "la conexión al servidor fue reiniciada mientras la página se cargaba". Ayer era lento, pero al menos andaba. Hoy ni eso.
¿A alguien más le pasa?

Hola. Lo estoy probando y anda casi igual que ayer, tal vez un poco más lento y me tiró un par de errores (ofreció guardar un archivo php y tiro una página en blanco).
Saludos

---

### Post by atari130xe on 2010-10-14
El script me funcionó ayer un rato y luego de puso complicado, asi que lo tuve que desactivar, en cuanto a los de bajar archivos .php me viene pasando desde hace rato y más en Ubuntuforums... Por supuesto como desde hace varias semanas vengo llamando al 0800 333 7733 opción cero para "activar" mi reclamo... "estamos trabajando en solucionar el inconveniente, pero no tenemos aún una fecha estimada de solución, de todas maneras seguramente (sic) los días sin servicio le serán descontados en su proxima factura" :lolflag:

---

### Post by marcelo_bur on 2010-10-14
Hola. Pasé a Window$ (Perdón, no se si está permitido postear aqui usandolo...) y no tira ningún error, en tanto que con Ubuntu la cosa venía muy pesada. El scrip a mi me funciona bastante bien y en realidad solo pase un rato a Windo$ para scanear, aún no he conseguido un programa que me scanee bien y rápido en Ubuntu. Y de paso quise ver como andaba navegando.
Saludos

PD: Yo tendría que renovar mi reclamo si para mñana por la tarde el problema subsiste. Lo más curioso es que ni siquiera me preguntaron que sistema operativo uso, ni que navegador, en realidad nada, se limitaron a tomar el reclamo y darme el numero.

---

### Post by edboy on 2010-10-14
> **marcelo_bur said:**
> Hola. Pasé a Window$ (Perdón, no se si está permitido postear aqui usandolo...) y no tira ningún error, en tanto que con Ubuntu la cosa venía muy pesada. El scrip a mi me funciona bastante bien y en realidad solo pase un rato a Windo$ para scanear, aún no he conseguido un programa que me scanee bien y rápido en Ubuntu. Y de paso quise ver como andaba navegando.
Saludos

PD: Yo tendría que renovar mi reclamo si para mñana por la tarde el problema subsiste. Lo más curioso es que ni siquiera me preguntaron que sistema operativo uso, ni que navegador, en realidad nada, se limitaron a tomar el reclamo y darme el numero.

Porque son re grosos, ya saben de antemano cual es tu problema y seguro que te lo van a solucionar ;).

> **guillermolisi said:**
> Firestarter es una interface grafica para  administrar las reglas de iptables del firewall de Linux, que se  encuentra como parte del kernel. Es decir, Firestarter no es el  firewall, solo una aplicacion grafica (que ya tiene sus años y que para  entornos personales y domesticos esta muy buena. Para entornos mas  exigentes hay otras como Shorewall, Zentyal -ex eBox-, FirewallBuilder,  etc.)

¡¡¡Gracias por la aclaración!!!  Entonces me voy a instalar alguno de esos firewalls para administrar mejor a iptables solo para probarlos, me gusta mucho el tema de la seguridad informática y bueno para aprender no debe venir mal, además si el proxy no me provee seguridad alguna prefiero que algo lo haga.

Con respecto a los problemas que arrojó hammertor a mi también me pidió un par de veces de bajar un .php, pero fueron contadas y después no lo hizo más.

Saludos.

---

### Post by guillermolisi on 2010-10-14
Cuando te pide bajar un archivo .php es porque algo no anduvo bien en la conexion con el website, nada mas que eso. Los .php son scripts que se ejecutan en el server pero si algo no funciona bien entre el server y elcliente suele pasar el archivo para su descarga.

---

### Post by marcelo_bur on 2010-10-15
Hola. Después de estar navegando un rato, ayer por la tarde, con XP sin que se presente el problema del que estamos tratando, debo reconocer que mis esperanzas de que este tema se solucione con rapidez han disminuido considerablemente. Al igual que me sucedió con Terabox, me da la impresión de que los usuarios de Linux somos para Speedy, y posiblemente para otros ISP también, clientes de segunda y, en cualquier momento, nos van a decir, como me sucedió con el mencionado Terabox, que Speedy garantiza el servicio únicamente para usuarios bajo ciertos SO que, por cierto, no incluyen Linux. Y lamentablemente en este querido, pero difícil muchas veces de comprender, país parece que son más importantes los derechos de un delincuente que los derechos de un usuario. Hay mucho que solucionar, entre ello lograr que nosotros mismos tomemos conciencia de nuestros derechos y de nuestra **obligación** de hacer respetar esos derechos. Aquí todo el mundo te pisotea y nadie dice nada, desde lo más alto del gobierno hasta nosotros mismos, hablando en términos generales. Y, aunque en realidad no viene al tema, me hace recordar al spam telefónico que recibimos continuamente, yo participo en un foro yanqui y se comentó el tema, allí basta con hacer una llamada a una especie de ente regulador, dar tu número y pedir que no te llamen con ofertas y listo.
Bue, me estoy yendo por las ramas, espero tener tiempo y acordarme de renovar mi reclamo esta tarde.
Saludos

---

### Post by guillermolisi on 2010-10-15
Algo que surgio anoche, durante la Release Party de BsAs, es que podrian existir posibilidades de alguna especie de sabotaje y/o conflicto interno en esa empresa que la complican operativamente para que logre resolver el inconveniente.

Hace unos años atras hubieron casos de conflictos gremiales que se materializaron con la rotura de troncales de fibra optica en las cajas subterraneas de Telefonica y que dejaron por varios dias a muchisima gente sin telefonia y comunicacion de datos.

Por otra parte, creo que siendo este problema tan masivo a nivel nacional, deberian canalizar las quejas a traves de los organismos de defensa del consumidor que existan en cada zona. Seria una buena manera de integrar los reclamos en lugares donde saben bien con quien hablar, como plantear el tema y que derechos y obligaciones deben ser observadas por las partes.

---

### Post by marcelo_bur on 2010-10-15
> **guillermolisi said:**
> Algo que surgio anoche, durante la Release Party de BsAs, es que podrian existir posibilidades de alguna especie de sabotaje y/o conflicto interno en esa empresa que la complican operativamente para que logre resolver el inconveniente.

Hace unos años atras hubieron casos de conflictos gremiales que se materializaron con la rotura de troncales de fibra optica en las cajas subterraneas de Telefonica y que dejaron por varios dias a muchisima gente sin telefonia y comunicacion de datos.



Hola. Tal vez sea posible, pero hay un detalle que a mi me hace pensar que no viene por ahí la cosa. Por las mañanas, horas de menos tráfico en la red, a mi el servicio me funciona muy bien, después del mediodia cada vez se pone peor. Si algo estuviese saboteado, roto o como sea, sería constante las 24 hs. del día. Salvo que se puedan hacer sabotajes con "timer", no se tanto.
Saludos

---

### Post by atari130xe on 2010-10-15
En micaso no tengo horarios específicos, casi siempre funciona mal, de a momento bien de a momentos mal pero no hay uniformidad. Las acutalizaziones de Ubuntu son una pesadilla, porque dan error continuamente (refused) así que debo insistir con "instalar actualizaciones" al menos 4 veces hasta que acepta la petición el servidor de Ubuntu y logra bajar los paquetes. Ya me tomé por costumbre llamar al 0800 333 7733 cada 72/96hs y reclamar para no dejar que me cierren el caso al menos obtener una compensación económica.

---

### Post by marcelo_bur on 2010-10-15
Hola. Supongo que lo mejor sería acudir a Defensa del Consumidor [http://www.adduc.org.ar/]("http://www.adduc.org.ar/") tal como sugirio Guillermo Lissi. Sería interesante presentarnos todos juntos en Capital, sin embargo no es tan fácil de coordinar. En el link que acabo de dejar figuran las direcciones de las filiales, en Burzaco por ejemplo hay una. Si luego de algunos reclamos más a Speedy todo sigue igual voy a ver que puedo hacer presentandome en la filial de Burzaco.
Saludos

---

### Post by biale on 2010-10-15
Desgraciadamente he comprobado que hammerofthor comienza funcionando muy bien, pero pasado un cierto tiempo se bloquea la conexión "mal", sin forma sencilla de resolver la situación. 

> Si algo estuviese saboteado, roto o como sea, sería constante las 24 hs. del día.

Coincido!

> creo que siendo este problema tan masivo a nivel nacional, deberian canalizar las quejas a traves de los organismos de defensa del consumidor que existan en cada zona.  

O sea que los organismos estatales de control (CNC, etc) están al tanto o deberían estarlo. De todas maneras sospecho (y coincido) que vamos a tener que ir a Defensa al Consumidor para que Speedy respete los días caídos en la facturación.

Toque de humor: Dicen que algunas netbooks del plan conectar se entregarían con Ubuntu (?). Si hoy intentaran conectarlas a la red de Speedy entonces...

---

### Post by guillermolisi on 2010-10-15
> **biale said:**
> 
Toque de humor: Dicen que algunas netbooks del plan conectar se entregarían con Ubuntu (?). Si hoy intentaran conectarlas a la red de Speedy entonces...
Si, 2.5 millones de netbooks salen con Ubuntu dentro de ese plan. El tema es que no solo tienen el problema de Telefonica sino que la gran mayoria no tiene suficiente ancho de banda para sostener la cantidad de netbooks que se conectaran en cada escuela (algunas ni tienen enlace).

De hecho en una de Ramos Mejia haran una conexion de 10Mb especialmente por este asunto del Plan Conectar Igualdad, con lo cual viene la otra pregunta obligada ... las troncales soportaran este aumento geometrico de demanda ? Y los enlaces internacionales ? Todo un tema.

PS: La CNC no existe, asi que vayan por el lado de Defensa del Consumidor.

---

### Post by dannet on 2010-10-15
Buenas gente, no tuve tiempo de leer los mensajes anteriores por lo que es posible que lo que diga ya lo hayan dicho.

En mi caso solucioné (al menos temporalmente, como parche) el problema con las siguientes rules de iptables:

```
iptables -A OUTPUT -p tcp --dport 80 -m state --state NEW -m recent --set --name thor --rdest -j ACCEPT
iptables -A INPUT -p tcp -m tcp --tcp-flag RST RST -m state --state ESTABLISHED -m recent --name thor --rcheck --rsource --seconds 1 -j DROP
```

Encontré esta solución hace algunos días en una lista de correos y funciona muy bien, obviamente los créditos van para su autor el cual lamentablemente no recuerdo quien fue. 
Lógicamente se hace un poco más lenta la conexión, pero en realidad esto ocurre con la respuesta RST, por lo que en realidad ahorramos tiempo ya que evitamos el error mostrado en el navegador y tener que recargar, es decir, la carga termina siendo igual de rápida/lenta que sin las reglas.

Por otro lado, hablando con un técnico de speedy que sabe mucho del tema (uno de los pocos que conocí en esa empresa que estudio redes y sabe y tiene vocación), me contó que desde hace unos días está trabajando para solucionar esto un tipo que sabe también mucho, encargado de capacitar a los técnicos, por lo que es probable que en poco tiempo se solucione.

También leí recien al pasar en uno de los pots últimos de este thread sobre acudir al CNC, yo voy a ir si puedo hoy o el lunes que viene a presentar el reclamo, creo que lo ideal seria que el que pueda hacerlo lo haga, al menos para meterle más presión a la empresa al ver que varios usuarios están presentando reclamos.

Saludos!
Daniel

---

### Post by mama21mama on 2010-10-15
Creo que la [fuente es aquí]("https://lists.ubuntu.com/archives/ubuntu-ar/2010-October/034015.html") de las reglas de iptables. 

en a lista de correo de ubuntu-ar

probare este método luego de probar el hammeroftor,

---

### Post by atari130xe on 2010-10-15
Bueno al menos ya obtuve el primer descuento del servicio de Internet que compensa los días del més de Setiembre (17 al 31) que en mi caso son $ 32,50 menos a pagar (de una factura total de 114,50) algo es algo al menos por el lado económico hoy hablé con la parte administrativa y les hice el reclamo y una señorita del sector facturación me anuló la última factura que ya está impresa, Veremos hasta que solucionen el problema, que pasa con los días subsiguientes...

---

### Post by marcelo_bur on 2010-10-15
> **guillermolisi said:**
> Si, 2.5 millones de netbooks salen con Ubuntu dentro de ese plan. El tema es que no solo tienen el problema de Telefonica sino que la gran mayoria no tiene suficiente ancho de banda para sostener la cantidad de netbooks que se conectaran en cada escuela (algunas ni tienen enlace).

De hecho en una de Ramos Mejia haran una conexion de 10Mb especialmente por este asunto del Plan Conectar Igualdad, con lo cual viene la otra pregunta obligada ... las troncales soportaran este aumento geometrico de demanda ? Y los enlaces internacionales ? Todo un tema.

PS: La CNC no existe, asi que vayan por el lado de Defensa del Consumidor.


Creo que ha cruzado por la cabeza de muchos usuarios este asunto de la enorme cantidad de nuevos usuarios que, además de los normales, se conectarán con el Plan Conectar Igualdad. Supuestamente tendría que haber un estudio previo de las consecuencias y de los ajustes necesarios para que todo funcione bien, sin perjudicar a nadie. Pero vivimos donde vivimos y, a pesar de que tiendo a ser un "nacionalista", no puedo negar que en este país muchas cosas se hacen solo por ganar réditos políticos sin una debida planificación.
Si las redes no aguantan el problema que aquí estamos tratando y que repercute especialmente en usuarios de Linux y Mac, se extenderá a todos los usuarios del pais y, en definitiva, ya no se tratará de un "Plan Conectar Igualdad, sino en un **[COLOR="Red"]"Plan Nadie Pueda Conectarse Igualdad"[/COLOR]**.
Saludos

---

### Post by biale on 2010-10-15
> no tiene suficiente ancho de banda para sostener la cantidad de netbooks que se conectaran en cada escuela (algunas ni tienen enlace).

Y todavía falta mencionar el problema de la "última milla", que suele ser mas dramático de lo que se piensa. Con ADSL cuesta llegar a los 10 Mbps y si hay que plantar antena el chiche es caro.

De todas maneras la Web "sencilla" no carga mucho a la red. El problema comienza cuando hay que sostener flujos de datos con BW impuesto por la calidad del servicio. O sea que no soy un gran creyente en los proxys solo para ahorrar ancho de banda.

Ademas nos hemos auto-generado una situación kafkiana. Se trata de desconectar y reconectar el 20/ 25% de la red instalada para mediados de diciembre, para luego (supuestamente) revolear la infraestructura fibra-cable. Desde el punto de vista estrictamemte económico: eso no es gratis, las molestias y los mayores costos alguien los tiene que pagar.

---

### Post by Sarumannet on 2010-10-15
> **mama21mama said:**
> Creo que la [fuente es aquí]("https://lists.ubuntu.com/archives/ubuntu-ar/2010-October/034015.html") de las reglas de iptables. 

en a lista de correo de ubuntu-ar

probare este método luego de probar el hammeroftor,

Probé la solución por iptables :) y está buena !!!
Lo conveniente del parche es que es independiente del navegador que uses. Lo probé con el ópera, firefox, chrome y funca :mrgreen:

Para no tener que abrir una ventana de comandos y cargar las reglas cada vez que se arranca el sistema, armé un script para que cargue las reglas, las guarde en el /etc/iptables.rules y las recargue automáticamente desde /etc/network/if-pre-up.d/iptablesload

Para instalarlas, inicien el sistema sin que las reglas estén cargadas.
Descompriman el archivo que les adjunto en una carpeta, como por ejemplo *~/Downloads/Solución\ por\ IPTables*

Abran una ventana de terminal y cambien a esa ubicación, por ejemplo:
*$ cd ~/Downloads/Solución\ por\ IPTables*

Luego sólo hay que hacer:
*$ sudo ./Config-IPTables.sh*

Listo.

Si quieren probar la navegación sin las reglas, pueden ejecutar*** iptables --flush*** o si quieren remover la carga automática borren el archivo[I][B] /etc/network/if-pre-up.d/iptablesload
[/B][/I]
Saludos!
Espero que les sirva.):P

---

### Post by edboy on 2010-10-15
> **Sarumannet said:**
> Probé la solución por iptables :) y está buena !!!
Lo conveniente del parche es que es independiente del navegador que uses. Lo probé con el ópera, firefox, chrome y funca :mrgreen:

Para no tener que abrir una ventana de comandos y cargar las reglas cada vez que se arranca el sistema, armé un script para que cargue las reglas, las guarde en el /etc/iptables.rules y las recargue automáticamente desde /etc/network/if-pre-up.d/iptablesload

Para instalarlas, inicien el sistema sin que las reglas estén cargadas.
Descompriman el archivo que les adjunto en una carpeta, como por ejemplo *~/Downloads/Solución\ por\ IPTables*

Abran una ventana de terminal y cambien a esa ubicación, por ejemplo:
*$ cd ~/Downloads/Solución\ por\ IPTables*

Luego sólo hay que hacer:
*$ sudo ./Config-IPTables.sh*

Listo.

Si quieren probar la navegación sin las reglas, pueden ejecutar*** iptables --flush*** o si quieren remover la carga automática borren el archivo[I][B] /etc/network/if-pre-up.d/iptablesload
[/B][/I]
Saludos!
Espero que les sirva.):P

Creo que esa solución es algo más segura que el Thor por lo que estuve viendo (tomen en cuenta que acabo de aprender iptables hace 2 minutos xD), las reglas que se agregan al fw del Linux lo que hacén es rebotar cada paquete TCP con el flag RST que se hayan devuelto en el rango menor a 1 segundo.

La desventaja de esto es que si, hubo un RST real (en el rango de tiempo < a 1 segundo) y no la farsa de Speedy la conexión podría quedar abierta más tiempo de lo común, aunque luego se cerraría por el timeout del TCP.

Es una buena herramienta y algo más rápida que el martillo de Thor, cuyo funcionamiento prueba la conexión luego de 0.33 seg, luego dentro de 0.66 seg, luego de 0.99 segundos y por último 1.98 segúndos, esto se hace 20 veces, según nota del autor en el script de Python.

De igual manera no se olviden de chequear si la cnx sin las reglas realmente está funcionando periódicamente ya que esta solución debe ser provisoria.

Para los interesados en seguridad informática y, agregando mi bocado al comentario de Guillermo sobre el posible sabotaje, les paso un link muy interesante (Está en Ingles) [http://www.kb.cert.org/vuls/id/435052](http://www.kb.cert.org/vuls/id/435052) tal vez los pobres de Speedy esten pasando por esto xD.

Saludos.

---

### Post by mama21mama on 2010-10-15
> **edboy said:**
> De igual manera no se olviden de chequear si la cnx sin las reglas realmente está funcionando periódicamente ya que esta solución debe ser provisoria.




Si me olvido quitar esas reglas navegare de un modo inferior a lo normal, cuando el servicio esta normalizado?;
Cualquier cosa avisen si se normalizo :D

Saludos

---

### Post by coskibukowski on 2010-10-15
Yo venía usando el hammerofthor y andaba bien, pero solo en el navegador... los demás programas q se conectan a inet y q no pueden usar proxys SOCKS seguían para el tujes...

Con las reglas de iptables ahora tuve uno q otro pantallazo de "no se puede conectar" pero bueh, anda mucho mejor q sin nada (aunque thor parecía más efectivo, pero iptables tiene la ventaja de ser universal).

Supuestamente cuando arreglen el proxy las reglas de iptables no van a j***r, porque solo actúan cuando viene un paquete RST? no??

Saludos

---

### Post by Sarumannet on 2010-10-16
> **coskibukowski said:**
> Yo venía usando el hammerofthor y andaba bien, pero solo en el navegador... los demás programas q se conectan a inet y q no pueden usar proxys SOCKS seguían para el tujes...

Con las reglas de iptables ahora tuve uno q otro pantallazo de "no se puede conectar" pero bueh, anda mucho mejor q sin nada (aunque thor parecía más efectivo, pero iptables tiene la ventaja de ser universal).

Supuestamente cuando arreglen el proxy las reglas de iptables no van a j***r, porque solo actúan cuando viene un paquete RST? no??

Saludos

Obvio, cuando los paquetes no vuelvan con un RST innecesario no van a actuar... jeje a J***r

Salu2

---

### Post by marcelo_bur on 2010-10-16
> **Sarumannet said:**
> Probé la solución por iptables :) y está buena !!!
Lo conveniente del parche es que es independiente del navegador que uses. Lo probé con el ópera, firefox, chrome y funca :mrgreen:

Para no tener que abrir una ventana de comandos y cargar las reglas cada vez que se arranca el sistema, armé un script para que cargue las reglas, las guarde en el /etc/iptables.rules y las recargue automáticamente desde /etc/network/if-pre-up.d/iptablesload

Para instalarlas, inicien el sistema sin que las reglas estén cargadas.
Descompriman el archivo que les adjunto en una carpeta, como por ejemplo *~/Downloads/Solución\ por\ IPTables*

Abran una ventana de terminal y cambien a esa ubicación, por ejemplo:
*$ cd ~/Downloads/Solución\ por\ IPTables*

Luego sólo hay que hacer:
*$ sudo ./Config-IPTables.sh*

Listo.

Si quieren probar la navegación sin las reglas, pueden ejecutar*** iptables --flush*** o si quieren remover la carga automática borren el archivo[I][B] /etc/network/if-pre-up.d/iptablesload
[/B][/I]
Saludos!
Espero que les sirva.):P


Hola. Por lo visto estoy entre los más ignorantes de este foro en cuanto a manejar scripts y esas cosas. Seguí las instrucciones pero no pasó nada, cuando entro a la carpeta y escribo sudo ./Config-IPTables.sh luego doy enten, supongo que es lo que corresponde, y me devuelve "orden no encontrada"... :confused:
Saludos

---

### Post by atari130xe on 2010-10-16
Telefónica ya tiene mucha experiencia con esto del "Proxy Caché" miren esta info de españa:

[http://www.adslayuda.com/n2525-Telefonica-NO-va-a-poner-el-proxy-cache.html]("http://www.adslayuda.com/n2525-Telefonica-NO-va-a-poner-el-proxy-cache.html")

---

### Post by marcelo_bur on 2010-10-16
> **marcelo_bur said:**
> Hola. Por lo visto estoy entre los más ignorantes de este foro en cuanto a manejar scripts y esas cosas. Seguí las instrucciones pero no pasó nada, cuando entro a la carpeta y escribo sudo ./Config-IPTables.sh luego doy enten, supongo que es lo que corresponde, y me devuelve "orden no encontrada"... :confused:
Saludos

Bueno, todo sirve para algo, la solución por iptables no la he podido instalar, pero al menos aprendí que el firewall instalado en el kernel viene por defecto desactivado y aprendí como activarlo y también baje un programa para configurarlo. De todo se aprende algo...
Saludos

---

### Post by marcelo_bur on 2010-10-16
> **atari130xe said:**
> Telefónica ya tiene mucha experiencia con esto del "Proxy Caché" miren esta info de españa:

[http://www.adslayuda.com/n2525-Telefonica-NO-va-a-poner-el-proxy-cache.html]("http://www.adslayuda.com/n2525-Telefonica-NO-va-a-poner-el-proxy-cache.html")

HOla. Entré a leer en ese sitio y encontre links para hacer pruebas que permiten ver si estás navegando a traves de un proxy, sin embargo en ambas pruebas me dio negativo....
Saludos

---

### Post by atari130xe on 2010-10-16
> **marcelo_bur said:**
> HOla. Entré a leer en ese sitio y encontre links para hacer pruebas que permiten ver si estás navegando a traves de un proxy, sin embargo en ambas pruebas me dio negativo....
Saludos

Hola como vá? si los de la sociación de Internautas de España, yo vengo haciendo sus pruebas desde hace un par de semanas y tmb me dice que no paso por ningún proxy (cosa que dudo), pero algo que si te avisa si estás tras uno es intentar bajar algo de taringa por ejemplo: archivos de cualquier tipo alojados en Rapidshare, si estás detras de un proxy, te va a avisar que ya estás descargando desde tu dirección IP y que has excedido el límite de descargas, sinó, lo baja de una, al menos eso aprendí con todo este tema, cosa que antes no comprendía.

PD: aclaro bajarse UN ÚNICO ARCHIVO a la vez, porque si se baja más de uno a la vez y no estás pagando por el servicio por razones ovbias vas a estar imposibilitado de bajar en paralelo desde la misma IP.

---

### Post by marcelo_bur on 2010-10-16
> **atari130xe said:**
> Hola como vá? si los de la sociación de Internautas de España, yo vengo haciendo sus pruebas desde hace un par de semanas y tmb me dice que no paso por ningún proxy, pero algo que si te avisa si estás tras uno es intentar bajar algo de taringa por ejemplo: archivos de cualquier tipo alojados en Rapidshare, si estás detras de un proxy, te va a avisar que tu dirección IP ya está descargando ese archivo y que ha excedido el límite de descargas, sinó lo baja de una, al menos eso aprendí con todo este tema, cosa que antes no comprendía.

PD: aclaro bajarse UN ÚNICO ARCHIVO a la vez, porque si se baja más de uno a la vez y no estás pagando por el servicio por razones ovbias vas a estar imposibilitado de bajar en paralelo desde la misma IP.

Hola. Cada vez entiendo menos que pasa entonces, porque uno de mis pocos vicios en la pc es bajar peliculas pero sin usar programas del tipo Ares o Emule, o sus equivalentes para Linux, por lo cual uso continuamente servidores como rapidshare, upload, netload, fileserver, megaupload, etc. y nunca tengo ese problema.
Saludos

---

### Post by atari130xe on 2010-10-16
> **marcelo_bur said:**
> Hola. Cada vez entiendo menos que pasa entonces, porque uno de mis pocos vicios en la pc es bajar peliculas pero sin usar programas del tipo Ares o Emule, o sus equivalentes para Linux, por lo cual uso continuamente servidores como rapidshare, upload, netload, fileserver, megaupload, etc. y nunca tengo ese problema.
Saludos

Mirá esto que acabo de comentar lo leí en una de las explicaciónes sobre Proxy caché, que entre cositas ocasiana eso, de manera aleatoria. 

Acá hay una opción del 2006 para "saltear" el proxy de telefónica en Linux (aún no lo probé)

[http://www.linuca.org/body.phtml?nIdNoticia=208]("http://www.linuca.org/body.phtml?nIdNoticia=208")

---

### Post by marcelo_bur on 2010-10-16
Hola Atari. Bajé el programita Privoxy del sitio oficial pero aún no lo instalé, si vos lo instalas y te va bien avisa y pruebo, porque al final estoy perdiendo más tiempo con todas estas pruebas que dandole a la F5 y, ademas, el Hammerofthor me funciona bastante bien cuando la cosa de pone muy pesada.
Saludos

PD.: Creo que este es un foro más que nada técnico y que en cualquier momento nos van a llamar la atención por usarlo como medio para conversar. Puse un link a mi Yahoo Messenger en el perfil y tambien disponemos de mi foro llegado ese caso.

---

### Post by biale on 2010-10-16
Ese tipo de programas funcionaban bastante bien en el 2006, pero ahora los programas para proxy son mas sofisticados y etc.

De todas maneras la idea de este tipo de progranas es distinta: forzar al proxy a obtener siempre la pagina web desde Intenet y no leerla desde su cache (si ya la tuviera).

Y la argumentación era que el proxy tardaba mas tiempo en leer desde cache que en obtener la página directamente.

---

### Post by guillermolisi on 2010-10-16
> **marcelo_bur said:**
> 
PD.: Creo que este es un foro más que nada técnico y que en cualquier momento nos van a llamar la atención por usarlo como medio para conversar. Puse un link a mi Yahoo Messenger en el perfil y tambien disponemos de mi foro llegado ese caso.
Este es el subforo del LoCo Team Argentino, dentro de Ubuntu Forums, y mientras se trate de resolver problemas, intercambiar opiniones, contar experiencias, ayudarnos a que Ubuntu sea cada vez mejor, etc., todo dentro de la pauta que enmarca el CoC, esta todo bien.

Este caso particular y dado que el problema es exogeno a Ubuntu, lo movi a Comunidad casualmente para que se pueda desarrollar tranquilamente.

Como pauta general: Si se puede patear, el mensaje va en Hardware. Si solo se lo puede insultar, entonces va en Software. Si esta relacionado con la comunidad Ubuntu, da para opinar, etc., y si se lo hace con una birra mucho mejor aun, entonces va en Comunidad. :D

---

### Post by atari130xe on 2010-10-16
> **guillermolisi said:**
> Este es el subforo del LoCo Team Argentino, dentro de Ubuntu Forums, y mientras se trate de resolver problemas, intercambiar opiniones, contar experiencias, ayudarnos a que Ubuntu sea cada vez mejor, etc., todo dentro de la pauta que enmarca el CoC, esta todo bien.

Este caso particular y dado que el problema es exogeno a Ubuntu, lo movi a Comunidad casualmente para que se pueda desarrollar tranquilamente.

Como pauta general: Si se puede patear, el mensaje va en Hardware. Si solo se lo puede insultar, entonces va en Software. Si esta relacionado con la comunidad Ubuntu, da para opinar, etc., y si se lo hace con una birra mucho mejor aun, entonces va en Comunidad. :D

Es verdad Guillermo, es más vos de 2 threads (posts) hiciste uno con el mio y este mismo porque tenemos el mismo problema, con el mío utilizaste el título y con el otro el primer post :P, yo estoy muy a gusto con este foro, siempre que pudieron me ayudaron y cuando pude aportar y ayudar tmb lo hice, en fín, la escencia de este foro :)

---

### Post by marcelo_bur on 2010-10-16
Hola. Espero que nadie haya pensado que quiero llevarme gente a mi foro. Nada más lejos de la realidad, yo uso mi foro como si fuese un blog, y si no cambio el formato es por simple comodidad. 
Solo que se que en este foro hay que ser muy específico respecto de los temas que se tratan y, a veces y como en este caso, los motivos que afectan el servicio que brinda Speedy, especialmente a usuarios de Linux, tienen ramificaciones de todo tipo que pueden llevar a alguien como yo a salirse un poco de lo específico, y eso es lo que no quiero hacer aqui, por simple respeto a las reglas de estos foros.
Saludos

---

### Post by guillermolisi on 2010-10-17
> **marcelo_bur said:**
> Hola. Espero que nadie haya pensado que quiero llevarme gente a mi foro.....
Saludos
Ubuntu Forums no es propietario de quienes lo usan, la gente lo adopta y no hay contrato de exclusividad :)

Es un foro libre que tiene la entidad que la gente le da, le genera y no se piden explicaciones (salvo cuando alguien se sale del marco del CoC o se da una situacion confusa).

Si tenes dudas respecto de las reglas, en la seccion general del subforo del LoCo Argentino, como sticky threads, esta todo escrito, en Ingles y en Español.

Relax and enjoy !

---

### Post by biale on 2010-10-17
> y dado que el problema es exogeno a Ubuntu, lo movi a Comunidad

Justamente lo mas valioso del thread es haber podido determinar que el problema es exógeno a Ubuntu y a linux en general.

Además, por ser un foro internacional las opiniones (y expresiones) vertidas son accesibles para cualquiera desde la web, e incluso argumentables según los casos.

@marcelo_bur: yo al menos nunca pensé que quisieras llevarte gente.

---

### Post by firewall27 on 2010-10-17
HAY QUE INTENTAR HACER ALGO

Por mas que parezca complicado yo creo que hay que intentar hacer algo.
Todos los logros de la humanidad comenzaron siempre desde un sueño imposible de lograr, como el sueño de volar.

MI IDEA

No soy especialista en redes pero supongo que el problema pasa por los protocolos TCP/IP de linux.
Si en WinShit anda bien, supongo que tendriamos que tratar de semejarlos un poco, o si se puede, mezclarlos.
Puede ser que este diciendo una estupidez tremenda, pero de todas las ideas que digamos alguna va a servir.
Ya es imposible navegar en este sistema, con speedy y no concidero tener que cambiar de proveedor porque en win mal o bien anda....

---

### Post by atari130xe on 2010-10-17
Con respecto al tema puntual "Proxy Caché" y la dudosa privacidad que tenemos todos los usuarios ya sea que naveguemos por Ubuntuforums, CartoonNetwork o algún sitio "fonográfico", es realmente legal que se apliquen estos métodos por parte de un ISP? lo pregunto porque en un foro encontré que muy legal no suena... :

[http://blog.salinas.com.ar/2010/10/07/telefonica-y-el-proxy-de-los-misterios/]("http://blog.salinas.com.ar/2010/10/07/telefonica-y-el-proxy-de-los-misterios/")

precisamente en esta parte:

> #  Javier Dijo:
el 9 de octubre de 2010 a las 10:09

Das Werke:
Yo no he podido hacer todavía la prueba de ese sitio. Creo que en algún momento habría que iniciarle juicio al java y declarar su uso delito de lesa humanidad.
Pero según las leyes argentinas y mi forma de interpretarlas, lo de Telefónica es un delito.
En el inciso 16 del art. 173 del Código Penal se incorporó, por la ley 26388, el siguiente texto:
&#8220;El que defraudare a otro mediante cualquier técnica de manipulación informática que altere el normal funcionamiento de un sistema informático o la transmisión de datos.&#8221;
Este inciso lo que hace es incluir como caso especial de defraudación la alteración de sistemas.
¿Que dice el art. 172, justo el anterior?
&#8220;Será reprimido con prisión de un mes a seis años, el que defraudare a otro con nombre supuesto, CALIDAD SIMULADA, falsos títulos, influencia mentida, abuso de confianza o aparentando bienes, crédito, comisión, empresa o negociación o valiéndose de cualquier otro ardid o engaño.&#8221;
¿Y como se define la defraudación?
Como la acción de &#8220;Privar a alguien, con abuso de su confianza o con infidelidad a las obligaciones propias, de lo que le toca de derecho.&#8221;

Es decir, uno contrata un servicio y tiene derecho a recibirlo bajo ciertos parámetros de calidad. Si estos parámetros no se cumplen o se simulan, con engaños, como es negar el uso de proxys aunque estén mas que evidenciado que los tienen, manipulando y alterando los datos transmitidos, como es el caso del cambio de headers, entonces estamos ante un delito bien tipificado.


Uds. que opinan?

---

### Post by Sarumannet on 2010-10-17
> **firewall27 said:**
> HAY QUE INTENTAR HACER ALGO

Por mas que parezca complicado yo creo que hay que intentar hacer algo.
Todos los logros de la humanidad comenzaron siempre desde un sueño imposible de lograr, como el sueño de volar.

MI IDEA

No soy especialista en redes pero supongo que el problema pasa por los protocolos TCP/IP de linux.
Si en WinShit anda bien, supongo que tendriamos que tratar de semejarlos un poco, o si se puede, mezclarlos.
Puede ser que este diciendo una estupidez tremenda, pero de todas las ideas que digamos alguna va a servir.
Ya es imposible navegar en este sistema, con speedy y no concidero tener que cambiar de proveedor porque en win mal o bien anda....

Hola Firewall, a lo largo de este hilo de conversación se aportaron varias alternativas. Particularmente yo probé varias y la que estoy usando actualmente sin problemas es la configuración por iptables.

```
sudo iptables -A OUTPUT -p tcp --dport 80 -m state --state NEW -m recent --set --name thor --rdest -j ACCEPT
sudo iptables -A INPUT -p tcp -m tcp --tcp-flag RST RST -m state --state ESTABLISHED -m recent --name thor --rcheck --rsource --seconds 1 -j DROP
```

Para probarla sólo hay que abrir una ventana de terminal, copiar y pegar cada una de las líneas del código. Va a funcionar hasta que reinicies el sistema. En un post anterior dejé un adjunto para automatizar la carga de las reglas por iptables. Si los comandos así como están no te funcionan (te tiran algún error), puede ser que te falte algún requisito o dependencia.

El problema también pasa con WinSlow, y se hace más evidente con navegadores como el Chrome, y pasa más desapercibido con el Internet Explorer. 

Saludos!

---

### Post by z37a on 2010-10-17
> **emiliano_raso said:**
> Bueno gente. Empezemos a organizarnos. Comencemos por reunir toda la información referente a los reclamos. Anoten los siguientes datos de los reclamos que ya hicieron y de los que vayan a hacer:

- Numero de reclamo, fecha y hora.
- Tiempo de espera que nos dieron (clasico 72hs)
- Tiempo que tardó el tecnico en venir en realidad
- Cuanto hace que tenemos el problema.
- etc.

Tambien hay que averiguar:
- Cual es el ente regulador encargado de Speedy
- Que datos son necesarios para levantar un reclamo ante el ente regulador

Otra alternativa podria ser elevar una carta documento en nombre de la comunidad Linuxera al ente regulador.

Te comento que el ente regulador es la CNC, la misma que salto el problema con Fibertel. Este ente regula todo lo referido a comunicaciones, teléfono, señales de radios, lineas de datos, correo, etc...

En una época cuando llamabas y amenazabas con denuncia a la CNC te respondían enseguida, ahora con Fibertel se dieron cuenta que si no les prestan atención no pasa nada y no les interesan mas las denuncias!

Si el ISP fuera una PyME creanme que enseguida tiene el problema solucionado(la multa es muy grande, pero para telefónica es un vuelto).

---

### Post by pol666 on 2010-10-18
nadie pudo solucionar esto? me cambio a telecentro nomás?

---

### Post by mama21mama on 2010-10-18
> **pol666 said:**
> nadie pudo solucionar esto? me cambio a telecentro nomás?

fijate antes telecentro de donde chupa internet. por las dudas xD

Yo no estoy mirando si se normalizo, me da fiaca quitar las reglas de iptables, pero el que las saque, y pruebe sin regla que avise. si funca o no.

Saludos

---

### Post by marcelo_bur on 2010-10-18
Hola. Después de varios intentos conseguí instalar lo de las iptables con el el scrip que dejó Surumannet, así que supongo que ahora mi pc funciona de acuerdo a esas normas. Pero de todas formas sigue el problema, pero en forma menos marcada. En cuanto a cambiarse a Telecentro, que puede ser una de mis opciones también, si buscas en la red vas a encontrar montones de comentarios hablando pestes del servicio, y lo mismo si buscas datos de cualquier otro ISP (en una ocasión contraté para llevar en la note el servicio de Claro y eso si que fue un desastre...). Por lo que considero que habiendo tenido un servicio aceptable por parte de Speedy, al menos en mi caso, por casi diez años, prefiero esperar todavía un tiempo a ver que pasa antes de arriesgarme a salir de Guatemala para caer en Guatepeor.
Saludos

---

### Post by atari130xe on 2010-10-18
Yo probé con el script y me funciona bién solo en horas de la noche onda 1 de la mañana o muy temprano por la mañana, luego sigue igual o peor que siempre, (las páginas no cargan)...

---

### Post by marcelo_bur on 2010-10-18
> **atari130xe said:**
> Yo probé con el script y me funciona bién solo en horas de la noche onda 1 de la mañana o muy temprano por la mañana, luego sigue igual o peor que siempre, (las páginas no cargan)...

En mi caso durante los lapsos que mencionas a mi me funcionaba muy bien sin ningun script, el problema se presenta desde el mediodia hasta algo pasada la medianoche. Con el script, si es que lo carga bien, hay una pequeña mejoría pero no funciona "siempre" bien, hay momentos es que casi no se nota mejoría alguna. Lo que si me saca de apuros cuando anda muy mal el servicio es el hammerofthor, es lento, pero rara vez una página no abre bien.
Saludos

---

### Post by josecuervo86 on 2010-10-18
Estoy probando el script de iptables y parece que anduviera bien =)

---

### Post by teotihuacano on 2010-10-18
Recién me dijeron que "el equipo ténico ya detectó el problema en el proxy" y "esperan resolverlo en esta semana".
Crucemos los dedos. Si no me preparo para odiar a Telecentro.

---

### Post by josecuervo86 on 2010-10-18
> **josecuervo86 said:**
> Estoy probando el script de iptables y parece que anduviera bien =)

A ver, me corrijo, anda **bastante** bien, pero me sigue tirando errores aleatorios, en menor medida que si no tuviera puesta esas reglas, pero al menos es una mejora bastante sustancial

---

### Post by edboy on 2010-10-18
> **teotihuacano said:**
> Recién me dijeron que "el equipo ténico ya detectó el problema en el proxy" y "esperan resolverlo en esta semana".
Crucemos los dedos. Si no me preparo para odiar a Telecentro.

El tema no es que es que encuentren el problema sino la solución que le den, es un problema que afecta a ciertos tipos de SO, van a tener que realizar un laburo de prueba y error bastante grande y les va a llevar mucho tiempo. Además hay que ver que se les ocurre para solucionarlo...

Por lo de Telecentro me hablaron muy mal del servicio, sobre todo de la telefonía IP.

Por mi parte con el script de iptables la voy remando.

Saludos.

---

### Post by hectorivand on 2010-10-19
> **edboy said:**
> El tema no es que es que encuentren el problema sino la solución que le den, es un problema que afecta a ciertos tipos de SO, van a tener que realizar un laburo de prueba y error bastante grande y les va a llevar mucho tiempo. Además hay que ver que se les ocurre para solucionarlo...

Por lo de Telecentro me hablaron muy mal del servicio, sobre todo de la telefonía IP.

Por mi parte con el script de iptables la voy remando.

Saludos.

[OT] ehhh como vas a decir que la telefonía IP anda mal, hay un asterisk como backend de todo eso :D [/OT]

---

### Post by chulelinux on 2010-10-19
Hoy a la mañana pensaba que ya estaba solucionado pero noo... el "esperando, resolviendo, conectando, transfiriendo, resolviendo" para que al fin me aparezca un "No se puede conectar" siguió su cotidaneidad. 
Llamé, hice el reclamo, le dije que no me haga perder tiempo haciendo pruebas que ya sé no funcionan y nada... en 48 o 72 "tendría" que estar solucionado. ja ja ¿Cómo tendría? le pregunté. En fin. Yo tenía un mega y como para conformarme me pasaron a tres para "ver si así se solucionaba". 

Escribo principalmente para que aquellos que tengan un Mega como yo pidan los 3 que si me lo dieron a mí sin más es porque saben del problema y a modo de salvavidas te habilitan un poco más de banda. 

Saludos

---

### Post by guillermolisi on 2010-10-19
> **chulelinux said:**
> .... En fin. Yo tenía un mega y como para conformarme me pasaron a tres para "ver si así se solucionaba". 

Escribo principalmente para que aquellos que tengan un Mega como yo pidan los 3 que si me lo dieron a mí sin más es porque saben del problema y a modo de salvavidas te habilitan un poco más de banda. 

Saludos

Yo esperaria recibir la factura del proximo periodo antes de ponerme contento.

Lo de "te damos 3Mb" es solo una postura de marketing ya que solo lo logras si estas solo en el nodo y a una razonable distancia del mismo como para no tener perdidas en el enlace fisico (siempre hablando de ADSL).

No es para "pincharte el globo" pero nadie regala nada en esta vida.

---

### Post by hectorivand on 2010-10-19
> **guillermolisi said:**
> Yo esperaria recibir la factura del proximo periodo antes de ponerme contento.

Lo de "te damos 3Mb" es solo una postura de marketing ya que solo lo logras si estas solo en el nodo y a una razonable distancia del mismo como para no tener perdidas en el enlace fisico (siempre hablando de ADSL).

No es para "pincharte el globo" pero nadie regala nada en esta vida.

No solamente hay que tener presente el tema de la distancia, también el estado de los pares, cuando tenia Speedy tuve la "brillante" idea de subir a 3MB a partir de ahí, el módem dejaba de sincronizar con el DSLAM, según ellos fallas del Módem.

Renegando, renegando, al final, accedieron al pedido que les hice de verificar los pares de la cuadra (instalados hace quince años, cero mantenimiento) por supuesto que estaban mal, nunca los cambiaron, me di de baja :S

---

### Post by atari130xe on 2010-10-19
Nosotros "importamos" de todo lean este pedido de los usuarios de ADSL Telefónica en España, les suena conocido? (por cierto el servicio de internet en España ahora se llama Movistar)

[http://www.petitiononline.com/proxycac/petition.html]("http://www.petitiononline.com/proxycac/petition.html")

---

### Post by chulelinux on 2010-10-19
> **guillermolisi said:**
> Yo esperaria recibir la factura del proximo periodo antes de ponerme contento.

Lo de "te damos 3Mb" es solo una postura de marketing ya que solo lo logras si estas solo en el nodo y a una razonable distancia del mismo como para no tener perdidas en el enlace fisico (siempre hablando de ADSL).

No es para "pincharte el globo" pero nadie regala nada en esta vida.

Je je... yo pensé lo mismo cuando me lo dijo... Pero me contestó que solo era para que funcioné mejor hasta que se arreglara el problema... Igual da igual, y el reclamo fue más para molestar o sumarles uno más. Por el momento sigue siendo muy molesto el problema con la conexión...

---

### Post by hectorivand on 2010-10-20
> **atari130xe said:**
> Nosotros "importamos" de todo lean este pedido de los usuarios de ADSL Telefónica en España, les suena conocido? (por cierto el servicio de internet en España ahora se llama Movistar)

[http://www.petitiononline.com/proxycac/petition.html](http://www.petitiononline.com/proxycac/petition.html)

[OT] en breve acá también se va a llamar Movistar, bajo esa marca unifican todo, Telefonía móvil, fija, internet. lo único que queda diferente son algunos servicios como twis. [/OT]

Saludos
Nacho

---

### Post by atari130xe on 2010-10-20
> **hectorivand said:**
> [OT] en breve acá también se va a llamar Movistar, bajo esa marca unifican todo, Telefonía móvil, fija, internet. lo único que queda diferente son algunos servicios como twis. [/OT]

Saludos
Nacho

Si me imagino que será asi, como lo que ocurrió con el logo de Movistar que se creó allá en España, es lógico que también la misma empresa utilice los mismos metodos y sistemas acá, en España no dejo de ver quejas sobre Telefónica.

---

### Post by turok on 2010-10-25
Hola, me uno medio tarde al thread. Yo tb estoy teniendo problemas como todos. Alguien ha hecho la denuncia a defensa del consumidor ? Tienen un formulario web para hacer denuncias, que les parece si floodeamos todos con denuncias a ver que pasa ? estaría bueno tb mandar la noticia a varios medios como leí por ahí. Yo para serles sincero ni he llamado al servicio técnico, y hace meses que venimos con esto, pero ya me tienen podrido. Hagamos algo, quejemosnos al menos, no perdemos nada. También postié esto en el foro del mac users group de argentina. 
[http://www.macusergroup.com.ar/foro/showthread.php?t=28834&page=34](http://www.macusergroup.com.ar/foro/showthread.php?t=28834&page=34)
Por si a alguien le interesa. 

[http://www.consumidor.gov.ar/entrar/](http://www.consumidor.gov.ar/entrar/)

Ese es el link de defensa al consumidor, hay que hacerse una cuenta para poder poner la denuncia, pero es una boludes, es un wordpress choto, en 2 segs (y unos cuantos refresh de por medio) se hace.
Saludos !

---

### Post by turok on 2010-10-25
Ahí mandé un mail a un diario online de mendoza... no es mucho, pero por algo se empieza

---

### Post by dzertik on 2010-10-25
Si vamos a hacer eso deberíamos, los que no tengamos, reportar los casos para que generen un número, si a las 72 hs. no se resuelven reportarlos a defensa del consumidor.

Aquellos que tengan ya su número de caso guardenlos hasta el gran día... xD.

Abrazo!

[http://twitpic.com/2zklet](http://twitpic.com/2zklet) (Una imágen vale más que mil palabras)

---

### Post by marcelo_bur on 2010-10-25
Hola. Creí que el asunto estaba arreglado, por la falta de nuevos comentarios, y que el único gil que queda soy yo dandole a la F5. Sin embargo veo que no es  asi y, por añadidura, hoy me encontré con que también tengo problams usando Window$, cosa que antes no me ocurría.
Pregunta... ¿Cuál es tu sistema operativo dzertik?
Saludos

---

### Post by josecuervo86 on 2010-10-25
Ya hice el reclamo ante Defensa al consumidor quedaron en responderme... veremos que pasa. Yo sigo con problemas, pareciera que un poco menos, pero seguir siguen los problemas

---

### Post by hard_rock_heavy on 2010-10-25
Hola que tal! hace mas o menos dos semanas que me están ocurriendo problemas al navegar en ubuntu , es verdaderamente insoportable estar apretando F5 todo el tiempo y además se cancelan las descargas directas y tengo que apretar varias veces para que se actualicen o instalen paquetes o programas.

Saludos desde Mendoza
Speedy apesta

mañana los voy a llamar a ver que me dicen

---

### Post by atari130xe on 2010-10-25
En mi caso hoy volví a reclamar (por enésima vez) e inclusive hice la descarga en el canal Twitter de telefónica y me respondieron que están trabajando en el problema. En estos momentos tengo rachas de funcionamiento aceptable y otras de funcionamiento "F5" en fín... a esperar...

---

### Post by emiliano_raso on 2010-10-25
Chicos. Ando con mucho laburo y estudio. Me RE colgué con el tema.
Mil disculpas.
Alguien me podría hacer un mini-resumen de como viene la mano?

Saludos y gracias!

---

### Post by dzertik on 2010-10-26
> **marcelo_bur said:**
> Hola. Creí que el asunto estaba arreglado, por la falta de nuevos comentarios, y que el único gil que queda soy yo dandole a la F5. Sin embargo veo que no es  asi y, por añadidura, hoy me encontré con que también tengo problams usando Window$, cosa que antes no me ocurría.
Pregunta... ¿Cuál es tu sistema operativo dzertik?
Saludos

Uso Ubuntu 10.10, sin embargo tengo un dual boot con XP y ahí me anda bien, de hecho en la máquina virtual que tengo con XP anda bien también.

Un saludo!

---

### Post by marcelo_bur on 2010-10-26
> **emiliano_raso said:**
> Chicos. Ando con mucho laburo y estudio. Me RE colgué con el tema.
Mil disculpas.
Alguien me podría hacer un mini-resumen de como viene la mano?

Saludos y gracias!

Hola. Creo que un resumen válido de este tema podría ser:

Todos los que aquí posteamos hemos hecho, en mayor o menor medida, reclamos a la empresa.

A todos nos han prometido soluciones o nos han dicho que se está trabajando en el problema.

Y la pura verdad es que todo sigue **"como cuando llegamos de España"**, frase anticuada que espero que todos conozcan y que me pareció muy apropiada.

Algunos foristas han aportado soluciones transitorias como el script "hammerofthor" y las "reglas por iptables", que han contribuido a facilitar un poco la navegación, o sea que los que aqui participan nos han brindado muchas más soluciones, provisorias insisto, que Speedy. Otros foristas nos han dejado links donde dejar nuestros reclamos via internet, personalmente he utilizado el del sitio gubernamental de defensa del consumidor.

Saludos

---

### Post by atari130xe on 2010-10-26
Son las 10:56 de la mañana del Martes 26 de Octubre de 2010, acabo de atender un llamado y eran de Telefónica, NO se están preocupando por el tema y los pocos que pueden estarlo NO dán en el clavo con el problema, estoy 100 % seguro que los que "tocaron" el maldito Proxy caché no saben como reconfigurarlo y volverlo a su estado anterior (en mi caso Setiembre 15), la señorita que me acaba de llamar me hizo todas las preguntas como si fuera la primera vez que hablamos y se "entera" del problema: "Digame por favor ¿Cuál es exactamente el problema que tiene? ¿No puede navegar? Bueno estamos viendo cuál es problema" NO saben como solucionarlo creo que no tienen idea, en España haciendo exactamente lo mismo tuvieron que poner como OPCIÓN (al que lo solicita se lo hacen) de sacarle el proxy cache por los miles de problemas y quejas en masa que recibieron desde el 2003 año en que empezaron a implementarlo. Hay que armarse se MUUUCHA paciencia o simplemente hacer un reclamo en masa, pero juntar realmente muchos usuarios de todos los OS (Linux, Mac & Win -también afecta a Win en menor medida-). Para que implementen lo mismo en Argentina, si nos causa tantos inconvenientes que nos de&#324; la opción como hacen en España (Matriz de la empresa) de deshabilitarnos el proxy caché porque de la manera que ellos lo implementan NO sirve, sin contar que en un País como el nuestro la privacidad es tan "segura" como un papel de arroz...

---

### Post by marcelo_bur on 2010-10-26
Si, supongo que lo único que resta por hacer es armarse de paciencia y seguir reclamando. Tal vez consigamos algo. Por mi parte creo que, salvo que surja alguna novedad importante, ya no hay mucho que escribir aqui. Yo desde hace unos minutos he comenzado a mostrar capturas de pantalla con el eterno error en el tema abierto en mi foro, no se para que pueda servir, mi intención es poder eventualmente hacer que cuando hago un reclamo sirva para mostrarles el error. Subire capturas de pantalla cada vez que pueda durante el día. Si a alguien le parece útil y quiere agregar las suyas, pues, bienvenido.
Saludos

---

### Post by chulelinux on 2010-10-26
Consulto a quienes más coordinan el foro ¿No es posible realizar un reclamo colectivo desde el foro e invitando a otros foros sobre sistemas con el mismo problema? Aunque sea un reclamo por los diferentes espacios virtuales posibles y públicos firmado con los id de los reclamos que realizamos los usuarios a la empresa. Habría que dar un tiempo para consensuar una nota que creo más allá del reclamo se debería fundamentar en el derecho a usar soft libre y que en ningún momento se planteo incompatibilidades del servicio con estos SO.
Saludos

En mi caso a algunos horarios se mejoró el problema pero a otros es insoportable. Yo hasta hace dos meses no conocía el F5, aunque el problema es de un poquito antes pero yo mixturaba un poco más los SO y no me daba tanto cuenta o no le daba importancia porque de última reiniciaba. Justamente me di cuenta que era por el problema de conexión que fui usando cada vez menos ubuntu. Ahora decidí utilizarlo más intensivamente y tratar de lograr dejar la dependencia a güi pero esto de la conexión es un obstáculo importante. Le daré un poco de changüí y sino a buscar las ofertas de verano pero es molesto cambiar de proveedor.

F5: recarga < Saludos

---

### Post by hectorivand on 2010-10-26
Gente por favor, no se queden con el "seguir reclamando hasta que lo solucionen" inicien una demanda colectiva por incumplimiento o algo parecido. Hay legislación al respecto, aprovechen.

Saludos
Nacho

---

### Post by guillermolisi on 2010-10-26
Hay algo que me llama la atencion en todo esto y es que habiendo gente a las que les funciona bien (si, leyeron bien) nunca expresaron nada en este tema.

Conozco una persona (confiable) que me ha dicho que usando Speedy en su casa, tanto con Win como con Ubuntu, no tiene ningun tipo de problemas. Es mas, dice que nunca tuvo mejor servicio que ahora.

Esta persona vive en uno de los barrios Lugano, CABA.

Puede ser que sea la unica "elegida" ?
Por que cuando hay muchas personas sufriendo este inconveniente a el le funciona perfecto ? Sera zonal la cosa ?

---

### Post by marcelo_bur on 2010-10-26
> **guillermolisi said:**
> Hay algo que me llama la atencion en todo esto y es que habiendo gente a las que les funciona bien (si, leyeron bien) nunca expresaron nada en este tema.

Conozco una persona (confiable) que me ha dicho que usando Speedy en su casa, tanto con Win como con Ubuntu, no tiene ningun tipo de problemas. Es mas, dice que nunca tuvo mejor servicio que ahora.

Esta persona vive en uno de los barrios Lugano, CABA.

Puede ser que sea la unica "elegida" ?
Por que cuando hay muchas personas sufriendo este inconveniente a el le funciona perfecto ? Sera zonal la cosa ?

Hola. Personalmente conozco a una persona que dice que ahora anda mejor que nunca, es el técnico que se ocupa de mi pc cuando está grave, pero el usa nada más que Win y, donde segun sus propias palabras, se nota la mejoría es en todo lo que tenga que ver con subida y bajada de archivos, lo cual también he expresado yo por ahi. A mi me dio una configuracion para cambiar en el router para que pruebe, pero no solucionó nada.
Si es zonal es bastante raro, creo que en este foro se ha quejado mucha gente de diversos lugares del pais y, ademas, recorriendo la web he encontrado cientos de quejas similares a las que aqui se han manifestado. Por otra parte veo bastante consistente con nuestras costumbres no escribir en un foro donde la gente se queja de algo para decir que a ellos si les funciona, supongo que no quieren volverse impopulares a sabiendas de que los servicios en general que nos brindan en este país son bastante deficientes y teléfonica no es la excepción.
Saludos

---

### Post by teotihuacano on 2010-10-26
Sres: tengo que decirles que puedo navegar con un 99% de efectividad. Este horario hasta el viernes pasado era imposible y había muchas cosas que no funcionaban. Pero ahora anda todo de una salvo una o dos página (sobre no menos de 200) en las que tuve que usar F5.
Vivo en Almagro, Lucyd Linx. Hice reclamos a granel, pero no sé si tiene que ver. Es más, no sé si va a durar.
Veo la luz...

---

### Post by biale on 2010-10-26
> Conozco una persona (confiable) que me ha dicho que usando Speedy en su casa, tanto con Win como con Ubuntu, no tiene ningun tipo de problemas. Es mas, dice que nunca tuvo mejor servicio que ahora.

Hasta donde yo experimenté, el problema es fuertemente dependiente de la carga que tenga la red. Ejemplo: (aquí) a las 07:00 hs anda bien. Y en ese horario, todo lo que sea download de archivos incluso anda mejor.

O sea que las zonas que tengan la infraestructura mas libre (o sea "zonas menos sobrevendidas") tendrían que funcionar mejor. Y para todas las zonas, en los horarios de baja también tendrían que funcionar mejor.

> ]no escribir en un foro donde la gente se queja de algo para decir que a ellos si les funciona

Sería interesante que si existe algún forista que conozca casos "Speedy & Linux/ Mac OK", los diga. Y si incluye la url de su test de Berkeley, todavía mejor.

En otro orden de cosas, dentro de unos días nos llegará la factura a pagar en noviembre: descuento por días caídos? Según Speedy, el descuento es automático cuando "se solucione el problema". Y entretanto?

---

### Post by marcelo_bur on 2010-10-26
> **teotihuacano said:**
> Sres: tengo que decirles que puedo navegar con un 99% de efectividad. Este horario hasta el viernes pasado era imposible y había muchas cosas que no funcionaban. Pero ahora anda todo de una salvo una o dos página (sobre no menos de 200) en las que tuve que usar F5.
Vivo en Almagro, Lucyd Linx. Hice reclamos a granel, pero no sé si tiene que ver. Es más, no sé si va a durar.
Veo la luz...

Quizás a fuerza de reclamos te hayan quitado el proxi, como comentó atari que hacen en España, aunque aqui no te lo digan expresamente.
Saludos y ojalá te dure.

PD: Este es mi segundo intento de enviar el mensaje
PD: Est es mi tercer intento de enviar el mensaje.

---

### Post by dzertik on 2010-10-26
Si llega a ser zonal fuimos xD, dudo muchísimo que se pongan a relevar toda la información de los pops que tengan falla y después sentarse y analizar a ver que onda...

Saludos.

---

### Post by atari130xe on 2010-10-27
Es muy raro que a algunos usuarios les funcione bién teniendo Linux o Mac, a mi en particular me funciona desastrosamente mal en algunos horarios es literalmente INUSABLE, es algo similar a navegar a 1 o 2kbps lo triste del caso es que hasta el 15/09 era una maravilla en cuanto a velocidad y agilidad tanto para descarga como navegación llegando a 490kbps teniendo un perfil de 3MB. 

Les dejo un link de Movistar España (Speedy versión Española) donde explica como funciona su proxy caché, etc.es un pdf que puede ser bajado para su lectura offline:

[http://www.movistar.es/on/es/micro/adsl/proxycache/guias.htm]("http://www.movistar.es/on/es/micro/adsl/proxycache/guias.htm")


y otros 2 links de sitios Españoles hablando del dichoso Proxy Caché y sus consecuencias para los usuarios:

[http://www.vsantivirus.com/lio-proxy-cache.htm]("http://www.vsantivirus.com/lio-proxy-cache.htm")

[http://www.vsantivirus.com/proxy-cache2.htm]("http://www.vsantivirus.com/proxy-cache2.htm")

---

### Post by marcelo_bur on 2010-10-27
Hola. En verdad no estoy muy seguro de la conveniencia de publicar este mensaje, por eso de no quemarlo como se dice, pero para mi asombro la conección funcionó a toda velocidad durante todo el día sin que una sola página se cargase mal, hoy pude olvidarme de los scripts y de la F5. Claro que aún me restaría quitar las reglas de iptables, pero antes igual funcionaba muy mal. Al menos una alegría el día de hoy, espero no haberlo quemado y que dure.
Saludos

---

### Post by Sergius14 on 2010-10-28
Con el script fue un paliativo importante, ya que se evitaba el F5 o las páginas mal cargadas (sin imágenes, etc.) muy bien. No obstante, aún así ciertas paginas no abrían (tardaban) y había que darle F5.

Sin script mi paciencia era nula: La baja era inminente.

Con script mi paciencia era tolerable: esperaba una solución definitiva mientras pensaba si pasarme a Fibertel 6 megas (doble) por casi misma plata.

Desde hace unos días, noté que no pasa nada con la conexión, que me funciona con normalidad.

Saqué el script ahora para ver sucede, pero a priori, está funcionando bien. Antes era algo rápidamente reproducible (10 clics, 2 o 3 fallas, a veces más). Ahora no tuve fallas directamente.

Esperemos que siga así.

Si veo que sigue el problema (sin script) les avisaré, y sino, también :P.

---

### Post by atari130xe on 2010-10-28
YO no toco nada más porque simplemente no es algo en mi OS así que solo me resta esperar a ver que pasa, estaría muy bueno que a los que les "desapareció" el problema vayan posteando la zona, tomando en cuenta un tiempo prudencial de prueba 24 a 72hs. (nunca se sabe)

---

### Post by marcelo_bur on 2010-10-28
> **atari130xe said:**
> YO no toco nada más porque simplemente no es algo en mi OS así que solo me resta esperar a ver que pasa, estaría muy bueno que a los que el problema les desapareció vayan posteando la zona.

Hola. La localidad donde habito figura en mi perfil, pero por las dudas amplio la información:

Ciudad de Burzaco, Partido de Almirante Brown, Provincia de Buenos Aires, 25 km al sur de la Ciudad Autónoma de Buenos Aires.

Hasta el momento el sevicio sigue funcionando bien.

Saludos

---

### Post by hard_rock_heavy on 2010-10-28
A mi me sigue funcionando pésimo

---

### Post by Sergius14 on 2010-10-28
Yo estoy Banfield, también zona sur.

Ayer saqué el script como les dije, y ahora sigo así.

Funciona perfecto sin script.

Podría decir que el problema fue resuelto en mi casa.

---

### Post by atari130xe on 2010-10-28
> **hard_rock_heavy said:**
> A mi me sigue funcionando pésimo

Idem mi conexión, obviamente sigo reclamando cada 72hs (tiempo estimado de resolución de problemas)...

---

### Post by chulelinux on 2010-10-29
Ojala se te haya solucionado el problema Sergilus. A mí me paso que el lunes y martes, día más día menos, pensé que el problema se había solucionado pero antes de postear quería esperar un poquito más porque ya me había pasado. Y la verdad que desde ayer es un desastre nuevamente. Nuevo reclamo y así seguiremos como atari cada 72hs. Saludos

---

### Post by marcelo_bur on 2010-10-29
> **chulelinux said:**
> Ojala se te haya solucionado el problema Sergilus. A mí me paso que el lunes y martes, día más día menos, pensé que el problema se había solucionado pero antes de postear quería esperar un poquito más porque ya me había pasado. Y la verdad que desde ayer es un desastre nuevamente. Nuevo reclamo y así seguiremos como atari cada 72hs. Saludos

Hola. Todo es posible por estos pagos y no me extrañaría demasidado que el problema resurja, sin embargo hay que tener un mínimo de optimismo para afrontar la vida. Haste este momento todo OK por aquí, y ojalá nos dure a todos aquellos que de alguna forma desconocida para nosotros mismos, el problema ha dejado de existir.
Saludos

---

### Post by marcelo_bur on 2010-10-29
I'm sorry... Ojalá también se solucione para el resto de los usuarios, sino lo que escribí suena muy egoista cuando no es mi intención serlo.
Saludos.

---

### Post by atari130xe on 2010-10-29
Desde hace unos 60 mins estoy probando y parece que ya están reconfigurando el bendito proxy, ahora ya casi no se nota pero sigue siendo aleatorio el problema (perceptible) ahora funciona mucho mejor pero aparentemente falta la "sintonía fina"... (me acaban de llamar de Telefónica para avisarme que ya funciona bien y les comenté que no del todo, así que lo volvieron a pasarle el dato a la gente que está trabajando con el servidor)

---

### Post by edboy on 2010-10-29
Por aca todo parece andar normalmente, estoy en San Justo AMBA.

Abrazo!!!

---

### Post by atari130xe on 2010-10-29
Aparentemente ya reconfiguraron el servidor y comenzó a funcionar bién (voy a esperar 48hs para confirmarlo pero anda bién)

resultado de un speedtest:

[[IMG]http://img830.imageshack.us/img830/608/pantallazo5c.png[/IMG]](http://img830.imageshack.us/i/pantallazo5c.png/)

Uploaded with [ImageShack.us](http://imageshack.us)

Las velocidades son las "normales" para un perfil de 3 Megas comparadas con las que tenía antes del 15 de Setiembre que llegaban a 4 Megas pero lo importante es que ya no tengo que darle a F5 ni "reload", esperemos sea definitivo.

---

### Post by chulelinux on 2010-10-30
Hoy la red despertó por estos lados andando normalmente y muy bien. Todavía no tuve que que apretar en ningún momento F5, deporte que se me había hecho cotidiano. Esperaremos y comentamos.
Saludos

---

### Post by josecuervo86 on 2010-10-31
Por aca esta andando bien tambien, solo lo noto un poco mas lento que lo habitual pero nada grave. Era hora que se pusieran las pilas y lo arreglaran...

---

### Post by marcelo_bur on 2010-10-31
Hola. Solo confirmo que, por suerte, el problema no regresó. Solo bajó un poco la velocidad de carga y descarga directa de archivos, aunque creo que sigue siendo superior a la que tenía antes del problema. Ojala este tema vaya quedando en el olvido, lo cual significaría que por fin nos están dando buena parte de aquello por lo cual pagamos. Reitero, como lo dije en otro post, que durante 10 años Speedy me brindó un servicio aceptable aunque no excelente. Por ello mi renuencia a cambiar inmediatamente de proveedor.
Saludos

---

### Post by atari130xe on 2010-10-31
Bueno en mi casó confirmo que reconfiguraron el proxy transparente (no lo removieron) y funciona bien, como dije en mi último post la velocidad es la "normal" para un perfil de 3MB pero funciona correctamente. Esperemos se mantenga de esta forma. Ahora a reclamar los días de mal funcionamiento desde el 1 del 10 hasta el 29 del 10. Esperemos terminen de arreglarlo para todos los usuarios. No dejen de reclamar por los días con mal servicio, es lo que corresponde sin dudas.

---

### Post by pol666 on 2010-11-01
Que suerte que tienen, yo me pudrí y me cambié, el miercoles me ponen Telecentro

---

### Post by chulelinux on 2010-11-03
Confirmo que me sigue andando bien la conexión. Quizás un poco más lenta en cargar las páginas pareciera pero sin problemas.

Saludos

---

### Post by atari130xe on 2010-11-03
Lo que sí está confirmado en mi caso es que al Proxy caché no lo sacaron... para saber si estás bajo en proxy cache "transparente" se puede ingresar acá al sitio de la Universidad de Berkeley (USA) y les hace una análisis completo y minucioso de su conexión a internet.

[http://netalyzr.icsi.berkeley.edu/]("http://netalyzr.icsi.berkeley.edu/")

La navegación funciona bíen, en cuanto a la velocidad es la "Standard" (máximo 309kbps download) antés del problema llegaba cómodamente a 410kbps. el resto está "normal".

---

### Post by marcelo_bur on 2010-11-03
> **atari130xe said:**
> Lo que sí está confirmado en mi caso es que al Proxy caché no lo sacaron... para saber si estás bajo en proxy cache "transparente" se puede ingresar acá al sitio de la Universidad de Berkeley (USA) y les hace una análisis completo y minucioso de su conexión a internet.

[http://netalyzr.icsi.berkeley.edu/]("http://netalyzr.icsi.berkeley.edu/")

La navegación funciona bíen, en cuanto a la velocidad es la "Standard" (máximo 309kbps download) antés del problema llegaba cómodamente a 410kbps. el resto está "normal".

Hola. Mientras podamos navegar normalmente lo del proxy es cosa de ellos. Yo hice el test y marca algunas irregularidades, pero ¿cómo saber si otros ISP no hacen lo mismo o peor?
Saludos

---

### Post by atari130xe on 2010-11-03
> **marcelo_bur said:**
> Hola. Mientras podamos navegar normalmente lo del proxy es cosa de ellos. Yo hice el test y marca algunas irregularidades, pero ¿cómo saber si otros ISP no hacen lo mismo o peor?
Saludos

Mientras tipeo esto me rio solo porque con este sitio me dá el tipico error "no se encuentra" jajaja, bueno lo del proxy afecta para ciertas cosas muy puntuales como por ej: bajar archivos desde Megaupload, fileserver, etc. ¿Porqué? simple esos sitios de almacenamiento toman las direcciones de IP para autorizar la bajada de archivos y si uno no tiene cuenta en ellos, y ese archivo está siendo bajando por otras personas desde el mismo ISP (proveedor de internet) aparece un aviso en el navegador que dice "no puede realizar la descarga porque ya está siendo descargado desde la IP....." (tu número de IP), otros ISP suelen hacer eso tmb. En cuanto a las "irregularidades" son nada más y nada menos que cualquier con los conocimientos adecuados puede tomar control de tu navegador" por una vulnerabilidad... ¿que lendo no? :S

---

### Post by marcelo_bur on 2010-11-03
> **atari130xe said:**
> Mientras tipeo esto me rio solo porque con este sitio me dá el tipico error "no se encuentra" jajaja

Es verdad, me ha pasado un par de veces y únicamente con este foro, al principio me preocupé pero luego recordé que antes también pasaba muy de vez en cuando


>  bueno lo del proxy afecta para ciertas cosas muy puntuales como por ej: bajar archivos desde Megaupload, fileserver, etc. ¿Porqué? simple esos sitios de almacenamiento toman las direcciones de IP para autorizar la bajada de archivos y si uno no tiene cuenta en ellos, y ese archivo está siendo bajando por otras personas desde el mismo ISP (proveedor de internet) aparece un aviso en el navegador que dice "no puede realizar la descarga porque ya está siendo descargado desde la IP....." (tu número de IP), otros ISP suelen hacer eso tmb.

Esto no me sucede. No uso la pc con juegos, no bajo música, pero... nadie es perfecto. Bajo cantidades de archivos desde Megaupload, Fileserver, Hotfile, Netload, Filesonic... de películas que veo luego en la misma pc. Es más, generalmente no bajo peliculas en un solo archivo, uso un sitio que pone muy buenas peliculas, con buena calida y audio latino, las suben a los servidores que nombré como archivos .RAR divididos en partes de entre 100 y 400 megas, por lo que para completar algunas peliculas he llegado a pasar todo un dia descargando archivos uno tras otro hasta que el sitio me dice que me excedí en el limite de descarga para usuaris FREE. Pero nada sobre la IP.

>  En cuanto a las "irregularidades" son nada más y nada menos que cualquier con los conocimientos adecuados puede tomar control de tu navegador" por una vulnerabilidad... ¿que lendo no? :S

Yo entiendo a lo que te referís, pero supongo que cualquiera con los suficientes conocimientos podría meterse en mi pc de quererlo, con o sin proxi. Y el pobre se llevaría una gran decepción, no va a encontrar ni un número de tarjeta de crédito ni nada que valga la pena (y creo que nadie debería dejar ese tipo de información disponible en una pc que se conecta habitualmente a internet), salvo que se trate de uno de esos crakers, pero bue... tambien podés salir a la calle y te pisa un camión.

Y a no creer que todo esto lo escribo para defender a la empresa, se perfectamente lo que son y como abusan, pero aqui el problema era que no podiamos navegar y eso se solucionó.
Saludos

---

### Post by atari130xe on 2010-11-03
> **marcelo_bur said:**
> Es verdad, me ha pasado un par de veces y únicamente con este foro, al principio me preocupé pero luego recordé que antes también pasaba muy de vez en cuando




Esto no me sucede. No uso la pc con juegos, no bajo música, pero... nadie es perfecto. Bajo cantidades de archivos desde Megaupload, Fileserver, Hotfile, Netload, Filesonic... de películas que veo luego en la misma pc. Es más, generalmente no bajo peliculas en un solo archivo, uso un sitio que pone muy buenas peliculas, con buena calida y audio latino, las suben a los servidores que nombré como archivos .RAR divididos en partes de entre 100 y 400 megas, por lo que para completar algunas peliculas he llegado a pasar todo un dia descargando archivos uno tras otro hasta que el sitio me dice que me excedí en el limite de descarga para usuaris FREE. Pero nada sobre la IP.



Yo entiendo a lo que te referís, pero supongo que cualquiera con los suficientes conocimientos podría meterse en mi pc de quererlo, con o sin proxi. Y el pobre se llevaría una gran decepción, no va a encontrar ni un número de tarjeta de crédito ni nada que valga la pena (y creo que nadie debería dejar ese tipo de información disponible en una pc que se conecta habitualmente a internet), salvo que se trate de uno de esos crakers, pero bue... tambien podés salir a la calle y te pisa un camión.

Y a no creer que todo esto lo escribo para defender a la empresa, se perfectamente lo que son y como abusan, pero aqui el problema era que no podiamos navegar y eso se solucionó.
Saludos

Jejeje si Marcelo no te preocupes nadie te acusa de nada :P, somos usuarios de una empresa y nada más. Tendría que hacer un PrintScreen de una de esas situaciones sobre la IP que comenté.

Si hiciste el test de la U. de Berkeley seguro habrás visto el comienzo del resultado del análisis:

> Summary of Noteworthy Events &#8211;
Major Abnormalities

    * An HTTP proxy was detected which may be vulnerable to attack.
    * A detected in-network HTTP cache incorrectly caches information 

Minor Aberrations

    * Certain TCP protocols are blocked in outbound traffic
    * The network path does not reply when it needs to fragment traffic
    * Network bandwidth may be low
    * An HTTP proxy was detected based on added or changed HTTP traffic
    * A detected in-network HTTP cache exists in your network 



Yo normalmente tampoco bajo juegos pero si bajo archivos grandes que usualmente están en esos servidores y me ocurre eso. (suele pasar cuando por ej bajo iso´s modificadas y personalizadas) Estamos totalmente de acuerdo en que ahora se puede usar el servicio de manera, normal, solo te aclaré algunos inconvenientes de estar detrás de un Servidor Proxy Transparente, en España con Telefónica hubo un revuelo bastante improtante allá por el 2003 o antes no recuerdo bién por el tema de la privacidad y todos estos inconvenientes que nos vinieron pasando a los usuarios vernáculos. La lógica a mi entender sería que NO tengamos nada que filtre, cachée, etc. nuestra conexión, eso se llama invertir de manera real en una buena conexión sin recurrir a estos medios para prestar un servicio. De echo como mencioné en uno de los tantos posts de este mismo tema, en España está la opción de elegir no pasar por el proxy en cuestión.
saludos :)

---

### Post by chulelinux on 2010-11-05
Exactamente el mismo resultado me tiró el test que se posteó. Y leyendo un poco al respecto parece nada menor lo de la vulnerabilidad y las cuestiones que señalás Atari. Y sí, uno debería poder tener la opción de no estar intermediado por el proxy, cuestión que les regala además facilmente una consultora on line más o menos...
Saludos

---

### Post by gmunioz on 2010-11-05
Para solucionar la vulnerabilidad a la que estamos expuestos,
basta con habilitar iptables, con un script como este:

#!/bin/sh
## SCRIPT de IPTABLES - Ejemplo del manual de iptables
## Ejemplo de script para proteger la propia máquina con DROP por defecto

echo -n Aplicando Reglas de Firewall...

## FLUSH de reglas
iptables -F
iptables -X
iptables -Z
iptables -t nat -F

## Establecemos politica por defecto: DROP
iptables -P INPUT DROP
iptables -P OUTPUT DROP
iptables -P FORWARD DROP

## Empezamos a abrir! porque ahora esta TODO denegado.
## Debemos decir de manera explicita qué es lo que queremos abrir

# Operar en localhost sin limitaciones
/sbin/iptables -A INPUT -i lo -j ACCEPT
/sbin/iptables -A OUTPUT -o lo -j ACCEPT

# A nuestra IP le dejamos todo
/sbin/iptables -A INPUT -s 192.168.1.33 -j ACCEPT
/sbin/iptables -A OUTPUT -d 192.168.1.33 -j ACCEPT

# Permitimos que la maquina pueda salir a la web
/sbin/iptables -A INPUT -p tcp -m tcp --sport 80 -m state --state RELATED,ESTABLISHED -j ACCEPT
/sbin/iptables -A OUTPUT -p tcp -m tcp --dport 80 -j ACCEPT

# Y tambien a webs seguras
/sbin/iptables -A INPUT -p tcp -m tcp --sport 443 -m state --state RELATED,ESTABLISHED -j ACCEPT
/sbin/iptables -A OUTPUT -p tcp -m tcp --dport 443 -j ACCEPT

# Reglas necesarias para FTP pasivo y activo. Se permiten conexiones entrantes YA establecidas
/sbin/iptables -A INPUT -p tcp -m tcp --sport 20:21 -m state --state RELATED,ESTABLISHED -j ACCEPT
/sbin/iptables -A OUTPUT -p tcp -m tcp --dport 20:21 -j ACCEPT
/sbin/iptables -A INPUT -p tcp -m tcp --sport 1024:65535 --dport 1024:65535 -m state --state ESTABLISHED -j ACCEPT
/sbin/iptables -A OUTPUT -p tcp -m tcp --dport 1024:65535 -m state --state NEW,RELATED,ESTABLISHED -j ACCEPT

# Permitimos la consulta a un primer DNS de Speedy
/sbin/iptables -A INPUT -s 200.10.122.10 -p udp -m udp --sport 53 -j ACCEPT
/sbin/iptables -A OUTPUT -d 200.10.122.10 -p udp -m udp --dport 53 -j ACCEPT

# Permitimos la consulta a un segundo DNS de Speedy
/sbin/iptables -A INPUT -s 200.10.122.11 -p udp -m udp --sport 53 -j ACCEPT
/sbin/iptables -A OUTPUT -d 200.10.122.11 -p udp -m udp --dport 53 -j ACCEPT

# Barrera de backup por si cambiamos a modo ACCEPT temporalmente
# Con esto protegemos los puertos reservados y otros well-known
/sbin/iptables -A INPUT -p tcp -m tcp --dport 1:1024 -j DROP
/sbin/iptables -A INPUT -p udp -m udp --dport 1:1024 -j DROP
/sbin/iptables -A INPUT -p tcp -m tcp --dport 1723 -j DROP
/sbin/iptables -A INPUT -p tcp -m tcp --dport 3306 -j DROP
/sbin/iptables -A INPUT -p tcp -m tcp --dport 5432 -j DROP

echo " OK . Verifique que lo que se aplica con: iptables -L -n"

# Fin del script

Donde:
192.168.1.33 es la Ip de nuestra máquina.
200.10.122.10 200.10.122.11 son los servidores DNS de Speedy

---

### Post by atari130xe on 2010-11-06
> **gmunioz said:**
> Para solucionar la vulnerabilidad a la que estamos expuestos,
basta con habilitar iptables, con un script como este:

#!/bin/sh
## SCRIPT de IPTABLES - Ejemplo del manual de iptables
## Ejemplo de script para proteger la propia máquina con DROP por defecto

echo -n Aplicando Reglas de Firewall...

## FLUSH de reglas
iptables -F
iptables -X
iptables -Z
iptables -t nat -F

## Establecemos politica por defecto: DROP
iptables -P INPUT DROP
iptables -P OUTPUT DROP
iptables -P FORWARD DROP

## Empezamos a abrir! porque ahora esta TODO denegado.
## Debemos decir de manera explicita qué es lo que queremos abrir

# Operar en localhost sin limitaciones
/sbin/iptables -A INPUT -i lo -j ACCEPT
/sbin/iptables -A OUTPUT -o lo -j ACCEPT

# A nuestra IP le dejamos todo
/sbin/iptables -A INPUT -s 192.168.1.33 -j ACCEPT
/sbin/iptables -A OUTPUT -d 192.168.1.33 -j ACCEPT

# Permitimos que la maquina pueda salir a la web
/sbin/iptables -A INPUT -p tcp -m tcp --sport 80 -m state --state RELATED,ESTABLISHED -j ACCEPT
/sbin/iptables -A OUTPUT -p tcp -m tcp --dport 80 -j ACCEPT

# Y tambien a webs seguras
/sbin/iptables -A INPUT -p tcp -m tcp --sport 443 -m state --state RELATED,ESTABLISHED -j ACCEPT
/sbin/iptables -A OUTPUT -p tcp -m tcp --dport 443 -j ACCEPT

# Reglas necesarias para FTP pasivo y activo. Se permiten conexiones entrantes YA establecidas
/sbin/iptables -A INPUT -p tcp -m tcp --sport 20:21 -m state --state RELATED,ESTABLISHED -j ACCEPT
/sbin/iptables -A OUTPUT -p tcp -m tcp --dport 20:21 -j ACCEPT
/sbin/iptables -A INPUT -p tcp -m tcp --sport 1024:65535 --dport 1024:65535 -m state --state ESTABLISHED -j ACCEPT
/sbin/iptables -A OUTPUT -p tcp -m tcp --dport 1024:65535 -m state --state NEW,RELATED,ESTABLISHED -j ACCEPT

# Permitimos la consulta a un primer DNS de Speedy
/sbin/iptables -A INPUT -s 200.10.122.10 -p udp -m udp --sport 53 -j ACCEPT
/sbin/iptables -A OUTPUT -d 200.10.122.10 -p udp -m udp --dport 53 -j ACCEPT

# Permitimos la consulta a un segundo DNS de Speedy
/sbin/iptables -A INPUT -s 200.10.122.11 -p udp -m udp --sport 53 -j ACCEPT
/sbin/iptables -A OUTPUT -d 200.10.122.11 -p udp -m udp --dport 53 -j ACCEPT

# Barrera de backup por si cambiamos a modo ACCEPT temporalmente
# Con esto protegemos los puertos reservados y otros well-known
/sbin/iptables -A INPUT -p tcp -m tcp --dport 1:1024 -j DROP
/sbin/iptables -A INPUT -p udp -m udp --dport 1:1024 -j DROP
/sbin/iptables -A INPUT -p tcp -m tcp --dport 1723 -j DROP
/sbin/iptables -A INPUT -p tcp -m tcp --dport 3306 -j DROP
/sbin/iptables -A INPUT -p tcp -m tcp --dport 5432 -j DROP

echo " OK . Verifique que lo que se aplica con: iptables -L -n"

# Fin del script

Donde:
192.168.1.33 es la Ip de nuestra máquina.
200.10.122.10 200.10.122.11 son los servidores DNS de Speedy

Gracias por la data Gabriel, la pregunta es la siguiente, no leí todo el script pero hay que configurar los puertos para:BitTorrent, etc.? o así como está podemos usar cualquier programa/gestor de descargas?

---

### Post by biale on 2010-11-06
Pareciera que estan hablando de dos cosas distintas (?)

Cualquier ISP puede copiar los datos (paquetes) que pasan por la red, con o sin proxy...

El script que posteo Gabriel sirve para evitar intrusiones desde la Internet y hacia nuestra computadora

Entendí bien?

---

### Post by marcelo_bur on 2010-11-06
> **gmunioz said:**
> Para solucionar la vulnerabilidad a la que estamos expuestos,
basta con habilitar iptables, con un script como este:

#!/bin/sh
## SCRIPT de IPTABLES - Ejemplo del manual de iptables
## Ejemplo de script para proteger la propia máquina con DROP por defecto

echo -n Aplicando Reglas de Firewall...

## FLUSH de reglas
iptables -F
iptables -X
iptables -Z
iptables -t nat -F

## Establecemos politica por defecto: DROP
iptables -P INPUT DROP
iptables -P OUTPUT DROP
iptables -P FORWARD DROP

## Empezamos a abrir! porque ahora esta TODO denegado.
## Debemos decir de manera explicita qué es lo que queremos abrir

# Operar en localhost sin limitaciones
/sbin/iptables -A INPUT -i lo -j ACCEPT
/sbin/iptables -A OUTPUT -o lo -j ACCEPT

# A nuestra IP le dejamos todo
/sbin/iptables -A INPUT -s 192.168.1.33 -j ACCEPT
/sbin/iptables -A OUTPUT -d 192.168.1.33 -j ACCEPT

# Permitimos que la maquina pueda salir a la web
/sbin/iptables -A INPUT -p tcp -m tcp --sport 80 -m state --state RELATED,ESTABLISHED -j ACCEPT
/sbin/iptables -A OUTPUT -p tcp -m tcp --dport 80 -j ACCEPT

# Y tambien a webs seguras
/sbin/iptables -A INPUT -p tcp -m tcp --sport 443 -m state --state RELATED,ESTABLISHED -j ACCEPT
/sbin/iptables -A OUTPUT -p tcp -m tcp --dport 443 -j ACCEPT

# Reglas necesarias para FTP pasivo y activo. Se permiten conexiones entrantes YA establecidas
/sbin/iptables -A INPUT -p tcp -m tcp --sport 20:21 -m state --state RELATED,ESTABLISHED -j ACCEPT
/sbin/iptables -A OUTPUT -p tcp -m tcp --dport 20:21 -j ACCEPT
/sbin/iptables -A INPUT -p tcp -m tcp --sport 1024:65535 --dport 1024:65535 -m state --state ESTABLISHED -j ACCEPT
/sbin/iptables -A OUTPUT -p tcp -m tcp --dport 1024:65535 -m state --state NEW,RELATED,ESTABLISHED -j ACCEPT

# Permitimos la consulta a un primer DNS de Speedy
/sbin/iptables -A INPUT -s 200.10.122.10 -p udp -m udp --sport 53 -j ACCEPT
/sbin/iptables -A OUTPUT -d 200.10.122.10 -p udp -m udp --dport 53 -j ACCEPT

# Permitimos la consulta a un segundo DNS de Speedy
/sbin/iptables -A INPUT -s 200.10.122.11 -p udp -m udp --sport 53 -j ACCEPT
/sbin/iptables -A OUTPUT -d 200.10.122.11 -p udp -m udp --dport 53 -j ACCEPT

# Barrera de backup por si cambiamos a modo ACCEPT temporalmente
# Con esto protegemos los puertos reservados y otros well-known
/sbin/iptables -A INPUT -p tcp -m tcp --dport 1:1024 -j DROP
/sbin/iptables -A INPUT -p udp -m udp --dport 1:1024 -j DROP
/sbin/iptables -A INPUT -p tcp -m tcp --dport 1723 -j DROP
/sbin/iptables -A INPUT -p tcp -m tcp --dport 3306 -j DROP
/sbin/iptables -A INPUT -p tcp -m tcp --dport 5432 -j DROP

echo " OK . Verifique que lo que se aplica con: iptables -L -n"

# Fin del script

Donde:
**[COLOR="Red"]192.168.1.33 es la Ip de nuestra máquina.[/COLOR]**
200.10.122.10 200.10.122.11 son los servidores DNS de Speedy

Sinceramente a mi me parece muy complicado todo eso, ni sabría como configurarlo. Pero, más allá de mi ignorancia, me llama la atencion que también se debe configurar la IP de la máquina, y en mi caso esa IP varía con cada vez que me conecto, así que no entiendo ¿hay que cambiarla cada vez que te conectas?
Personalmente corriendo un SO Linux y con el firewall que viene con el kernel activado ya me siento tranquilo. Como dije en otro post... podés salir a la calle y te pisa un camión.
Saludos

---

### Post by gmunioz on 2010-11-06
Los gestores de descarga funcionan sin problemas.

Para las ip dinámicas se deberían especifica el rango
de la red y el dispositivo, algo asi como:

# A nuestra IP le dejamos todo
/sbin/iptables -A INPUT -s 192.168.1.0/24 -i eth0 -j ACCEPT
/sbin/iptables -A OUTPUT -d 192.168.1.0/24 -i eth0 -j ACCEPT

---

### Post by edboy on 2010-11-08
> **marcelo_bur said:**
> Sinceramente a mi me parece muy complicado todo eso, ni sabría como configurarlo. Pero, más allá de mi ignorancia, me llama la atencion que también se debe configurar la IP de la máquina, y en mi caso esa IP varía con cada vez que me conecto, así que no entiendo ¿hay que cambiarla cada vez que te conectas?
Personalmente corriendo un SO Linux y con el firewall que viene con el kernel activado ya me siento tranquilo. Como dije en otro post... podés salir a la calle y te pisa un camión.
Saludos

Marcelo, el firewall viene por defecto y activado, es verdad, pero no tiene ninguna regla específica, es decir acepta y deja salir cualquier paquete por defecto, si bien la arquitectura del SO es distinta y tenés que conocer algo de Linux para infiltrarte desde afuera no es para nada seguro un firewall sino se le dice lo que tiene que hacer.

De igual manera no quiero comentar más sobre esto para no desvirtuar el tema de onda xD.

Abrazo!

---

### Post by guillermolisi on 2011-11-30
> **petersacco4 said:**
> I have a question that is the Linux platform independent ?

Could you be more explicit with your question, please ?

---

