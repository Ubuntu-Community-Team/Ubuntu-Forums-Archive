---
title: "Que opinan de la privacidad con OpenDNS?"
date: 2010-09-16
forum: Comunidad
---

### Post by atari130xe on 2010-09-16
Desde ayer estoy teniendo problemas para navegar por cualquier página obteniendo un "sitio no encontrado...etc." con Firefox, probé con Google Chrome y dá igual, hoy decidí cambiar los servidores DNS de mi proveedor (Speedy) por los de OpenDNS, y googleando un poco para ver opiniones me encontré con este post, uds que opinan al respecto? (es del 2008 pero no sé que validéz tendrá hoy en el 2010)

[http://www.kriptopolis.org/adios-opendns]("http://www.kriptopolis.org/adios-opendns")

saludos!

---

### Post by guillermolisi on 2010-09-16
Lo mismo que en los casos de uso de Gmail, Facebook, Twitter, etc. Depende del grado de paranoia de cada uno y de las posibilidades alternativas.

Si tenes una alternativa mejor, usala, pero (como casi siempre) lo mas importante no es lo que se dice sino lo que NO se dice (por ejemplo que los DNS de tu ISP puedan estar haciendo lo mismo que OpenDNS pero de una forma mas oculta).

---

### Post by juancarlospaco on 2010-09-16
*FYI* ojo, OpenDNS rompe el protocolo DNS. :)

---

### Post by atari130xe on 2010-09-16
Gracias por las respuestas, no se porqué desde ayer navegar es un castigo con Speedy me refiero a que venia muy bien es más la velocidad de transferencia de datos (down y up) son muy buenas (casi 4MB) pero navegar es un problema, debo darle a "actualizar" para que carguen las páginas de manera correcta es raro que alguna cargue sin que no tenga que hacer eso.

---

### Post by guillermolisi on 2010-09-16
> **juancarlospaco said:**
> *FYI* ojo, OpenDNS rompe el protocolo DNS. :)
Sisi, ok, la pregunta entonces es "Que DNS puedo usar que efectivamente no haga lo que hacen los de OpenDNS ?"

Usar los de los ISP locales es lo mismo que nada. No rompen el protocolo pero tampoco resuelven.

Implementar un DNS propio ... si pero hay que montarlo, utilizar un enlace confiable, mantenerlo y hacer los tramites en nic.ar.

Nada de otro planeta, pero es la gran diferencia entre usar los que existen y usar uno propio.

---

### Post by alfplayer on 2010-09-16
Podés considerar los de Google también, que tenían muy buena latencia comparable a los de Speedy la última vez que lo verifiqué.

---

### Post by juancarlospaco on 2010-09-16
Google:
8.8.8.8
8.8.4.4

Root DNS Servers:
[http://en.wikipedia.org/wiki/Root_nameserver#Root_server_addresses]("http://en.wikipedia.org/wiki/Root_nameserver#Root_server_addresses")
*Esos 13 servers son los unicos que manejan los DNS de todo internet, el resto copia al vecino.*

---

### Post by josecuervo86 on 2010-09-16
No sabia de los de Google. Estaba usando OpenDNS en cambio de los de Speedy que apestan, pero tampoco note gran diferencia. En especial este foro me tarda siglos en cargar y eso que tengo 5 megas. Voy a ver que tal andan los de la gran G

---

### Post by alfplayer on 2010-09-16
Siempre me pareció muy rápido este foro.

Con Speedy, con Google DNS tenía latencias de aprox. 40 ms (cerca de los valores de Speedy), y con OpenDNS tenía valores de aprox. 200 ms. Una diferencia grande, como si los servidores de OpenDNS estuvieran en Estados Unidos.

---

### Post by alfplayer on 2010-09-16
> **juancarlospaco said:**
> Root DNS Servers:
Esos 13 servers son los unicos que manejan los DNS de todo internet, el resto copia al vecino.

Simplificado, no? :p

---

### Post by atari130xe on 2010-09-17
> **josecuervo86 said:**
> No sabia de los de Google. Estaba usando OpenDNS en cambio de los de Speedy que apestan, pero tampoco note gran diferencia. En especial este foro me tarda siglos en cargar y eso que tengo 5 megas. Voy a ver que tal andan los de la gran G

No sos el único al que le cuesta entrar a Ubuntuforums, a mi me demora mucho poder ingresar a este sitio, antes no me pasaba pero desde hace unos meses es muy problemático entrar y es más a veces se "cuelga" queda como "el servidor a superado el tiempo de espera" es raro... por cierto cambié a los DNS de Google a ver que onda, hasta ahora funcionan mejor que los de OpenDNS...

---

### Post by madbyte on 2010-09-18
Usando OpenDNS una vez entre a un sitio el cual voy a obviar su direccion, ya se imaginaran de que se trataba je, y no me lo abrio y en cambio me salio una pagina de OpenDNS que decia: TE ESTOY MIRANDO DESDE EL CIELO! NO DEBERIAS ENTRAR A ESTE SITIO! ja Cambie de IP y chau mensajito pero si agarras una IP que quedo con algun tipo de filtro te pueden pasar cosas 'raras'. Hace rato que uso los DNS de Google y hasta ahora no hay mensajito... jeje

Saludos.

---

### Post by atari130xe on 2010-09-18
> **madbyte said:**
> Usando OpenDNS una vez entre a un sitio el cual voy a obviar su direccion, ya se imaginaran de que se trataba je, y no me lo abrio y en cambio me salio una pagina de OpenDNS que decia: TE ESTOY MIRANDO DESDE EL CIELO! NO DEBERIAS ENTRAR A ESTE SITIO! ja Cambie de IP y chau mensajito pero si agarras una IP que quedo con algun tipo de filtro te pueden pasar cosas 'raras'. Hace rato que uso los DNS de Google y hasta ahora no hay mensajito... jeje

Saludos.

Uy yo tengo poca imaginación jajaja :P Mi problema parece ser de un equipo de Telefónica y hoy vinieron a ver que pasaba con la parte hard y averiguando parece que hay un equipo de enlace (sarasa supongo) que no funciona como debe, que en el plazo de 8 a 10 días debería estar resuelto, de todas formas cambié los DNS de OpenDNS por los de Google y noto que hay máyor velocidad de carga...veremos

---

