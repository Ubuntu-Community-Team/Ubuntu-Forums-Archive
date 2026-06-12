---
title: "unable to turn on visual effects"
date: 2009-11-21
forum: Desktop Environments
---

### Post by mIXpRo on 2009-11-21
hi, 
i'm having problem with :
1-)turning on the visual effects
2-)and my screen resolution sucks 
3-)tried to install flash player but it didnt work i get black screen with no buttons on youtube
 
could i get some help 
this what i get when running the compiz-check :
```

Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
 Driver in use:         vesa
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: vesa driver in use 

Would you like to know more? (Y/n) y

 The vesa driver is not capable of running Compiz, you need to install
 the proper driver for your graphics card.

```
thanks anyway

---

### Post by coffeecat on 2009-11-21
The reason for problems 1 and 2 is that you are using the vesa driver which has no 3d capabiities and supports only a limited number of screen resolutions. The Intel video chipset you are using is the identical one to what I have on my Sony laptop, but in Jaunty (9.04) and Karmic (9.10) my system was set up to use the intel driver. Both compiz visual effects and screen resolution are fine in both Jaunty and Karmic. So is flash but your flash problem may or may not be related.

I was surprised that the 8.04 installer didn't set you up with the intel driver, but then I realised that the Mobile 4 chipset is a relatively recent one and perhaps the 8.04 intel driver (which is an earlier version that the ones in 9.04 and 9.10) may not work with that chipset. Maybe - I don't know. Perhaps that's why your system is running with the vesa driver.

A couple of questions: what is the laptop you are using? Are you using 8.04 for a specific reason? Have you thought of running a later version? If you were put off Jaunty by reports of intel video problems, I can tell you that those problems bypassed the Mobile 4 chipset. It wasn't affected.

If you want to consider running either 9.04 or 9.10, download the desktop CD ISOs and try running them live. You can enable compiz in the live session with intel video. And you will also be able to see whether you get the correct screen resolution.

---

### Post by mIXpRo on 2009-11-23
first : 
my laptop is dell latitude e5500
second :
i tried to install ubuntu 9.10 but at the boot screen it gave me dead white screen and so when i tried to install the 8.04.
but then i read at the forum that the problem might be solved by fixing the graphic boot configurations , and so i tried to change them with both ubuntu 9.10 and 8.04, but the only one worked is 8.04.

---

### Post by coffeecat on 2009-11-23
I've found a couple of threads where people have managed to install 9.10 on a Dell Latitude e5500. If you were having problems booting up the live CD, the most likely cause was a bad CD or a bad ISO.

Did you check the md5sum of the downloaded ISO and did you burn at a low speed? Have a look here:

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

and for md5sum here:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by mIXpRo on 2009-11-24
i did what you have told me to do i checked the cd's burned another one ,with minimum
speed. 
but it still gave the white screen . 
i have no idea of what to do

---

### Post by sabre2th on 2009-11-24
Where do you get the white screen?  Is it before the LiveCD load screen (gives you the option to boot the LiveCD, boot from HD, check the disk, etc)?  Or after?

If you do get that screen, first check the disk.  If it passes the test, try booting in safe graphics mode.  That option is tucked into a menu and I believe it is accessed with F4.

Edit: If we can't get the LiveCD working, you should be able to install using the Alternate Install CD, which doesn't bother with the fancy graphical stuff until you're actually running from the hard drive.

---

### Post by mIXpRo on 2009-11-24
i tried booting with safe graphic mode and it worked with the 8.04,
but the resolution screen sucked and i couldn't enable the visual effects.

but no worries :D my problem solved i booted up the 9.04 from usb stick and it worked
fine , it amazing 

                                  thanks for you anyway.:P

---

