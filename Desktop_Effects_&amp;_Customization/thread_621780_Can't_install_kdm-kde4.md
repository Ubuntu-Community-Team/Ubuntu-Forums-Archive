---
title: "Can't install kdm-kde4"
date: 2007-11-24
forum: Desktop Effects &amp; Customization
---

### Post by hotweiss on 2007-11-24
Everytime I try to install kdm-kde4 I get this error. When I type ''sudo apt-get install kdm-kde4" a blue screen comes up asking me if I would like kdm or kdm-kde4. If I select kdm, everything installs. If I select kdm-kde4 I get this error.

> Unpacking kdm-kde4 (from .../kdm-kde4_4%3a3.96.0-1ubuntu3~ppa2_i386.deb) ...
Setting up kdm-kde4 (4:3.96.0-1ubuntu3~ppa2) ...
dpkg: error processing kdm-kde4 (--configure):
 subprocess post-installation script returned error exit status 1
E: Sub-process /usr/bin/dpkg returned an error code (1)

Of course I have followed all the install instructions.

---

### Post by pasnox on 2007-11-24
Same error there !

---

### Post by hotweiss on 2007-11-25
bump

---

### Post by samotholt on 2007-11-27
I have exactly the same problem. Fix would be appreciated ;)

---

### Post by CrazyPoultry on 2007-11-30
Just tried to install kdm-kde4 and my results were the same any help would be appreciated

---

### Post by Apocalypse_dn on 2007-12-31
Try  ```
sudo apt-get install pykdeextensions
``` and after that reinstall kdm-kde4. It helped me

---

### Post by indeed on 2007-12-31
Same problem, with pykdeextensions installed.

---

### Post by indeed on 2007-12-31
Ah. See [https://bugs.launchpad.net/ubuntu/+source/kdebase-workspace/+bug/165274](https://bugs.launchpad.net/ubuntu/+source/kdebase-workspace/+bug/165274)
No solution, just have to wait for repo to be updated I guess.

---

