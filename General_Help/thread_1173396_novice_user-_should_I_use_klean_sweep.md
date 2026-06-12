---
title: "novice user- should I use klean sweep?"
date: 2009-05-29
forum: General Help
---

### Post by kingnug on 2009-05-29
Hello, 
I just downloaded "Klean Sweep" from the add remove programs window to try to free up some space on my computer... when I opened it, it told me that only advanced users should use this program because you can do damage with it... is there any suggestions for what I can delete or maybe a different program you know of? thank you for your time...

---

### Post by ghindo on 2009-05-29
There are several things you can do to free up hard drive space:[LIST][*]You can uninstall programs you don't use.  
[*]Delete files you don't need.  You can see what's taking up the most space by using the "Disk Usage Analyzer."
[*]Empty the trash.[/LIST]If you've tried all those things, you can run a few terminal commands:```
sudo apt-get autoremove
sudo apt-get autoclean
sudo apt-get clean
```That should free up a bit of space for you. :)

---

### Post by lisati on 2009-05-29
Ubuntu 9.04 comes with a "Computer Janitor" on the System->Administration menu.

---

### Post by oldos2er on 2009-05-29
Also install and run 'localepurge' to free up some hard disk space.

---

### Post by kingnug on 2009-05-29
thank you all very much, I didn't even know there was a new version of ubuntu, I will check it out.

---

### Post by kingnug on 2009-05-29
how do I mark this thread as solved?

---

### Post by amoun on 2009-05-30
Edit and change the title, I think :)

---

### Post by ghindo on 2009-05-30
> **kingnug said:**
> thank you all very much, I didn't even know there was a new version of ubuntu, I will check it out.Yup, every six months :)

---

### Post by mocoloco on 2009-05-30
In synaptic go to Settings -> Preferences -> Files, and have it "Delete downloaded packages after installation".  Depending on how many apps you have installed that can clear up quite a bit of space. And keep it clear, so you don't have to manually purge the cache.

---

