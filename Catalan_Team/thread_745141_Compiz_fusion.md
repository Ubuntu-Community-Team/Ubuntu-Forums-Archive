---
title: "Compiz fusion"
date: 2008-04-04
forum: Catalan Team
---

### Post by lFossil on 2008-04-04
Hola nois, seguint el consell del Gambusí preguntaré això al fòrum perquè no sembla que trovi què passa quan intento instal·lar el Compiz Fusion.
Quan poso el comand  ($ sudo aptitude install compiz # compiz-gnome AND/OR compiz-kde) mapareix el següent missatge [http://reg.imageshack.us/content.php?page=blogpost&files=img297/8695/captura1ir1.png](http://reg.imageshack.us/content.php?page=blogpost&files=img297/8695/captura1ir1.png)
Alguna idea?:) 

A més a més, a l'hora de intentar descarregar actualitzacions em dona el mateix error, té alguna relació?  [http://reg.imageshack.us/content.php?page=blogpost&files=img170/4725/captura2og3.png](http://reg.imageshack.us/content.php?page=blogpost&files=img170/4725/captura2og3.png)

---

### Post by papapep on 2008-04-04
> sudo aptitude install compiz # compiz-gnome AND/OR compiz-kde

....d'on has tret la sintaxi d'aquesta ordre?

```
sudo aptitude install compiz compiz-gnome
```

farà la feina.

Et recordo que no et cal fer la impresió de pantalla, és engorrós per a tu i per nosaltres. Enganxa el text del terminal aquí i tot és més simple. ;-)

---

### Post by lo gambusí on 2008-04-04
edito: ja t'han respost :P

---

### Post by lFossil on 2008-04-04
Em surt altre cop el mateix:


E: El tipus «wget» no és conegut en la línia 41 de la llista de fonts /etc/apt/sources.list
E: El tipus «wget» no és conegut en la línia 41 de la llista de fonts /etc/apt/sources.list
E: No s'ha pogut llegir la llista de fonts.
E: El tipus «wget» no és conegut en la línia 41 de la llista de fonts /etc/apt/sources.list
E: No s'ha pogut llegir la llista de fonts.
jasiel@jasiel-laptop:~$

---

### Post by papapep on 2008-04-04
Tens algun error al fitxer que t'indica. Enganxa'ns el seu contingut, si us plau:

```
sudo nano /etc/apt/sources.list
```

---

### Post by lFossil on 2008-04-04
Fica això:


deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy restricted multiverse universe main
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy restricted multiverse universe $

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates restricted multiverse unive$
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates restricted multiverse u$

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe

                             [ 44 línies llegides ]
^G Ajuda     ^O Desa      ^R Llegeix   ^Y Pàg Ant   ^K Talla     ^C Pos Act
^X Surt      ^J Justifica ^W Cerca     ^V Pàg Seg   ^U Destalla e^T Ortografia

---

### Post by papapep on 2008-04-04
Ostres, ostres, quin batibull que hi tens... és obvi que ha de petar per totes bandes :-D

Ens sortirà més a compte començar de cap i de nou que no pas corregir el que hi ha.

Fes a un terminal:

```
sudo nano /etc/apt/sources.list
```

esborra tot el que hi ha, i enganxa-hi això:

```
deb http://archive.ubuntu.com/ubuntu/ gutsy restricted multiverse universe main
deb-src http://archive.ubuntu.com/ubuntu/ gutsy restricted multiverse universe main

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates restricted multiverse universe main
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-updates restricted multiverse universe main

deb http://security.ubuntu.com/ubuntu gutsy-security restricted multiverse universe main

```

Deses amb Ctrl+X i un cop fet fas:

```
sudo aptitude update
```

i immediatament després:

```
sudo aptitude safe-upgrade
```

i tornes a provar la ordre d'instal·lació del compiz (la meva, no la teva :-D)

---

### Post by CarlesOriol on 2008-04-05
papapep:

Jo ho veig bé... fixa't que li has demanat un **nano** en comptes d'un cat

---

### Post by lFossil on 2008-04-05
Ei  gràcies papapep, he fet el que m'has dit i s'ha instal·lat correctament, però a l'hora de crear una llançadora d'aplicacions a l'escriptori, com diu el segon pas de la guia per a l'instalació del compiz fusion en l'ubuntu 7,10 he afegit ( compiz --replace) al terminal però em surt això:


jasiel@jasiel-laptop:~$ compiz --replace
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 

Avans ja em sortia aquest error, què pot ser?

---

### Post by papapep on 2008-04-05
Jo de gràfiques no controlo gaire, per això tenim el CarlesOriol :-D, però crec que hauries de provar a configurar la teva gràfica (per cert, quina tens?) amb un programa que es diu [Envy]("http://albertomilone.com/ubuntu/nvidia/scripts/legacy/envy_0.9.10-0ubuntu9_all.deb").

Per poder dir-nos quina placa tens, fes:

```
lspci | grep VGA
```

i enganxa'ns el que et surti.

---

### Post by lFossil on 2008-04-05
Tinc aquesta placa:
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
Ara em baixaré aquest programa.

---

### Post by lluisanunez on 2008-04-05
Però... si tens Ubuntu 7.10 gutsy, el compiz-fusion ja el tens insta&#320;lat per defecte, no?
Pots comprovar-ho: a Administració > Preferències > Apariència t'han de sortir les opcions d'efectes especials (encara que no s'activin)
El que et faltaria insta&#320;lar és el compiz-settings-manager, a més de l'Envy per controlar la teva tarja.

---

