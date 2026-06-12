---
title: "microphone"
date: 2009-05-20
forum: General Help
---

### Post by ultratek on 2009-05-20
this is my sound card on my dell xps420:
*-multimedia
       description: Audio device
       product: 82801I (ICH9 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel

how do i get my mic to stay un muted in jaunty 64bit
and actually record something
i have a cheap pluginto the front of pc mic pink jack
thx

---

### Post by paradigm2 on 2009-05-20
Install gnome-alsamixer if you have not already.  There you should be able to mute, unmute, and adjust volume and possibly boom settings for the mic.

---

