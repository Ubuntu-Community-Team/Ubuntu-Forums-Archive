---
title: "[SOLVED] Inhabilitar Touchpad Dell Vostro 1400"
date: 2008-08-28
forum: Catalan Team
---

### Post by Alins on 2008-08-28
He googlejat per buscar com desactivar el touchpad d'un Dell Vostr0 1400 sense resultats positius.
Algun en sap alguna cosa? Gràcies

Jordi Alins

---

### Post by papapep on 2008-08-28
Hola Jordi!

Ens ajudaria veure el contingut que tens dins /etc/X11/xorg.conf. Més específicament, el que posa a un apartat que comença amb 

```
Section "InputDevice"
Identifier      "Synaptics Touchpad"

```

---

### Post by papapep on 2008-08-28
De fet, el que cal fer (per anar més per feina ;-)) és el següent:

1.- Assegurar-te que dins l'apartat que t'he comentat de l'***/etc/X11/xorg.conf*** hi ha la línia **Option "SHMConfig" "on"**


Per exemple, sense que hagi de ser exactament així, realment l'important és afegir la línia en vermell:

```
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
        [COLOR="Red"]**Option          "SHMConfig"             "on"**[/COLOR]
EndSection

```

2.- **Un cop fet això, has de reiniciar el servidor gràfic** (ctrl+alt+tecla enrera) o, potser més fàcil, reiniciar l'ordinador.

3.- Finalment, si executes a un terminal:

```
synclient TouchpadOff=1
```

hauria de deixar de funcionar-te el touchpad.

4.- Si, posteriorment, t'interessa tornar-lo a habilitar, amb un simple:

```
synclient TouchpadOff=0
```

hauria de tornar a funcionar.

Hi ha moltes més coses que es poden fer amb aquest programa (synclient), però per començar podries provar això :-)

---

### Post by Alins on 2008-08-28
Ha funcionat a la primera :guitar::). Fantàstic perquè anava de bòlid.
Salut.
Jordi Alins

---

### Post by oriolsbd on 2008-08-29
Hola, Alins.

Si ja et funciona, recorda't de marcar el fil com a "[SOLVED]".

Salut!

---

### Post by SiscoGarcia on 2008-08-29
Jordi, recorda que per marcar el fil com a resolt has d'anar a *Thread Tools/Mark this thread as solved* ;)

---

### Post by patrickfromspain on 2008-08-30
Merci papapep!

Amb el que has dit, he pogut habilitar la combinació FN+F6 per activar o desactivar el touchpad. No funcionava de serie i no em vaig molestar a trobar una solució, però amb el que has dit, ho he pogut solucionar.

En el meu cas, fn+f6 no feia res i el dmesg mostrava aixo:
```

[31.286862] atkbd.c: Unknown key pressed (translated set 2, code 0x82 on isa0060/serio0).
[31.286862] atkbd.c: Use 'setkeycodes e002 <keycode>' to make it known.

```

Per solucionar-ho, s'ha d'anar a un terminal Control+Alt+F1 i des d'allà fer dumpkeys > dumpkeys.log 

Ara ja podem tornar a gnome i obrim l'arxiu dumpkeys.log i busquem algun numero no associat, per exemple  "keycode  91 =". Si darrere = no hi ha res, significa que aquest codi no esta agafat i ens servira.

gksudo gedit /etc/rc.local i, abans de exit 0 hi afegim setkeycodes e002 91 (us tocara posar el que us vingui bé a vosaltres, es clar).

Instal·larem el xbindkeys: sudo apt-get install xbindkeys xbindkeys-config

Creem un executable nou: gksudo gedit /usr/local/bin/touchpad i hi posem el següent:
```

#!/bin/sh

if ( synclient -l | grep "TouchpadOff             = 0")
then synclient TouchpadOff=1
else synclient TouchpadOff=0
fi

```
El fem executable: sudo chmod +x /usr/local/bin/touchpad

Anem a Sistema->Preferencies->Sessions i hi afegim una entrada nom el que vulgueu i que executi la commanda xbindkeys

Ara podem reiniciar, ja queda poc.

Despres de reiniciar, l'unic que ens cal fer es executar xbindkeys-config. Apretem new i get key, llavors apretem la combinacio de tecles. A run action hi posem exec touchpad i llavors fem save & apply & exit

Ara amb la combinacio de tecles ja hauria de funcionar i continuar-ho fent en successius resets.

salut

---

