---
title: "Problem installing Enemy Territory Team Fortress"
date: 2006-11-11
forum: Gaming &amp; Leisure
---

### Post by intel352 on 2006-11-11
When I try to install etf v1.60 (a .run file), I get the following error *after* integrity has been verified. it occurs when the installer attempts to  decompress:

> ./search.sh: 20: Syntax error: Bad substitution

Any idea what could cause this issue?

Using Ubuntu Edgy Eft (6.10)

---

### Post by Coinz on 2006-11-15
i have the same exact problem someone help us plz ](*,)

---

### Post by bunnythebunny on 2006-11-21
I have the same issue. Please help us. 

> ./search.sh: 35: Syntax error: Bad substitution

I've got Ubuntu Edgy 6.10 as well.

---

### Post by qrm on 2006-11-21
try commenting that line (or little section) out from that .sh file . Look around in forums and search for "dash" there was something that you had to change in the file to get it running under the true bash. In edgy they changed the bash to dash :)

---

### Post by bunnythebunny on 2006-11-23
Ok guys i found this 

> Are you running Edgy?

If so then try editing the .sh file and changing the line /bin/sh at the top to /bin/bash

Just a thought.

hth

it didn't work for me. Although i might have messed up.

---

### Post by zoly on 2007-01-12
This migh be the solution for this problem (and for installing True Combat: Elite, too):
the installer is fixed to allow for dash the only solution is to re-link /bin/sh to point to /bin/bash:

sudo mv /bin/sh /bin/sh.orig
sudo ln -s /bin/bash /bin/sh

(I've found somewhere in this ubuntuforums.org)
Regards

---

