---
title: "AWN i els applets"
date: 2008-08-10
forum: Catalan Team
---

### Post by MiquelBLL on 2008-08-10
Faig servir l'AWN  des que vaig començar amb linux amb l'Ubuntu 7.04, ara ja estic amb 8.04 i ahir vaig actualitzar l'AWN i resulta que m'han desaparegut els applets, he buscat com  poder fer-ho per bastants llocs i no ho he aconseguit, tambe he tornat a instal.lar l'anterior versio del AWN pero els applets que tenia no apareixen.  Algu li passa el mateix? Si algu em pot dir alguna cosa. Gracies.    Miquel.

---

### Post by MiquelBLL on 2008-09-04
Res que torno a posar la pregunta, a veurer si a algu li ha passat. Ja se m'ha actualitzat el AWN 2 vegades pero segueixo igual, els applets no apareixen.

---

### Post by Daerun on 2008-09-06
Passa't per [aquest]("http://ubuntuforums.org/showthread.php?t=856755") tema, a veure si és això-

---

### Post by MiquelBLL on 2008-09-07
tinc instal.lat el launchpati els applets no apareixen, em surt un anomenat launcher/Taskmanager i res mes. A vans m'en sortien un mun.

---

### Post by Druiling on 2008-09-08
Hola,

Amb les màximes precaucions (u siga, esperar que algú amb més experiència ens ho confirmi), podria ser que fent això et sortissin els applets:

***sudo apt-get install awn-manager-trunk awn-extras-applets-trunk***

Dic jo, per que era el pas següent a l'update de després d'instal·lar la versió del launchpad.

Fins ara.

---

### Post by PauGNU on 2008-09-09
Caldria que feres el següent:

1. Desinstal·la tot allò relacionat amb l'avant-window-navigator (cerca al synaptic paquets amb el nom awn i avant-window). Això no borrarà el perfil que tu tingues de l'avant (quan el tornes a instal·lar, t'apareixerà tal i com ho tenies).

2. Si tens un repositori extra per a l'awn, elimina-lo.

3. Afegeix aquest repositori:
```
deb http://ppa.launchpad.net/awn-testing/ubuntu hardy main
deb-src http://ppa.launchpad.net/awn-testing/ubuntu hardy main
```

4. Instal·la novament el awn:
```
sudo apt-get install awn-manager-trunk awn-extras-applets-trunk
```

Ja ens dius.

Salut

---

### Post by LitusMayol on 2008-09-09
Jo vaig tenir un problema semblant.

Vaig fer:
```
sudo aptitude remove avant-window-navigator
```

i després vaig seguir el post que havia iniciat la **Druiling** (que és el que en **Daerun** t'ha posat el link: [aquest]("http://ubuntuforums.org/showthread.php?t=856755")).

A mi em funciona... un xic lent de vegades, però normalment bé.

---

### Post by MiquelBLL on 2008-09-09
Tinc aquest repositori*  i faig tot l'indicat pero segueixo igual. A veurer si si se m'arregla amb la 8.10. Gracies.

*deb [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main

---

