---
title: "¿Speedy que pasa? Volvimos a las andadas?"
date: 2011-02-08
forum: Comunidad
---

### Post by atari130xe on 2011-02-08
No sé a Ustedes pero yo desde hace unos días estoy experimentado los típicos problemas para cargar páginas, no al nivel que en Setiembre pasado, pero sí molestos principalmente con sitios internacionales (Facebook, etc.) o cargan muy lentamente (fotos y flash) o directamente el navegador queda en blanco... habrá que llamar al soporte técnico nuevamente? :confused:

---

### Post by juancarlospaco on 2011-02-08
los DNS como andan, probaste los de Google ?

---

### Post by atari130xe on 2011-02-08
Sip son los que uso 8.8.8.8 y 8.8.4.4 pero bueno estoy con estos inconvenientes, para poder responder en este momento tuve que salir y volver a cargar Ubuntuforums.org porque quedo "esperando" sin cargarse...

---

### Post by marcelo_bur on 2011-02-08
Por el momento todo normal por Burzaco.

Saludos

---

### Post by mama21mama on 2011-02-08
en lincoln creo que todavía alquila fibertel la fibra óptica de speedy.
anda medio chotongo el internet hace algunos días.

---

### Post by atari130xe on 2011-02-08
> **mama21mama said:**
> en lincoln creo que todavía alquila fibertel la fibra óptica de speedy.
anda medio chotongo el internet hace algunos días.

Luego de "normalizar" la conexión allá por Septiembre pasado no tuve problemas pero sí dejé de tener la velocidad que tenía antes del problema:

antes llegaba a tener promedios de 3.88MB o más, ahora obtengo estos con suerte:

[[IMG]http://www.speedtest.net/result/1149108944.png[/IMG]](http://www.speedtest.net)

---

### Post by mama21mama on 2011-02-08
[[IMG]http://www.speedtest.net/result/1149162349.png[/IMG]](http://www.speedtest.net)

supuesta mente tengo 3mb

---

### Post by marcelo_bur on 2011-02-09
> **atari130xe said:**
> Luego de "normalizar" la conexión allá por Septiembre pasado no tuve problemas pero sí dejé de tener la velocidad que tenía antes del problema:

antes llegaba a tener promedios de 3.88MB o más, ahora obtengo estos con suerte:

[[IMG]http://www.speedtest.net/result/1149108944.png[/IMG]](http://www.speedtest.net)

Hola, durante la época del problema yo también tenía velocidades de descarga muy superiores a las normales, pero no se podía navegar...
Luego todo volvió a la normalidad, incluyendo las velocidades de descarga.
Saludos

---

### Post by atari130xe on 2011-02-09
> **marcelo_bur said:**
> Hola, durante la época del problema yo también tenía velocidades de descarga muy superiores a las normales, pero no se podía navegar...
Luego todo volvió a la normalidad, incluyendo las velocidades de descarga.
Saludos

En mi caso no era así, funcionaba todo bién, tanto las descargas como la navegación, pero en estos últimos días cuando deseo entrar en algunos sitios queda así: Conectando... (Ubuntuforums.org, google.com.ar, facebook.com y la lista sigue...)

---

### Post by atari130xe on 2011-02-09
> **mama21mama said:**
> [[IMG]http://www.speedtest.net/result/1149162349.png[/IMG]](http://www.speedtest.net)

supuesta mente tengo 3mb

te compadezco... eso no es 3MB ni por asomo... ahora el ping que tenés es muy bueno.

---

### Post by omniwired on 2011-02-09
Si ahce unos dias empezaron los problemas de nuevo y estas lineas

iptables -A OUTPUT -p tcp --dport 80 -m state --state NEW -m recent --set --name thor --rdest -j ACCEPT
iptables -A INPUT -p tcp -m tcp --tcp-flag RST RST -m state --state ESTABLISHED -m recent --name thor --rcheck --rsource --seconds 1 -j DROP

no lo arreglan esta vez, me voy a poner a ver un poco el trafico con wireshark. Si encuentro algo como el RST de la vez pasada posteo.

Los DNS tengo los de google, y la velocidad de descarga es como siempre (500 k+), la latencia es insufrible. Hice un test con pingtest.com y me dio B (bien). 

a ver si a alguien se le ocurre algo.

---

### Post by mama21mama on 2011-02-09
bueno hice mi reclamo formal a fibertel... espero una noticia buena.
luego comento si me dieron el por que de mi conexión.

---

### Post by atari130xe on 2011-02-09
> **omniwired said:**
> Si ahce unos dias empezaron los problemas de nuevo y estas lineas

iptables -A OUTPUT -p tcp --dport 80 -m state --state NEW -m recent --set --name thor --rdest -j ACCEPT
iptables -A INPUT -p tcp -m tcp --tcp-flag RST RST -m state --state ESTABLISHED -m recent --name thor --rcheck --rsource --seconds 1 -j DROP

no lo arreglan esta vez, me voy a poner a ver un poco el trafico con wireshark. Si encuentro algo como el RST de la vez pasada posteo.

Los DNS tengo los de google, y la velocidad de descarga es como siempre (500 k+), la latencia es insufrible. Hice un test con pingtest.com y me dio B (bien). 

a ver si a alguien se le ocurre algo.

MMM ya me parecía, estoy tan curtido con lo que me pasó de Setiembre a Octubre pasado que imaginé no era un problema ni de mi modem/router, OS o PC. hice un pingtest y acá tenés el resultado (estoy a 500 metros -o menos- de la centra telefónica)

[[IMG]http://www.pingtest.net/result/34224639.png[/IMG]](http://www.pingtest.net)

---

### Post by marcelo_bur on 2011-02-09
[[IMG]http://www.pingtest.net/result/34254031.png[/IMG]](http://www.pingtest.net)

[[IMG]http://www.speedtest.net/result/1150579979.png[/IMG]](http://www.speedtest.net)

Yo tengo contratado el plan de 1MB

---

### Post by atari130xe on 2011-02-10
Bueno acabo de llamar a soporte por 1era vez haciéndoles saber que me está pasando, me dijeron que yo era el 1er llamado hablandoles sobre el tema. Me regeneraron la linea (me siento como David Vincent en "The invaders"jejeje) y funciona un poco mejor de todas maneras voy a chequear dentro de las 48hs el funcionamiento de la navegación y vuelvo a comunicarme.

---

### Post by atari130xe on 2011-02-13
Bueno confirmado, ya vengo viendo a varias personas con los mismos problemas: Telefònica està toqueteando su proxy cache asi que paciencia... a empezar a reclamar.

[http://www.bandangosta.com.ar/index.php/topic,5490.0.html]("http://www.bandangosta.com.ar/index.php/topic,5490.0.html")

[http://www.bandangosta.com.ar/index.php/topic,5194.240.html]("http://www.bandangosta.com.ar/index.php/topic,5194.240.html")

---

### Post by mama21mama on 2011-02-15
[[IMG]http://www.pingtest.net/result/34686626.png[/IMG]](http://www.pingtest.net)
[[IMG]http://www.speedtest.net/result/1158943843.png[/IMG]](http://www.speedtest.net)
esto me salio ahora; parece que se normalizo.
[video en youtube]("http://www.youtube.com/watch?v=g5AN11WzxI0&hd=1") probando también con nethogs.

---

### Post by atari130xe on 2011-02-16
> **mama21mama said:**
> [[IMG]http://www.pingtest.net/result/34686626.png[/IMG]](http://www.pingtest.net)
[[IMG]http://www.speedtest.net/result/1158943843.png[/IMG]](http://www.speedtest.net)
esto me salio ahora; parece que se normalizo.
[video en youtube]("http://www.youtube.com/watch?v=g5AN11WzxI0&hd=1") probando también con nethogs.


Chequeaste tu conexion con un servidor en Asheville, North Carolina, USA! en tu prueba de velocidad pero el test del ping lo hiciste con el servidor que está en la Pcia. de Santa Fé fijate como cambian los resultados del ping. la conexión te quedó muy buena.

---

### Post by mama21mama on 2011-02-16
**packet loss** sera por el servidor que use o tengo problemas?

---

### Post by atari130xe on 2011-02-16
> **mama21mama said:**
> **packet loss** sera por el servidor que use o tengo problemas?

no, solo que tuviste paquetes perdidos por que muy probablemente usaste un servidor que esta muy lejos, proba usando el de buenos aires

---

### Post by mama21mama on 2011-02-19
faaa otra vez... le pase un archivo de 8mb via skype a un colega y tardaba mucho mas de lo normal, y se lo mande via bashare al toque le llego; luego el me envió una imagen y también tardaba.

con speedtest.net no marca mucho que pasa el de por que esto.

pero hice otro análisis y me salio esto.



[The ICSI Netalyzr]("http://n1.netalyzr.icsi.berkeley.edu/summary/id=43ca253f-10442-b6ef478f-ebcd-4525-87cb")

realmente no se por que skype hace esto. :s

---

### Post by juancarlospaco on 2011-02-19
dns lentos lol, probar con el DNSBench

---

### Post by mama21mama on 2011-02-19
no creo que sea las dns, si estaba ya echa la conexión.

---

### Post by kidonaipe on 2011-02-20
Idem a todo lo que ya dijeron. (cargan paginas por la mitad,tardan demasiado,o se queda en blanco el navegador; hay q darle al f5 varias veces seguidas).

soy de mardelplata y me viene pasando hace unas semanitas esto, primero pense que estaba paranoico y q era demasiado esperar el tiempo de carga, pero no . 

hoy llame a speedy para quejarme, y el cristiano que me atendio me dijo que tenia microcortes y que me mandaba un tecnico en 72 hs para q me revise el cableado; cualquier verdura, tengo el cableado intacto, es el mismo que siempre, y no soy al unico que le pasa (por suerte pude confirmarlo gracias a ustedes); me parece que mañana llamo para cancelar al tecnico porque al re p**o, pero nose, ustedes que dicen q haga? 

alguno encontro alguna solucion? estoy harto de ver el facebook a medias.

---

### Post by gmunioz on 2011-02-20
Cuando comenzaron mis problemas con Speedy, utilicé el test de
velocidad de conexión y me dí cuenta que el sistema estaba expuesto, por eso implementé un iptables drop, para proteger mi sistema y el problema se arregló, este el el script que utilizo:

==========================================================

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
/sbin/iptables -A INPUT -s 192.168.1.0/24 -j ACCEPT
/sbin/iptables -A OUTPUT -d 192.168.1.0/24 -j ACCEPT

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

==============================================================
Naturalmente 192.168.1.0/24, es el rango de Ip en que esta configurado mi Zixel 600.

---

### Post by kidonaipe on 2011-02-21
Me alegra saber que si hay tecnicos de speedy que saben de lo que les estas hablando. Por otro lado, mi problema sigue ahi, pero el loco hizo todo lo q pudo, hasta llamo a gestion y me puso el altavoz para que escuchara una larga charla con un ignorante que poco sabia la verdad, y el termino "algo raro" fue nombrado con repeticion. Ah, me olvidaba, ni siquiera le andaba el sistema a el, asi q no podia ver si estaba o no sincronizando mi modem. Asi que imaginense como esta speedy.  

Le comente al tecnico que buscando en foros, a mi me parecia que el problema era del interleaved. Pero me respondio que hace bastante que estan asi, porque genera mucho menos trabajo para los perfiles de las cuentas.

Por otro lado, dijo que andan con unos quilombitos desde hace un tiempo. La verdad bastante sincero el loco.

Ya no se que hacer. Lo ultimo que me dijo fue "paciencia". 

Asi que si alguien sabe algo, por favor que avise.

---

### Post by mama21mama on 2011-02-21
> **kidonaipe said:**
> Idem a todo lo que ya dijeron. (cargan paginas por la mitad,tardan demasiado,o se queda en blanco el navegador; hay q darle al f5 varias veces seguidas).


esto me esta pasando, le haces al link click y no carga a la primera; y eso que uso fibertel/telefonica si.... aquí fibertel le paga la fibra en alquiler a telefónica aquí en [Lincoln]("http://maps.google.com.ar/maps/ms?ie=UTF8&hl=en&msa=0&msid=202017481724632607150.000492238511937c91e1b&t=h&z=19").

---

### Post by atari130xe on 2011-02-22
Lo primero que te hacen cuando llamás a soporte técnico de Speedy es decir que ellos "no están registrando quejas de este tipo y que uno es el primero" luego te "regeneran" la línea y finalmente te funciona 1 o 2 hs hasta que lastimósamente todo vuelve a la "anormalidad" F5 por favor... :(

---

### Post by kidonaipe on 2011-02-22
> **atari130xe said:**
> Lo primero que te hacen cuando llamás a soporte técnico de Speedy es decir que ellos "no están registrando quejas de este tipo y que uno es el primero" luego te "regeneran" la línea y finalmente te funciona 1 o 2 hs hasta que lastimósamente todo vuelve a la "anormalidad" F5 por favor... :(


Coincido. Ayer llame y estuve como media hora hablandole al chabon, y digo hablandole porque hablaba yo solo, y el no decia nada, no entendia que era interleaved, que era fast, y ni siquiera entendia que era el p*to ping. Se disculpo por no poder ayudarme y bueno me quede con toda la bronca.

Hoy a la mañana, me di cuenta que mi modem estaba sincronizando a menos que ayer. Habitualmente lo hace a 5mb y hoy lo hacia a 3mb. Dandone un Snr Margin en bajada realmente malo ( 4 db ).  Llame hace un rato para ver que pasaba con respecto a eso , y nada pudo hacer. Pense que habia jodido el router, porq en el unico adsl mode q levantaba era en G.Lite. 
Frustrado, conecte el modem usb q me dieron los de speedy en su momento( ahora estoy usando un modem/router wifi q compre por mi cuenta), y me di cuenta que tampoco sincronizaba; asi que a llamar a soporte otra vez. Me regeneró la linea al toque, y volvio a sincronizar a 5mb con modo gdmt. 
__________________________________

Sigo teniendo problemas con el ping en navegacion internacional, me ha llegado a 400ms q la verdad es una barbaridad. Lo peor de todo es que los de soporte me comentaron que si los valores de bajada sobre mi conexion contratada estan correctos no pueden hacer nada.
La verdad nose si estan teniendo problemas con el Dslam en la central, o la migracion de los perfiles a interleaved jodio todo definitivamente.

Estoy frustrado, ya no se que hacer ;D  .

---

### Post by hectorivand on 2011-02-22
Que pueden esperar de una empresa que usa 13 sistemas y que tarda 60 días en aprovisionar una linea de datos.

Sinceramente les digo, los que pueden búsquense otra alternativa.

Fuente.: Soy un Ex Project Manager de Telefónica Empresas.

Saludos
Nacho

---

### Post by atari130xe on 2011-02-23
> **hectorivand said:**
> Que pueden esperar de una empresa que usa 13 sistemas y que tarda 60 días en aprovisionar una linea de datos.

Sinceramente les digo, los que pueden búsquense otra alternativa.

Fuente.: Soy un Ex Project Manager de Telefónica Empresas.

Saludos
Nacho

Es bueno saberlo Nacho, en España están minados de quejas tmb.

---

### Post by omniwired on 2011-02-28
Fijanse si con estas 2 reglas mejora:

iptables -A INPUT -p tcp --tcp-flags RST RST -j DROP
y
iptables -A output -p tcp --tcp-flags RST RST -j DROP

Yo las puse arriba de un router con OpenWRT y con el modem de speedy en modo bridge.

---

