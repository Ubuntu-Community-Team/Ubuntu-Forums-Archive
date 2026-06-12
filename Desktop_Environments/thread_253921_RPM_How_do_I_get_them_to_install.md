---
title: "RPM? How do I get them to install"
date: 2006-09-09
forum: Desktop Environments
---

### Post by Scorpion2k5 on 2006-09-09
](*,) How do I go about getting an RPM Package to install under Ubuntu 6.06 LTS? I just installed this OS have some stuff that are RPM that I want to install but can't cause for some reason the Archiver I have install won't unpackage them... Is there anyone out there that can help me...](*,) :confused:

---

### Post by Phasmagon on 2006-09-09
You can always use alien.

apt-get alien, will take care of the dependencies.

then use alien as instructed in the man pages to convert the rpm to deb and then

dpkg -i package to install

---

### Post by Perfect Storm on 2006-09-09
I'm almost sure you can find the ting you needed if you set up your sourcelist correctly.
What application(s) are we talking about?

---

