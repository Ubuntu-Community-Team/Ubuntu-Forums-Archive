---
title: "estalvi de pantalla amb xfce"
date: 2007-12-19
forum: Catalan Team
---

### Post by hakd0c on 2007-12-19
Hola,

Tinc un ordinador amb xfce per veure la tele, el problema es que estic mirant algun programa i de cop la pantalla es queda en negra, moc la rateta i es recupera (tipic estalvi de pantalla o estalvi d'energia)

Ja he anat a la configuració de l'screensaver hi he deshabilitat la opció de que es carregui l'estalvi de pantalla quant hi ha inactivitat, però continua passant.

Hi ha algun lloc on pugui controlar lo que ab hasefroch es "l'ahorro de energia" o alguna manera amb mode text de poder comprovar aquesta parametres?

---

### Post by papapep on 2007-12-19
Crec que per a anar a configurar coses d'aquestes has d'invocar la ordre "xfce-setting-show".

---

### Post by kukat on 2007-12-19
Gràcies!! Hem passava el mateix, i anava a preguntar-ho. Ara miraré d'arreglar-ho.

---

### Post by hakd0c on 2007-12-19
Hola,

Ja he executat el :
```

xfce-settings-show

```

hi vaig a parar al mateix lloc que des dels menus. I a l'apartat del screensaver tinc desmarcada la opció que posa:
```

activate screensaver when computer is idle

```

---

### Post by papapep on 2007-12-19
Doncs així assumeixo que el que se t'activa no és el salvapantalles, ja que no el tens instal·lat, sinó que t'entra en hivernació o suspensió o com punyetes es digui. O sigui, que has d'anar a on es configuri l'estalvi d'energia.

---

### Post by kukat on 2007-12-19
A mi hem passa el mateix. 

Tinc el protector de pantalla desactivat, i a la finestra de "Gestor d'Energia" o tinc tot configurat en "MAI", així que no se el que deu passar.

---

### Post by hakd0c on 2007-12-19
On esta el gestor d'energia amb xubuntu?

---

### Post by lluisanunez on 2007-12-19
> **hakd0c said:**
> On esta el gestor d'energia amb xubuntu?

Sistema > Preferències > Gestor d'energia

També pots configurar-lo des del menú del salvapantalles, pestanya "avançades"

Amb quin player mires les pe&#320;lícules? El Mplayer té una opció a la configuració per a desactivar-lo, i funciona.

---

### Post by hakd0c on 2007-12-21
Sistema -> Preferencies -> Gestor d'energia => això es ubuntu i no Xubuntu, o almenys jo no trobo enlloc el Gestor d'Energia.

Tampoc tinc pestanyes al gestor del salvapantalles

---

### Post by lluisanunez on 2007-12-21
El programa es diu gnome-power-preferences per si el pots  arrencar des de la línia de comandes

---

### Post by hakd0c on 2007-12-21
No tinc aquest programa.

He de confessar que no es una xubuntu pura la instal·lada sino que es una mythbuntu, que porta moltes coses retallades, no porta openoffice, gimp...

Tot això deu quedar gravat en algun lloc editable directament des de linia de comandes

---

### Post by papapep on 2007-12-21
Per saber si realment és l'estalvi d'energia, pots provar a veure si et deixa de "molestar" passant-li el paràmetre **acpi=off** a l'arrencada. I si et funciona com tu vols així, posar-ho al grub i desinstal·lar l'**apmd**.

---

### Post by kukat on 2007-12-21
Ja he provat l'opció del reproductor VLC de llevar l'estalvi de pantalla, però als 10 minuts aprox. hem torna la pantalla negra. Mous el ratolí i torna. 

Tinc el protector de pantalla desactivar i en les opcions d'energia ho tinc tot posat en MAI. Així que no sé el que tinc que fer...

---

### Post by papapep on 2007-12-21
> Així que no sé el que tinc que fer...

El que he dit just abans que tu :-)

---

### Post by kukat on 2007-12-21
Doncs:

Pose acpi=off al menú grub (sudo gedit /boot/grub/menu.lst)???

I després faig un sudo apt-get remove apmd?

Gràcies! Perdó, no havia vist la teva resposta abans, ja que anava a escriure i tenia la finestra oberta des de feia unes hores... :)

---

### Post by papapep on 2007-12-21
Ja has provat, abans de desinstal·lar res, que et funcioni la solució passant-ho a l'arrencada?

---

### Post by kukat on 2007-12-22
He posat acpi=off al menú Grub i no ha passat res. Al cap de 10 minuts exactes, la pantalla es queda negra

---

### Post by CarlesOriol on 2007-12-22
Si pots entrar en gnome

Ves a : Sistema > Preferencies > Gestor d'energia ( gnome-power-preferences)

I posa a mai les opcions de l'estalvi d'energia. (Posar la pantalla en baix consum)

---

### Post by kukat on 2008-01-01
Bé, he solucionat el  problema !!!

Per si algú li passa el mateix, la pantalla negra després de 10 minuts d'inactivitat, a pesar de tindre l'estalvi de pantalla i el gestor d'energia correctament configurat, la solució es senzilla:

Hi ha que editar el xorg:

A la consola: 
 sudo gedit /etc/X11/xorg.conf

I afegiu al final el seguent codi: (des de Section fins a EndSection)

Section "ServerFlags"
Option "blank time" "0"
Option "standby time" "0"
Option "suspend time" "0"
Option "off time" "0"
EndSection

A mi m'ha funcionat i ara ja puc veure pelis sense tindre que menejar el ratolí o el teclat cada 10  minuts.:)

---

### Post by albert-I on 2008-01-01
Això pero es pq has tocat alguna cosa? a mi mai m'ha passat això. 
Tambe es cert que jo si que tinc l'instal·lació ordinaria.

---

### Post by kukat on 2008-01-02
Jo diria que no he tocat res. Des de la primera vegada que vaig posar una peli que als 10 minuts s'hem feia negra (crec que era un capitol de Embruixades, que hem fa fàstic, però a la novia li encanta...:))...

Igual té alguna cosa a veure amb el Compiz, o amb Ati, no ho sé, però no he estat tocant res del fitxer xorg...
Però ara va de meravella!!!!

---

### Post by hakd0c on 2008-01-02
Perfecte,

A mi amb aquesta modificació a l'xorg també se m'aguanta engegat.

PD: Jo tinc Nvidia i si havia tocat el fitxer per activar el xinarema i altres, però no havia tocat aquest apartat

---

### Post by kukat on 2008-01-02
Bé! Ja podem posar [SOLVED]. També estaría bé que algú ens explicara quins són els motius per els que ha pogut passar, per si ens tornara a passar.:popcorn:

Salut!

---

