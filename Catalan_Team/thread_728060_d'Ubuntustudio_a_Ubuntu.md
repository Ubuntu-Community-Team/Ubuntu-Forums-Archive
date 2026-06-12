---
title: "d'Ubuntustudio a Ubuntu"
date: 2008-03-18
forum: Catalan Team
---

### Post by bratac on 2008-03-18
Bones,

l'altre dia em vau aconsellar de seguir la guia que es proposa des d'aquí:

[http://www.cesarius.net/como-instalar-ubuntu-studio-musica-para-seres-humanos/](http://www.cesarius.net/como-instalar-ubuntu-studio-musica-para-seres-humanos/)

per a instal·lar-me ubuntu studio, de fet, el que va fer va ser instal·lar-me l'escriptori d'ubuntustudio. Ara me'l voldria desinstal·lar. Em podeu ajudar a fer-ho?

gràcies!

---

### Post by patrickfromspain on 2008-03-18
si haguessi fet un sudo aptitude install ubuntustudio-desktop, hagues estat realment senzill de desfer. Havent fet un apt-get.. ara et toca desintal·larte tot el que et vas instal·lar a ma.. tens feina xD

A veure si algu te una llista a ma del que t'hauries d'instal·lar. En el meu cas, vol instal·lar tot aixo:  
```

apmd foomatic-db-hpijs hpijs hplip libsane scim-modules-table
  scim-tables-additional sound-juicer tango-icon-theme tango-icon-theme-common
  ubuntustudio-default-settings ubuntustudio-desktop ubuntustudio-gdm-theme
  ubuntustudio-icon-theme ubuntustudio-look ubuntustudio-menu
  ubuntustudio-screensaver ubuntustudio-sounds ubuntustudio-theme
  ubuntustudio-wallpapers usplash-theme-ubuntustudio

```

Podries començar per un:   sudo apt-get remove ubuntustudio-default-settings ubuntustudio-desktop ubuntustudio-gdm-theme  ubuntustudio-icon-theme ubuntustudio-look ubuntustudio-menu  ubuntustudio-screensaver ubuntustudio-sounds ubuntustudio-theme  ubuntustudio-wallpapers usplash-theme-ubuntustudio

salut!

PD: es estrany que no hagi demanat d'instal·lar cap aplicació multimedia no?

---

### Post by bratac on 2008-03-19
Gràcies, per tot! 

Ho he fet pel sinàptic...

fins ara!

---

