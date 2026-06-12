---
title: "kernel compiling"
date: 2005-04-26
forum: Desktop Environments
---

### Post by [pl]ice on 2005-04-26
hi, i'm new to this distro...
i have read the info about kernel on this web, everything should be ok, but i cannot (as root) find make-kpkg  !! man doesn't exist either... 
description;
i only user SuSE and fc3 before,(now i jumbed with distr...) when i compiled kernel etc. and changed grub, i can't boot , error: kernel panic-not syncing:VFS:unable to mount fs on unknown -block(0,0)  
i guess that i need initrd, so tried to make it initrd -o /initrd-... etc, gave me an initrd file(not an image) in /boot  , still didn't work, but i don't need initrd, so i don't really want to use it,, looked up google and got $ fakeroot make-kpkg --append-to-version=.181004 kernel_image --initrd binary
     will that install or by-pass initrd? i would like to try it, BUT i can't find make-kpkg, even in the upgrate packet manager...
please help!
thank you, sorry for my crappy english ;)

---

### Post by az on 2005-04-26
Why compile a new kernel?

make kpkg is in the package called kernel-package.  It is in universe.

---

### Post by Firetech on 2005-04-26
There is an excellent guide at: [http://www.ubuntulinux.org/wiki/KernelHowto](http://www.ubuntulinux.org/wiki/KernelHowto) (Which probably is the one you found with google.) If you read all of it, you'll see that you have to run "sudo apt-get install build-essential fakeroot kernel-package" first.
The upgrade package manager only lists packages to upgrade, you should run Synaptic or Kynaptic to install new packages.
Also, this isn't a Kubuntu specific issue, it should be in the normal Ubuntu forums AFAIK.

---

### Post by [pl]ice on 2005-04-26
um, why? looks like it didn't find my sound card, and 2ndly i need a practice at that, once i start something i never give up  ](*,)  , but it's mainly for the practice i guess.
  thnx for the link, and will post messeges in the right spot next time.

---

