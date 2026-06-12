---
title: "Ayuda con los audifonos"
date: 2012-12-01
forum: Comunidad
---

### Post by Maha108 on 2012-12-01
Hola quisiera saber si me pueden ayudar, tengo ubuntu 10.04 mi notebook es un olidata l41ii1 y no me funciona el sonido frontal, para conectar los audifonos, los conecto y el sonido sigue saliendo por los parlantes, he buscado alguna informacion en varios foros, intente buscando en el alsamixer , haciendo click en el simbolo del parlante pero no logro hacerlo funcionar, espero me puedan ayudar, muchas gracias.

---

### Post by squakie on 2012-12-02
No hablo espanol - [www.ubuntu.com/support/community/local-language]("http://ubuntuforums.org/www.ubuntu.com/support/community/local-language")

---

### Post by Sef on 2012-12-02
Moved to Chile team.

---

### Post by Maha108 on 2012-12-02
> **Sef said:**
> Moved to Chile team.
Gracias

---

### Post by BenjaminCHILOE IS. on 2013-01-25
Abre la terminal de linux y anota esta linea: (con copia pega es facil)


sudo apt-add-repository ppa:ubuntu-audio-dev/alsa-daily

Te pedira tu contraseña de usuario o password, la anotas y ENTER. Luego aparecen varias palabras en ingles y te pide un segundo ENTER.

Seguido anotas en la terminal para actualizar tus cambios esta linea  y oprimes ENTER( copia y pega es mas facil) se iniciara la actualizacion y esperas hasta completar el 100% de actualizacion.

sudo apt-get update   


Una vez completada la actualizacion en un 100% y para finalizar anotas esta nueva linea de instalacion de paquetes..( copia y pega las instrucciones) 

sudo apt-get install alsa-hda-dkms

y das ENTER seguramente te volvera a pedir tu contraseña de usuario de ubuntu...anotas tu contraseña y Enter....apareceran los paquetes a instalar y preguntara en ingles si instalas o no de este modo  Y/N  tu eliges Y=yes y esperas a que instale y termine el 100%

cierra la terminal y REINICIA tu equipo y prueba tu sonido en los audifonos y en los parlantes

Espero te sirva
Saludos desde Chiloe y Valdivia
):P

---

