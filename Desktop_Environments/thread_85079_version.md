---
title: "version??"
date: 2005-11-01
forum: Desktop Environments
---

### Post by mechanic on 2005-11-01
here's another query: if I install from a Warty CD then update everything using apt-get/synaptic, am I left with the latest Badger version or with Warty? And how can I tell from the desktop in front of me? I don't see any version labels.

m.

---

### Post by jasay on 2005-11-01
If you install warty and 
```
sudo apt-get update
```
it will update the list of possible programs to download.  If you then 
```
sudo apt-get upgrade
```
you'll get the newest warty packages.  To get to breezy packages you have to edit (with root/sudo) /etc/apt/sources.list and everywhere it says warty change it to breezy.  Then 
```
sudo apt-get update
sudo apt-get dist-upgrade
```
You might have to go warty > hoary > breezy though.  I'm not sure on that one.

System > about ubuntu used to say the version I think, but doesn't seem to in Breezy.  Since Ubuntu follows the gnome release cycle you could probably date the release by the version of gnome (System about gnome).  I believe Gnome 2.8 is with warty, gnome 2.10 with hoary, and gnome 2.12 with breezy.

---

### Post by mechanic on 2005-11-02
Ok, thanks for that. How do these versions stack up against the Debian Sarge/Testing/Sid model? Is Warty the stable version or is it obsolete?

m.

---

### Post by NewWithoutClue on 2005-11-02
not obsolete, but also not stable.


Paul.

---

### Post by Riverside on 2005-11-02
[QUOTE=jasay]System > about ubuntu used to say the version I think, but doesn't seem to in Breezy.[/QUOTE]
anthony@trafford:~$ lsb_release -idr
Distributor ID: Ubuntu
Description:    Ubuntu (The Breezy Badger Release)
Release:        5.10

---

### Post by drummer on 2005-11-02
[QUOTE=NewWithoutClue]not obsolete, but also not stable.[/QUOTE]
It is stable, just not the current/latest stable version... i guess that's what you meant, just making it clear.

---

### Post by NewWithoutClue on 2005-11-02
[QUOTE=drummer]It is stable, just not the current/latest stable version... i guess that's what you meant, just making it clear.[/QUOTE]
Thanks for that.
No i didn't mean that, i guess I'm incorrect.

Paul.

---

### Post by mechanic on 2005-11-02
Of course this is a bit confusing because 'stable' has special meaining in debian releases, as does 'testing'.

m.

---

### Post by drummer on 2005-11-02
Hmm.. i see your point, but you can't really compare the releases to debian's. While code is pulled from sid for the development releases, the release cycle is completely different from debian... it has 2 active branches, whereas Ubuntu has 1, they also release new versions whenever they're ready, and so base their releases more on stability (Ubuntu is based on time, every 6 months).

---

### Post by jasay on 2005-11-02
[QUOTE=Riverside]anthony@trafford:~$ lsb_release -idr
Distributor ID: Ubuntu
Description:    Ubuntu (The Breezy Badger Release)
Release:        5.10[/QUOTE]

Nice.  Thanks.

---

### Post by mechanic on 2005-11-03
Hitting Cntrl+Alt+F1 shows the same info from the console (I just discovered); Cntrl+Alt+F7 to get the GUI back.

m.

---

