---
title: "Problemas con LiveUSB Jaunty// Jaunty LiveUSB problems."
date: 2009-03-29
forum: Development CD/DVD Image Testing
---

### Post by danirolo7 on 2009-03-29
Hello, this post is writen in Spanish and English.

Hola, este post está escrito en castellano e inglés.

Castellano/ Spanish:

Bien, pues cuando salió la beta de Jaunty, me decidí a instalarlo con un LiveUsb a partir de la imagen iso bajada del sitio oficial por torrent. Creé el LiveUSB con Unetbootin, cuando reinicio e inicio con el LiveUSB, no pasa del Usplash, se queda mucho tiempo en él y luego dice que no encuentra el modules.dep en /lib/modules/(uname -r)-generic, hago uso de la  consola del Initramfs y hago un $ls en dicha carpeta y el modules.dep sí que está.Probé copiando los archivos a mano y usando Syslinux, el mismo error. ¿A qué se debe esto?. Intenté con las versiones de 32 y 64 bits, también con la Alternate, pero dice que no puede encontrar/montar el CD..no sé cómo indicarle que las cosas están en el Usb. ¿Alguna idea?

Inglés/English:

Well, as soon as the Jaunty Beta got out I decided to isntall it from a LiveUsb, so I made the LiveUSb with Unetbootin, when I rebooted and booted from the LiveUSB...Initramfs, /lib/modules/(uname -r)/modules.dep file not found. So I tryed again copying the files manually and with Syslinux, same error. ¿Why does this happen? I've tryied with both 32 and 64 bits versions, also with Alternate CD, but it says something like "cannot mount/find CD" and I don't know how to tell the installer that the files are in the Usb-unit. ¿Any ideas?

Thanks/gracias!.

PD: you can answer in English or Spanish, I don't mind. Podéis responder en Inglés o castellano, no me importa.

---

### Post by Rallg on 2009-03-29
It also did not work for me.

---

### Post by danirolo7 on 2009-03-29
Then I think it's a bug with the beta and LiveUSB...because I installed Alpha 6 with an Usb. Going to Launchpad.

---

