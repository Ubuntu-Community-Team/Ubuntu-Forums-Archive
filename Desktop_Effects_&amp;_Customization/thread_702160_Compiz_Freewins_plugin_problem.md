---
title: "Compiz Freewins plugin problem?"
date: 2008-02-20
forum: Desktop Effects &amp; Customization
---

### Post by chunchengch on 2008-02-20
I follow this thread [http://ubuntuforums.org/showthread.php?t=602062&highlight=freewins](http://ubuntuforums.org/showthread.php?t=602062&highlight=freewins) to install Freewins plugin, it works fine but can not rotate in 3d like Metisse dose, so I download .tar.gz file from gitweb, but I get error message while making, can anyone tell me what the problem is? and how to fix it?

Thanks a lot for reply!


error message:

$ make
convert   : freewins.xml.in -> build/freewins.xml
bcop'ing  : build/freewins.xml -> build/freewins_options.h
bcop'ing  : build/freewins.xml -> build/freewins_options.c
schema    : build/freewins.xml -> build/compiz-freewins.schema
make: *** No rule to make target `build/freewins.lo', needed by `c-build-objs'.  Stop.

---

### Post by jryprt on 2008-02-20
> **chunchengch said:**
> I follow this thread [http://ubuntuforums.org/showthread.php?t=602062&highlight=freewins](http://ubuntuforums.org/showthread.php?t=602062&highlight=freewins) to install Freewins plugin, it works fine but can not rotate in 3d like Metisse dose, so I download .tar.gz file from gitweb, but I get error message while making, can anyone tell me what the problem is? and how to fix it?

Thanks a lot for reply!


error message:

$ make
convert   : freewins.xml.in -> build/freewins.xml
bcop'ing  : build/freewins.xml -> build/freewins_options.h
bcop'ing  : build/freewins.xml -> build/freewins_options.c
schema    : build/freewins.xml -> build/compiz-freewins.schema
make: *** No rule to make target `build/freewins.lo', needed by `c-build-objs'.  Stop.

Try [My Guide](http://ubuntuforums.org/showthread.php?t=659282) look for Freely Transform Windows was (Freewins) (Its renamed in ccsm)

---

### Post by chavanak on 2008-02-20
Yes that guide is simply superb credits to jryprt.. But some people have issues like non responding notification area, etc. So if you face the problem disable it

---

### Post by chunchengch on 2008-02-20
Thanks for reply and guide, but I would really like to know what causes the error [[COLOR="Red"]make: *** No rule to make target `build/freewins.lo', needed by `c-build-objs'. Stop.[/COLOR]]?

Thanks!

---

