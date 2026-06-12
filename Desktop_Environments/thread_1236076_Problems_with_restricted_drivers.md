---
title: "Problems with restricted drivers"
date: 2009-08-09
forum: Desktop Environments
---

### Post by Jockboy98295 on 2009-08-09
Alright, I built this computer about a year and a half ago. Im now having problems with the restricted card drivers, i no longer have a gui. Ive tried everything i can to get the stupid thing to remove the restricted driver so that i can install envy ,if its still a viable option any more, its been a while since ive had the internet so im a little behind my game. :(   Just wondering if any of you have any hints or tips that ive forgot. I havent had this problem with any other version of ubuntu, currently on 9.04 64 bit.    Thanx.  



1.     XFX MB-N590ASH9 NVIDIA Socket AM2 ATX Motherboard
2.     AMD Athlon 64 FX-62 2.80GHz CPU (Overclocked to 3.2 GHz)
3.     Seagate 320GB 7200RPM 16MB Cache SATA Hard Drives (2 Drives set to RAID 0 Mode)
4.     Ultra 2048MB Dual Channel PC6400 DDR2 800MHz Memory (2 sets of 1GB sticks for a total of 4 GB)  
5.     XFX GeForce 8600 GTS XXX 256MB DDR3 SLI Ready PCI Express Graphics Cards (2 Cards in SLI mode)
6.     Ultra 3.5 Floppy Drive w/Multi Card Reader, SATA
7.     Lite-On LH-20A1S SuperWrite SATA DVD Burner (2 Drives)
8.     Acer AL2216WBD 22" Widescreen LCD Monitor (1 Monitor).    
9.     OCZ GameXStream 1000 Watt Power Supply Unit
10.    Linksys Dual-Band Wireless-N USB Network Card
11.    3Ware Hardware RAID 0 Controller Card

---

### Post by 3rdalbum on 2009-08-10
It's odd that you're having trouble with the restricted drivers for that card.

In any case, you can easily remove the driver. At the terminal, simply type:

```
sudo apt-get remove --purge nvidia-glx-180
```

After this, reboot, and you should have basic unaccelerated video back.

You might want to check that your monitor is still working as it should. Trust me on this :-)

---

### Post by stinger30au on 2009-08-10
what were you doing with the pc before it died?
had you done any upgrades???

you say there is 2 cards in sli.

what if you run only one card? make any difference?

---

### Post by dagrump on 2009-08-10
Okay, I think this will fix you up. With both cards installed & bridged (does your mobo require a card flipped or jumper switched?) I'm assuming & you know how dangerous that is, that if you reboot you get a terminal type login. then try the following.
After the drivers are installed & it boots back up, go ahead & log in.
Then you need to enter "lspci" this will list your hardware, find & write down the BusID of both cards.
Now enter "sudo nvidia-xconfig", it will ask for your password (there will be no visual feedback when typing your password).
That creates your xorg.conf file. Now to edit it.
You would enter "sudo nano /etc/X11/xorg.conf", nano is an editor.
Now arrow down till the cursor is at the EndSection line of the device section, hit enter twice.
Arrow up twice and enter line looks like so; BusID "XX:YY:ZZ", with XYZ being the numbers recorded earlier, of your primary card.
Drop to the next line & try; Option "SLI" "SFR".
Now crtl+o to write & crtl+x to exit.
And a "sudo shutdown -r now", to reboot & if all goes well you are working.

********
Please note where referencing CLI entries the quote marks should not be used, but during edit of xorg.conf they are needed.
IIRC the "SFR" is split screen rendering.
This is what my xorg.conf looks like, yours will be different due to detected hardware.

---

### Post by Jockboy98295 on 2009-08-12
Thanks guys. Thats all very helpful. Yes my card does require a card bridge, but nothing else. It has always worked in SLI on linux with no problems.  All I did was upgrade to 9.04. When I did, it disabled the old restricted drivers, so i re-enabled them. The new set of drivers did not work at all, an error kept occuring.  So i figured that my cards were too old, installed the old driver and it worked great until i rebooted the computer (I had rebooted the X-org server by using ctrl + backspace, everything was working great, and it was working as SLI).  Thanks guys, ill give it a try and get back to you.

---

### Post by Jockboy98295 on 2010-01-28
Well, before I could do what ya'll asked me to do, my motherboard decided to crap out on me. My new build is this.  Unfortunately I have had to completely reformat the hard drives (stupid vista) and start all over again. So Now I have a fresh install of 9.10 and a new set of issues. SLI wont enable! :(  Any help in that particular department would be much appreciated. Thanks again. 

1. ASUS M3N-HT Deluxe Socket AM3 ATX Motherboard
2. AMD Phenom 9750 Quad Core 2.40GHz CPU (Overclocked to 3.3 GHz)
3. Seagate 320GB 7200RPM 16MB Cache SATA Hard Drives (2 Drives set to Dual Boot OS, Win Vista & Ubuntu))
4. Ultra 2048MB Dual Channel PC6400 DDR2 800MHz Memory (2 sets of 1GB sticks for a total of 4 GB)
5. XFX GeForce 8600 GTS XXX 256MB DDR3 SLI Ready PCI Express Graphics Cards (2 Cards in SLI mode)
6. Ultra 3.5 Floppy Drive w/Multi Card Reader, SATA
7. Lite-On LH-20A1S SuperWrite SATA DVD Burner (2 Drives)
8. Acer AL2216WBD 22" Widescreen LCD Monitor (1 Monitor).
9. OCZ GameXStream 1000 Watt Power Supply Unit
10. Linksys WUSB600N V.2 Wireless card
11. Microsoft Ergonomic Keyboard 4000
12. Logitech Trackman Mouse
__________________

---

### Post by Jockboy98295 on 2010-11-02
Sorry its taken so long to get back to yall. Been really busy. Anyway< did as "dagrump" stated and after everything was done, it works great. thanks guys.

---

