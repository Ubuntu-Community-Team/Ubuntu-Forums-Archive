---
title: "[SOLVED] Compilar kernel 2.6.27"
date: 2008-10-10
forum: Catalan Team
---

### Post by patrickfromspain on 2008-10-10
Hola gent,

estic intentant compilar un kernel 2.6.27, ja que vull afegir l'hibernar mitjançant tux on ice i treure algunes coses que no utilitzo. El problema es que sembla que alguna cosa ha canviat i no es deixa compilar. El tinc tant després d'aplicar el pedaç com abans, o sigui que no es del pedaç que hi aplico. L'error que dona es el següent:

```

patrick@patrick-laptop:~/Escriptori/linux-2.6.27$ make-kpkg clean 
exec debian/rules  DEBIAN_REVISION=5:10.Custom  clean 
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 3: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 4: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator

====== making target CLN-common [new prereqs: testdir]======

====== making target CLN-common [new prereqs: ]======
You may need root privileges - some parts may fail.
/usr/bin/make -f ./debian/rules real_stamp_clean
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 3: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 4: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
make[1]: Entering directory `/home/patrick/Escriptori/linux-2.6.27'
====== making target real_stamp_clean [new prereqs: ]======
running clean
test ! -f scripts/package/builddeb.kpkg-dist ||                     \
          mv -f scripts/package/builddeb.kpkg-dist scripts/package/builddeb
test ! -f scripts/package/Makefile.kpkg-dist ||                     \
          mv -f scripts/package/Makefile.kpkg-dist scripts/package/Makefile
test ! -f .config  || cp -pf .config config.precious
test ! -f Makefile || \
            /usr/bin/make    ARCH=xen distclean
make[2]: Entering directory `/home/patrick/Escriptori/linux-2.6.27'
Makefile:518: /home/patrick/Escriptori/linux-2.6.27/arch/xen/Makefile: No such file or directory
make[2]: *** No rule to make target `/home/patrick/Escriptori/linux-2.6.27/arch/xen/Makefile'.  Stop.
make[2]: Leaving directory `/home/patrick/Escriptori/linux-2.6.27'
make[1]: *** [real_stamp_clean] Error 2
make[1]: Leaving directory `/home/patrick/Escriptori/linux-2.6.27'
make: *** [CLN-common] Error 2

```

Aixo passa tant amb la versió del paquet linux-source-2.6.27 com amb la versió baixada de kernel.org. El problema sembla estar amb el ARCH=xen, ja que provant a compilar un kernel 2.6.26.5 de kernel.org al fer el make-kpkg clean no dona error i mirant hi diu ARCH=x86_64:

```

patrick@patrick-laptop:~/Escriptori/linux-2.6.26.5$ make-kpkg clean 
exec make -f /usr/share/kernel-package/ruleset/minimal.mk clean 
====== making target minimal_clean [new prereqs: ]======
Cleaning.
test ! -f .config || cp -pf .config config.precious
test ! -e stamp-building || rm -f stamp-building
test ! -f Makefile || \
            make    ARCH=x86_64 distclean
make[1]: Entering directory `/home/patrick/Escriptori/linux-2.6.26.5'
  CLEAN   scripts/basic
  CLEAN   scripts/kconfig
  CLEAN   include/config
  CLEAN   .config include/linux/autoconf.h
make[1]: Leaving directory `/home/patrick/Escriptori/linux-2.6.26.5'
test ! -f config.precious || mv -f config.precious .config
rm -f modules/modversions.h modules/ksyms.ver conf.vars scripts/cramfs/cramfsck scripts/cramfs/mkcramfs applied_patches  stamp-build stamp-configure stamp-image stamp-headers stamp-src stamp-diff stamp-doc stamp-manual stamp-patch stamp-buildpackage stamp-debian

```

He provat a fer un link de arch/x86 a arch/xen però res, acaba fallant igual.

Algu te la mes mínima idea al respecte? He obert un [bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/280173"), però de moment no en se res. 

Salut i merci!

---

### Post by orestesmas on 2008-10-11
Fa la pinta que intentes compilar amb suport per XEN, però sense haver aplicat prèviament els pedaços per al XEN.

Com has configurat el nucli? a partir d'alguna configuració antiga? de la del teu nucli actual? uses XEN al teu nucli actual? En qualsevol cas, pjo provaria de buscar i desactivar el suport per XEN, i potser el problema et desapareix.

Jo provaria a netejar la configuració i usar la configuració predeterminada (tot com a mòduls) per començar. Després ja aniràs afegint els drivers que necessitis enllaçats estàticament.

De tota manera, jo que fa molt de temps també em compilava els meus nuclis t'aconsello que t'ho pensis dues vegades abans de fer-ho: Cada actualització de nucli suposa un problema, perquè ho has de tornar a compilar tot tenint en compte els pedaços aplicats i les coses que han canviat i és un maldecap.

A més, l'estructura modular del nucli fa que només es carreguin aquelles coses que realment es necessiten, o sigui que no veig que calgui treure "coses que no utilitzes", perquè si és així, realment no s'utilitzen.

---

### Post by patrickfromspain on 2008-10-11
gracies orestes, ahir a la nit toquetejant ho vaig poder solucionar. Es el que dius: al treure el xen, tot va funcionar perfecte.

El que jo havia fet va ser instalar el linux-source-2.6.27 (codi font del nucli d'intrepid, no?) i fer un make oldconfig, que tinc entes que configura les opcions llegint la configuracio del nucli arrancat. Despres feia el make-kpkg clean i donava l'error. Però certament, treient totes les opcions del xen ha solucionat el contratemps.

Respecte a compilar el nucli no hi tinc cap problema. El nom del nucli es diferent i no interfereix amb els de l'ubuntu. Jo el que volia realment era aplicar el pedaç del tux on ice (antic suspend2), un mètode d'hibernació que m'agrada molt i que trobo força millor que es uswsusp o el mètode acpi que ve per defecte. A més, hi aplico el pedaç per al control dels voltatges de la cpu, que en un portatil es una cosa que s'agraeix moltissim (encara que es pot fer sense haver de recompilar tot el kernel) i ja per ultim: en el kernel d'ubuntu ve desactivada la opció d'estalvi d'energia en el bus pci express, que jo activo.

Despres simplement m'oblido dels kernel de l'ubuntu, ja que acabaré desintal·lant els paquets del quals penjen les actualitzacions a l'ultim kernel. Quan em vagi venint de gust, ja comprobare si hi ha res de nou a kernel.org i recompilare. Es un follon, però al final de tot això en vaig aprenent i amb els petits problemes que surten (com aquest, o trovar un pedaç que funcioni, etc) hi estic entretingut.

salut i merci!

---

