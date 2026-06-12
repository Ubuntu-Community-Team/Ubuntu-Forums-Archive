---
title: "Sound doesnt work anymore..."
date: 2009-08-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by holycow131415 on 2009-08-29
Hello, im not a pro at linux. So i have a Inspiron 4000 laptop. I had to edit the xorg.conf file in etc/X11/ to get my video card to display a 1024x768 res. That is working now, but now i do not get any sound.I do not have alsa mixer as an option in my sound mixer. Before it saw my audio card in the mixer, but now all i see is pulseaudio. i have installed alsamixer from package manger, but still i get an error.  lspci sees my audio card, but when i do alsactl, it doesnt see it.

Is there a module that should be in the xorg.conf file that isnt there anymore? Before i did anything to it, the file was blank... I dont understand how my sound could disappear. Alsa website doesnt list my audio card, but my audio was working on a fresh install.

00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:03.0 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
00:03.1 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
00:08.0 Multimedia audio controller: ESS Technology ES1983S Maestro-3i PCI Audio Accelerator (rev 10)
01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility M3 AGP 2x (rev 02)
02:00.0 Ethernet controller: 3Com Corporation 3cCFE575CT CardBus [Cyclone] (rev 10)

---

### Post by holycow131415 on 2009-08-29
Also, i forgot to mention that my computer does beep loud and clear. i hope someone helps me =(

---

### Post by holycow131415 on 2009-08-30
i figured out the solution... i used grub back up entry, saw that my sound was still there and that my res was still fixed. so i went into package manager, deselected new linux-images so that it boots to the working linux-image...

---

