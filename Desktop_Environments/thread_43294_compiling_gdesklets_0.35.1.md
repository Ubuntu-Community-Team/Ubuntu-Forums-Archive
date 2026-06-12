---
title: "compiling gdesklets 0.35.1"
date: 2005-06-21
forum: Desktop Environments
---

### Post by gdcondor on 2005-06-21
hi

i managed to create a deb binary under ubuntu hoary without any problem (uncompressing the sources, then dh-make && dpkg-buildpackage -rfakeroot)

but when i tried to install the package i've the following error :
--------------
dpkg : erreur de traitement de //home/gdcondor/gdesklets_0.35.1-1_i386.deb (--unpack) : tentative de remaplcement de " /usr/share/applications/mimeinfo.cache", qui appartient aussi au paquet capplets-data
---
which means (not sure about the exact words in english) :
------------
dpkg : error while running //home/gdcondor/gdesklets_0.35.1-1_i386.deb (--unpack) : try to replace "/usr/share/applications/mimeinfo.cache", which also belongs to the package capplets-data
-----------

any idea ? (removing capplets-data will "destroy" my gnome environment...)
i have exactly the same pb with gdesklets 0.35 and 0.35.1 Sad

thx ! (and of course if i managed to solve this i can send you the binary but i'm not an expert in building binaries...)

GdCondor

ps : i asked on the gdesklets' forum but they told me i should ask here !

---

### Post by Bandit on 2005-06-21
[QUOTE=gdcondor]hi

i managed to create a deb binary under ubuntu hoary without any problem (uncompressing the sources, then dh-make && dpkg-buildpackage -rfakeroot)

but when i tried to install the package i've the following error :
--------------
dpkg : erreur de traitement de //home/gdcondor/gdesklets_0.35.1-1_i386.deb (--unpack) : tentative de remaplcement de " /usr/share/applications/mimeinfo.cache", qui appartient aussi au paquet capplets-data
---
which means (not sure about the exact words in english) :
------------
dpkg : error while running //home/gdcondor/gdesklets_0.35.1-1_i386.deb (--unpack) : try to replace "/usr/share/applications/mimeinfo.cache", which also belongs to the package capplets-data
-----------

any idea ? (removing capplets-data will "destroy" my gnome environment...)
i have exactly the same pb with gdesklets 0.35 and 0.35.1 Sad

thx ! (and of course if i managed to solve this i can send you the binary but i'm not an expert in building binaries...)

GdCondor

ps : i asked on the gdesklets' forum but they told me i should ask here ![/QUOTE]

And they siad ask here.. LOL.. I asked some questions before about installing gdesklets on SuSE 9.3 and they kept telling me to install packages that I KNOW I had already installed.
I installed 0.35.1 on my system, but I did it by compiling this program from source.
Have you tried installing it from source first and seeing if it works.
Rule of thumb with making RPMs or DEBs packages is that if you cant install from source then you will not be able to produce a working packaged.
When I installed mine I had to go grab and install a few dependencies. Which was not hard at all with that Snypt Pkg Mngr that comes with Ubuntu.
Try that. Cuz the error you have I dont have a clue what could be,
Cheers,
Joey

---

### Post by dare2dreamer on 2005-07-09
Anyone ever solve the problem with the "capplets-data" thing under hoary? I've run into the same problem compiling gdesklets from source, and I'm stumped.

---

### Post by Bandit on 2005-07-09
[QUOTE=dare2dreamer]Anyone ever solve the problem with the "capplets-data" thing under hoary? I've run into the same problem compiling gdesklets from source, and I'm stumped.[/QUOTE]

He never got back with a reply so I dont know.
I compiled gDesklets from source, so I am not sure what he might have configured wronge when he built the deb packageds..
Cheersm
Joey

---

