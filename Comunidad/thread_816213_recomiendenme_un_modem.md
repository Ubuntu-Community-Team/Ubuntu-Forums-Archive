---
title: "recomiendenme un modem"
date: 2008-06-02
forum: Comunidad
---

### Post by estebantal on 2008-06-02
me estoy volviendo loco con el moden de telefónica speedtouch 330.
hay algun modem para usar con ubuntu que no requiera instalación o que sea medianamente fácil.
soy muy nuevo con ubuntu y no entiendo mucho, pero quiero conectarme a internet. 
por favor, si alguien puede guiar a este "nuevito" se agradecerá.

---

### Post by crosssover on 2008-06-02
lesite esto ?, parecee que funciona. [http://ubuntuforums.org/showthread.php?t=797804](http://ubuntuforums.org/showthread.php?t=797804)

antes tenia ese modem y con un poco de esfuerzo lo pude hacer funcionar en ubuntu edgy, feisty y gutsy. Parece que ahora la cosa esta mas facil con hardy

---

### Post by estebantal on 2008-06-02
no entiendo nada. y si es en inglés menos.
recién estoy aprendiendo la consola. yo necesito algo más práctico para empezar.
todavía no se lo suficiente para instalarlo usando la consola.
necesito algo más directo.
si no se puede, no importa, en algun momento aprenderé y seguire usando el windows,que no me gusta nada, para conectarme a internet.
soy un nuevo newbie, ni newbie soy todavia.

---

### Post by osensei on 2008-06-02
La otra que te queda, que te va a andar seguro, es con un modem adsl con puerto ethernet (se conecta a la placa de red), no USB.

---

### Post by santiagoward2000 on 2008-06-02
Hola!
Yo antes tenia un Arescom 1060. Lo habia podido hacer andar con [esta guia]("http://ubuntu-ar.org/soporte/comos/modem-huawei-smartax-mt810") en Feisty y Gutsy. Es para el Huawei SmartAX MT810, pero a mi me anduvo con el Arescom, podes probar. Esta en castellano y es bastante facil de seguir.
Si no, como dijo osensei, lo mas facil seria conseguir un modem con puerto ethernet.
Saludos!

---

### Post by pol666 on 2008-06-02
Pedile a telefonica que te lo cambie por uno ethernet..capas te lo dejan barato. Y ahi te conectas con pppoeconf

---

### Post by atari130xe on 2008-06-03
Agregandome a la sugerencia de la respuesta anterior:
pedile a Speedy que te lo cambie por un modem Speedtouch ST510 v6. es el que uso yo con la conexion 2.5MB y los pasos son:
Cable de red a la placa Ethernet de la PC
Cable de Linea Tel. al modem
Abris una consola: sudo pppoeconf
varios "intros" hasta llegar a "usuario" (donde escribís tu nro de tel 45555555@speedyplus) y la clave
un par de intros mas y listo....
tas navegando :)

---

### Post by pol666 on 2008-06-03
no dijo que era speedy :P

---

### Post by atari130xe on 2008-06-04
> **pol666 said:**
> no dijo que era speedy :P
Tenei razón :lolflag:
No se cual es la cia de teléfonos solo sugerí la que tengo yo jejeje

---

### Post by llove on 2008-06-04
si te sirve de algo, yo uso un cisco 677. ningun drama hasta ahora, hace bastante que lo tengo, supongo q con cualquier ethernet como comentaron antes vas a estar bien. saludos

---

### Post by faktorqm on 2008-06-04
atari130xe y pol666: los modems ethernet por lo general son routeables, sus modems tienen esa opcion? de ser asi pppoeconf no es la mejor opcion para conectarse...... salu2!

---

### Post by atari130xe on 2008-06-04
> **faktorqm said:**
> atari130xe y pol666: los modems ethernet por lo general son routeables, sus modems tienen esa opcion? de ser asi pppoeconf no es la mejor opcion para conectarse...... salu2!
la verdad que no lo sé, pero podrias decirnos cual seria la mejor opcion para conectarse con estos modems? tks :)
PD Aclaro que no uso Router ni Conexion inhalambrica, solo la conexion "normal" linea tel. placa ethernet (única PC conectada)

---

### Post by mauro7g on 2008-06-04
Buenas tardes: En primer lugar no sé quien es el que tiene el problema del modem...segundo punto...Exigí a tu compañia de tel. (creo que debe ser Speedy) que te faciliten un Modem Zyxel P600. si tenés instalado window$ también en tu pc lo podés configurar de ahí (buscá en google Zyxel P600 + telefonica y es el primer link de la busqueda) de lo contrario con figuralo via web ke para acceder por default debe ser la dire en el explorador 192.168.0.1 del router y de ahí configurarlo para ke kede almacenado el usuario y contraseña directamente en el modem. Yo por lo menos lo hice así. Porke con un modem usb es un poco mas complicado....cualkier cosa avisá para ayudarte. Salu2!:)

---

### Post by santiagoward2000 on 2008-06-04
> **mauro7g said:**
> Buenas tardes: En primer lugar no sé quien es el que tiene el problema del modem...segundo punto...Exigí a tu compañia de tel. (creo que debe ser Speedy) que te faciliten un Modem Zyxel P600. si tenés instalado window$ también en tu pc lo podés configurar de ahí (buscá en google Zyxel P600 + telefonica y es el primer link de la busqueda) de lo contrario con figuralo via web ke para acceder por default debe ser la dire en el explorador 192.168.0.1 del router y de ahí configurarlo para ke kede almacenado el usuario y contraseña directamente en el modem. Yo por lo menos lo hice así. Porke con un modem usb es un poco mas complicado....cualkier cosa avisá para ayudarte. Salu2!:)

Hola!
No se como sea alla en Bs.As., pero cuando yo quise cambiar mi modem Arescom 1060 usb por uno ethernet, en Speedy me sacaron corriendo! Me dijeron que ellos no podian cambiarlos, y que si queria uno, tenia que comprarlo en otro lado.
No se si es muy facil que ellos te lo cambien.
Saludos

---

### Post by madelaki on 2008-06-04
No es facil que te lo cambien, pero el Zyxel Prestige 600 es muy conocido y accesible. No creo que tengan muchas excusas para no cambiarlo. Yo lo tengo, lo configure desde Red y con pppoeconf y listo, nunca mas un problema.

---

### Post by faktorqm on 2008-06-05
> **atari130xe said:**
> la verdad que no lo sé, pero podrias decirnos cual seria la mejor opcion para conectarse con estos modems? tks :)
PD Aclaro que no uso Router ni Conexion inhalambrica, solo la conexion "normal" linea tel. placa ethernet (única PC conectada)

La mejor es hacer que el modem routee, y te maneje el tema del marcador y del firewall. Asi tenes 2 software's menos corriendo sin razon en tu computadora y gastando (perdón, malgastando) recursos que bien podrias usar para otra cosa mejor. Otra ventaja por ejemplo, es la parte de la instalacion, directamente podes instalar todos los paquetes de idiomas y demas paquetes "bajables" desde el vamos sin necesidad de arrancar, configurar internet, luego seguir instalando. 

mauro7g: yo tengo ese, coincido plenamente en que es uno de los mejores modems, y yo es su epoca lo pagué 70 mangos. (los de speedy me ofrecian uno usb y les saque roja directa) pero no podemos pretender que todos los que tengan problemas con usb se pasen a ethernet.

santiagoward2k: te explico como se hace, llamas y ninguneas a la empleada/o que te atienda, hasta que te atienda un supervisor (intenta no insultarla/o). Luego de que el chabon/a te explica de que no te lo puede cambiar gratis, no tiene stock y etc le decis que directamente te cansaste y que lo queres sacar, que se lleven todo YA (se lo gritas) que arnet esta ofreciendo modems ethernet y flash cambio a cablemodem y que tb tiene modems ethernet. Vas a ver como cambian de opinion, o por lo menos van a perder un cliente valioso. (decile que trabajas en una radio o esas cosas y que no lo vas a recomendar a tus amigos). 

Bueno, ya esta contestado este thread, creo que no hace falta aclarar mas XD

---

