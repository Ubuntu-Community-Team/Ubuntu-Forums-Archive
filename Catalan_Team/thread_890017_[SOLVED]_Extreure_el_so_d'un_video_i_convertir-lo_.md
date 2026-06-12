---
title: "[SOLVED] Extreure el so d'un video i convertir-lo en .ogg"
date: 2008-08-14
forum: Catalan Team
---

### Post by LitusMayol on 2008-08-14
Hola-hola!

Doncs crec que el títol ja és pro explícit. Vull extreure el so d'[aquest]("http://http://www.youtube.com/watch?v=n9HKsvHgs8Q") video. És un video d'una versió acústica *Send Me a sign* de *Gamma Ray* (un grup que m'encanta) que ells mateixos van fer a Tokyo el 2003.

El video el puc baixar amb un script que en **Quiron** va fer un dia que s'avorria. Però un cop el tinc guarda... com n'extrec el so per tal de fer-ne un *.ogg*?(la vull poder portar al reproductor, amunt i avall! :) )

Merci! :P

---

### Post by papapep on 2008-08-14
El vídeo el pots copiar del directori /tmp després d'haver-lo reproduït al navegador sense necessitat de res més. Prova-ho.

Respecte l'extracció a ogg, segur que alguna ordre similar a la d'aquest post (ai, ai, ai.....) indicant que vols un ogg en vers d'un mp3 farà la feina:

[http://ubuntuforums.org/showpost.php?p=5144559&postcount=2](http://ubuntuforums.org/showpost.php?p=5144559&postcount=2)
[B]
EDICIÓ 00:05h:[/B]

No sembla que hagi una manera directa de passar l'audio a ogg, però fent un pas més sí que es pot:

```

sudo aptitude install mp32ogg
mp32ogg --quality=10 --delete --rename=%t audio.mp3
```

així et crearà un fitxer audio.ogg.

---

### Post by LitusMayol on 2008-08-15
Merci **papapep**!

El tema d'anar a */tmp/* i copiar el video a l'Escriptori genial! (No ho sabia!). Però el video es veu com a càmara lenta... Tot i així he pensat que potser el fitxer d'àudio que porta intrísec no estari malmès ni re,però quan he intentat fer el pas que indicava l'**orestesmas** al post mira que m'ha deixat anar:
```
litus@mayolets-desktop:~/Escriptori$ mplayer -dumpaudio -dumpfile audio.mp3 SendMe.flv
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: AMD Sempron(tm) Processor 2800+ (Family: 15, Model: 44, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing SendMe.flv.
libavformat file format detected.
[lavf] Video stream found, -vid 0
[lavf] Audio stream found, -aid 1
VIDEO:  [FLV1]  320x240  0bpp  25.000 fps    0.0 kbps ( 0.0 kbyte/s)
Core dumped ;)

Exiting... (End of file)
litus@mayolets-desktop:~/Escriptori$ 
```

Sabeu que vol dir?

Per tan em quedo igual que com estava:
[LIST=1]
[*]Sense video
[*]Sense so
[/LIST]

Merci de totes maneres!

---

### Post by papapep on 2008-08-15
> Playing SendMe.flv.
libavformat file format detected.
[lavf] Video stream found, -vid 0
[lavf] Audio stream found, -aid 1
VIDEO:  [FLV1]  320x240  0bpp  25.000 fps    0.0 kbps ( 0.0 kbyte/s)
**Core dumped ;)**



No tens un fitxer de nom audio.mp3 al directori on tens el SendMe.flv??? 
Em fa l'efecte que no ho has mirat bé...:-|

Jo vaig provar tot el procés abans d'explicar-t'ho i funciona perfectament.

---

### Post by LitusMayol on 2008-08-15
> **papapep said:**
> No tens un fitxer de nom audio.mp3 al directori on tens el SendMe.flv??? 
Em fa l'efecte que no ho has mirat bé...:-|

Val...Sóc un desastre. xD Hi és. Es que he vist "*core Dumped*" i he pensant "això no és bo"... Però com que tinc tres o quatre arxius per al **TuxGuitar** ni m'hi he fixat...](*,) Perdó **papapep**...:oops:

Així doncs el tema de extreure'n l'àudio (ara si que en el títol del post he posat "eStreure"...) està resolt.


Però el video se m'ha baixat sencer... però l'arxiu d'àudio és incomplet. Saps perquè pot ser això?



Merci! :)

---

### Post by papapep on 2008-08-15
L'única opció que se m'acudeix per a que no estigui sencer és que el que has visualitzat al navegador no estigui sencer a l'orígen o que l'hagis copiat abans d'acabar de descarregar-se.

---

### Post by LitusMayol on 2008-08-15
Acabo de baixar el video: m'he assegurat de que hi fóra tot sencer i...

```
litus@mayolets-desktop:~/Escriptori$ mplayer -dumpaudio -dumpfile audio.mp3 FlashIjHtNa.flv
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: AMD Sempron(tm) Processor 2800+ (Family: 15, Model: 44, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing FlashIjHtNa.flv.
File not found: 'FlashIjHtNa.flv'
Failed to open FlashIjHtNa.flv.


Exiting... (End of file)
litus@mayolets-desktop:~/Escriptori$
```

Ha variat el missatge... i no tinc l'arxiu. (me n'he assegurat, heheh)

---

### Post by papapep on 2008-08-15
No hauràs tancat el navegador abans de copiar-lo de /tmp, oi? si es fa s'esborra el fitxer temporal. Els fitxers que es desen a /tmp no tenen l'extensió flv, cal modificar-los el nom per a que ho tinguin...

---

### Post by LitusMayol on 2008-08-15
No no.
El navegador encara el tinc obert. No li havia canviat el nom. Ara ja ho he fet i em deia exactament el mateix...

Però ara, benvolgut **papapep**, ve el moment en que m'has de fúmer un clatellot de l'estil els que en Filemó reparteix sense parar a en Mortadelo. Havia canviat el nom per "SendMe"... hi trobes a faltar alguna cosa? Doncs si... Error elemental: el ".flv".

Com deia aquell anunci de cervesa: "*Increïble però cert*".



En fi, merci! I ho sento... :P

---

### Post by papapep on 2008-08-15
Bé, espero que aquestes experiències serveixin pels més novells per veure que hi ha certes coses bàsiques que s'han de verificar abans de pensar a demanar ajut. :-)

---

### Post by LitusMayol on 2008-08-15
Si **papa**(pep),
he après la lliçó!

---

### Post by LitusMayol on 2008-08-15
Perfecte ara que ja havia posat el "*[SOLVED]*"...

L'arxiu, si l'obro amb qualsevol reproductor de video (**Mplayer**, **GStreamer**...) Dura 3.16 (el que ha de durar). Per contra si l'obro amb qualsevol reproductor d'àudio (**Amarok**, **Rythmbox**...) dura 24 minuts llargs! (i simplement es va repetint la cançó).

Si el problema fóra que simplement és molt llarg, doncs apa vinga: **Ardour** i s'ha acabat. Però l'arxiu pesa 1,4Mb (cosa normal per una cançó de 3 minuts!)... 

Alguna idea?


**EDITO:**

Aquest problema s'acaba de convertir en curiositat!

Resulta que només reprodueixen (els reproductors d'àudio) els 3 minuts! 
Tot i així és curiós que en tots marqui 24 minuts...!

---

### Post by papapep on 2008-08-15
Passa'm la url del vídeo, si us plau.

---

### Post by LitusMayol on 2008-08-15
[Aquí]("http://es.youtube.com/watch?v=n9HKsvHgs8Q&feature=related") el tens. 


Que vols fer?

---

### Post by papapep on 2008-08-15
> Que vols fer? 

Escoltar la cançó.... :-P

No, provar si em passa el mateix, home.... :-D

---

### Post by papapep on 2008-08-15
Convertit a ogg:

Banshee: 3.36 min. sense problemes.
Amarok: 3.36 min. sense problemes.
Totem: 3.36 min. sense problemes.
Gxine: 3.36 min. sense problemes.
Kaffeine: 3.36 min. sense problemes.
Mplayer: 3.36 min. sense problemes.
VLC: 3.36 min. sense problemes.
Rhythmbox: 3.36 min. sense problemes.

Ja no tinc més reproductors per provar.....:-)

Conclusió: el problema sembla alié al procés de conversió (aka: és teu :-P).


PD: la cançó és divertida

---

### Post by LitusMayol on 2008-08-15
Ostres **papapep**, pots deixar de destrossar-me? :p


Doncs jo he reiniciat la sessió (vaja: sortir i tornar a entrar de tota la vida). I ja està. Ja em marca 3.36 mins. No ho sé el meu ordinador deu tenir ganes de venir amb mi a Gràcia aquesta nit i com que no el deixo em fastigueaj. hehe


(m'alegro que t'agradi Gamma Ray! heheh)

---

