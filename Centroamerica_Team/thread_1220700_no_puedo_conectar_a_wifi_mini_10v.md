---
title: "no puedo conectar a wifi mini 10v"
date: 2009-07-23
forum: Centroamerica Team
---

### Post by adrianlancer on 2009-07-23
Acabo de comprar una dell mini 10v lo primero ke hice fue instalarle el ubuntu remix 9.04 jajaja ni lo pense. bueno el problema es el siguiente mientras lo probaba corriendo live desde el usb todo anduvo bien conecto al wifi sin prob. instale usando la particion ext3 por accidente luego volvi a instalar usando ext4 y ahora no conecta. Detecta la red sin problemas y la potencia de la misma pero no se conecta. ahora viendo en los controladores vi ke el controlador inalambrico broadcom STA apacere como activo, tiene un msj ke dice ke esta comprobado por los desarrolladores de ubuntu y su licencia es privativa. no se  ke hacer les agradesco cualkier ayuda.

---

### Post by adrianlancer on 2009-07-23
hoy se logro conectar a la red de mi casa pero demora un monton para cargar las paginas, encima de eso creo ke la velocidad de descarga mas rapida ke llego fue 8 kbps y de subida 1 o 2 kbps trate de usar el drver generico y daba los mismos resultados.me conecte por medio de cable al router e hice las acutalizaciones disponibles en el gestor de actualizaciones y ni aun asi tiene mejoras... no kiero usar windows  :(:( auxilio!

---

### Post by eivar on 2009-07-23
hola adrianlancer no comprendo, dices que cuando le instalaste con ext3 si funcionaba todo bien???

Tienes que dar más detalles sobre tu hardware:
* las caracteristicas de la dell mini.
* datos de la tarjeta de red, como: modelo y fabricante.

Ya que lo mencionas dinos también más datos sobre el controlador instalado, por ejemplo la versión.

Saludos.

---

### Post by adrianlancer on 2009-07-25
> **eivar said:**
> hola adrianlancer no comprendo, dices que cuando le instalaste con ext3 si funcionaba todo bien???

Tienes que dar más detalles sobre tu hardware:
* las caracteristicas de la dell mini.
* datos de la tarjeta de red, como: modelo y fabricante.

Ya que lo mencionas dinos también más datos sobre el controlador instalado, por ejemplo la versión.

Saludos.

hola,
no lo que digo es que no conecta el wireless, entonces les echo el cuento denuevo pero con un par de detalles nuevos.
compre una dell mini 10v todo funciona excelente hasta ahora, excepto conectarme a la red inalambrica de mi casa, fui a la casa de un amigo y funciono perfectamente. es mas pude aprovechar su banda ancha casi al maximo. en mi cas no llega ni a 5 kbps  ni de subida ni bajada al parecer segun he leido a otra persona ke tuvo un problema similar parece ser el router asi ke por ahora estoy encaminando mi investigacion al router que por cierto es un TP-Link y suckea de gran manera :( bueno si encuentro algo les aviso y al parecer no es el dispositivo de red gracias eivar por la respuesta

---

### Post by Nugar on 2009-07-27
Hola adrianlancer,

Con el permiso de los mods, porque esto que estoy a punto de hacer es casi que threadjacking...

Te recomiendo que consigas un Linksys WRT54G. Cuando lo encuentres para comprarlo (aqui en Panama lo consigues por alrededor de $60 o $70), fijate que tenga antenas desmontables.

Luego le haces un flash y le instalas dd-wrt, una distribucion de Linux especial para eso y tendras un router con las funciones de uno de $600.

Hay otros que funcionan. Lamentablemente, busqué y al TP-Link no se le puede hacer.

Espero que esto te ayude!

Saludos,

Nugar

PD. Me fije en el WRT54G2, que esta muy cool y le puedes hacer esa instalacion tambien. (Y esta en $60)

---

### Post by adrianlancer on 2009-07-27
> **Nugar said:**
> Hola adrianlancer,

Con el permiso de los mods, porque esto que estoy a punto de hacer es casi que threadjacking...

Te recomiendo que consigas un Linksys WRT54G. Cuando lo encuentres para comprarlo (aqui en Panama lo consigues por alrededor de $60 o $70), fijate que tenga antenas desmontables.

Luego le haces un flash y le instalas dd-wrt, una distribucion de Linux especial para eso y tendras un router con las funciones de uno de $600.

Hay otros que funcionan. Lamentablemente, busqué y al TP-Link no se le puede hacer.

Espero que esto te ayude!

Saludos,

Nugar

PD. Me fije en el WRT54G2, que esta muy cool y le puedes hacer esa instalacion tambien. (Y esta en $60)

voy a buscar  gracias

---

### Post by adrianlancer on 2009-10-24
bueno al parecer el driver privativo no funciona bien con redes WEP segun encontre en internet no se ke website, la cuestion fue que cambie a WPA y todavia estaba jodido entonce cambie al canal 11 y al parcer funciona ahora si y estoy escribiendoles desde la mini 10v o 1011 como la conoscan :D

---

### Post by Nugar on 2009-10-25
¡Felicidades, Adrian!

Se siente bien cuando uno resuelve el asunto ¿eh?

Saludos,

---

### Post by adrianlancer on 2009-10-26
ohhh si que siii jajajaja ya puedo usar la compu en la paz de mi cuarto jajajaja  la sala tiene muchas distracciones

---

### Post by Nugar on 2009-10-26
Y encima se dan cuenta de TODO lo que estas viendo! JAJAJJAA

---

