---
title: "Black Screen After Enabling ATI Graphics Driver"
date: 2009-06-09
forum: General Help
---

### Post by scythian on 2009-06-09
Hi, I am new to this forum and have just tried out Linux for the first time. I have had a bit of trouble with a graphics driver and would be grateful if anybody could point me in the right direction or give any advice.
 
I have installed Ubuntu v 8.04.2 (i386) Desktop edition on a PC with the following specs :-
 
3GHz Pentium 4 CPU
4GB RAM
ATI Radeon X1650 Pro AGP 8x 512MB graphics card
Intel D865GBF mobo
 
After installation everything looked OK, and there was an icon at the top right hand side saying an ATI graphics driver was available, which may provide better graphics performance. So, I selected the option to enable this driver, but on reboot I now get a black screen every time.
 
I am just wondering if I'd be better off just leaving the 'generic' driver that has been installed during the installation from the Live CD - ie. is it not worth bothering with this supposedly 'better' driver ?
 
Is my graphics card not very well supported on Ubuntu ?
 
Is there any way to recover a Linux system which is black screening like this on every boot ? Like in Windows you can go into a 'Safe Mode'.
 
Also would it be worth trying the Linux driver for the graphics card as downloaded from ATI web-site. This is a '.run' file ('ati-driver-installer-9-3-x86.x86_64.run'). Do you just copy this to the Linux system and double click it to automatically install it ?
 
I am basically wondering what is the best approach to use with drivers for graphics cards such as ATI cards ? If I had a newer system would it likely work much better ?
 
Any advice would be much appreciated as I'm total newbie to Linux.

---

### Post by Mehashi on 2009-06-09
Hello!

I am having this same problem and still have not figured it out, but the usual way to try to fix this is to:

Reboot, Wait for grub to pop up and press [esc] you should then get a recovery mode option. What you are looking for here is an option along the lines of "fix graphics problems". Try that, it works for some but it hasnt for me and I have the x1950 512mb card.

Good luck, nVidia is easy on *nix, but Ati is a nightmare!

---

### Post by scythian on 2009-06-10
Hi there! Thank you for reply. I just tried the 'Fix X Server' option on the Grub menu and this allows me to get as far as logging in but then the screen goes white.
 
I have never used Linux before - its certainly a lot different from Windows, but in some ways it looks pretty impressive.
 
Did you try the ATI supplied Linux driver for your card ?
 
For my card this a .run file. I will have to reinstall the system to try this out.

---

### Post by Legace on 2009-06-10
Reboot PC, select "Recovery mode" in boot-manager (GRUB) and then go for "root shell" option (you might need to press the DOWN arrow a couple of times). 
After that just type:
```
sudo apt-get remove xorg-driver-fglrx
```

Now you will need to restore your original settings, so either restore any backed-up copy of file /etc/X11/xorg.conf or run something like:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

or another one (you will have to answer a few simple questions)
```
sudo dpkg-reconfigure xserver-xorg
```

then type
```
exit
```

and select "resume normal boot"

This should get you back to your Ubuntu desktop, but running on default drivers.

---

### Post by Mehashi on 2009-06-10
Thank you!

This has fixed my problems, and I am back to my original purple cube, all of the effects are now as they were before I installed the ATI driver from the add/remove menu! Great stuff thank you!

The step I had not done was
```
sudo apt-get remove xorg-driver-fglrx
```followed by 
```
apt-get autoremove
```to get rid of the extraneous files. I had only tried to re-write the xorg conf file and the recovery mode option. Now everything is working again (after reconfiguring xorg.conf)! 

Thank you very much, that system was out of action for two days! [COLOR=Magenta]^_^b[/COLOR]

---

### Post by scythian on 2009-06-10
Thank you very much Legace - that has got the system back up and running without having to reinstall - that has saved me time thanks

---

