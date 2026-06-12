---
title: "Asus eee pc x101ch grafica GMA 3600 de intel"
date: 2012-09-11
forum: Colombia Team - Colombia
---

### Post by gonedcc on 2012-09-11
Que tal, en estos días estoy a punto de recibir mi netbook Eee pc x101ch viene sin OS, solo el Express Gate... y estoy buscando que distro de linux instalar, buscando en la web me doy cuenta que no existe un soporte para la gráfica integrada que trae que es GMA 3600. Encontré esta información que es reciente, llevo apenas 3 meses en linux y hay cosas de las que hablan que no entiendo. Dejo Las Paginas como ayuda para encontrar solución.

[http://blogdrake.net/consulta/solicito-paquete-para-la-gma-3600-de-intel-powervr]("http://blogdrake.net/consulta/solicito-paquete-para-la-gma-3600-de-intel-powervr")

[http://www.muylinux.com/2012/06/14/cuidado-con-los-intel-atom-cerdaview-cedar-trail-soporte-complejo-en-linux/]("http://www.muylinux.com/2012/06/14/cuidado-con-los-intel-atom-cerdaview-cedar-trail-soporte-complejo-en-linux/")

[http://repo.meego.com/MeeGo/builds/1.2.0/latest/repos/non-oss/ia32/packages/]("http://repo.meego.com/MeeGo/builds/1.2.0/latest/repos/non-oss/ia32/packages/")

Hasta el momento tengo pensado probar MeeGo haber como me va, no tengo ni idea de esa distro!

---

### Post by darkhole on 2012-09-11
Si existe soporte, pero como los controladores son propietarios y la empresa no ayuda mucho pues aun no son muy buenos. Estos chips de video no son fabricados por Intel, sino que es una empresa externa.

Puede que esto sea interesante cuando instales Ubuntu 12.04: [http://daily.siebler.eu/2012/06/ubuntu-12-04-driver-for-intel-cedarview-atom-n2000-und-d2000-serie/](http://daily.siebler.eu/2012/06/ubuntu-12-04-driver-for-intel-cedarview-atom-n2000-und-d2000-serie/)

De esta forma usas el ultimo controlador, pero segun veo asi sin hacer nada raro en la ultima version de Ubuntu todo funciona bien.

Sin embargo al parecer es recomendable usar mejor la proxima version de Ubuntu 12.10. Con esa tendras menos problemas, puedes desscargarla de aqui:
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

Es una version Beta pero ya falta solo casi 1 mes para que sea lanzada.

---

### Post by gonedcc on 2012-09-12
Ok muchas gracias, pregunta... ubuntu 12.04 LTS actualizando después de instalar no quedaría igual que la versión beta que me dices? o es mejor instalar la que me dices y después actualizar??

---

### Post by darkhole on 2012-09-14
> **gonedcc said:**
> Ok muchas gracias, pregunta... ubuntu 12.04 LTS actualizando después de instalar no quedaría igual que la versión beta que me dices? o es mejor instalar la que me dices y después actualizar??

No, no es lo mismo, la version 12.04 recibe actualizaciones de seguridad y de correccion de fallos durante 5 años.

La version 12.10 que esta en Beta saldra con nuevas versiones de aplicaciones y nuevos controladores (como los que ese portatil necesitan), y tendra un soporte de año y medio.

Sin embargo si es posible actualizar de la version 12.04 a la 12.10 pero no lo recomiendo aun, dado que esto es mas para tareas de testing dado que la version 12.10 aun no sale.

---

### Post by gonedcc on 2012-09-14
ok entiendo, gracias! El día de ayer recibí por fin el computador, se suponía que no traía OS y para mi sorpresa viene con certificado de ubuntu y tan pronto lo encendí se instalo ubuntu 12.04 funcionando muy bien... ahora tengo otro problema: al actualizar dejo de funcionar el altavoz pero la salida de audio 3.5 si funciona, no se a que se debe eso!

intenté seguir este tutorial...
[http://deknileech.info/solucionar-problema-de-sonido-en-ubuntu-12-04/]("http://deknileech.info/solucionar-problema-de-sonido-en-ubuntu-12-04/")
pero llego a este comando "sudo apt-get install libncursesw5-dev build-essential libncurses-dev gettext xmlto xmltoman linux-headers-`uname -r" y se queda esperando como si faltara algo..... :(

---

### Post by darkhole on 2012-09-20
> **gonedcc said:**
> ok entiendo, gracias! El día de ayer recibí por fin el computador, se suponía que no traía OS y para mi sorpresa viene con certificado de ubuntu y tan pronto lo encendí se instalo ubuntu 12.04 funcionando muy bien... ahora tengo otro problema: al actualizar dejo de funcionar el altavoz pero la salida de audio 3.5 si funciona, no se a que se debe eso!

intenté seguir este tutorial...
[http://deknileech.info/solucionar-problema-de-sonido-en-ubuntu-12-04/]("http://deknileech.info/solucionar-problema-de-sonido-en-ubuntu-12-04/")
pero llego a este comando "sudo apt-get install libncursesw5-dev build-essential libncurses-dev gettext xmlto xmltoman linux-headers-`uname -r" y se queda esperando como si faltara algo..... :(
Hola

Debes verificar que version de Ubuntu tienes y que kernel tienes, puedes hacer las dos ejecutando el comando:
uname -a
en una terminal.

Ademas de esto, si nos envias el resultado del comando
lspci
y el comando
lsusb

podremos ayudate mucho mas.

---

### Post by gonedcc on 2012-09-20
Ok, después de hacer lo que me dijiste, sale esto:
_________________________________________________________________
eduardo@eduardo-X101CH:~$ uname -a
Linux eduardo-X101CH 3.2.0-31-generic-pae #50-Ubuntu SMP Fri Sep 7 16:39:45 UTC 2012 i686 i686 i386 GNU/Linux
eduardo@eduardo-X101CH:~$ lspci
00:00.0 Host bridge: Intel Corporation Atom Processor D2xxx/N2xxx DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Atom Processor D2xxx/N2xxx Integrated Graphics Controller (rev 09)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA Controller [AHCI mode] (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
02:00.0 Network controller: Atheros Communications Inc. AR9485 Wireless Network Adapter (rev 01)
04:00.0 Ethernet controller: Atheros Communications Inc. AR8152 v2.0 Fast Ethernet (rev c1)
eduardo@eduardo-X101CH:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 04f2:b26f Chicony Electronics Co., Ltd 
_______________________________________________________________

He investigado también por google, no se mucho pero lo que alcanzo a entender es que existe un problema para asociar el driver con la maquina. te doy la pagina y los resultados de lo que dice. Solo la información que sale ya que no he realizado ningún cambio que proponen para no meter la pata!
[http://www.taringa.net/posts/linux/15325819/Ubuntu-12_04-sin-sonido-_solucionado_.html]("http://www.taringa.net/posts/linux/15325819/Ubuntu-12_04-sin-sonido-_solucionado_.html")
_______________________________________________________________

eduardo@eduardo-X101CH:~$ lsmod | grep snd 
snd_hrtimer            12648  1 
snd_hda_codec_hdmi     31775  1 
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  3 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  3 snd_hrtimer,snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  16 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
_____________________________________________________________________
y en alsamixer me sale esto:

[https://docs.google.com/open?id=0B3AQ-H8n_mnUVDVid01CQTBvVWM]("https://docs.google.com/open?id=0B3AQ-H8n_mnUVDVid01CQTBvVWM")

espero sea útil la información! Gracias....

---

### Post by gonedcc on 2012-09-30
Hola, espero no ser inoportuno ni grosero, pero la verdad necesito solucionar este inconveniente lo mas pronto posible, soy músico y ya se imaginarán lo importante que es para mi tener sonido... agradezco cualquier ayuda sugerencia realizada pues la verdad ya he buscado mucho en google y no encuentro solución alguna! :(

---

### Post by gonedcc on 2012-11-05
> **gonedcc said:**
> ok entiendo, gracias! El día de ayer recibí por fin el computador, se suponía que no traía OS y para mi sorpresa viene con certificado de ubuntu y tan pronto lo encendí se instalo ubuntu 12.04 funcionando muy bien... ahora tengo otro problema: al actualizar dejo de funcionar el altavoz pero la salida de audio 3.5 si funciona, no se a que se debe eso!

intenté seguir este tutorial...
[http://deknileech.info/solucionar-problema-de-sonido-en-ubuntu-12-04/]("http://deknileech.info/solucionar-problema-de-sonido-en-ubuntu-12-04/")
pero llego a este comando "sudo apt-get install libncursesw5-dev build-essential libncurses-dev gettext xmlto xmltoman linux-headers-`uname -r" y se queda esperando como si faltara algo..... :(

Después de mucho buscar encontré un reporte de fallo en la pagina de Ubuntu, donde parece ya estar solucionado el problema con el sonido del altavoz interno. [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1037763]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1037763")

Respecto a los problemas que he leído sobre la resolución de pantalla (Asus Eee pc x101ch con Ubuntu 12.04 pre-instalado)desde que tengo el equipo no he tenido ese problema... al instalarse ubuntu por primera ves, en Controladores Adicionales (Configuración del sistema/Controladores Adicionales) me indica que está trabajando con controladores privativos...

drm driver for the Intel GMA500
Controlador para gráficos Intel Cedarview

son los controladores que me dice. El único problema que he encontrado es el soporte para aceleración 3D, no existe!
No se mucho de esto, espero sea útil esta información. Fuera de esto lo demás funciona muy bien para ser un portátil económico!

---

