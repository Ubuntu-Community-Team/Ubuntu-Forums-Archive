---
title: "Get rid of grub loader"
date: 2009-03-03
forum: General Help
---

### Post by outy565 on 2009-03-03
Hey guys i just installed ubuntu 8.10 and i am also running vista.  i would like to get rid of grub loader and just use the normal boot loader.  is there a way for me to do this without uninstalliiing ubuntu?

---

### Post by James- on 2009-03-03
In vista download EasyBCD (i think its 1.7.2 now) and you can add the linux partition and restore the vista boot loader with the linux partition:

[http://neosmart.net/wiki/display/EBCD/linux](http://neosmart.net/wiki/display/EBCD/linux)

---

### Post by outy565 on 2009-03-28
ok, i have easybcd and added ubuntu to the mbr boot screen.  now my problem is that grub is the first boot manager to load.  in order to get to windows i have to select the longhorn option in grub.
What i want to do is have mbr the first boot loader to load.  from there i want to select one of my three OS's, vista, 7, or ubuntu.

So now my question is, how do i override grub with mbr so that mbr is the first bootloader to load.

---

