---
title: "www.google.com.ar (¿les funciona?)"
date: 2008-08-20
forum: Comunidad
---

### Post by atari130xe on 2008-08-20
Desde hace 3 días no puedo acceder o lo hago aleatoriamente a [www.google.com.ar](www.google.com.ar) (lo tengo como pagina de inicio en Firefox), ¿es algo que me está pasando a mí? ¿o es algo que está pasando a todos? la única manera de poder entrar al buscador de Google es tipeando por ej.: .cl (Chile) o .ca (Canada), llamé a Speedy porque tmb noto que anda muy lento, y me dijeron que tenia "seteado" el servicio a 512k jejeje (pago por 2.5MB) si le pasa a alguien lo de Google me gustaria saberlo por favor, gracias como siempre :)

---

### Post by pol666 on 2008-08-20
a mi me anda bien, lo unico que recien me quise meter en cualquier pagina y me salian mensajes de speedy que decia que mi pc estaba desprotegida que llame para comprar Mc Affe antivirus JAJAJAJAJAJAJAJAJAJAJAJ

---

### Post by valucha on 2008-08-20
> **pol666 said:**
> a mi me anda bien, lo unico que recien me quise meter en cualquier pagina y me salian mensajes de speedy que decia que mi pc estaba desprotegida que llame para comprar Mc Affe antivirus JAJAJAJAJAJAJAJAJAJAJAJ+


[COLOR="DarkOrchid"]
JAJAJAJAJAJA!...


Yo aveces tampoco puedo entrar a google, pero a ningún google, me dice "Listo" y no veo nada.
Me pasa tanto en Win2 con Firefox, y en Ubuntu con Firefox, tenía miedo de que sea Fibertel, pero capaz que es algo de....... Google?! :|[/COLOR]

---

### Post by luks911 on 2008-08-20
Puedo entrar sin problemas. ¿Probaste cambiando los DNS?

---

### Post by atari130xe on 2008-08-20
> **luks911 said:**
> Puedo entrar sin problemas. ¿Probaste cambiando los DNS?

Esto me está pasando desde hace unos días es raro nunca antes me había pasado, hoy llamé (hace 2hs) a Speedy lo único que me "confirmaron" es que tenía "asignada" una velocidad de 512Kb en lugar de 2.5mb que es por lo que pago. Leí por ahi que Google Argentina tuvo problemas el Domingo pasado con lás búsquedador, sigo probando ahora mismo y se demora una enormidad si quiera en conectar con el servidor y tampoco logra entrar... No cambié los DNS todavía.

---

### Post by leo_rockway on 2008-08-20
A mí me funciona perfecto.

Se puede usar el servicio de Down for everyone or just me [0] para ver si la página está caída o si ustedes son los del problema.

[0] [http://downforeveryoneorjustme.com/](http://downforeveryoneorjustme.com/)

---

### Post by InsektO on 2008-08-20
A mí esporádicamente me pasa que no me funciona Google. En realidad, se resuelve bien evidentemente, pero no carga nada, queda en blanco la página en el navegador y te dice "Listo"... :/

Por casualidad tenés FiberTel?

Por cierto, yo probé cambiando los DNS y no me ayudó mucho.

---

### Post by anka on 2008-08-20
Hoy le paso a uno de nuestros clientes enfrente mio, imposible meterse a google, con fibertel, yo en casa sin problemas.

No se que sera, de paso.., cambio la pagina de yahoo.., se vendra algo por parte del gigante con g de gato gordo? :P

Saludos!

---

### Post by vampichoke on 2008-08-21
yo tengo speedy.. 

y si estos ultimos... 4 dias 
arranco la pc carga automaticamente el screenlet del weather y mi pagina de inicio de firefox (google) 

y .. si a veces salta listo o no se pudo comunicar con la pagina... 


no me preocupe puesto q el wheater cargo al instantes solo actualizo un par de veces y aparece... deben ser los dns de nuevo...

---

### Post by niko_3100 on 2008-08-21
Miren muchachos vamos a ser sinceros no creo que sea problemas de google sino de sus proveedores de internet, google es perfecto sepanlo!!! jajaja!!!

---

### Post by guillermolisi on 2008-08-23
Yo tengo Fiber 2Mb y desde Marzo vengo con problemas con los DNS de esta bendita empresa.

Para poder entrar a los servicios de Google (Gmail, Google, Fotologs, etc.) termine agregando (prepend) DNSs de OpenDNS en la maquina que corre Ubuntu y es el gateway a Internet de las otras que tengo en casa. Asi y todo no siempre carga de primera intencion los sitios.

Si a alguien le interesa como hacerlo que chifle y le paso el tip.

Como tambien tengo PCs con XP (por cuestiones laborales de otros miembros de mi familia) edite el archivo hosts y las urls de Google se resuelven localmente, asi me desentiendo del problema de Fibertel y en casa no me molestan porque no pueden conectarse a esos servicios.

---

### Post by sergiom99 on 2008-08-31
guillermo, como hiciste?
en el router tengo como dns estaticos los opendns y a partir de ayer en la laptop con kubuntu tambien.
sin embargo no puedo abrir nada de google ni winehq.

update: lo raro es que en la desktop con XP si puedo entrar sin ningun problema a ambos.

---

### Post by guillermolisi on 2008-08-31
> **sergiom99 said:**
> guillermo, como hiciste?
en el router tengo como dns estaticos los opendns y a partir de ayer en la laptop con kubuntu tambien.
sin embargo no puedo abrir nada de google ni winehq.

update: lo raro es que en la desktop con XP si puedo entrar sin ningun problema a ambos.
En las maquinas con XP edite el c:/WINDOWS/System32/drivers/etc/hosts y les agregue las direcciones IP de los servicios de Google que se usan (Gmail, Google.com o Google.com.ar, etc.)
Como no tengo router porque uso una PC con Kubuntu como gateway a Internet, en esa misma edite el archivo /etc/dhcp3/dhclient.conf y edite la linea que empieza con:
```
prepend
```Me quedo asi:
```
prepend domain-name-servers 208.67.222.222, 208.67.220.220;
```De esta forma cada vez que el ISP te renueva la direccion IP y se referscan las IPS de los DNSs lo primero que agrega son las IPs de openDNS y luego los del ISP.

Igual he observado que cuando hay mucha demanda de ancho de banda de Fibertel en la zona donde estoy la respuesta de requerimientos a Internet es erratica con lo cual se me ocurre que deben tenr mas de un problema en los DNSs.

Cuando no hay demanda exagerada, es decir fuera de los horarios pico, anda bastante bien todo.

Se me ocurre que en tu caso deberias revisar que los DNSs de openDNS figuren como los primeros, asi solo vas a los de Fiber cuando esos fallan.

Ahh... y por las dudas, me registre en openDNS.

No se si respondi tu pregunta.

---

### Post by sergiom99 on 2008-08-31
si, todo esto lo hice en la notebook (son las instrucciones de openDNS) pero sigo sin google. tuve toda la tarde desconectado el cablemodem para volver a enganchar nueva IP, y nada. La PC con Windows funciona perfecto y navego por todos lados con los DNS predeterminados.

hay algun comando para vaciar la cache de dns o algo por el estilo?

---

### Post by guillermolisi on 2008-08-31
Un detalle que me olvide mencionar: En la PC que oficia de gateway tengo instalado y operativo Bind9 (DNS server), configurado simple y basicamente.

Probe en otra PC de la misma LAN que corre Ubuntu 8.04 server, sin Bind9, y no logro en estos momentos ver paginas de Google en esa maquina. En ese server no toque el contenido de /etc/hosts.

Mañana a la mañana pruebo, que hay mas ancho de banda disponible, y comento.

---

### Post by sergiom99 on 2008-08-31
despues de estar chateando media hora con los inutiles de soporte  de fiber, que obviamente dicen que no pasa nada y esta todo bien y no tienen nada reportado, logre zafar por ahora.
Como tampoco me funcionaba usando los openDNS, lo que hice fue fijarme en un server remoto que DNS de fiber tiene, porque no habia problemas para entrar a google ahi.
Y en el paso que me paso guillermo arriba lo agregue y por ahora puedo entrar en google:
```
 prepend domain-name-servers 200.49.130.25,208.67.222.222,208.67.220.220;
```

internet sin google, como dijo el diego="me cortaron las piernas"

---

