---
title: "beryl using ATI card"
date: 2007-06-19
forum: Desktop Environments
---

### Post by Ultra Magnus on 2007-06-19
Well, I've just got my new computer (Dell Inspiron 6400) and I have got a vista / ubuntu dual boot and everything works fine!

The computer has an ati video card though - at this point I ought to point out that I owe lifeempowered.com a great deal of thanks - I followed this post ([http://ubuntuforums.org/showthread.php?t=399913&highlight=Feisty+%26amp%3B+Beryl+On+Dell+Inspiron+6400](http://ubuntuforums.org/showthread.php?t=399913&highlight=Feisty+%26amp%3B+Beryl+On+Dell+Inspiron+6400)) to get x to work and it worked perfectly! - except I can't seem to get beryl up and running, its all installed (I have the frgl driver because my x1400 card isn't supported on the open source driver).

When I try to start beryl it tells me "No Compositing extention" - I've tried reinstalling xorg and the drivers but it says I am up to date - Any ideas how to get beryl working with this card?

Thanks 

Jim

edit - also i have two options to boot ubuntu from the boot menu, i know i can edit the menu.lst file but i don't know which to delete?

---

### Post by llamakc on 2007-06-19
> **Ultra Magnus said:**
> 

edit - also i have two options to boot ubuntu from the boot menu, i know i can edit the menu.lst file but i don't know which to delete?

Why would you delete one? It is not hurting anything. If you have the current kernel and a second one that says (recovery mode) you do NOT want to delete the recovery mode. If you have an older kernel version in there, you can use apt-get/Synaptic/aptitude to remove that version. Frankly, they take up very little space. I suggest not worrying about them.

---

### Post by tronica on 2007-06-19
only open source drivers for ati work with aiglx, so if you use the proprietary driver you have to use Xgl.

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29)

check that out.
also one thing i noticed with ati cards is you have to disable composite extension

---

