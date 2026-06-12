---
title: "Gran embolic amb temes de GRUB"
date: 2008-05-08
forum: Catalan Team
---

### Post by Joan Marc on 2008-05-08
Hola,
Estic molt confós, i les persones que m'han intentat ajudar encara m'hi han deixat mes :(.
El cas es que farà un parell de dies, quan engegava l'ordinador, aquest es reniciava abans de mostrar el GRUB.
Vaig demanar ajuda a un amic, i em va dir que entrant amb la consola de recuperació de WinXP, i teclejant fixmbr i fixboot, segur que podria tornar a entrar...
El cas es que no se si va entendre que jo abans tenia el meu GRUB amb ubuntu 8.04 i Windows XP.
El cas es que ara si que arranca el Windows XP, però no em mostra el GRUB.
He demanat ajuda a d'altres persones, i m'han dit que fins ara estaba utilutzant un GRUB que està a l'ubuntu (que és cert xD), i que és aquest el que està espatllat.
El cas és que vaig entrar amb un LiveCD, i el vaig canviar per complet per una copia de seguretat que havia fet després d'actualitzar, amb l'esperança que així tornés a sortir.
Però això no va passar, i ara em trobo que no puc iniciar l'ubuntu perquè no hi ha GRUB...

Em sabríeu dir quines diferències hi ha entre tenir el GRUB a l'ubuntu o tenir-lo a l'XP? Vaig errat d'idees?...com ho puc arreglar?

PErdoneu que posi assumptes d'altres SO, com entrar a la consola de recuperació i axo, però m'agradaria tornar a entrar a l'ubuntuuuu 	:cry:

---

### Post by menut on 2008-05-08
Mira't el [WinGRUB (instal·la el GRUB des del Hasefroch).]("http://sourceforge.net/projects/grub4dos")

---

### Post by Joan Marc on 2008-05-08
Merci per contestar, el que passa es que no se què he de fer amb el WinGRUB... saps d'algun manual?

---

### Post by CarlesOriol on 2008-05-08
Cerca restaurar grub al fòrum.

D'això ja n'hem parlat mil cops sempre pel mateix. 

Si us plau llegeix [http://ubuntuforums.org/showthread.php?t=599965](http://ubuntuforums.org/showthread.php?t=599965).

---

### Post by Joan Marc on 2008-05-08
Perdona'm CarlesOriol, jo em pensava que era diferent a una restauració del grub com quan instales el Windows, ja que per restaurar-lo, s'ha de fer:
```

> sudo grub
> root (hdX,Y)
> **setup** (hdX)
> quit 
```
Però jo en comptes de posar setup, li posava install, i com que em donava error, em pensava que es tractava d'un problema més greu.

Merci però, als dos tant en Menut com en CarlesOriol per la contribució

---

### Post by Miquel Ubuntero on 2008-05-08
Hola Joan Marc.
Intentaré d'aclarir-te una mica el lio que comentes que tens.
Tu preguntes textualment “Em sabríeu dir quines diferències hi ha entre tenir el GRUB a l'ubuntu o tenir-lo a l'XP?”
Be, el GRUB no el tens ni al xp ni al Ubuntu. Als disc durs hi ha una part anomenada MBR (Master Boot Record), és en aquesta par del disc on l'instal·lador del Ubuntu i posa el GRUB.
El problema ve quant després del Ubuntu hi poses el guindous. Aquest últim s.o. és tan inútil que no te en compte si en tens d'altres i esborra el MBR posant-hi el seu arrencador. Es per aquest motiu que es recomana primer instal·lar win i després altres s.o. (per ex. Ubuntu) que al posar-hi el GRUB respectin altres sistemes que hi puguin haver.
Espero que ara ho tinguis una miqueta més clar.
Salut!

---

### Post by Joan Marc on 2008-05-08
Ara ja ho entenc més bé.
Com que el menu.lst que obria des del terminal estava en una carpeta del sistema de l'ubuntu, em pensava que pertanyia a aquest :D

Gràcies!

---

### Post by Miquel Ubuntero on 2008-05-09
Hola Joan Marc.

Crec que l'arxiu menu.lst que està a una carpeta de l'Ubuntu, es com una copia o semblant, del arxiu que està al MBR.
Es per aixó que encara que s'esborri del MBR, sempre el podrem recuperar del nostre sistema, tal com s'explica aquí:
[http://www.guia-ubuntu.org/index.php?title=Recuperar_GRUB](http://www.guia-ubuntu.org/index.php?title=Recuperar_GRUB)
Salut!

---

