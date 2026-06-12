---
title: "disk full, cannot launch Gnome/terminal"
date: 2005-05-05
forum: Desktop Environments
---

### Post by secundar on 2005-05-05
So, I'm not so new to Linux but not experienced enough to get myself out of this one.

Using Synaptic I did a dist-upgrade. I shoulda known better as it's a smallish HD with dual boot XP. Anyway, the process failed. I noticed the disk was full and started deleting things from my home folder. The bytes free wouldnt update though so Iogged out and couldn't log in cause there's no room to write the Xuathority file.  :? 

I tried alt+F1... to get a commandline but the ubuntu login screen wouldn't have it.

(i think i'm still warty. even though i changed my repositories to hoary it's not fully updated.)

---

### Post by nad on 2005-05-05
Boot to recovery mode and start cleaning. You can start with: sudo apt-get autoclean . This ought to clear several tens to hundreds of megs.

---

### Post by secundar on 2005-05-05
Thanks Dan! Worked like a charm. Time for a bigger HD i think! :)

---

### Post by DutchLau on 2005-05-05
Maybe time for a bigger Ubuntu partition?  :razz: 

I made the mistake of giving Ubuntu Warty a 2 gb partition in October 2004 to test it out. Turns out it was almost full only after the install  :grin: 

Now I *only* have Ubuntu installed as I don't need windoze anymore for anything. I found all the linux counterparts!  :) 

Cheers,

DutchLau

---

