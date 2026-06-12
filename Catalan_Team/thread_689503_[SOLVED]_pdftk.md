---
title: "[SOLVED] pdftk"
date: 2008-02-06
forum: Catalan Team
---

### Post by SiscoGarcia on 2008-02-06
Hola,

Després d'haver seguit amb interès el fil sobre ["unir arxius PDF en un de sol"]("http://ubuntuforums.org/showthread.php?t=688280") m'he descarregat i instal·lat el programa pdftk des del Synaptic i el tinc a /usr/bin (fent whereis pdftk al terminal). El que no he pogut és obrir-lo i fer-lo córrer. He vist [aquest fil]("http://ubuntuforums.org/showthread.php?t=292102") al fòrum anglès d'iniciació i he  googlejat per tal de cercar una manera d'instal·lar una llançadora, però no l'he trobada. De manera que agrairia que em donéssiu un cop de mà. Gràcies.

---

### Post by papapep on 2008-02-06
Botó de la dreta sobre l'escriptori i posa, si no recordo malament, crear una llançadora. A partir d'aquí, fiques els paràmetres que et demani i no hauria de tenir més secrets.

---

### Post by CarlesOriol on 2008-02-06
Poca cosa farem amb una llançadora. És un programa que funciona en linia de comandes.

Si vols un programa gràfic usa el que et va recomanar la lluisa a l'altre fil

---

### Post by papapep on 2008-02-06
Doncs aleshores tinc clar que el que et fa falta és el [pdfsam]("http://www.pdfsam.org/") (pdf split and merge).

---

### Post by SiscoGarcia on 2008-02-06
Gràcies a tots dos, de fet sí que és això el que vull, fer-ho de forma gràfica; ho sento papapep, encara no controlo prou el terminal:(

Ara el baixo i miro d'instal·lar-me'l, tot i que, [pel que he vist]("http://www.pdfsam.org/?page_id=10"), necessita suport Java per córrer.

Us tindré informats.

---

### Post by SiscoGarcia on 2008-02-06
Em sembla molt que sóc un negat per les comandes. No me'n surto d'instal·lar el codi font. Us enganxo una captura del terminal, a veure si podeu ajudar-me. (papapep, m'he llegit el teu [manual sobre línies de comandes]("https://wiki.ubuntu.com/JosepS%c3%a0nchez/documentaci%c3%b3/interpret_comandes") abans d'intentar instal·lar-lo però res.:confused:

---

### Post by papapep on 2008-02-06
No pateixis, només és problema de conceptes. És que no cal que "instal·lis" el codi font, baixa't [el binari]("http://http://downloads.sourceforge.net/pdfsam/pdfsam-0.7sr1-out.zip?use_mirror=osdn").

Un cop l'hagis baixat, descomprimeix la carpeta on vulguis. Dins, entre altres coses, trobaràs un fitxer de nom **pdfsam-0.7sr1.jar**. Aquest fitxer és el que has d'executar per a tenir l'aplicació funcionant. Sense més ;-)

```
java -jar pdfsam-0.7sr1.jar
```

Cal que t'asseguris de que tens el paquet sun-java6-bin instal·lat per a que funcioni:

```
sudo aptitude install sun-java6-bin
```

Si ja el tens no farà res, si no el tens l'instal·larà.

---

### Post by SiscoGarcia on 2008-02-07
Sí senyor, papapep. Me n'he sortit. Moltes gràcies. Només una cosa, havia de ser ```
java -jar pdfsam-0.7sr1[COLOR="Red"].jar[/COLOR]
``` perquè funcionés. La resta perfecte.

Una altra cosa, potser s'hauria de canviar el nom del fil pel de pdftk-pdfsam, no?

Ja diràs i després ho tanco.

Gràcies:)

---

### Post by SiscoGarcia on 2008-02-07
Una altra cosa, si no és abusar. És possible crear una llançadora pel pdfsam? Jo no me n'he sortit i l'única forma que tinc d'obrir-lo és per consola. Gràcies.

---

### Post by SiscoGarcia on 2008-02-07
Perdó papapep, acabo de veure que la comanda que recomanaves ja incloïa [COLOR="Red"].jar[/COLOR] al final i jo me l'havia saltada. :oops:

---

### Post by papapep on 2008-02-07
No, l'he rectificat per que si algú ho veia no ho fes malament. Jo m'havia deixat el .jar 

Au, dóna el fil com a resolt ;-)

---

### Post by SiscoGarcia on 2008-02-07
Bé, veig que l'hauré d'arrencar des de consola. Acabaràs convertint-nos a "consolaries", eh papapep ;) Què hi farem, menys és no res. Gràcies de tota manera. Tanco el fil.

---

### Post by papapep on 2008-02-07
Noooo, no cal!! (i que no senti precedent) :-D

Si crees una llançadora que invoqui el .jar aquest, crec que t'hauria de funcionar. Fes la prova!

---

### Post by SiscoGarcia on 2008-02-07
Doncs no, papapep. O he perdut capacitats o no sé què em passa darrerament. Si no ho entenc malament, com pots veure a la captura, he invocat el .jar però no llença res. El que em mosqueja és que diu que m'ha denegat el permís. Li canvio els permisos i tampoc no me'n surto. Què puc fer?

Gràcies.

---

### Post by papapep on 2008-02-07
Enganxan's el que mostrin les següents ordres:

```
ls -la /home/sisco/
ls -la /home/sisco/Documents/
ls -la /home/sisco/Documents/pdfsam-basic/
```

---

### Post by SiscoGarcia on 2008-02-07
Allà va:

sisco@sisco-laptop:~$ ls -la /home/sisco/
total 3184
drwxr-xr-x 34 sisco sisco    4096 2008-02-07 17:43 .
drwxr-xr-x  4 root  root     4096 2008-02-04 19:03 ..
drwx------  3 sisco sisco    4096 2008-02-05 19:38 .adobe
-rw-------  1 sisco sisco    1807 2008-02-07 16:18 .bash_history
-rw-r--r--  1 sisco sisco     220 2008-02-04 18:13 .bash_logout
-rw-r--r--  1 sisco sisco    2298 2008-02-04 18:13 .bashrc
drwxr-xr-x  3 sisco sisco    4096 2008-02-04 18:21 .cache
drwxr-xr-x  4 sisco sisco    4096 2008-02-05 09:23 .config
-rw-------  1 sisco sisco      28 2008-02-07 17:43 .dmrc
drwxr-xr-x  3 sisco sisco    4096 2008-02-07 10:56 Documents
drwxr-xr-x  2 sisco sisco    4096 2008-02-07 16:47 Escriptori
-rw-------  1 sisco sisco      16 2008-02-04 18:21 .esd_auth
drwxr-xr-x  7 sisco sisco    4096 2008-02-07 16:49 .evolution
lrwxrwxrwx  1 sisco sisco      26 2008-02-04 18:13 Examples -> /usr/share/example-content
drwx------  3 sisco sisco    4096 2008-02-06 19:53 file:
drwxr-xr-x  2 sisco sisco    4096 2008-02-07 09:55 .fontconfig
drwx------  5 sisco sisco    4096 2008-02-07 17:43 .gconf
drwx------  2 sisco sisco    4096 2008-02-07 17:52 .gconfd
-rw-r-----  1 sisco sisco       0 2008-02-06 19:54 .gksu.lock
drwxr-xr-x  3 sisco sisco    4096 2008-02-04 18:21 .gnome
drwx------ 13 sisco sisco    4096 2008-02-07 16:49 .gnome2
drwx------  2 sisco sisco    4096 2008-02-04 18:21 .gnome2_private
drwxr-xr-x  2 sisco sisco    4096 2008-02-06 11:56 .gstreamer-0.10
-rw-r--r--  1 sisco sisco     118 2008-02-07 17:43 .gtk-bookmarks
-rw-r--r--  1 sisco sisco      87 2008-02-04 18:21 .gtkrc-1.2-gnome2
-rw-------  1 sisco sisco     855 2008-02-07 17:43 .ICEauthority
drwxr-xr-x  2 sisco sisco    4096 2008-02-07 16:48 .icons
drwxr-xr-x  2 sisco sisco    4096 2008-02-07 16:47 Imatges
drwxr-xr-x  2 sisco sisco    4096 2007-11-21 00:24 install_flash_player_9_linux
-rw-r--r--  1 sisco sisco 3036127 2008-02-05 09:23 install_flash_player_9_linux.tar.gz
drwxr-xr-x  3 sisco sisco    4096 2008-02-04 18:21 .local
drwx------  3 sisco sisco    4096 2008-02-05 19:38 .macromedia
drwx------  3 sisco sisco    4096 2008-02-04 18:21 .metacity
drwx------  3 sisco sisco    4096 2008-02-05 09:07 .mozilla
drwxr-xr-x  3 sisco sisco    4096 2008-02-05 19:44 Música
drwxr-xr-x  3 sisco sisco    4096 2008-02-07 16:49 .nautilus
drwx------  3 sisco sisco    4096 2008-02-07 11:01 .openoffice.org2
drwxr-xr-x  2 sisco sisco    4096 2008-02-04 18:21 Plantilles
-rw-r--r--  1 sisco sisco     566 2008-02-04 18:13 .profile
drwxr-xr-x  2 sisco sisco    4096 2008-02-04 18:21 Públic
-rw-------  1 sisco sisco     308 2008-02-07 11:01 .recently-used
-rw-r--r--  1 sisco sisco   20857 2008-02-07 16:49 .recently-used.xbel
-rw-r--r--  1 sisco sisco       0 2008-02-04 18:22 .sudo_as_admin_successful
drwxr-xr-x  2 sisco sisco    4096 2008-02-07 16:48 .themes
drwx------  4 sisco sisco    4096 2008-02-06 22:25 .thumbnails
drwx------  2 sisco sisco    4096 2008-02-04 18:21 .Trash
drwxr-xr-x  2 sisco sisco    4096 2008-02-04 18:22 .update-manager-core
drwx------  2 sisco sisco    4096 2008-02-04 18:21 .update-notifier
drwxr-xr-x  2 sisco sisco    4096 2008-02-04 18:21 Vídeos
-rw-------  1 sisco sisco     123 2008-02-07 17:43 .Xauthority
-rw-r--r--  1 sisco sisco    5123 2008-02-07 17:43 .xsession-errors


sisco@sisco-laptop:~$ ls -la /home/sisco/Documents/
total 4496
drwxr-xr-x  3 sisco sisco    4096 2008-02-07 10:56 .
drwxr-xr-x 34 sisco sisco    4096 2008-02-07 17:43 ..
-rw-r--r--  1 sisco sisco   39936 2008-02-07 10:55 cartaampes.doc
-rw-r--r--  1 sisco sisco  528551 2008-02-07 10:02 pdfsam-0.7sr1-out-src.zip
-rw-r--r--  1 sisco sisco 4004142 2008-02-06 23:13 pdfsam-0.7sr1-out.zip
drwxr-xr-x  5 sisco sisco    4096 2007-06-12 18:21 pdfsam-basic
-rw-r--r--  1 sisco sisco      66 2008-02-07 10:37 pdfsam.txt

Aquest pdfsam.txt l'he creat jo per tenir clar com arribar-hi des de consola.

i

sisco@sisco-laptop:~$ ls -la /home/sisco/Documents/pdfsam-basic/
total 172
drwxr-xr-x 5 sisco sisco   4096 2007-06-12 18:21 .
drwxr-xr-x 3 sisco sisco   4096 2008-02-07 10:56 ..
-rw-r--r-- 1 sisco sisco    574 2008-02-07 10:10 config.xml
drwxr-xr-x 2 sisco sisco   4096 2007-08-28 14:43 doc
drwxr-xr-x 2 sisco sisco   4096 2007-08-28 14:43 lib
-rw-r--r-- 1 sisco sisco  44503 2007-08-28 13:28 pdfsam-0.7sr1.jar
-rw-r--r-- 1 sisco sisco 100864 2007-08-28 11:41 pdfsam-starter.exe
drwxr-xr-x 4 sisco sisco   4096 2007-08-28 14:43 plugins

Ja diràs.

---

### Post by papapep on 2008-02-07
Molt bé. Canviem alguns permisos:

```
chmod 755 /home/sisco/Documents/pdfsam-basic/pdfsam-0.7sr1.jar
```

I ara prova a veure si funciona la llançadora.

---

### Post by SiscoGarcia on 2008-02-07
No hi ha manera, papapep. Què és el que no faig bé?

1.- Clico amb el botó contrari a l'escriptori i demano "Crea una llançadora"
2.- Trio Tipus: Aplicació (potser és aquest el problema?)
3.- Li poso nom "pdfsam".
4.- Trio l'Ordre...Navego... fins que hi arribo "/home/sisco/Documents/pdfsam-basic/pdfsam-0.7sr1.jar"
5.- Clico "D'acord" i ja està.

Doncs quan vull obrir no fa res.  :(

---

### Post by papapep on 2008-02-07
Prova a anar amb el navegador de fitxers fins on tens el pdfsam-0.7sr1.jar i amb el botó de la dreta del ratolí ves fins a on parla de amb quina aplicació obrir-lo i digues-li que ho fagi amb la màquina virtual java.

---

### Post by SiscoGarcia on 2008-02-07
D'acord, així l'obre i sempre és més ràpid que fer-ho per consola; al menys per mi ;)

Moltíssimes gràcies pel teu interès, de debò.

---

