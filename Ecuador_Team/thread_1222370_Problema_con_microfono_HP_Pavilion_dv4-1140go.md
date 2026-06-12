---
title: "Problema con microfono HP Pavilion dv4-1140go"
date: 2009-07-24
forum: Ecuador Team
---

### Post by kazohnine on 2009-07-24
Hola! 
Este es mi primer post aqui. No hace mucho decidi instalar Ubuntu en mi laptop, despues de haber sido usuario de Windows desde que conozco "un computador". 
A lo mejor ya existe algun post con este tipo de problema pero la verdad NO logro arreglar este UNICO problema que tengo desde que isntale Ubuntu.
El sonido va a la perfeccion, pero el microfono no sirve, para nada.

Aqui les adjunto algunos datos para ver si les podria ayudar a buscar una solucion. 

[lspci]("http://pastebin.com/m3221c2c")
[http://pastebin.com/m3221c2c](http://pastebin.com/m3221c2c)

[[SIZE=3]aplay -l[/SIZE]]("http://pastebin.com/m555df563")
[http://pastebin.com/m555df563](http://pastebin.com/m555df563)

[[SIZE=3]cat /proc/asound/card0/codec#* | grep Codec[/SIZE]]("http://pastebin.com/m491b363a")
[http://pastebin.com/m491b363a](http://pastebin.com/m491b363a)


Ya he visitado foros, e incluso he recibido ayuda con codecs y todo lo que se deberia hacer; pero nada.
Les agradeceria muchisimo su ayuda!
Gracias de antemano.

---

### Post by kazohnine on 2009-07-24
Ya esta! 

Tengo una HP Pavilion dv4-1140go.
El sonido y el microfono trabajan con Ubuntu 9.04.

Los unicos cambios que he hecho fue, añadir unas lineas al alsa-base.conf

Code:

options snd-hda-intel model=hp 
options snd-hda-intel enable_msi=1
#options snd-hda-intel model=3stack-dig 
#options snd-hda-intel enable_msi=1 
#options snd-hda-intel single_cmd=1

En las Opciones de Sonido ( Sistema > Preferencias > Sonido todo debe estar en Autodetectar. Excepto para Captura de Sonido que sera ALSA. Device elegimos HDA Intel (Alsa Mixer).

En el Control del Volumen (el panel). Master, Audifonos, PCM, Microfono deben estar activos. (Asegurense de haber marcado en Preferencias todos los cuadros que aparecen en el dialogo)
En la pestaña de Grabar todas las opciones deben estar al maximo. 


Mi lspci

```
 

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
02:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
04:00.0 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
04:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller
04:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller
04:00.4 System peripheral: JMicron Technologies, Inc. xD Host Controller
 


```

---

