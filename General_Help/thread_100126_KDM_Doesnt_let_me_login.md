---
title: "KDM Doesnt let me login"
date: 2005-12-06
forum: General Help
---

### Post by feniix on 2005-12-06
I had search through the forum and couldbt find a problem similar to mine.

It seems the after updating from hoary to breezy something went wrong with the fonts, that makes kdm render the login as i type as squares, that makes it do a wron login/failed authentication.

Does anybody know how to solve this incident?
I am rendered outside my graphical environment as i can login in text console mode, but kdm fails to log me in Xorg


Thanks in advance,
Sebastian.

---

### Post by atoponce on 2005-12-06
Did you install KDE on top of Gnome?  If so, it might be as easy as launching the xorg-config and reconfigure your X server.  Try this from your command prompt, and when finished, see what happens:

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by feniix on 2005-12-07
the xserver starts just fine, the problem exists in authentication, as it seems that the chars kdm send to pam are corrupted. 
does anybody know how to fix this?

any ideas?

thanks in advance, Sebastian

---

### Post by Zaventh on 2005-12-07
Try sudo apt-get install --reinstall kdm ?

---

### Post by feniix on 2006-04-13
```
sudo dpkg-reconfigure xserver-xorg
```

did it

thanks!

---

