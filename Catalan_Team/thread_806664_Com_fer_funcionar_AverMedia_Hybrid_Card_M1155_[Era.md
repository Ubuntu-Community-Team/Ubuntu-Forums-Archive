---
title: "Com fer funcionar AverMedia Hybrid Card M1155 [Era:Puc veure la TV amb aquesta ...?]"
date: 2008-05-25
forum: Catalan Team
---

### Post by rajoar on 2008-05-25
Tinc una targeta AverMedia Hybrid Card M115S i no tinc idea de què ni com haig de configurar per poder veure la TV...

Si faig un lspci em llista això:
ramon@ramon-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation G86M [GeForce 8400M GT] (rev a1)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 12)
06:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
08:03.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
08:03.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
08:03.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
08:05.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
08:06.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
ramon@ramon-desktop:~$

Algú en sap quelcom?...

---

### Post by CarlesOriol on 2008-05-25
Connectala, escrius dmesg i ens copies les darreres linies.

---

### Post by rajoar on 2008-05-25
x0 field=4 memory=1 m=0x1a000 length=53248
[ 3220.765938] r5u870-0: urbstream[6] urb complete: f5327180/0
[ 3220.765979] r5u870-0: urbstream[6] processing f5327180
[ 3220.769962] r5u870-0: urbstream[6] urb complete: f5327960/0
[ 3220.769992] r5u870-0: urbstream[6] processing f5327960
[ 3220.771342] usbcam: received v4l ioctl: 1074026003
[ 3220.771693] r5u870-0: aborting frame 0/f7675180
[ 3220.771701] r5u870-0: completing frame 0/f7675180 STATE_ERROR
[ 3220.772276] r5u870-0: aborting frame 1/f76759c0
[ 3220.772283] r5u870-0: completing frame 1/f76759c0 STATE_ERROR
[ 3220.772819] r5u870-0: aborting frame 2/f7675b40
[ 3220.772825] r5u870-0: completing frame 2/f7675b40 STATE_ERROR
[ 3220.773359] r5u870-0: aborting frame 3/f7675000
[ 3220.773364] r5u870-0: current frame aborted, stopping capture
[ 3220.773369] r5u870-0: invoking minidriver cap_stop
[ 3220.773374] r5u870-0: urbstream[6] stopping
[ 3220.773927] r5u870-0: urbstream[6] urb complete: f5327ae0/0
[ 3220.773933] r5u870-0: urbstream[6] request canceled, ignoring
[ 3220.777949] r5u870-0: urbstream[6] urb complete: f5327180/0
[ 3220.777956] r5u870-0: urbstream[6] request canceled, ignoring
[ 3220.778564] r5u870-0: urbstream[6] stopped
[ 3220.778571] r5u870-0: minidriver aborting all frames
[ 3220.778575] r5u870-0: completing frame 3 STATE_ERROR
[ 3220.780608] r5u870-0: urbstream[6] stopping
[ 3220.780616] r5u870-0: urbstream[6] stopped
[ 3220.780636] r5u870-0: minidriver capture stopped
[ 3220.780664] r5u870-0: VIDIOC_STREAMOFF: res:0
[ 3220.780674] usbcam: received v4l ioctl: -1069263351
[ 3220.780681] r5u870-0: VIDIOC_QUERYBUF in: index=0 type=1
[ 3220.780689] r5u870-0: VIDIOC_QUERYBUF out: index=0 type=1 bytesused=50688 flags=0x1 field=4 memory=1 m=0x0 length=53248
[ 3220.780721] usbcam: received v4l ioctl: -1069263351
[ 3220.780726] r5u870-0: VIDIOC_QUERYBUF in: index=1 type=1
[ 3220.780732] r5u870-0: VIDIOC_QUERYBUF out: index=1 type=1 bytesused=50688 flags=0x1 field=4 memory=1 m=0xd000 length=53248
[ 3220.780754] usbcam: received v4l ioctl: -1069263351
[ 3220.780758] r5u870-0: VIDIOC_QUERYBUF in: index=2 type=1
[ 3220.780764] r5u870-0: VIDIOC_QUERYBUF out: index=2 type=1 bytesused=50688 flags=0x1 field=4 memory=1 m=0x1a000 length=53248
[ 3220.780786] usbcam: received v4l ioctl: -1069263351
[ 3220.780791] r5u870-0: VIDIOC_QUERYBUF in: index=3 type=1
[ 3220.780797] r5u870-0: VIDIOC_QUERYBUF out: index=3 type=1 bytesused=50688 flags=0x1 field=4 memory=1 m=0x27000 length=53248
[ 3220.780818] usbcam: received v4l ioctl: -1069263351
[ 3220.780822] r5u870-0: VIDIOC_QUERYBUF in: index=4 type=1
[ 3220.780827] r5u870-0: VIDIOC_QUERYBUF res:-22
ramon@ramon-desktop:~$

---

### Post by patrickfromspain on 2008-05-25
millor fes: dmesg > dmesg.log i ens adjuntes el fitxer dmesg.log

salut

---

### Post by rajoar on 2008-05-25
Nota de moderador: t'he esborrat el totxo que has enganxat. Quan es té tant de text per enganxar s'ha de pujar el fitxer adjunt, no enganxar-lo, ja que fa el fòrum insufrible.

---

### Post by papapep on 2008-05-25
Aquí tens el fitxer correctament adjuntat. Recordem-ho tots plegats per a properes ocasions, si us plau.

---

### Post by papapep on 2008-05-25
Aquí tens el fitxer adjuntat. Recordem-ho tots plegats per a properes ocasions, si us plau.

---

### Post by CarlesOriol on 2008-05-25
Jo en aquest log no veig els missatges del moment de la connexió.

---

### Post by patrickfromspain on 2008-05-25
de la tarjeta de tv no se.. pro que tens algun problema amb la webcam, segur xD

---

### Post by rajoar on 2008-05-25
En primer lloc moltes gràcies a tots i disculpeu pel totxo de enviat...,  procuraré que no torni a passar i en d'altres ocasions enviar-lo com a fitxer...
A veure, de la web cam vaig carregar el ricoh-webcam-r5u870-2.6.24-16-generic_0.11.0-0arakhne0_i386.deb i vaig configurar l'Ekiga i em va semblar que funcionava..., però també sembla que hi hagi un conflicte entre l'AverMedfia i la Ricoh Web Cam perquè  les respostes que em dona el terminal són diferents si he fer servir l'Ekiga o no...
Per exemple, després de reiniciar l'ubuntu i introduir la instrucció
dmesg | grep saa7134
el terminal contesta:
[ 24,73392] saa7134 ALSA driver for DMA sound loaded...
Si aquesta mateixa instrucció la demano després de utilitzar l'Ekiga no em contesta res de res...
Es a dir en cap cas sembla que detecti la targeta AverMedia, però si que detecta el driver DMA immediatament després de reiniciar el sistema...
En fi, amb els meus pocs coneixements no sé cap on haig de tirar...

---

### Post by papapep on 2008-05-25
Rajoar, si ara vols mirar el tema de la webcam ho hauries de fer a un fil nou a banda, si us plau.

---

### Post by CarlesOriol on 2008-05-26
> **rajoar said:**
> 
dmesg | grep saa7134
el terminal contesta:
[ 24,73392] saa7134 ALSA driver for DMA sound loaded...


El dmesg sols et llegeix el log i el grep te'l filta.
El que passa és que tens tants errors que el log sols recorda una quantitat determinada i al fer-ho despres d'usar el ekiga no és que et desaparegui res, és que no queda espai per guardar tants missatges.

---

### Post by rajoar on 2008-05-26
Ok per l'aclariment Carles..., però que només contesti amb el driver d'audio vol dir que no detecta la targeta de TV AverMedia?...
Que puc fer?...
(els missatges d'error de la web cam problablement venent d'haver carregat un kernel generic de Ricoh que no es compatible al 100%. En tot cas, pensaba que podia tenir relació amb els problemes de l'AverMedia i per això ho havia esmentat, però tal com m'ha indicat el Papapep, ja obriré un altra fil per aquest tema)

---

### Post by CarlesOriol on 2008-05-26
Al moment de connectar el dispositiu t'informa de que ha trobat i que li cal.

Et pots trobar en dues situacions:

1. que et calgui un firmware que veuras indicat al dmesg

2. que a mes et calgui recompilar els controladors

Per tant primer cal veure la informació que et mostra al connectar.

---

### Post by rajoar on 2008-05-26
A veure hi una cosa que no tinc clara...
Quan dius al connectar a què et refereixes exactament?
...La targeta és una targeta interna que està connectada i amb el cable d'antena (analogic i TDT) endollat...

---

### Post by papapep on 2008-05-26
Doncs, per començar, crec que ens hauries d'identificar clarament de quina targeta estem parlant des d'el principi, per què em sembla que anem malament des del primer moment....del model que indiques no em surt cap ni una referència a internet (i no és massa normal...).

Segona, fes a un terminal:

```
lspci
```

i enganxa el resultat aquí, si us plau.

---

### Post by rajoar on 2008-05-26
Bona nit Papapep,
El resultat de lspci és el mateix de l'inici del post:
08:05.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
08:06.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev d1)

Segons el catàleg, el windows i el que he pogut trobar per internet la targeta és: AverMedia Hybrid H/W MPEG Card M115S (DVBT/NTSC/PAL/SECAM) SigmaTel High Definition Audio Codec...

A veure, més informació. El resultat de lspci -v:
08:05.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
	Subsystem: Avermedia Technologies Inc Unknown device e836
	Flags: bus master, medium devsel, latency 32, IRQ 21
	Memory at fc006800 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>

08:06.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
	Subsystem: Avermedia Technologies Inc Unknown device e936
	Flags: bus master, medium devsel, latency 32, IRQ 23
	Memory at fc007000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>

---

### Post by ilku on 2008-05-27
si fas el lspci -v com a sudo et surtiran les Capabilities.

---

### Post by CarlesOriol on 2008-05-27
A veure:

fes: 

dmesg | grep firm
i
dmesg | grep dvb
i 
dmesg | AverMedia

i després ens copies el contingut.

Però fes-ho tot just engegat l'ordinador, sinò amb tants errors no podrem veure res de res.

---

### Post by rajoar on 2008-05-27
ramon@ramon-desktop:~$ su
Password: 
root@ramon-desktop:/home/ramon# dmesg | grep firm
root@ramon-desktop:/home/ramon# dmesg | grep dvb
root@ramon-desktop:/home/ramon# dmesg | AverMedia
bash: AverMedia: command not found
root@ramon-desktop:/home/ramon# 

Això és tot, Carles...

---

### Post by papapep on 2008-05-27
El post núm. 24 d'aquest fil: [http://ubuntuforums.org/showthread.php?t=304444&page=3](http://ubuntuforums.org/showthread.php?t=304444&page=3)

diu que la fet funcionar aquesta placa. Fes-li un cop d'ull.

---

### Post by rajoar on 2008-05-27
...Encara que no és exactament la mateixa està basada amb el saa7134. Creus que hauria de provar això sense cap variació?:

Originally Posted by tzulberti  View Post
Yo tengo una saa7134...
Mini How-to:
en /etc/modprobe.d/ crear un archivo llamado saa7134 con el siguiente contenido:
alias char-major-81 videodev
alias char-major-81-0 saa7134
options saa7134 tuner=37 card=51
Paso 2: reiniciar
Paso 3:
Configurar el tvtime, para que lea cable (dpkg-reconfigure tvtime). Dentro de la configuracion del tvtime, hacer que el mismo use PAL-NC y yo lo tengo que poner en TV (mono only)
Espero que eso te sea de ayuda, ya que a mi me funciona

---

### Post by CarlesOriol on 2008-05-27
ups... m'he deixat un grep abans d'AverMedia

dmesg | grep AverMedia

tot i que de moment portes molts números per haver de compilar els controladors. I això no és garantia de que et funcioni

---

### Post by rajoar on 2008-05-27
Doncs més del mateix..., res de res...

ramon@ramon-desktop:~$ dmesg | grep firm
ramon@ramon-desktop:~$ dmesg | grep dvb
ramon@ramon-desktop:~$ dmesg | grep AverMedia
ramon@ramon-desktop:~$

---

