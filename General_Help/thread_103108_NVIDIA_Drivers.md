---
title: "NVIDIA Drivers"
date: 2005-12-13
forum: General Help
---

### Post by kg4gyt on 2005-12-13
I installed the NVIDIA drivers on my box, and now when I try to switch to another terminal (Ctrl-Alt-F?) I get a screen of random pixels when I'm on an analog cable (Digital just gives a monitor no signal error) and the system can't recover from it when switching back.  I'm using the 7667 drivers from nvidia.  Any thoughts?

---

### Post by tonysathre on 2005-12-13
open synaptic and search for nvidia-glx and make sure thats installed, then search for just nvidia and check to make sure all the proper packages are installed, if that doesnt work run this:
sudo dpkg-reconfigure xserver-xorg to reconfigure your new drivers for your xserver

---

### Post by kg4gyt on 2005-12-13
I gave it a try, and its still doing the same thing.  Any other solutions?

---

### Post by kg4gyt on 2005-12-15
It seems that if you disable usplash in the /boot/grub/menu.lst file and reboot the problem is solved, only you don't get a fancy boot splash screen.

---

### Post by Hoop on 2005-12-15
Ubuntu default xorg settings, even after installing nvidia-glx, need changing. I have nvidia gfx 5500 and had to edit xorg.conf, disable dri by putting a '#' infront of 

#Load   "dri"

#Section "dri"
#dri = (whatever)
#end section

dri is an ATI function apparently and not used by Nvidia.

I also had to change my default depth to 16, as my card supports 16 or 32 bit, not 24 bit.

---

### Post by kg4gyt on 2005-12-15
I use a GeForce FX 5700 Ultra and was able to leave the dri in. 

I did not use any packages through apt-get (Synaptic), instead in uninstalled nvidia-glx through that and then installed the drivers direct from nVidia.

---

