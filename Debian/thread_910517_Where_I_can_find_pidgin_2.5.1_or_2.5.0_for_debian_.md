---
title: "Where I can find pidgin 2.5.1 or 2.5.0 for debian lenny?"
date: 2008-09-04
forum: Debian
---

### Post by Sycron on 2008-09-04
I really wish to have at least pidgin 2.5.0 on debian lenny.

---

### Post by rampageoberon on 2008-09-04
At a guess [http://packages.debian.org](http://packages.debian.org) or use aptitude in the distro or compile from source if its not there in the repository

---

### Post by zvacet on 2008-09-04
[Here]("http://packages.debian.org/search?keywords=pidgin&searchon=names&suite=experimental&section=all")

---

### Post by Sycron on 2008-09-05
:| There are alot of dependency problems if I download pidgin from *experimental* packages.

I think i'll build it.

---

### Post by Sycron on 2008-09-05
I wonder how do I unninstall what i've installed with```
apt-get build-dep pidgin
```

This is eating >130MB of my precious space.

---

### Post by overdrank on 2008-09-05
Moved    :)

---

### Post by Sycron on 2008-09-05
I've done it with:
```
aptitude markauto $(apt-cache showsrc YOUR_APP_NAME | grep Build-Depends: | sed -e 's/Build-Depends:\|,\|([^)]*)//g')
```

I don't knwo what exactly means that very very long command but it worked. I've won 162MB.

---

### Post by markharding557 on 2008-09-05
You should consider moving up to debian sid or siddux these will make using experimental very easy

---

