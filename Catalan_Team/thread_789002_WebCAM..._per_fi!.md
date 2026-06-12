---
title: "WebCAM... per fi!"
date: 2008-05-10
forum: Catalan Team
---

### Post by Joan Marc on 2008-05-10
Hola!
No fa ni cinc minuts, que per aburriment, m'he connectat a l'aMSN.
Com que no sabia que fer, he mirat (per enèssima vegada) si em detectava la meva WebCAM, i per gran sorpresa s'ha engegat :D
Molt estranyat, he fet un lsusb, i m'he adonat que em surt igual que sempre (a la 7.10 també era així):
```
gami@gami:~$ lsusb
Bus 005 Device 005: ID 05e3:0702 Genesys Logic, Inc. USB 2.0 IDE Adapter
**Bus 005 Device 004: ID 05e1:0501 Syntek Semiconductor Co., Ltd **
Bus 005 Device 002: ID 0471:082b Philips 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 046d:c019 Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  

```
Després m'he fixat, que a l'aMSN surt com a v4l2: Syntek Usb Video Camera, i com podeu veure, a lsusb també surt...
No sé si és per l'actualització a Hardy Heron, o per la actualització de l'aMSN a 0.97 que m'ha detectat la webcam... sincerament jo estic un pèl estranyat, ja que amb Gutsy Gibbon, el lsusb era el mateix...

Bé, a part d'aquesta incògnita, també voldria demanar-vos aviam si sabeu d'algun programa que em permeti capturar imatges, video i so de la webcam, ja que des de l'aMSN no puc.

Fins ara!:lolflag:

---

### Post by pespin on 2008-05-10
De moment l'únic programa que he trobat pots veure'l aqui: [http://ubuntuforums.org/showpost.php?p=4749091&postcount=6]("http://ubuntuforums.org/showpost.php?p=4749091&postcount=6")

---

### Post by Joan Marc on 2008-05-10
Merci pespin :)
Quan faig:
```
streamer -q -c /dev/video1 -f rgb24 -r 25 -t 00:30:00 -o clip.avi -F stereo
```
Em surt això
```
gami@gami:~$ streamer -q -c /dev/video1 -f rgb24 -r 25 -t 00:30:00 -o clip.avi -F stereo
v4l2: open /dev/video1: No such file or directory
v4l2: open /dev/video1: No such file or directory
v4l: open /dev/video1: No such file or directory
no grabber device available
gami@gami:~$
```
Em diu que no ha trobat cap gravador... però l'aMSN si que el troba...¿?

---

### Post by pespin on 2008-05-10
Perquè estàs utilitzant un dispositiu que en el meu cas és adient però no en el teu. Jo tinc la càmera a /dev/video1 perquè el /dev/video0 el tinc ocupat per un altre maquinari, pero tu segurament deus tenir la càmera a /dev/video0

Per tant:

```
streamer -q -c /dev/video0 -f rgb24 -r 25 -t 00:30:00 -o clip.avi -F stereo
```


Per a més informacio:
$ streamer --help

$ man streamer

---

### Post by Joan Marc on 2008-05-10
si tens raó, és video0 (fent $streamer --help ho he comfirmat)
tinc un parell de preguntes:
- quan a "-t" es refereix a la durada del clip no?
- on es desen els clips?

GRacies.

---

### Post by orestesmas on 2008-05-10
> **Joan Marc said:**
> 
No sé si és per l'actualització a Hardy Heron, o per la actualització de l'aMSN a 0.97 que m'ha detectat la webcam... sincerament jo estic un pèl estranyat, ja que amb Gutsy Gibbon, el lsusb era el mateix...


No hi té res a veure. El "lsusb" només pregunta als dispositius USB, i aquests sempre han de contestar. És en funció de la resposta que el nucli decideix carregar un controlador específic o no, i la Hardy deu haver incorporat al que necessites.

> **Joan Marc said:**
> 
Bé, a part d'aquesta incògnita, també voldria demanar-vos aviam si sabeu d'algun programa que em permeti capturar imatges, video i so de la webcam, ja que des de l'aMSN no puc.


Ja te n'han dit algun, però n'hi ha més: VLC (VideoLan), MPlayer...

---

### Post by pespin on 2008-05-10
> - quan a "-t" es refereix a la durada del clip no?
Sí. Si vols tallar-lo abans del temps límit, prem CTRL+C

> - on es desen els clips?
```
-o clip.avi
```

a l'arxiu clip.avi desat al directori des d'on has fet córrer el streamer. :)

---

### Post by Joan Marc on 2008-05-10
> **orestesmas said:**
> Ja te n'han dit algun, però n'hi ha més: VLC (VideoLan), MPlayer...
orestesmas, merci pels programes, no sabia que des del VLC es pogués (des del MPlayer no ho he trobat) veure la webcam, el qur no trobo però, és cap opció per gravar el video... 
Ah! i gracies també per l'explicació.

[QUOTE=pespin]a l'arxiu clip.avi desat al directori des d'on has fet córrer el streamer. [/QUOTE]
L'streamer no l'he instal·lat del fil que m'has passat, ja que jo això dels tar-gz no ho domino i no me n'he sortit... jo l'he instal·lat des dels repositoris, per això no sé on és.

Estic buscant algun programa, n'he trobat un, el [iCam2]("http://linux.softpedia.com/get/Multimedia/Video/iCam2-559.shtml") però com he dit abans no sé instal·lar els .tar... aviam si tu ho pots fer i em dius què tal el programa... i de pas em dones un cop de ma per instal·lar-lo jeje.

Gracies als dos!:)

---

### Post by pespin on 2008-05-10
> L'streamer no l'he instal·lat del fil que m'has passat, ja que jo això dels tar-gz no ho domino i no me n'he sortit... jo l'he instal·lat des dels repositoris, per això no sé on és.

No, si jo també l'he instal·lat des del repositoris xDD

Et referies a on es guarda l'arxiu de video que es grava no? doncs llavors ja t'he respost :)

Si et refereixes a l'aplicació, no crea cap menú, has de fer-lo córrer des de la terminal. posant "streamer" ja et funciona. L'executable està situat a "/usr/bin/streamer".





Respecte a l'iCam2...

Instal·lació:

1 - Instal·lar dependències: sudo aptitude install libimlib2-dev

2 - Baixar l'arxiu: wget [http://prdownloads.sourceforge.net/icam2/iCam2-1.1.tar.gz?download](http://prdownloads.sourceforge.net/icam2/iCam2-1.1.tar.gz?download)

3 - Descomprimir l'arxiu: tar -zxvf iCam2-1.1.tar.gz

4 - Compil·lar: ./configure && make

5 - Instal·lar: sudo make install

6 - Córrer: iCam2

------

7 - Desinstal·lar: *situar-se a la carpeta des d'on has compilat* sudo make uninstall




Et poso la opció 7 perquè en el meu cas al engegar el programa simplement em diu "MMAP failed!" i no fa res més xDD

---

### Post by Joan Marc on 2008-05-12
He seguit el que m'has dit, però al fer correr l'iCam2 em surt això:
```
gami@gami:~$ iCam2
bash: iCam2: command not found

```

Seguiré buscant algun altre programa... aviam si el deu google m'ajuda :D
Gracies igualment!

---

### Post by oriolsbd on 2008-05-12
En comptes d'escriure simplement iCam2, prova de fer:
./iCam2

A veure si et funciona (assegura't que estiguis en el directori on s'ha deixat el fitxer iCam2.

Salut!

---

### Post by Joan Marc on 2008-05-12
> **pespin said:**
> Et poso la opció 7 perquè en el meu cas al engegar el programa simplement em diu "MMAP failed!" i no fa res més xDD

Gràcies oriolsbd, ara ja m'ha sortit... el problema és que també em surt el mateix error que en pespin...:(
Vés a saber què és això del MMAP...:confused:

---

### Post by pespin on 2008-05-12
Potser em vaig eqivocar al posar el nom de l'executable, que el vaig posar de memòria xD

pots buscar-lo amb la ordre:
$ locate *bin*icam*
$ locate *bin*iCam*

---

### Post by MiquelBLL on 2008-05-18
Un programa que esta be per la camara web es el Cheese.

---

### Post by Joan Marc on 2008-05-18
Oh! 
Bon programa, jo no l'havia trobat xDD
Gràcies Miquel.

---

