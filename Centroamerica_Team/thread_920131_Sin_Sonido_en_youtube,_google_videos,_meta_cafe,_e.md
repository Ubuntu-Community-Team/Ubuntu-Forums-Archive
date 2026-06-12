---
title: "Sin Sonido en youtube, google videos, meta cafe, etc"
date: 2008-09-14
forum: Centroamerica Team
---

### Post by adrianlancer on 2008-09-14
Bueno tuve un problema con el audio de los flash en  linea como youtube. aqui les comparto lo que encontre. Porcierto es con el Firefox 3 y Ubuntu 8.04.

Fuentes
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/192888](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/192888)

Antes de empezar: Porfavor lea los siguientes puntos para asegurar si aplica.
    * Esta guia es solo para Ubuntu 8.04. aunque muchos pasos funcionan para el release en desarrollo (Intrepid), existen algunos problemas del kernel en la version Intrepid que no les dire mas de ellas.
    *Si estas Corriendo Kubuntu/Xubuntu/Edubuntu 8.04, esta guia noe es para ti.(PulseAudio no es usado en estas distribuciones).
    * Si no tienes audio bajo ninguna circunstancia(mp3, divx, etc),entonces probablemente estas sufriendo una falla del kernel o el ALSA- esta guia probablemente no es para ti
    * Si tienes una tarjeta de audio nueva probablemente no este soportada por ALSA, y/o estas usando OSS v4 - esta guia no es para ti.
    * Si estas experimentando muchos "stuttering sound" en tu sistema,especialmente despues de haber actualizado a Hardy(Ubuntu 8.04), esta guia es para ti.
    * Si puedes obtener audio en algunas aplicaciones pero no todas, o encontraste que el "audio mixing" no funciona, esta guia es para ti.
    * Si deseas tener "sound system-wide" ecualizado, esta guia es para ti.


1. Nesecitamos remover el "flashplugin-nonfree" package, descargar el nesesario paquete "nspluginwrapper" desde el Lauchpad, luego reinstalar "nspluginwrapper", "flashplugin-nonfree" and "libflashsupport":
Code:

$ sudo apt-get remove --purge flashplugin-nonfree
$ wget -c [http://launchpadlibrarian.net/16150887/nspluginwrapper_1.1.0-0conn2_i386.deb](http://launchpadlibrarian.net/16150887/nspluginwrapper_1.1.0-0conn2_i386.deb)
$ sudo dpkg -i nspluginwrapper_1.1.0-0conn2_i386.deb
$ sudo apt-get install flashplugin-nonfree libflashsupport

***esto se escribe en el terminal sin el signo de "$"***

Saludos espero les ayude

---

### Post by srlinux on 2008-10-06
> **adrianlancer said:**
> Bueno tuve un problema con el audio de los flash en  linea como youtube. aqui les comparto lo que encontre. Porcierto es con el Firefox 3 y Ubuntu 8.04.

Fuentes
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/192888](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/192888)

Antes de empezar: Porfavor lea los siguientes puntos para asegurar si aplica.
    * Esta guia es solo para Ubuntu 8.04. aunque muchos pasos funcionan para el release en desarrollo (Intrepid), existen algunos problemas del kernel en la version Intrepid que no les dire mas de ellas.
    *Si estas Corriendo Kubuntu/Xubuntu/Edubuntu 8.04, esta guia noe es para ti.(PulseAudio no es usado en estas distribuciones).
    * Si no tienes audio bajo ninguna circunstancia(mp3, divx, etc),entonces probablemente estas sufriendo una falla del kernel o el ALSA- esta guia probablemente no es para ti
    * Si tienes una tarjeta de audio nueva probablemente no este soportada por ALSA, y/o estas usando OSS v4 - esta guia no es para ti.
    * Si estas experimentando muchos "stuttering sound" en tu sistema,especialmente despues de haber actualizado a Hardy(Ubuntu 8.04), esta guia es para ti.
    * Si puedes obtener audio en algunas aplicaciones pero no todas, o encontraste que el "audio mixing" no funciona, esta guia es para ti.
    * Si deseas tener "sound system-wide" ecualizado, esta guia es para ti.


1. Nesecitamos remover el "flashplugin-nonfree" package, descargar el nesesario paquete "nspluginwrapper" desde el Lauchpad, luego reinstalar "nspluginwrapper", "flashplugin-nonfree" and "libflashsupport":
Code:

$ sudo apt-get remove --purge flashplugin-nonfree
$ wget -c [http://launchpadlibrarian.net/16150887/nspluginwrapper_1.1.0-0conn2_i386.deb](http://launchpadlibrarian.net/16150887/nspluginwrapper_1.1.0-0conn2_i386.deb)
$ sudo dpkg -i nspluginwrapper_1.1.0-0conn2_i386.deb
$ sudo apt-get install flashplugin-nonfree libflashsupport

***esto se escribe en el terminal sin el signo de "$"***

Saludos espero les ayude


hola amigo al parecr alguno eso lo les funciona por ejemplo a mi cuando instalo el libflashsupoort se me cierra el firefox :D asi q mejor prefiero quedarme asi jejej y esperar la solucion final

---

### Post by ssthormess on 2008-10-07
Verifica si no tienes en MUTE o en 0% el PCM en los controles de volumen de tu Equipo, a mi me paso hace tiempo.

---

### Post by meldon12 on 2008-10-27
muchas gracias adrian !!!!! me ha servido, tenia el mismo problema y ya se soluciono.

saludos

---

### Post by adrianlancer on 2008-10-28
> **meldon12 said:**
> muchas gracias adrian !!!!! me ha servido, tenia el mismo problema y ya se soluciono.

saludos
 a la orden siempre ke tenga un problema tratare de postearlo y buscarle solucion si alguien no la encuentra antes que yo :):lolflag:

---

### Post by ense on 2008-12-16
> **adrianlancer said:**
> 
$ wget -c [http://launchpadlibrarian.net/16150887/nspluginwrapper_1.1.0-0conn2_i386.deb](http://launchpadlibrarian.net/16150887/nspluginwrapper_1.1.0-0conn2_i386.deb)
$ sudo dpkg -i nspluginwrapper_1.1.0-0conn2_i386.deb
$ sudo apt-get install flashplugin-nonfree libflashsupport

***esto se escribe en el terminal sin el signo de "$"***


Antes que nada, un saludo adrianlancer, ya que soy nuevo tanto en este foro como en ubuntu. 

Yo utilizo la misma versión de ubunto que que espones en este hilo, con la salvedad de que utilizo un procesador x86-64 (amd64) y como es lógico el dpkg me devuelve que el paquete no corresponde con el sistema, además tamponco encuentró el libflashsupport cuando reistale el flash. ¿Hay alguna forma de solucionar estos errores?

Gracias por todo.

---

### Post by eivar on 2008-12-16
Hola ense, para linux x64 hay un paquete que me parece que se llama linux32 o algo por el estilo, te permite ejecutar programas para la acquitectura de 32 bits en procesadores x64.

Busca en synaptic y nos cuentas que tal.

Suerte

---

### Post by adrianlancer on 2009-05-09
bueno al parecer con la actualizacion del kernel a 2.6.24-24 tengo problemas denuevo con las paginas de videos:confused: o no me salen los videos o me salen como pausados o laggeados :S alguien sabe algo?

---

### Post by eivar on 2009-05-10
Hola adrianlancer
Probaste ya reinstalar el plugin para flash.


saludos

---

### Post by adrianlancer on 2009-05-11
bueno simplemente comenzo a funcionar no recuerdo haber echo ninguna otra actualizacion pero aveces las hago medio dormido:P gracias

---

