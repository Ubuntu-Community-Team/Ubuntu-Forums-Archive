---
title: "Prolem when install atlantis plugin"
date: 2008-03-18
forum: Desktop Effects &amp; Customization
---

### Post by sothacom on 2008-03-18
when i install atlantis plugin, i have a problem. Who can have me?

> sotacom@sotacom-desktop:~/compiz/atlantis (2)$ make
bcop'ing  : build/atlantis.xml -> build/atlantis_options.h
bcop'ing  : build/atlantis.xml -> build/atlantis_options.c
schema    : build/atlantis.xml -> build/compiz-atlantis.schema
compiling : shark.c -> build/shark.lo
compiling : atlantis.c -> build/atlantis.loIn file included from atlantis.c:109:
build/atlantis_options.h:15:27: error: compiz-common.h: No such file or directory
In file included from atlantis.c:109:
build/atlantis_options.h:19: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'CompPluginVTable'
atlantis.c:111: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'static'
atlantis.c: In function 'initAtlantis':
atlantis.c:137: error: 'displayPrivateIndex' undeclared (first use in this function)
atlantis.c:137: error: (Each undeclared identifier is reported only once
atlantis.c:137: error: for each function it appears in.)
atlantis.c: In function 'freeAtlantis':
atlantis.c:222: error: 'displayPrivateIndex' undeclared (first use in this function)
atlantis.c: In function 'atlantisClearTargetOutput':
atlantis.c:250: error: 'displayPrivateIndex' undeclared (first use in this function)
atlantis.c: In function 'atlantisPaintInside':
atlantis.c:266: error: 'displayPrivateIndex' undeclared (first use in this function)
atlantis.c: In function 'atlantisPreparePaintScreen':
atlantis.c:395: error: 'displayPrivateIndex' undeclared (first use in this function)
atlantis.c: In function 'atlantisDonePaintScreen':
atlantis.c:413: error: 'displayPrivateIndex' undeclared (first use in this function)
atlantis.c: In function 'atlantisInitDisplay':
atlantis.c:467: error: 'displayPrivateIndex' undeclared (first use in this function)
atlantis.c: In function 'atlantisFiniDisplay':
atlantis.c:476: error: 'displayPrivateIndex' undeclared (first use in this function)
atlantis.c: In function 'atlantisInitScreen':
atlantis.c:492: error: 'displayPrivateIndex' undeclared (first use in this function)
atlantis.c: In function 'atlantisFiniScreen':
atlantis.c:528: error: 'displayPrivateIndex' undeclared (first use in this function)
atlantis.c: In function 'atlantisInit':
atlantis.c:544: error: 'displayPrivateIndex' undeclared (first use in this function)
atlantis.c: In function 'atlantisFini':
atlantis.c:555: error: 'displayPrivateIndex' undeclared (first use in this function)
make: *** [build/atlantis.lo] Error 1

---

### Post by sothacom on 2008-03-18
Please help me!!!

---

