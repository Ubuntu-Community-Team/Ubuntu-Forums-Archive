---
title: "[SOLVED] Diferència entre lliure i disponible"
date: 2008-04-16
forum: Catalan Team
---

### Post by jodufi on 2008-04-16
Tot mirant la memòria que tinc ocupada del disc utilitzant el «Monitor del sistema», veig que hi ha una important diferència entre la memòria lliure (14.4GB) i la memòria disponible (11.2).

Algú em podria explicar quina diferència hi ha entre aquestes dues i on estan els 3GB? :confused:

Gràcies

---

### Post by crazyserver on 2008-04-16
Uh! a mi em coincideix en les 5 particions que tinc... estrany.. molt extrany
Potser lliure es el que tens realment i disponible es el que tens lliure per poder utilitzar en aquest moment (es a dir sense arxius temporals...) m'ho acabo d'inventar XD

---

### Post by RainCT on 2008-04-17
No m'hi havia fixat abans però jo també tinc diferències entre la memòria lliure i la disponible per les particions. A veure si algú ens ho pot aclarar.

---

### Post by lluisanunez on 2008-04-17
Ondia!
                                                   
/dev/sda1  /   lliure:  41.7 GB   disponible: 39.4GB
/dev/sda2 /media/data  lliure: 225.8 GB  disponible: 213.3 GB

---

### Post by papapep on 2008-04-17
El journaling de l'ext3?

---

### Post by lluisanunez on 2008-04-17
El journaling se'm menja 13GB? Veig que és proporcional...

---

### Post by papapep on 2008-04-17
No dic que sigui això, ha estat un pensament "en tecla alta". Ha estat el primer que m'ha vingut a la "alone in the dark" neurona...:)

EDITO: Bé, la intuició no era exacta del tot, però he fregat el pal:

[https://answers.launchpad.net/ubuntu/+source/gnome-system-monitor/+question/8609](https://answers.launchpad.net/ubuntu/+source/gnome-system-monitor/+question/8609)

> The ext3 filesystem reserves an amount of the total space for root. If some user (or daemon) fills the disk then a login couldn't be possible anymore. So even root couldn't login anymore to fix it. Therefore ext3 reserves an amount of 5% (default) of the filesystem for the root user to prevent it (it doesn't work if root fills the disk).

Available space is now the total free space including the reserved space for root.
Free space is the free space that you as a user can fill :)

It is possible to change this with tune2fs (PLEASE consult the manpage before using this tool).

---

### Post by crazyserver on 2008-04-17
Exacte!:D per això jo utilitzo reiserfs XD

Great!

---

### Post by jodufi on 2008-04-18
Gràcies per la resposta!

Ja em va passar un cop que no tenia memòria, i l'ordinador em feia el tonto. Crec que això s'hauria de millorar i que l'Ubuntu t'avisés quan t'estàs quedant sense memòria, i no que te n'adonis perquè l'ordinador fa coses paranormals o no pots iniciar sesió.

Ara que hi penso, si em quedo sense memòria, com entro amb l'usuari root?

---

### Post by papapep on 2008-04-18
Primer de tot _cal no confondre_ **memòria **(RAM) amb **espai d'emmagatzematge** (DISC DUR o similar). Són coses completament diferents.
Després, precisament per a que puguis gestionar una teòrica manca d'espai al disc dur, et deixa espai reservat per a root per a que puguis entrar com a tal i sol·lucionar el problema. 
Tot i això, fa temps que no em passa, però juraria que el sistema t'avisa quan et queda poc espai de disc. Juraria recordar haver vist una finestretra petita que mostrava el missatge aquest.

---

### Post by crazyserver on 2008-04-18
Jo també la recordo! I el primer cop que la vaig veure vaig pensar... Es més maca que quan et surt al Harsefroch Vindoves!

---

### Post by jodufi on 2008-04-18
> **papapep said:**
> Primer de tot _cal no confondre_ **memòria **(RAM) amb **espai d'emmagatzematge** (DISC DUR o similar). Són coses completament diferents.
Després, precisament per a que puguis gestionar una teòrica manca d'espai al disc dur, et deixa espai reservat per a root per a que puguis entrar com a tal i sol·lucionar el problema. 
Tot i això, fa temps que no em passa, però juraria que el sistema t'avisa quan et queda poc espai de disc. Juraria recordar haver vist una finestretra petita que mostrava el missatge aquest.

Perdó, on deia memòria em referia a disc dur. 

I no recordo que m'avisés.
Encara que pot ser que si que avisés, però com que estava utilitzant l'ordinador la meva companya, no li fes cas a l'avís. Jo només vaig sentir les seves queixes de que l'ordinador feia coses rares i no podia desar res. :)

Però encara estic amb el dubte de saber com s'entra amb root, ja que tinc entès que aquest està desactivat.

---

