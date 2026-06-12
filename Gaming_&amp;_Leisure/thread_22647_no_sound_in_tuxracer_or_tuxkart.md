---
title: "no sound in tuxracer or tuxkart"
date: 2005-03-28
forum: Gaming &amp; Leisure
---

### Post by nix4me on 2005-03-28
I have no sound in both Tuxracer and Tuxkart.  My system sounds work fine and totem playes movies with sound just fine.

This is the error i saw in the console:
%%% tuxracer warning: Warning: Couldn't set 22050 Hz 16-bit audio
  Reason: No available audio device

Any ideas?
 
Mark

---

### Post by bruce89 on 2005-04-06
What I did was installed libsdl1.2debian-all and uninstalled libsdl1.2debain-oss.  This fixed the sound in PPracer which is the same as tuxracer.

---

### Post by brehloi on 2005-04-08
[QUOTE=bruce89]What I did was installed libsdl1.2debian-all and uninstalled libsdl1.2debain-oss.  This fixed the sound in PPracer which is the same as tuxracer.[/QUOTE]
thanks! this worked for me!  =D>

---

### Post by mandy2tom on 2005-04-10
when ever i have no sound i kill esd 
run in term
gconftool-2 --type boolean --set /desktop/gnome/sound/enable_esd false

---

### Post by Silwenae on 2005-04-10
This fixed the no sound problem I was having with UT2k4 as well, thank you!

---

### Post by Vaughn on 2005-04-25
This fixed the no sound problem with supertux as well.

One thing to note is that if you use synaptic and you select to install libsdl1.2debian-all then synaptic tells you that it is going to uninstall libsdl1.2debain-oss for you.

---

### Post by jerrykenny on 2005-06-15
Bruce89 . . . . that worked for me as well thanks  :razz:

---

