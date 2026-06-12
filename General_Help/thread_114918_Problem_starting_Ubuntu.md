---
title: "Problem starting Ubuntu"
date: 2006-01-09
forum: General Help
---

### Post by tornadotsunamilife on 2006-01-09
OK so first time user of linux and also first post/thread. <-- Please be kind

When I boot Ubuntu (it's on a partition and I'm dual-booting with Windows XP) it starts up, loading all modules and then I get a login screen in a command prompt style (DOS-esque), it flashes on and off a few times and then I get an X server problem (generic message pops-up).
I can then login and use commands (still no sign of Gnome, still a command prompt screen). I've tried installing the fglrx drivers (sudo apt-get install xorg-drivers-fglrx) but it says they aren't there. I've also tried using the vesa drivers (via: sudo dpkg-reconfigure xserver-xorg) and just editing the xorg configuration files (sudo nano /etc/X11/xorg.conf). But none of it is working :( 

Any light shed or help made on this problem would be greatly appreciated

EDIT* Sorry probably should of added some hardware specs (if it helps):-
Radeon X850XT graphics card
DFI nf4 Ultra-D motherboard
Athlon64 3200+ (not running 64-bit lnux though)
1GB Corsair Ram

---

### Post by Ocxic on 2006-01-09
if your video card is AGP check you bios for a video settingit should say
something like "video card to first initialize/use" with an option of AGP or PCI change that to whatever you video card is using and reboot. this can cause problemes with xorg. my vid card is AGP and if i use PCI and the option xorg no longer works.

---

### Post by tornadotsunamilife on 2006-01-09
Sadly it is PCI-e but thanks anyway

---

### Post by Ocxic on 2006-01-09
i hope you didn't misinterpret my post, you CAN use PCI video cards, i'm just saying check the settings in you bios for it to activate the PCI slot first and not the AGP slot. it should be in advanced settings of your bios.

---

### Post by tornadotsunamilife on 2006-01-09
Sorry, what I meant was, my vidoecard is pci-express. I don't have agp slots and no pci videocards

---

### Post by tornadotsunamilife on 2006-01-09
Is it possible to have some kind of sure fire way of getting into the gnome desktop (I thought 'vesa' drivers but that didn't work)? Because I could then download drivers of ATi's website or something

---

### Post by tornadotsunamilife on 2006-01-09
Sorry for all the posts but I was wondering if I could possibly use another distro  (like knoppix) to download the driver onto the partition and then install it using ubuntu?

Also, is it possible that I may have posted in the wrong part of the forum because I've just noticed a hardware/vision section and I think that is my main problem (drivers).

---

### Post by tornadotsunamilife on 2006-01-10
I'm unsure if it's against the forum rules but here's a bump...

---

