---
title: "[SOLVED] gnome i kde alhora?"
date: 2008-11-12
forum: Catalan Team
---

### Post by Daerun on 2008-11-12
M'agradaria probar una temporada el kde, és possible instal·lar-lo sense haver de renunciar al gnome?

---

### Post by papapep on 2008-11-12
Si tens la 8.10:

```
sudo aptitude install kubuntu-kde4-desktop
```

però després desfer-ho, si és que volguessis, no seria tan simple per que aquesta ordre instal·larà un bon grapat de dependències.

---

### Post by oriolsbd on 2008-11-12
Per fer el que demanes, el que et recomana el Papapep és correcte. Té el problema que ell mateix comenta.

Una altra opció és instal·lar Kubuntu en una màquina virtual (amb Virtualbox, per exemple). Així, si no t'agrada, et "desfàs" de la màquina virtual i ja està. Si t'agrada, sempre pots acabar-te instal·lant el KDE com comenta el Papapep.

---

### Post by orestesmas on 2008-11-12
> **papapep said:**
> 
però després desfer-ho, si és que volguessis, no seria tan simple per que aquesta ordre instal·larà un bon grapat de dependències.

Però hi ha una solució: Abans d'executar l'ordre que et diu el Pep, obre un terminal i fes:

```
dpkg --get-selections > paquets_abans.txt
```

Això et guarda una "foto" dels paquets que tens instal·lats en un moment donat.

Després instal·les el que vols i tornes a fer la foto:

```
dpkg --get-selections > paquets_despres.txt
```

Quan vulguis recuperar l'estat anterior, només cal que miris els paquets que són només a un dels fitxers (els instal·lats de nou). Això es fa amb l'ordre "comm", que compara fitxers i, amb les opcions que aquí es mostres, retorna només les diferències. D'aquestes diferències canviem l'ordre "install" per "purge" (això es fa amb el "sed") i li diem al dpkg que marqui com a purgats aquests paquets. Finalment amb l'apt-get executem les purgues.

```

comm -2 -3 paquets_despres.txt paquets_abans.txt | sed "s/install/purge/" |sudo dpkg --set-selections

sudo apt-get dselect-upgrade

```

I la cosa torna a quedar com abans, tot i que, com que t'agradarà més el KDE, no et caldrà desinstal·lar-lo :-D

(Un consell: si vols provar el KDE, espera a la versió 4.2 que sortirà el gener)

---

### Post by Daerun on 2008-11-13
Gràcies per les respostes :D Hauria d'haver especificatr que tinc la 8.04; funcionaria igual el que m'heu comentat?

---

### Post by blauigris on 2008-11-14
I no hi hauria alguna forma d'escollir quin entorn vols al kdm (o gdm)?

---

### Post by papapep on 2008-11-14
Evidentment que sí. El Gdm (el kdm ni idea, però assumeixo que deu ser similar) et deixa triar la sessió que vols obrir, i quina vols tenir definida com a predeterminada.

---

