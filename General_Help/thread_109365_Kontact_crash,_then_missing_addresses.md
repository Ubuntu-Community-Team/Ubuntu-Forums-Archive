---
title: "Kontact crash, then missing addresses"
date: 2005-12-28
forum: General Help
---

### Post by Seth Williamson on 2005-12-28
I am running Kubuntu 5.10, after having installed Ubuntu from CD--I upgraded to Kubuntu via apt-get.
 
A few days after I installed it, I noticed that, when I clicked on the Kontact icon, it would give me the "spinning clock" icon for a good deal of time, and then stop as if the app were then up--only it wasn't. I had to click it a second time to make Kontact appear.
 
A couple of days ago I started to get error messages saying that the KDE panel had crashed. I saved the backtrace for one of these. Then yesterday, I also noticed that my Kontact addressbook for Kmail had vanished.
 
 I just started kontact under kde in a terminal to see if I'd find any error messages, and I got this:
 
 seth@orthobox:~$ kontact
 kdecore (KAction): WARNING: KAction:lugAccel(): call to deprecated action.
 kdecore (KAction): WARNING: KAction:lugAccel(): call to deprecated action.
 kdecore (KAction): WARNING: KAction:lugAccel(): call to deprecated action.
 seth@orthobox:~$ WeaverThreadLogger: thread (ID: 1) suspended.
 WeaverThreadLogger: thread (ID: 2) suspended.
 WeaverThreadLogger: thread (ID: 3) suspended.
 WeaverThreadLogger: thread (ID: 4) suspended.
 
I don't know what this means. Does anybody have any idea what's going on here? And how to fix it?
 
 
 Seth Williamson
 Slings Gap
 Franklin County, VA
 USA

---

### Post by jeremy on 2005-12-29
I don't know what the errors mean, but, with a bit of luck you will find several files in ~/.kde/share/apps/kabc called std.vcf , std.vcf_1 etc. The largest of these should have all your contacts.

One thing you could try is to copy this file elsewhere, then reinstall kontact, then copy it back.

---

