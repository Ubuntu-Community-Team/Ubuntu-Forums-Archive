---
title: "beryl to compiz, compiz freezes system"
date: 2007-09-19
forum: Desktop Effects &amp; Customization
---

### Post by mega on 2007-09-19
I'm out of idea,s i've reinstalled compiz several times

when I enable desktop effects it slows the system to a halt, I end up having to go out to a shell and restart gdm


everything worked great in beryl, but I got "upgraded" to this new compiz program


any ideas?   I would like to ensure everything really is getting reset


mega@mainpc:~$ glxinfo | grep "direct rendering"
direct rendering: Yes

using the nvidia drivers

---

### Post by praet on 2007-09-20
When you reinstalled compiz, did you use the recommended repos?
I recommend removing the existing compiz and reinstall using amaranths repo (recommended) as described here:
[https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion)

Basically:
```
sudo apt-get --purge remove compiz* libcompizconfig*
```

Then remove trevino's repo if its there and add Amaranths in /etc/apt/sources.list
```
deb http://ppa.launchpad.net/amaranth/ubuntu feisty main
deb-src http://ppa.launchpad.net/amaranth/ubuntu feisty main
```

Then reinstall compiz:
```
sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get install compiz compizconfig-settings-manager 
```

---

### Post by mega on 2007-09-20
I did not use those

someone needs to go purge or delete all these threads with bad repo's in them, this forum has 15 different ways to get it to work, and 15x100 threads on it not working probably because of all the bad repo's going around


the whole problem, I went in and cleaned out a bad beryl repo


did a update/upgrade and boom everything blew up


as a side note, if I do compiz --replace it works great,  if I go up to the menu and enable desktop effects it crashes horribly

---

### Post by praet on 2007-09-20
I actually allow desktop-effects to be removed when uninstalling compiz (as it is a dependency).  Let me know if you can get compiz working properly now.

---

