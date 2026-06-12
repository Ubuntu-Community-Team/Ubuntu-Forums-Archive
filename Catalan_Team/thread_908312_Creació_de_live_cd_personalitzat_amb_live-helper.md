---
title: "Creació de live cd personalitzat amb live-helper"
date: 2008-09-02
forum: Catalan Team
---

### Post by JosepRibes on 2008-09-02
Hola amics,

ja fa uns dies que estic probant de crear un live cd de Debian personalitzat amb una serie de paquets i configuracions instal·lades. l'unic problema que estic tenit es a l'hora de definir l'idioma del teclat en que arrencarà aquest live cd. 
he probat amb la instrucció:

#lh_config ...  -bootappend "locale=es_ES.UTF-8 keyb=sp"

però em continua creant un live cd amb l'idioma del teclat amb anglès. 

Algú s'ha trobat amb el mateix problema i ho ha pogut resoldre??

Salutacions.

---

### Post by orestesmas on 2008-09-02
No et puc ajudar, perquè la meva experiència en personalitzar CD es limita a Kubuntu a través de l'eina UCK. Però d'allò que he anat aprenent  se m'acut que potser el teu problema és que estàs suposant que el "locale" i teclat del sistema global i el de l'entorn gràfic són el mateix, i (almenys en KDE) no és així.

En el cas de la kubuntu, si instal·lo els paquets de suport per al català (tant del sistema global com del KDE) la interfície gràfica ja surt en aquest idioma, i el teclat és el correcte.

---

