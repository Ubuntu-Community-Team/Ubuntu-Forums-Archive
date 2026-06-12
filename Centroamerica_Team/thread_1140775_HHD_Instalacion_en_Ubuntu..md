---
title: "HHD Instalacion en Ubuntu."
date: 2009-04-27
forum: Centroamerica Team
---

### Post by panafff on 2009-04-27
Que tal gentes, la verdad es que soy nuevo en el mundo de Ubuntu y me encanta. Disculpen la ignorancia pero tengo una peque;a pregunta en cuanto a la instalacion de un nuevo disco duro, voy a instalar proximamente en mi computadora un Maxtor 160GB DiamondMax 21, no se la verdad si mi Ubuntu (9.04) lo va a detectar automaticamente o hay cosas que tengo que saber para poder instalarlo, cualquier ayuda se apreciara. 
 
*Busque en la documentacion Online de Ubuntu pero no logre encontrar ningun topico relacionado a mi pregunta (al menos no todavia).
 
Saludos!:lolflag:

---

### Post by meldon12 on 2009-04-28
No hay problema panafff, recuerda que ubuntu se caracteriza por la gran comunidad y la buena voluntad de muchas personas por ayudar.

Volviendo al tema, si lo deberia detectar en caso de que ya venga con formato ntfs o fat32, si no te lo detecta entonces le tienes que dar formato y hariamos lo siguiente:

En la terminal escribes:
> sudo apt-get install gparted

Esperas a que termine de bajar e instalar (facilísimo sin nada de next next !!). Ahora te vas al menú Sistema >> Administración >> Editor de Particiones. Entonces se abrirá la ventana de gparted y te vas a la esquina superio derecha donde aparecera el disco duro principal algo así como /dev/sda, le das click para que despliegue la lista y escojes la particion de tu nuevo disco duro aún virgen, luego en la parte de arriba del gparted le das a Nuevo (si no me equivoco) y escoges el tipo de formato que le quieras dar, ntfs en caso de compartirlo con windows o ext3 si solo lo vas a usar con ubuntu, luego de eso esperas a que termine de darle formato y LISTO !!!

De todos modos te una guía mucho mas detallado con imágenes y todo:

[http://www.configurarequipos.com/doc719.html](http://www.configurarequipos.com/doc719.html)

Espero haberte ayudado, recuerda contar como te fue.

Saludos,

meldon12

---

### Post by eivar on 2009-04-29
Hola panaff,
bueno ya meldon te ha dado una respuesta muy completa, recuerda comentarnos que tal te fué y si tienes más dudas o manuales no dudes en colocarlos en el foro.

Saludos.

---

### Post by panafff on 2009-04-29
Hey gracias por la informacion a ambos. Ese website me ha sacado de varios lios ahora que me lo mencionas, gracias.
Aun no compro el Disco Duro, asi que en cuanto lo haga les cuento a ver que onda.
Como soy nuevo en Ubuntu actualmente estoy aprendiendo a utilizar el command line...ya he instalado actualizaciones y programas y he editado algunas cosas mas, es un vicio al comienzo no?
 
La verdad regare la voz para que mas gente se una al mundo Linux y al foro Ubuntu Panama loco team.

---

