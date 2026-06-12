---
title: "A todos los que tengan instalado Hardy"
date: 2008-05-23
forum: Comunidad
---

### Post by WanderingKnight on 2008-05-23
Habiliten el repositorio hardy-proposed y updateen el kernel.

Motivo: [este](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/188226) bug, que más que bug es pifiada, y que degrada bastante la experiencia del usuario de desktop. Antes de updatear a Hardy, podía ver videos en 720p (la gama "media" de High Definition) sin problema alguno simplemente reniceando mplayer, pero luego de pasar a Hardy empezó a andar trabado. De la misma manera, se notó una baja general en la performance de la UI.

Por eso, lo que recomiendo a absolutamente TODOS es que updateen el kernel. Para hacerlo simplemente tienen que agregar estas dos líneas al /etc/apt/sources.list:

```
deb http://br.archive.ubuntu.com/ubuntu/ hardy-proposed main restricted universe multiverse
deb-src http://br.archive.ubuntu.com/ubuntu/ hardy-proposed main restricted universe multiverse
```

...luego hagan:

```
sudo apt-get update
sudo apt-get upgrade
```

Lo más probable es que diga que los paquetes del kernel fueron retenidos, para instalarlos hay que hacer:

```
sudo apt-get dist-upgrade
```

Luego reiniciar y listo.

El cambio en la experiencia les aseguro que es muy notorio. Ya puedo volver a ver videos en 720p, hasta les diría mejor que antes.

---

### Post by majatu on 2008-05-23
Ahora lo hago, aver que onda, gracias!

---

### Post by WanderingKnight on 2008-05-23
Aclaración (que me parece que no es tan necesaria, por eso no la hice en un principio, pero nunca viene mal):

hardy-proposed son los paquetes que se envían a la comunidad para hacer testeo, en caso de andar todo bien, se mandan directamente a los patches comunes y corrientes. Puede que aparezcan nuevos bugs que antes no estaban, por eso, si ven que algo se rompe, no duden en:

1) Reportar el bug

2) Borrar hardy-proposed y hacer un rollback (sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get upgrade).

---

### Post by MeduZa on 2008-05-23
mm algo que nunca vi, ya que lo primero que hice al instalar hardy fue compilar mi propio kernel y por ahora me anda mas rapido que gutsy por lejos!

---

### Post by alfredo_cba on 2008-05-26
> **MeduZa said:**
> mm algo que nunca vi, ya que lo primero que hice al instalar hardy fue compilar mi propio kernel y por ahora me anda mas rapido que gutsy por lejos!

MeduZa, podrías abrir un post con los pasos para compilar el kernel o en su defecto pasarme algún link en el que lo expliquen, porque la verdad que a mi no me anda mejor que gusty, eso que hice una instalación limpia de cero.
Saludos y gracias

---

### Post by faktorqm on 2008-05-26
Apoyo la emocion de alfredo_cba, yo me sumo a la iniciativa, tanto de que hagas una guia, como de contribuir a generar una. Salu2!

---

### Post by crosssover on 2008-05-26
hola, soy nuevo por este foro y tambien me gustaria que publiquen una guia para compilar el kernel.
Saludos !!

---

### Post by MeduZa on 2008-05-26
ok, voy a buscar material al respecto y poner mis pasos.
Lo que si tienen que hacer todos es una lista de su hard, cuanto mas peinada mejor, yo en mi lista tengo hasta que chips usan los sensores de temperatuda, puertos que usa la pc, y capasidades del motherboard.
estoy buscando una guia que esplique que cosas quitar que sean viejas e inutiles para nosotros (por ejemplo el protocolo de comunicacion X25 y cosas asi que nadie aca va a usar y que si lo tiene que usar compila el kernel de nuevo y a otra cosa)

Veo que consigo y posteo.

---

### Post by Simbiosys on 2008-05-26
Ante todo, cual es el concepto de que cada cual compile su kernel? Eliminar todo lo que uno no usa y así optimizar el funcionamiento?

Disculpen, soy nuevo en el mundo ubuntu.

Saludos.

---

### Post by alfredo_cba on 2008-05-26
sinceramente se agradece. ;)

---

### Post by faktorqm on 2008-05-26
> **Simbiosys said:**
> Ante todo, cual es el concepto de que cada cual compile su kernel? Eliminar todo lo que uno no usa y así optimizar el funcionamiento?

Disculpen, soy nuevo en el mundo ubuntu.

Saludos.

Más o menos. Te lo explico para que lo entiendas, pero no es exactamente asi. El kernel es un nucleo de funcionamiento, el que administra la memoria, el microprocesador, y los perifericos en general. Como este obviamente no puede tener todos los drivers metidos ahi adentro, existe algo que se llaman modulos de kernel y que ofician de drivers que el kernel maneja. Hay algunos modulos que vienen embebidos en este mismo para no tener que instalarlos, otros que se agregan "a mano" digamos. Lo que nos interesa sacar a nosotros son los que estan embebidos y no podes sacarlos.

Ejemplo, tu mother tiene usb y firewire, pero vos tenes todos dispositivos usb y jamas usaste el firewire. Entonces agarras y recompilas el kernel sin el modulo de firewire y entonces te das cuenta de que te anda mucho mas rapido la compu a medida que vas a sacando cosas que... ¡jamas usaste!
A parte de todo esto, existen mejoras en cuanto a rendimiento del microprocesador, como ser los distintos conjuntos de instrucciones de cada micro (MMX, 3D-NOW, SSE I, II, III, IV) aunque estas mejoras son casi imperceptibles.
Ahora bien, un dia te agarro un raye y te compraste un dispositivo firewire, entonces agarras y lo agregas al inicio en /etc/modules.d/modules (creo que era algo asi) y lo cargas cuando arranca y listo. No tenes problemas. Salu2!!

---

### Post by Simbiosys on 2008-05-26
> **faktorqm said:**
> Más o menos. Te lo explico para que lo entiendas, pero no es exactamente asi. El kernel es un nucleo de funcionamiento, el que administra la memoria, el microprocesador, y los perifericos en general. Como este obviamente no puede tener todos los drivers metidos ahi adentro, existe algo que se llaman modulos de kernel y que ofician de drivers que el kernel maneja. Hay algunos modulos que vienen embebidos en este mismo para no tener que instalarlos, otros que se agregan "a mano" digamos. Lo que nos interesa sacar a nosotros son los que estan embebidos y no podes sacarlos.

Ejemplo, tu mother tiene usb y firewire, pero vos tenes todos dispositivos usb y jamas usaste el firewire. Entonces agarras y recompilas el kernel sin el modulo de firewire y entonces te das cuenta de que te anda mucho mas rapido la compu a medida que vas a sacando cosas que... ¡jamas usaste!
A parte de todo esto, existen mejoras en cuanto a rendimiento del microprocesador, como ser los distintos conjuntos de instrucciones de cada micro (MMX, 3D-NOW, SSE I, II, III, IV) aunque estas mejoras son casi imperceptibles.
Ahora bien, un dia te agarro un raye y te compraste un dispositivo firewire, entonces agarras y lo agregas al inicio en /etc/modules.d/modules (creo que era algo asi) y lo cargas cuando arranca y listo. No tenes problemas. Salu2!!

Ok, algo así imaginaba... igual por ahora voy a esperar a hacer andar todo, sentirme comodo... un buen backup y después me meteré en estos asuntos avanzados jajaja. Dejo de desvirtuar.

Muchas gracias por la aclaración.
Saludos.

---

### Post by pol666 on 2008-05-26
mataria por compilar el modulo

---

