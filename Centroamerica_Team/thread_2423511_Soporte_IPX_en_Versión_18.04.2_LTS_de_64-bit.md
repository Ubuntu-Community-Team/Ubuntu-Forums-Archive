---
title: "Soporte IPX en Versión 18.04.2 LTS de 64-bit"
date: 2019-07-24
forum: Centroamerica Team
---

### Post by achiaramello on 2019-07-24
Buenas tardes.
Les comento mi inconveniente: 
En la empresa hay montada una red NOVELL con protocolo IPX, Necesito acceder a estos servidores desde Ubuntu 18.04 pero solo me falta el soporte IPX en el kernel, ya tengo instalado NCPFS pero cuando ejecuto ipx_configure para darle los lineamientos a la interface de red me dice: "ipx_configure: zócalo: Esta familia de direcciones no está soportada por el protocolo" lo cual me da a entender que el KERNEL que uso no tiene el modulo IPX instalado. La version del kernel  4.18.0-25-generic x86_64.
Alguien tiene idea como podre hacer para agregar este modulo al kernel?
Gracias !

---

