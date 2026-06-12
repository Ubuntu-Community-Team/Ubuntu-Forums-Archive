---
title: "Beryl works; beryl-manager freezes computer"
date: 2007-04-06
forum: Desktop Effects &amp; Customization
---

### Post by Sgurd on 2007-04-06
Beryl 0.2.0 in Ubuntu 6.10 w/ NVidia:
beryl-manager used to work, until I changed some advance setting trying to get my window borders to appear.  Now beryl-manager freezes my computer everytime I run it so I can't change the advanced setting back to automatic.

If I reboot and just run 'beryl', then 'emerald --replace', everythign works, but I can't manage beryl.

I tried 'apt-get --purge remove beryl beryl-manager emerald . . .' etc etc
and reinstalling, but beryl-manager still freezes.

Any ideas?  Thanks in advance, beryl's awesome and God Bless - JD

---

### Post by Azakus on 2007-04-06
I'm getting the same error, but I didn't do anything to beryl settings in 2 weeks.

---

### Post by Azakus on 2007-04-06
Found the error. The new xorg updates break libglx.so, so do this.
```
cd /usr/lib/xorg/modules/extensions
sudo mv libglx.so libglx.so.bak
sudo ln -s libglx.so.1* libglx.so

```
Works for me now

---

### Post by Snookered on 2007-04-15
> **Azakus said:**
> Found the error. The new xorg updates break libglx.so, so do this.
```
cd /usr/lib/xorg/modules/extensions
sudo mv libglx.so libglx.so.bak
sudo ln -s libglx.so.1* libglx.so

```
Works for me now

Appearantly i hadn't rebooted for some time after my last update. System froze up, and had to kill power. Couldn't login again and would kicked back to the login screen. My other account for the family worked, though. Wayren has this post linked in another thread. This solution worked for me!

Thank you, Azakus

PS: Had to to use winxp for a whole week until I found your post. What a nightmare.

---

