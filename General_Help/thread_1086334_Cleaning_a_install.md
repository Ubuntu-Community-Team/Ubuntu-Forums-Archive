---
title: "Cleaning a install"
date: 2009-03-03
forum: General Help
---

### Post by fungihead on 2009-03-03
Is there a way to clean all the unused stuff from a install?

its just in windows all programs go into program files, but in linux they kinda get spread... around... places. so when i uninstall something it leaves its dependencies all around.. places.

Do i need to clean these out of the install somehow?

---

### Post by bodhi.zazen on 2009-03-03
You do not need to clean Linux in the same way as you would Windows. Presuming you are new you are probably best forgetting any type of cleaning for now.

You can look at these links if you wish :

[http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html](http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html)

    [http://ubuntuforums.org/showthread.php?&t=140920](http://ubuntuforums.org/showthread.php?&t=140920)

    [http://ubuntu-tutorials.blogspot.com/2007/01/cleaning-up-ubuntu-gnulinux-system.html](http://ubuntu-tutorials.blogspot.com/2007/01/cleaning-up-ubuntu-gnulinux-system.html)

In terms of removing unneeded applications, use synaptic or apt-get, but to be honest you are best off performing a minimal install and adding only what you want rather then removing things.

---

### Post by 3rdalbum on 2009-03-04
Actually, uninstallers on Windows leave all sorts of loose files and dependencies all over the place too. Or worse, they can delete files that other programs still depend on. Yuck.

In Linux, you can remove the "orphaned" dependencies - just run the command:

```
sudo apt-get autoremove
```

From the apt-get manpage:

>  autoremove is used to remove packages that were automatically installed to satisfy dependencies for some package and that are no more needed.


Not exactly good English, but the command does exactly what you want.

---

### Post by fungihead on 2009-03-04
whats about when i install stuff from source, the decide i dont want it

the package manager wont pick up on those files will it?

---

### Post by iaculallad on 2009-03-04
> **fungihead said:**
> whats about when i install stuff from source, the decide i dont want it

the package manager wont pick up on those files will it?

No, Synaptics will not be able to uninstall applications installed from manual compilation. You are to uninstall it using uninstall scripts w/c comes with the package.

---

### Post by InspiredIndividual on 2009-03-04
> **iaculallad said:**
> No, Synaptics will not be able to uninstall applications installed from manual compilation. You are to uninstall it using uninstall scripts w/c comes with the package.

Actually, I'm wondering, if you install from source using 'checkinstall'   instead of 'make install', will removing it from Synaptic do the trick? I'm not sure myself, but maybe someone more experienced can shed some light on this.

---

### Post by fungihead on 2009-03-04
also just curious, why is there no sort of "click on a file, install the software" type thing, like a exe installer

if the software i want isnt in a repo then i have a load of trouble finding it, and then more trying to install it

and if it doesnt follow the ./configure, make, make install, make clean way of installing im pretty much stumped

---

### Post by Skripka on 2009-03-04
> **fungihead said:**
> also just curious, why is there no sort of "click on a file, install the software" type thing, like a exe installer

if the software i want isnt in a repo then i have a load of trouble finding it, and then more trying to install it

and if it doesnt follow the ./configure, make, make install, make clean way of installing im pretty much stumped

There exists just such a thing for linux.  For Ubuntu look for precompiled Debian packages (*.deb).

For example: If you wanted to install Opera 10 Alpha2 on 64bit Ubuntu you'd download and then click on the .deb file here:

[http://snapshot.opera.com/unix/snapshot-4166/x86_64-linux/](http://snapshot.opera.com/unix/snapshot-4166/x86_64-linux/)

---

### Post by Skripka on 2009-03-04
> **InspiredIndividual said:**
> Actually, I'm wondering, if you install from source using 'checkinstall'   instead of 'make install', will removing it from Synaptic do the trick? I'm not sure myself, but maybe someone more experienced can shed some light on this.

Ding ding ding.  That is EXACTLY why you should choose checkinstall instead of make install.

---

### Post by iaculallad on 2009-03-04
This is what Ubuntu Community say about [checkinstall]("https://help.ubuntu.com/community/CheckInstall").

---

