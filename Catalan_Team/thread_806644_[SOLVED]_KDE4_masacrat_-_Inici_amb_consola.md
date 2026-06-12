---
title: "[SOLVED] KDE4 masacrat - Inici amb consola"
date: 2008-05-25
forum: Catalan Team
---

### Post by Joan Marc on 2008-05-25
Vaig voler provar el KDE4 a l'ubuntu, i ho vaig fer seguint [aquest fil]("http://ubuntuforums.org/showthread.php?t=798576"), on:
> **PellRoja said:**
> Benvingut :)

[http://www.informatics.cat/wiki/index.php/Ubuntu#Instal.C2.B7lar_tasques](http://www.informatics.cat/wiki/index.php/Ubuntu#Instal.C2.B7lar_tasques)

només has de marcar el ubuntu studio desktop, o el que t' interessi.[...]
Jo, primer vaig provar l'ubuntu studio, i després vaig voler provar el KDE4, que també hi era.
El fet és que vaig voler tornar al gnome, però no sé perquè desmarcant les caselles d'ubuntustudio i de KDE4, no feia res...
I després, vaig cometre el gran error de novell, que és buscar al synaptic el nom de kde4, i eliminar tots els paquets que tenia instal·lats. Quan vaig reiniciar, em surt com si ho estigués fent des de la consola...
Què puc fer ara? 
s'arreglaria postant a la consola això?
```
sudo apt-get install ubuntu desktop (o alguna cosa per l'estil)
```
Gràcies

---

### Post by papapep on 2008-05-25
Bé, quan us dediqueu a treure i posar "per jugar" escriptoris sencers, ja sabeu a què us exposeu :-) 

Respecte la reinstal·lació, sempre és millor fer servir l'aptitude que controla més acuradament (a vegades en excés) les dependències de paquets:

```
sudo aptitude update && sudo aptitude install ubuntu-desktop
```

---

### Post by Joan Marc on 2008-05-25
Merci papapep, he fet el que has posat i ha anat bé.
Però després, quan he tornat a intentar a iniciar, surt una línea que posa:
```
Not starting GNOME Display Manager (gdm): it is not the default display manager
```
I a continuació torna a sortir la consola.
Com li dic que el gdm sigui per defecte?

---

### Post by papapep on 2008-05-25
```
sudo aptitude install gdm
```

---

### Post by CarlesOriol on 2008-05-25
o millor un 

sudo dpkg-reconfigure gdm

---

### Post by Joan Marc on 2008-05-25
CarlesOriol: El teu em donava un error, em deia que no es podia recarregar...
papapep: Després de fer el d'en Carles he provat el teu i ha funcionat.
Gracies als dos!

---

