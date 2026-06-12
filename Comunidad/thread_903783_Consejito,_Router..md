---
title: "Consejito, Router."
date: 2008-08-28
forum: Comunidad
---

### Post by pol666 on 2008-08-28
Hola gente querida...  Les pido su consejo, tengo 2 pc, no estan en red, pero estoy en pos de hacerlo.. pense en la clasica pero deficiente conexion ethernet. Pero al ver los problemas que trae mas el trabajo extra que me lleva hacer el cableado, estoy pensando en comprarme un router, un linksys inalambrico tal vez?  Bueno por eso les pregunto. Saben... las dos pc tienen linux asi que no va  a tener drama. Quiero compartir datos, impresora e internet. Tambien aviso que tengo modem zyxel routeado, asi que no se si tengo que volver a la configuracion original para conectar otro router.

¿QUe tengo y que me recomiendan comprar?
¿Cuales son los pasos que debo hacer para llevar a cabo la red?
¿algun consejo de más? 


Saludos ;)

---

### Post by pol666 on 2008-08-28
Perdon,  lo quise poner en Hardware y se me chispotio aca sorry ^^#-o

---

### Post by marianom on 2008-08-29
Compra linksys que es lo mejorcito del mercado (aunque yo le tengo mucho cariño a netgear y me hubiera comprado uno si lo encontraba).

Si no querés cableado mucho me temo que vas a tener que ponerle placas wireless a ambas máquinas, de otra forma el router trae 4 bocas así que podes tener cableadas 4 y el resto por wireless...

más allá de eso... muchos consejos de seguridad para la red wireless (comprala y después los discutimos). Conectarla no es mucho secreto: el router al modem y de ahí a las máquinas: la administración y configuración es por navegador y es standard (aunque te dan un CD con todo automatizado ... que funciona con Vista y trae un antivirus por 30 días gratis... muy recomendable este CD para regalarselo a infantes)

---

### Post by pol666 on 2008-08-29
Y que placa wireless me anda 100% en linux'

Edito: Me senti un ignorante al no saber la diferencia entre wireless y wifi ^^, asi que google y ahora pregunto. SI yo me compro el linksys + las targetas correspondientes. Me sirven el dia de mañana para cuando yo tenga una portatil? (de aca a unos años, tal vez)

osea, voy a poder entrar en la red como cualquier conexion wi-fi publica que podria agarrar?

Pregunta estupida jaj

---

### Post by lega on 2008-08-29
yo pregunte por una tarjeta wireless pci linksys en Mercado Libre y me dijeron que no son compatibles ( no busque demasiado/nada en la web tampoco) pero averiguá antes así no renegas, con el router no vas a tener problemas.

---

### Post by faktorqm on 2008-08-29
Yo te recomendaria que te compres un switch noganet de 50 pesos de 8 bocas, tires 2 cables y se termino el problema.
Desde ya te aviso que vas a tener que reconfigurar por que en la tabla nat pusiste lo que quisiste y si pones 2 pc's no te va a andar, mejor dicho, te va a andar una sola. Salu2!

---

### Post by pol666 on 2008-08-29
ya lo puse igual que me habias mostrado vos.......

lo que quiero es simple, algo que me sirva wi-fi, con alcanze de 30mt (las pc estan a menos de 10 pero mi casa tiene 30, y pretendo que llegue ¬¬) y que ande en ubuntu sin nada raro.

como soy ignorante llano del tema, no tengo ni idea que tengo que comprar y si me dicen que conecte una papa con una antena al modem me lo creo :P

---

### Post by victor_nesta on 2008-08-30
Por lo que leí, los chips ¨atheros¨ se llevan bien con linux, hay una marca que conozco que las usa bastante que es TP-LINK, y tienen PCI o USB.

Respecto al router, una vuelta tuve que hacer una conexión de 4 pcs (todas Win) y use un linksys (ya me acordare el modelo) y funciono de prima.
Por la distancia no te preocupes, te compras una antenita mas copada y listo. Al tipo este una pc estaba atravesada por varias paredes y un piso de distancia, y le metí una antena de 9db y se le acabo el problema. Igual exagere, en el caso de no tener mucha potencia con una de 5db te tiene que sobrar y salen 40 mangos.

Sobre los aspectos técnicos WEP / WPA / WPA2 en linux, ni idea, se los dejo a los que saben..

---

### Post by marianom on 2008-08-30
> **victor_nesta said:**
> Sobre los aspectos técnicos WEP / WPA / WPA2 en linux, ni idea, se los dejo a los que saben..

No hay mucho misterio por lo menos en mi experiencia: yo tengo una placa wireless externa en mi Toshiba (o sea una máquina vieja) y Ubuntu HH anduvo sin problemas ni configuración adicional con WPA2 (de entrada creí que se iba a complicar porque vi algunas páginas donde describían algunos procesos medianamente complejos de configuración pero a mi no me funcionó perfecta de una).

---

### Post by faktorqm on 2008-08-30
Este tema lo hablé con Lisi en las JRSL, hay algunos chipsets de placas que no soportan WPA2 por hardware, y al parecer en windows si la placa no lo soporta, no lo podés hacer. yo tuve que poner wpa solo en una notebook con placa avaya wi-fi -> pcmcia por que no reconocia wpa2. 
de todas maneras yo pienso que eso se puede hacer por software, a un costo un poco alto, pero se puede. capaz alguien en gnu/linux ya lo hizo y esta todo ok. sera cuestion de jugartela, o sea, lo que tenes que hacer es averiguar si la placa soporta por hardwre wpa2, si la soporta averiguar si anda en gnu/linux, y de router creo que con el wrt64g no vas a tener dramas. Salu2!

---

### Post by excaliburs on 2008-09-06
yo tengo un d-link al que se conectan, 1 pc y 1 portatil con win y mi querida toshiba satellite con ubuntu y ningun problema.....no hay configuraciones raras que hacer para que la red funcione....a lo sumo tendrars que configurar las placas inalambricas de cada pc en el caso de que las instales.....pero no es tan terrible....en el ultimo de los casos [www.metacrawler.com](www.metacrawler.com) resuelve la mayoria de los problemas...o san google, dependiendo de los gustos de cada uno....
saludos y suerte con tu red

---

### Post by guillermolisi on 2008-09-06
Noganet no lo recomendaria ni a mi peor enemigo.

Linksys son buenos, tienen muy buen soporte local (conozco un caso que fue un tecnico a la casa del cliente y le hizo toda la configuracion del equipo y la red for free). Peeeero, no me gusta su filosofia privativa, sobre todo cuando antes permitian que uno actualizara el firmware por uno alternativo libre y a partir de cierto modelo le achicaron el tamaño de la RAM para que esos firmwares no se pudieran cargar, por lo menos por ahora).

En general uso D-Link, tanto routers como placas, y hasta ahora no tuve problemas de ninguna clase.

Lo que comenta Faktor me paso con maquinas de cierta antiguedad, particular y ultimamente con una eBook G3 y antes con notebooks de cierta antiguedad (primeros modelos con WiFi).

En todo caso consulta este site para mas informacion:

[http://linuxwireless.org/](http://linuxwireless.org/)

---

