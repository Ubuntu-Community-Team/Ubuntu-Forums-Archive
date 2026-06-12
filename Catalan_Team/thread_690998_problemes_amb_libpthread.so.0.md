---
title: "problemes amb libpthread.so.0"
date: 2008-02-08
forum: Catalan Team
---

### Post by hakd0c on 2008-02-08
Hola,

Podem dir que aquest post deriva d'un que ja vaig obrir parlant sobre problemes amb el wine.

No puc utilitzar cap programa que utilitzi aquesta llibreria.

Quant executo l'Opera o el wine (son els 2 que utilitzo que l'utilitzen) em salta el següent error.

```

david@david-desktop:~$ opera
ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
/usr/lib/opera/9.25-20071214.6/opera: error while loading shared libraries: /usr/lib/libpthread.so.0: invalid ELF header
david@david-desktop:~$ wine
wine: error while loading shared libraries: /usr/bin/../lib/libpthread.so.0: invalid ELF header
david@david-desktop:~$ sudo wine
[sudo] password for david:
wine: error while loading shared libraries: /usr/bin/../lib/libpthread.so.0: invalid ELF header
david@david-desktop:~$ 

```

He provat de reinstal·lar la llibreria i em fa exactament el mateix.

Ja no se què fer o sigui que agrairé qualsevol ajuda

---

### Post by CarlesOriol on 2008-02-08
Copia'ns el resultat de :

 ls -l /lib/libpthread*

---

### Post by guillemsola on 2008-02-08
No se tu, però jo si vaig a /usr/lib i busco l'arxiu libpthread.so.0 no el tinc. El que si que tinc és l'arxiu libpthread.so és a dir sense el .0 final.

Ja de tu miraria això i en tots cas provaria a fer un link simbòlic a aquest arxiu amb l'altre nom a veure si així el troba.

Per exemple en el cas de l'opera si tens l'arxiu /usr/lib/libpthread.so fes:

> 
sudo ln-s /usr/lib/libpthread.so /usr/lib/libpthread.so.0

ja diràs

---

