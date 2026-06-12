---
title: "K3b - problema a l'hora de gravar cd's"
date: 2007-11-24
forum: Catalan Team
---

### Post by neska on 2007-11-24
Hola,
m'ha sorgit un problema amb el K3b, i és que no em deixa gravar un cd, cosa que abans no m'havia passat mai... Ja fa temps que tinc el kubuntu, tot i que me'l van instal·lar, i fins ara sempre havia pogut gravar cd's sense problemes. Dir que no tinc ni idea de solucionar res del que em vagi sorgint, per tant, demano que, si algú sap com solucionar el problema (copiat a continuació) m'ho expliqui de manera fàcil i entenedora. Gràcies!!


```
System
-----------------------
K3b Version: 1.0.3

KDE Version: 3.5.8
QT Version:  3.3.7
Kernel:      2.6.22-14-generic
Devices
-----------------------
SONY CD-ROM CDU5211 YYS7 (/dev/scd1, ) [CD-ROM] [Error] [Cap]

SONY CD-RW  CRX175E 1.0j (/dev/scd0, ) [CD-R, CD-RW, CD-ROM] [CD-ROM, CD-R, CD-RW] [SAO, TAO, En brut, SAO/R96R, RAW/R96R]
Used versions
-----------------------
cdrecord: 1.1.6

cdrecord
-----------------------
/usr/bin/X11/wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.
scsidev: '/dev/scd0'
devname: '/dev/scd0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.6
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 0 = CD-DA
Driveropts: 'burnfree'
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'SONY    '
Identification : 'CD-RW  CRX175E  '
Revision       : '1.0j'
Device seems to be: Generic mmc CD-RW.
Current: 0x0009 (CD-R)
Profile: 0x0008 (CD-ROM) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x000A (CD-RW) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96R RAW/R96R
Drive buf size : 1821440 = 1778 KB
Drive DMA Speed: 2694 kB/s 15x CD 1x DVD
FIFO size      : 12582912 = 12288 KB
pregap1: -1
Track 01: audio   38 MB (03:49.41) no preemp swab copy
Track 02: audio   37 MB (03:41.62) no preemp swab copy
Track 03: audio   33 MB (03:20.16) no preemp swab copy
Track 04: audio   32 MB (03:11.72) no preemp swab copy
Track 05: audio   38 MB (03:47.56) no preemp swab copy
Track 06: audio   30 MB (03:03.02) no preemp swab copy
Track 07: audio   42 MB (04:10.96) no preemp swab copy
Track 08: audio   30 MB (02:58.65) no preemp swab copy
Track 09: audio   34 MB (03:25.48) no preemp swab copy
Track 10: audio   51 MB (05:07.49) no preemp swab copy
Track 11: audio   52 MB (05:11.41) no preemp swab copy
Track 12: audio   30 MB (03:04.01) no preemp swab copy
Track 13: audio   37 MB (03:42.98) no preemp swab copy
Track 14: audio   36 MB (03:34.32) no preemp swab copy
Track 15: audio   38 MB (03:47.26) no preemp swab copy
Track 16: audio   41 MB (04:04.56) no preemp swab copy
Track 17: audio   40 MB (03:59.21) no preemp swab copy
Track 18: audio   34 MB (03:25.80) no preemp swab copy
Speed set to 1411 KB/s
Track 19: audio   43 MB (04:16.32) no preemp swab copy
Track 20: audio   32 MB (03:13.38) no preemp swab copy
Track 21: audio   34 MB (03:24.22) no preemp swab copy
Total size:      790 MB (78:19.60) = 352470 sectors
Lout start:      790 MB (78:21/45) = 352470 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 5
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type B, low Beta category (B-) (4)
  ATIP start of lead in:  -11607 (97:27/18)
  ATIP start of lead out: 359849 (79:59/74)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 18
Manufacturer: Plasmon Data systems Ltd.
Blocks total: 359849 Blocks current: 359849 Blocks remaining: 7379
Starting to write CD/DVD at speed   8.0 in real SAO mode for single session.
Last chance to quit, starting real write in  2 seconds.
   1 seconds.
   0 seconds.
 Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Sending CUE sheet...
Writing pregap for track 1 at -150
Starting new track at sector: 0
Track 01:    0 of   38 MB written.
Track 01:    1 of   38 MB written (fifo  94%) [buf  78%]  71.0x.
Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 00 02 6D 00 00 1B 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: F1 00 03 FF FF D2 A9 12 00 00 00 00 02 00 00 00
Sense Key: 0x3 Medium Error, deferred error, Segment 0
Sense Code: 0x02 Qual 0x00 (no seek complete) Fru 0x0
Sense flags: Blk -11607 (valid) 
cmd finished after 0.130s timeout 200s
/usr/bin/X11/wodim: A write error occured.
/usr/bin/X11/wodim: Please properly read the error message above.
write track data: error after 1460592 bytes
Writing  time:   18.483s
Average write speed 381.6x.
Fixating...
Fixating time:    0.015s
/usr/bin/X11/wodim: fifo had 215 puts and 24 gets.
/usr/bin/X11/wodim: fifo was 0 times empty and 2 times full, min fill was 91%.

cdrecord command:
-----------------------
/usr/bin/X11/wodim -v gracetime=2 dev=/dev/scd0 speed=12 -dao driveropts=burnfree -eject -useinfo -audio /tmp/kde-neska/k3b_audio_0_01.inf /tmp/kde-neska/k3b_audio_0_02.inf /tmp/kde-neska/k3b_audio_0_03.inf /tmp/kde-neska/k3b_audio_0_04.inf /tmp/kde-neska/k3b_audio_0_05.inf /tmp/kde-neska/k3b_audio_0_06.inf /tmp/kde-neska/k3b_audio_0_07.inf /tmp/kde-neska/k3b_audio_0_08.inf /tmp/kde-neska/k3b_audio_0_09.inf /tmp/kde-neska/k3b_audio_0_10.inf /tmp/kde-neska/k3b_audio_0_11.inf /tmp/kde-neska/k3b_audio_0_12.inf /tmp/kde-neska/k3b_audio_0_13.inf /tmp/kde-neska/k3b_audio_0_14.inf /tmp/kde-neska/k3b_audio_0_15.inf /tmp/kde-neska/k3b_audio_0_16.inf /tmp/kde-neska/k3b_audio_0_17.inf /tmp/kde-neska/k3b_audio_0_18.inf /tmp/kde-neska/k3b_audio_0_19.inf /tmp/kde-neska/k3b_audio_0_20.inf /tmp/kde-neska/k3b_audio_0_21.inf
```

---

### Post by orestesmas on 2007-11-24
Segons els missatges que copies tens un error d'escriptura indeterminat.

1) Has provat a utilitzar més d'un CD? Podria estar ratllat...

2) Has provat d'utilitzar una altra marca de CD verges? L'has canviada darrerament? Algunes marques són força dolentes...

3) Has provat la gravadora en un altre sistema operatiu (windows, per exemple)? Hi ha certa possibilitat que la gravadora s'espatlli de sobte, són aparells força delicats.

4) Has fet recentment alguna operació que pugui afectar al funcionament de la gravadora? (per exemple, actualitzar el sistema).

---

### Post by CarlesOriol on 2007-11-25
Sobre tot fixa't en això que et diu l'Orestes de comprovar el disc o provar d'una altra marca ja que l'error és:

Sense Key: 0x3 Medium Error, deferred error, Segment 0

...i medium no vol dir vident ;-)

---

### Post by jaume69 on 2007-11-25
a mi tampoc em funciona gaire bé gravar CDs,lo de canviar de marca no ho he provat(ho provaré).
Jo el problema que tinc que no em grava bé les ISOS,per exemple música si que ho grava bé.
[[COLOR="Red"]L'error[/COLOR]]("https://answers.launchpad.net/ubuntu/+question/18250") que em donava a mi es similar al teu.
Ja ho arreglaran suposo...:confused:
Ciau.

---

### Post by CarlesOriol on 2007-11-25
No liem la troca. L'error que tu Jaume comentes és un i aquest és un altre. El fet que es produeixin al mateix programa no vol dir que passi el mateix... 

Mira el teu log i el seu veuras que no te res a veure. O pot ser a tu també et deia medium error????

---

### Post by CarlesOriol on 2007-11-25
> **jaume69 said:**
> 
[[COLOR="Red"]L'error[/COLOR]]("https://answers.launchpad.net/ubuntu/+question/18250") que em donava a mi es similar al teu.

Ciau.

En aquest missatge al launchpad no aconseguiras cap resposta ja que :

**Track 01: 697 of 697 MB written (fifo 100%) [buf 100%] 10.5x.**
Track 01: Total bytes read/written: **731009024/731009024** (356938 sectors).

Indica que tot a funcionat correctament.
I la resposta del k3bsetup... és una eina de configuració del k3b que avui ja no existeix per que és innecessària.

Perdona que no respongui al launchpad però ho has posat a l'apartat en castellà i no acostumo...

---

### Post by neska on 2007-11-25
Gràcies per tot nois! Ara no ho provaré pq és molt tard, po dma o l'altre m'ho miraré i si em segueix fallant, ja tornaré a dir alguna cosa!
Salut!

---

### Post by jaume69 on 2007-11-25
Doncs no sé pas on és el problema,(que quan reinicies sembla que hagi gravat bé la ISO,li dones a Iniciar o Instal.lar i queda bloquejat)deu ser cosa estrictament de computació...
Bé,gràcies.:-)

---

