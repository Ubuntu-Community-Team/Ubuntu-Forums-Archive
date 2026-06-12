---
title: "Keeping my upgrade safe"
date: 2006-01-07
forum: General Help
---

### Post by tamarku on 2006-01-07
I was a 5.04 Hoary user and I loved Ubuntu that I upgraded to 5.10 Breezy.  Well I do not have a CD or anything of 5.10.  Is there a way to burn an image of my system so that in the event of a failure I could reinstall 5.10 without have to load 5.04 again and going through the long process of upgrading?  Also, I ran a script called Automatix and to whoever wrote that thing it was a stroke of genius.  It made EVERYTHING so easy.  Also, what files do I want to backup?  So once I do get 5.10 back I can just reload.  Even though I've been experimenting with Linux for some time now please consider me a newbie.  Thank you for any and all help anyone can offer.  Also, if there is a Tips and Tricks I would appreciate that also. Thanks again!!

---

### Post by gila_monster on 2006-01-07
Sure thing. Just download the ISO image from the Ububtu download site and burn it to a disc. You will be able to install from it if necessary (but I hope it won't be).

gm

---

### Post by tamarku on 2006-01-07
Thanks a lot for the help.  I was wondering is there a way to burn my current setup and everything to CD so that if something came up I could just re-install and then the system would be just as I have it today?  Sorry, I wasn't very clear before, BUT, I do think I will be downloading a version 5.10 anyway.  If I can't burn my current setup onto a CD then what files and folders should I back up so that after I get 5.10 installed again I just re-instate my back up?

---

### Post by mcmillan on 2006-01-08
Pretty much everything you need to back up is in your home folder. If you make a copy of all of this into the new home folder it should keep most of you personal settings, just make sure you include the hidden files, the ones that start with a period.

---

### Post by tamarku on 2006-01-08
GREAT Thanks for the help!!

---

### Post by arphe_el on 2006-01-17
hello

have you try to upgrade from hoary to breezy using live CD or install CD by reconfiguring the sources.list and eventually apt-cdrom or synaptic will upgrade it?

any suggestions? thanks since i have a copy now of breezy and i don't want to go to a process of installing breezy again since i have to tweak everything all over again plus the backing up procedure is very tasky.

thanks hope to hear from you.


[QUOTE=tamarku]I was a 5.04 Hoary user and I loved Ubuntu that I upgraded to 5.10 Breezy.  Well I do not have a CD or anything of 5.10.  Is there a way to burn an image of my system so that in the event of a failure I could reinstall 5.10 without have to load 5.04 again and going through the long process of upgrading?  Also, I ran a script called Automatix and to whoever wrote that thing it was a stroke of genius.  It made EVERYTHING so easy.  Also, what files do I want to backup?  So once I do get 5.10 back I can just reload.  Even though I've been experimenting with Linux for some time now please consider me a newbie.  Thank you for any and all help anyone can offer.  Also, if there is a Tips and Tricks I would appreciate that also. Thanks again!![/QUOTE]

---

### Post by nocturn on 2006-01-17
If you boot with a liveCD, you can image your partitions with tar, write the resulting fire to a disc and restore from it later...

---

### Post by GeneralZod on 2006-01-17
[QUOTE=nocturn]If you boot with a liveCD, you can image your partitions with tar, write the resulting fire to a disc and restore from it later...[/QUOTE]

This is pretty much what I always do before an upgrade (although I make sure that /var/cache/apt/archives is archived separately, to keep the image-size/ compression-time down - it makes quite a difference).  I use the "bzip" tar option for compression - "man tar" will give you the details you need.

---

