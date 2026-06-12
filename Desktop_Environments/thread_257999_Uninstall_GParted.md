---
title: "Uninstall GParted"
date: 2006-09-15
forum: Desktop Environments
---

### Post by roe_polak on 2006-09-15
Hi. I want to remove GParted because it doesn't work. First I installed version 0.1 from the Ubuntu repositories and later I installed version 0.2.5 from source and it stopped working. Now I want to remove it completely so I can start over. I've tried to remove it from Synaptic and apt-get remove, but the "link" in the menu still remains and it won't load. I've also tried to reinstall the older version, but it has no effect. When I try to start it from a terminal it says: "gparted: error while loading shared libraries: libparted-1.7.so.1: cannot open shared object file: No such file or directory
". I have also installed this from source, but it does not show up in Synaptic. I do find it a bit strange that I am able to start it, even though I have removed it. I would like to know how to remove a program completely as I haven't been able to find any topics about it.

---

### Post by Dinerty on 2006-09-15
I to had a few issues with Gparted, so I downloaded Gparted Live CD, this worked a treat [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

To remove programs from source seems abit tricky (Well to many anyway :P). You can go to the installation directory of the program and enter "make uninstall" from there.

If you use aplitude to install programs you can remove them cleanly as they also deal with dependices which are not needed. 

Hal the time I just use this command :(
```

sudo rm -rf /usr/share/amsn
```

Not sure if they are the best options by any means, but I to have not a definite solution to this problem

---

