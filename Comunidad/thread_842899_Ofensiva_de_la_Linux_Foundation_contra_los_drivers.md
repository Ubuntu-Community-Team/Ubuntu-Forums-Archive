---
title: "Ofensiva de la Linux Foundation contra los drivers propietarios"
date: 2008-06-27
forum: Comunidad
---

### Post by Hei Ku on 2008-06-27
Vuelvo a repetir el post aca, para no desvirtuar thread de otros foros que son mas practicos.

> De acuerdo a los desarrolladores del kernel, los cuelgues por culpa del driver propietario de NVidia estan en el top 10 de manera constante. De hecho, mas de 130 firmaron una carta pidiendo que todos los fabricantes de hardware abran sus drivers de una buena vez. [https://www.linuxfoundation.org/en/Kernel_Driver_Statement](https://www.linuxfoundation.org/en/Kernel_Driver_Statement)
Es una acusacion directa a NVidia, que ya dijo que no va a abrirlos, porque "asi como estan, andan bien".
Hay un ensayo que cuenta la historia de los drivers de video de los 3 fabricantes mas importantes, Intel, ATI y NVidia, y le pega con un caño a este ultimo. [https://www.linuxfoundation.org/en/Linux_Graphics_Essay](https://www.linuxfoundation.org/en/Linux_Graphics_Essay)

Asi que, la proxima vez que pregunten que placa comprar, piensen a quien le dan su plata. Y que eso de que "mientras ande, no me importa si es libre" tiene sus consecuencias.

Para los que no leyeron el articulo, particularmente el ultimo. Cuenta como Intel y ATI abrieron sus drivers y lo que esto les significo en mejoras tecnicas y de performance. Y como ATI va a ser la primer empresa en mostrar el pingüinito en la caja de sus tarjetas.

Ademas, entre ATI e Intel representan mas del 70% del mercado y creciendo, mientras NVidia tiene menos de 1/4 y esta a la baja. O sea, hay razones tecnicas y economicas para abrir los drivers, más alla de las razones de principios y filosofía, que también son importantes. Esto es para los que dicen que no se puede, o que no nos van a prestar atención.

---

### Post by MeduZa on 2008-06-28
> **Hei Ku said:**
> Vuelvo a repetir el post aca, para no desvirtuar thread de otros foros que son mas practicos.



Para los que no leyeron el articulo, particularmente el ultimo. Cuenta como Intel y ATI abrieron sus drivers y lo que esto les significo en mejoras tecnicas y de performance. Y como ATI va a ser la primer empresa en mostrar el pingüinito en la caja de sus tarjetas.

Ademas, entre ATI e Intel representan mas del 70% del mercado y creciendo, mientras NVidia tiene menos de 1/4 y esta a la baja. O sea, hay razones tecnicas y economicas para abrir los drivers, más alla de las razones de principios y filosofía, que también son importantes. Esto es para los que dicen que no se puede, o que no nos van a prestar atención.

Me lo lei todo al articulo, la verdad que nvidia son unos nabos lo tienen al ejemplo en sus propias caras y no lo ven, ATI (ahora AMD) no es tonto y si a intel le funco le van a echar caña a eso.
Creo que mi proxima placa de video va a ser una ATI, siempre y cuando ande bien como las nvidia, a mi me andan de 10 las nvidia, no entiendo porque las ATI siempre hacen lio para andar, a mi me gustan mas las ATI pero uso NVIDIA por eso mismo.

Si sacaran un driver de ATI como el de Nvidia me paso de nuevo a ATI sin dudarlo y mas si es open source.
otra cosa, el nuevo chipset que saco ATI esta espectacular, es increible lo bien que anda y lo escalable que es, probado en HH anda 20 puntos, aun no acelera video HD creo, pero eso es un punto gris en todo esto, espero en el futuro el driver tenga la misma calidad o funcionalidad que los de windoes
El tiempo lo dira como siempre!

---

### Post by anka on 2008-06-28
A esto hay que sumarle a Via, con sus ultrareincompatibles chips, que empiezan a ser liberados de a poco (muy de a poco parece), pero algo es algo.

Las emprezas deberias de darse cuenta que abriendo las especificaciones tienen (minimo) una plataforma de testers dispuestos a mejorar el producto, bajan los costos y posiblemente aumenten la curva de innovacion y mejoras (decenas de miles de personas diciendo: "estaria mejor esto.."). Sin contar que entrarian plenamente al mercado Linux (algun dia dejare de preguntar si tiene chips intel para ver que es compatible con Linux)

El anuncio de Via es [este]("http://linux-foundation.org/weblogs/news/2008/04/09/eweek-via-to-open-up-its-devices/") y la seccion de Via para Linux es [esta]("http://linux.via.com.tw")

---

### Post by _kAz_ on 2008-06-30
> **MeduZa said:**
> Me lo lei todo al articulo, la verdad que nvidia son unos nabos lo tienen al ejemplo en sus propias caras y no lo ven, ATI (ahora AMD) no es tonto y si a intel le funco le van a echar caña a eso.
Creo que mi proxima placa de video va a ser una ATI, siempre y cuando ande bien como las nvidia, a mi me andan de 10 las nvidia, no entiendo porque las ATI siempre hacen lio para andar, a mi me gustan mas las ATI pero uso NVIDIA por eso mismo.


> **anka said:**
> A esto hay que sumarle a Via, con sus ultrareincompatibles chips, que empiezan a ser liberados de a poco (muy de a poco parece), pero algo es algo.


Jajaja yo tengo una placa de video ATI y una motherboard VIA... con las apreciaciones que acaban de hacer, ESTOY AL HORNOOOOO!!!!:lolflag:

Fuera de chiste... ultimamente se me está colgando Ubuntu, en un momento pensé que era el Firefox, pero con otros browsers me pasaba igual; después pensé que era el plugin de flash cuando navegaba, pero los ultimos cuelgues fueron sin estar abierto el browser; en definitiva no me queda otra que pensar que es algun conflicto con la placa de video (o sus drivers). :(

---

### Post by niko_3100 on 2008-06-30
Desintalale el powernowd  a ver si se te sigue colgando.

---

### Post by _kAz_ on 2008-06-30
> **niko_3100 said:**
> Desintalale el powernowd  a ver si se te sigue colgando.

Perdón la ignorancia... pero para qué sirve el powernowd y de dónde lo desinstalo?

---

### Post by Hei Ku on 2008-06-30
es un paquete mas, y sirve para hacer el control de energia. Segun vi, con Gnome se lleva para atras, al menos en Ubuntu.

---

### Post by niko_3100 on 2008-07-01
Tal cual, lo que hace es regular el clock del procesador dependiendo su uso. En mi sempron varia de 800, a 1800 y 2000, 2200 mhz esas frecuencias, pero experimentaba cuelgues onda... pantalla congelada y nada funcionaba, desintale eso por probar algo y ahora no se me cuelga.

---

### Post by _kAz_ on 2008-07-01
> **niko_3100 said:**
> Tal cual, lo que hace es regular el clock del procesador dependiendo su uso. En mi sempron varia de 800, a 1800 y 2000, 2200 mhz esas frecuencias, pero experimentaba cuelgues onda... pantalla congelada y nada funcionaba, desintale eso por probar algo y ahora no se me cuelga.

Eso es mas o menos lo que me pasa, no hay combinación que la saque del letargo, ni Ctrl+Alt+Bckspce ni Ctrl+Alt+F4 ni el famoso Alt+Print sostenido (que despues apretas supuestamente RSEUB o algo así).

Ayer tuve alta bronca con un cuelgue porque perdi medio trabajo práctico que estaba haciendo en el peor momento, ergo me quede libre en esa materia :(

Ya desisntalé el paquete ese, ojalá funcione porque sino me tendré que volver a Windows, o a Kubuntu 7.10 que nunca se me colgó así.

Ojalá que estos empiecen a ser problemas del pasado si se liberan todos los drivers y podemos contar con los originales de cada placa.

---

### Post by Hei Ku on 2008-07-27
Atheros libero y planea incorporar al kernel de linux el driver de sus placas 802.11n.

[http://madwifi.org/wiki/news/20080725/ath9k-atheros-unveils-free-linux-driver-for](http://madwifi.org/wiki/news/20080725/ath9k-atheros-unveils-free-linux-driver-for)

Broadcom y NVidia, los estamos mirando!! :)

---

