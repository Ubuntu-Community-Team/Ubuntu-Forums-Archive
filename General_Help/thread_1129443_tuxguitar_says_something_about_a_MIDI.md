---
title: "tuxguitar says something about a MIDI??"
date: 2009-04-18
forum: General Help
---

### Post by silverdrop on 2009-04-18
tuxguitar says: midi system is unavailable. what does that mean?? plz help!

---

### Post by justin_guerin on 2009-04-18
It means either your sound card is not configured to support midi ([http://en.wikipedia.org/wiki/Musical_Instrument_Digital_Interface](http://en.wikipedia.org/wiki/Musical_Instrument_Digital_Interface)) or tuxguitar doesn't know how to use it.  Your problem is likely the former.

If you don't know how to enable midi for your sound card, then post the exact type of sound card you have (lspci -vvv, trimmed to the appropriate details, should do), the kernel modules you have loaded (lsmod), and whether or not you've compiled your own kernel.

---

### Post by silverdrop on 2009-04-22
the first time, it run easily. but then i start the computer and suddenly doesnt work.

---

### Post by Kareeser on 2009-04-22
sudo apt-get install timidity

---

### Post by silverdrop on 2009-04-22
hey! that an error that has been appearing all time that i downloads updates. it says something about an error. when i did "sudo apt-get install timidity" command it says "error", what should i do? re-install? how?

---

### Post by BslBryan on 2009-04-22
Copy and paste from the terminal, please.  Also, please post results of lspci -vvv.

---

### Post by silverdrop on 2009-04-22
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up timidity (2.13.2-19ubuntu1) ...
 * Starting TiMidity++ ALSA midi emulation...                            [fail] 
invoke-rc.d: initscript timidity, action "start" failed.
dpkg: error processing timidity (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 timidity


and the "lspci-vvv" whats that?

---

### Post by BslBryan on 2009-04-22
It prints detailed information on your sound devices.  Also, are you able to download anything with apt-get?  Try ```
sudo apt-get install audacity
```

---

### Post by silverdrop on 2009-04-23
it download audacity so it works fine, but again, it says the timidity error. and how do i use the "lspci-vvv" command?

---

