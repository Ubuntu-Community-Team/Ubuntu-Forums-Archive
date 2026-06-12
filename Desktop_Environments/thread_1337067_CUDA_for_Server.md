---
title: "CUDA for Server?"
date: 2009-11-25
forum: Desktop Environments
---

### Post by njparton on 2009-11-25
I have a homemade NAS device that runs Ubuntu Server.
 
It runs Boinc-client when it's on and I can sucessfully manage it from Boinc Manager in Windows.
 
I currently don't have a desktop installed, the NAS is command line only.
 
I've got a GeForce 260 card lying around that I'd like to stick in the NAS to make available to Boinc via CUDA.
 
My questions are:
 
1. do I need to install both gnome desktop and latest nivdia display drivers to get this to work or are there other CUDA packages I can install to avoid this?
 
2. If I do need to install gnome and nvidia drivers, once I've done this can I close down gnome/gdm to save resources and will this impact on CUDA/Boinc?  Boinc client currently runs fine from just the command line.  i.e. for CUDA do I need to keep gnome running?
 
Thanks in advance for responses :D

---

### Post by Xyro on 2009-11-26
I am new to CUDA, but I don't see why you would need to install GDM. You'll need the latest nVidia drivers ( > 190 I think...). I think you'll need to do create the nVidia devices (in /dev/), since you don't have X11. I believe this is explained in the instructions from nVidia (just from the reading I've done, not from experience).

I see that BOINC incorporates CUDA enabled devices, I'd say give it a try and report findings!

---

### Post by njparton on 2009-11-27
Thanks for that.  Which nvidia instructions are you referring to?

---

