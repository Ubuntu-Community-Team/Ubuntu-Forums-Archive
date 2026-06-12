---
title: "No funciona el audio de audifonos"
date: 2018-09-03
forum: Centroamerica Team
---

### Post by monterosm on 2018-09-03
Bien, buenas soy Martino y quiero hablar del problema:
Hace no menos de 1 hora instale Lubuntu 18.04 (Anteriormente tenia Ubuntu pero era muy pesado y andaba bien lento, este problema no existia) y no andaba el audio al reproducir musica y videos como tales.

Necesito una solucion a esto, encontre algo "temporal" que consiste en tocar ```
Alsamixer
``` y subir el Speaker+ al tener conectado el auricular (esto pasa con todos, no solo 1, no he probado con altavoces los cuales se conecten en el jack ya que no tengo tales) y esa fue la unica manera

Tambien al poner el siguiente codigo en el terminal

```
sudo gedit /etc/modprobe.d/alsa-base.conf 
```

no hay nada escrito.


Al insertar el comando ```
lspci
``` aparece lo siguiente:

[PHP]00:00.0 Host bridge: Intel Corporation Atom Processor D2xxx/N2xxx DRAM Controller (rev 04)
00:02.0 VGA compatible controller: Intel Corporation Atom Processor D2xxx/N2xxx Integrated Graphics Controller (rev 0b)
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation NM10/ICH7 Family SATA Controller [AHCI mode] (rev 02)
00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 02)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller (rev 05)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)[/PHP]



y ```
aplay -l
``` esto

[PHP]aplay -l
**** Lista de PLAYBACK dispositivos hardware ****
tarjeta 0: Intel [HDA Intel], dispositivo 0: ALC269VB Analog [ALC269VB Analog]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 0: Intel [HDA Intel], dispositivo 3: HDMI 0 [HDMI 0]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
[/PHP]

Tambien mencionar que desactivar el Auto-Mute de Alsmixer no funciona, sigue el problem

Los espero

Pd: No se mucho sobre el foro de Ubuntu, mejor dicho como escribir, como se ve es mi primera vez :b

---

### Post by WHK on 2019-01-18
Hola, una de las grandes diferencias entre Lubuntu y Ubuntu es la utilización de Gnome3, pero vamos, Gnome no es solo una aplicación de aspectos gráficos, también está involucrado en todo lo que son servicios propios de Gnome, como por ejemplo, el manejo del servicio de red, audio, video, energía, etc. Al no tener Gnome3 pierdes todas estas comodidades y debes entrar a utilizar los gestores de configuración de Lubuntu o si no realizar todo manualmente tal como se hace en Debian.

De todas maneras eso me huele a un bug de Lubuntu y el controlador de tu audio, si no me equivoco probablemente no estés usando el audio de tu placa madre o tu placa debe ser algún modelo que ya no tiene soporte o está obsoleto y por ende no funciona bien.

En ubuntu antiguamente tenía un problema similar y es que cuando desocnectaba mis audífonos del pc no cambiaba automáticamente la salida del audio a los parlantes, probablemente sea un tema que debas reportar en el bug tracker.

Puedes postearnos el archivo /var/log/syslog?

saludos.

---

