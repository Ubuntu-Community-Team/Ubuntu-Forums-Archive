---
title: "Actualizando la PC...."
date: 2008-05-27
forum: Comunidad
---

### Post by fgl82 on 2008-05-27
Buenas!

Resulta que estoy pensando en actualizar mi PC a un AMD X2 de 4600, con uno o dos GB de RAM.

Pero me encuentro con un escollo: actualmente mi PC usa una placa de video AGP, dado que es un Athlon XP de 2400 de la época de cuando no existía el PCI Express. 

En principio, con esta actualización, perdería la posibilidad de usar mi plaquita AGP que tanta satisfacción me ha dado andando "out of the box" con Ubuntu.

Inicialmente, estaría usando la placa de video integrada que venga con el mother en cuestión, dado que no quiero gastar plata por el momento en una placa PCIE.

Por tanto, mi pregunta es (finalmente!!! :lolflag:), ¿qué placa integrada anda mejor con ubuntu? Las Nvidia 6100 se ven tentadoras pero no sé si Ubuntu (o incluso COMPIZ) funciona bien con ellas. Por otro lado están los mothers con placas VIA o Intel... Estoy medio perdido y bueno, antes de comprar, quería consultar acá.

¡Saludos y gracias!

---

### Post by faktorqm on 2008-05-27
Yo tengo en el laburo una ECS horrible con nvidia 6100, y un sempron 3000 creo... pero me dieron 256mb de ram ddr2.... si ustedes pensaban que no existian memorias tan chicas para ddr2... existen!!! :@
La placa de video va mas que mejor, y con los ultimos drivers. tiene chipset nforce4 y me reconocio absolutamente todo sin tocar nada. solo que tengo poca memoria, y si le doy a la placa mas de 64mb de ram... ubuntu se arrastra. es mas, estaba pensando aca si ponerme fluxbox :S pero bueno. la 6100 para aguantar esta bien, si te compras 2gb  de ram y le mandas 512 a la placa no vas a tener ningun drama. slau2!

---

### Post by fgl82 on 2008-05-27
> **faktorqm said:**
> Yo tengo en el laburo una ECS horrible con nvidia 6100, y un sempron 3000 creo... pero me dieron 256mb de ram ddr2.... si ustedes pensaban que no existian memorias tan chicas para ddr2... existen!!! :@
La placa de video va mas que mejor, y con los ultimos drivers. tiene chipset nforce4 y me reconocio absolutamente todo sin tocar nada. solo que tengo poca memoria, y si le doy a la placa mas de 64mb de ram... ubuntu se arrastra. es mas, estaba pensando aca si ponerme fluxbox :S pero bueno. la 6100 para aguantar esta bien, si te compras 2gb  de ram y le mandas 512 a la placa no vas a tener ningun drama. slau2!

¿Por qué 512?

Mi idea era darle 64 o 128 nomás...

¿Va muy mal con 64?

---

### Post by faktorqm on 2008-05-27
No va mal con 64, pero se te queda sin memoria el compiz capaz y si tenes mas de 15 ventanas abiertas como suelo tener yo te empiezan a desaparecer los bordes, o te muestra pantallas en negro, y esas cosas. Ponele 128mb y proba, sino ponele 256mb. 
Aparte vamos al hecho "crudo", cuando vas a usar 1536mb de ram si le pones 512 a la placa? o 1792mb si usas 256? a mi me parece que en contadas ocasiones vas a tener la memoria tan saturada... 
Salu2!

---

### Post by fgl82 on 2008-05-27
> **faktorqm said:**
> No va mal con 64, pero se te queda sin memoria el compiz capaz y si tenes mas de 15 ventanas abiertas como suelo tener yo te empiezan a desaparecer los bordes, o te muestra pantallas en negro, y esas cosas. Ponele 128mb y proba, sino ponele 256mb. 
Aparte vamos al hecho "crudo", cuando vas a usar 1536mb de ram si le pones 512 a la placa? o 1792mb si usas 256? a mi me parece que en contadas ocasiones vas a tener la memoria tan saturada... 
Salu2!

ok, gracias por describir los problemas :)

no es porque se me sature la memoria, pero más que nada una cuestión de "principios" :P, no me gusta darle más memoria de la que realmente merece al video on board.

¡¡Gracias una vez más por la rta!!

pd: eso si, yo no suelo tener 15 ventanas abiertas.

---

### Post by guillermolisi on 2008-05-27
> **fgl82 said:**
> Buenas!

Por tanto, mi pregunta es (finalmente!!! :lolflag:), ¿qué placa integrada anda mejor con ubuntu? Las Nvidia 6100 se ven tentadoras pero no sé si Ubuntu (o incluso COMPIZ) funciona bien con ellas. Por otro lado están los mothers con placas VIA o Intel... Estoy medio perdido y bueno, antes de comprar, quería consultar acá.

¡Saludos y gracias!

VIA noooo !! Por lo menos por ahora y hasta dentro de un tiempito, VIA no.

Entre Intel y nVidia, esta ultima cualquiera sea el modelo, sin duda.

Coincido con Faktor, si ya tenes el recurso, usalo a fondo. Ya lo pagaste y no se gasta por usarlo :-)

---

### Post by Dan_Dranath999 on 2008-05-27
Pues se supone que las placas Intel son las que soportan mejor Linux a día de hoy, no?  (Aunque yo con la MSI para cpu AMD Athlon nunca he tenido problema)

---

### Post by Mauro22 on 2008-05-27
Yo tengo el mother Gigabyte con la Geforce 6100 onboard y todo los chipset de nvidia tambien.

Anda todo al pelo :D

La 6100 se nego a andar, pero entre EnvyLG y el "controladores de hardware restingidos" con un par de veces de instalacion/desinstalacion, quedo de 10 !!

con compiz y toda la bola...

```

name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
[...]
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 6150SE nForce 430/PCI/SSE2/3DNOW!
OpenGL version string: 2.1.2 NVIDIA 169.12

```

---

