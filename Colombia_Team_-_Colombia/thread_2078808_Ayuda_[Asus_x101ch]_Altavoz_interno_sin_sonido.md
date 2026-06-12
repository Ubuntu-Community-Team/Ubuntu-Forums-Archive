---
title: "Ayuda [Asus x101ch] Altavoz interno sin sonido"
date: 2012-10-31
forum: Colombia Team - Colombia
---

### Post by gonedcc on 2012-10-31
Hola a todos, ya llevo un tiempo buscando la manera de hacer sonar el altavoz de mi Eee pc x101ch con Ubuntu 12.04 pre-instalado, que después de actualizar deja de funcionar. Googleando encontre una posible solución pero no cuento con el conocimiento para llevar a cabo el proceso que dan. Les voy a dejar la pagina del reporte de error donde dan una solución al final para que me colaboren diciéndome paso por paso lo que hay que hacer.

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1037763]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1037763")

Gracias de antemano! :D

---

### Post by gonedcc on 2012-11-05
Ya se encuentra solucionado el problema en la página de soporte de Ubuntu, les dejo las instrucciones y el enlace a la fuente!
__________________________________________________________________________

Open Terminal

write this command:

sudo gedit /etc/apt/sources.list

this command open program gedit: now you can modify the file sources.list
add to the file the lines:

deb [http://asus.archive.canonical.com/updates](http://asus.archive.canonical.com/updates) precise-yanshui public
deb-src [http://asus.archive.canonical.com/updates](http://asus.archive.canonical.com/updates) precise-yanshui public

save the file
close the gedit windows

back to terminal write command:

sudo apt-get update

wait for the prompt then write:

sudo apt-get install alsa-hda-realtek-patched-dkms

wait for the prompt then write:

sudo reboot

wait for reboot

Test the sound using:
System Settings -> Sound -> Test Sound
_________________________________________________________________________

Pueden traducir por google pero al copiar los comandos háganlo desde el texto original para que no les de errores de escritura.

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1037763]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1037763")

---

### Post by darkhole on 2012-11-09
Muchas gracias a ti Eduardo!

---

