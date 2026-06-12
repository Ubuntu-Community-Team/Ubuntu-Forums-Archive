---
title: "Audiojack / Micjack troubles..."
date: 2007-09-22
forum: Dell  Ubuntu Support
---

### Post by arcanus on 2007-09-22
I have just gotten my Precision M6300 and have installed Ubuntu on it. Im running 7.04, so its no testing packages breaking anything either.

Ive gotten all working, except the sound. That is, the sound IS working, not just the way i want it to... If i boot my computer without a headset plugged in, i get sound in my speakers. Good sound too, nothing wrong there. But if i plug in a headset i get NO sound in my headset, but its still on my speakers... If i boot the computer with a headset plugged in i get good sound in the headset. But if i unplug the headset... Guess what, no sound in the speakers... Is there anything i need to install to get that switch done? Make it use the headset if its plugged in and the speakers if nothing is plugged in? What do i need to edit? Where does the computer deside where the sound go? Help...

```
# uname -r
2.6.20-16-generic

# lshw
*-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: iomemory:febfc000-febfffff irq:20

```

---

### Post by neptho on 2007-09-22
This worked for my Inspiron 6400:

Edit /etc/modprobe.d/alsa-base (as root);

Add to the bottom:

```
options snd-hda-intel model=ref
```

Then, restart your system.  (This is just easier than trying to kill off all of the audio daemons and reload the modules by hand.)

Others have had luck with "model=dell"

---

### Post by perryrt on 2007-09-22
If it makes you feel any better, my Inspiron 1420n (which came pre-configured from Dell with Ubuntu) has two headphone jacks....but Ubuntu only works with one of them. No idea why.

So this isn't completely unique.

---

### Post by neptho on 2007-09-23
> **perryrt said:**
> If it makes you feel any better, my Inspiron 1420n (which came pre-configured from Dell with Ubuntu) has two headphone jacks....but Ubuntu only works with one of them. No idea why.

Are you sure that one isn't a microphone port?

---

### Post by arcanus on 2007-09-23
Unfortunatly that didnt work :(

Anyone else got a idea? :P

Is it any way i can manually swap the mutes? that would work equally good...

---

### Post by arcanus on 2007-09-24
Hmm... how do i make ALSA take control? It looks like its OSS that controlls the sound atm... ALSA controlls muted and still sound :shock:

---

### Post by arcanus on 2007-10-10
Shameless bump...

I dont want to reboot all the time =(

---

