---
title: "Out of Range - Post ATI Driver Installation"
date: 2009-06-03
forum: General Help
---

### Post by EmanuelO on 2009-06-03
I have just installed Ubuntu 64-bit. Everything was great except for my GPU which is a ATI Radeon 4350. Ubuntu wouldn't display at the proper resolution. Ubuntu was offering to install the graphics drivers for me automatically but it would never work, so I downloaded the drivers myself from the ATI site. The installation was claimed to be successful and I rebooted. Now my monitor is displaying Out of Range everytime I boot into Ubuntu. For whatever reason Ubuntu is displaying at a resolution and/or frequency that my monitor can't handle. How do I fix this so I can get into Ubuntu normally?

---

### Post by EmanuelO on 2009-06-03
This is in Ubuntu 9.04 BTW

---

### Post by EmanuelO on 2009-06-03
bump

---

### Post by EmanuelO on 2009-06-03
Do you guys require more information?

---

### Post by porchrat on 2009-06-03
When you load GRUB (the linux boot loader), boot the Ubuntu recovery option instead of the option you normally select. Then select the "Recover X" option.

That should at least reset your drivers to the originals so that you can get back into Ubuntu and do some further work on it.

If all you use is Ubuntu 9.04 then you will probably need to press F5 (you will be prompted) at some point to get the GRUB menu to display.

EDIT: Welcome to the forums by the way :)

EDIT again: How exactly did you install the driver? Did you use that GUI installer or did you follow a howto guide of some sort and install through the command line?

---

### Post by EmanuelO on 2009-06-03
> **porchrat said:**
> When you load GRUB (the linux boot loader), boot the Ubuntu recovery option instead of the option you normally select. Then select the "Recover X" option.

That should at least reset your drivers to the originals so that you can get back into Ubuntu and do some further work on it.

If all you use is Ubuntu 9.04 then you will probably need to press F5 (you will be prompted) at some point to get the GRUB menu to display.

EDIT: Welcome to the forums by the way :)

EDIT again: How exactly did you install the driver? Did you use that GUI installer or did you follow a howto guide of some sort and install through the command line?

I installed by following ATI's installation instructions. I had to activate the .run file through the command line then I followed a GUI installer. I would really like to get the driver to work so I can have video acceleration and the correct resolution.

---

### Post by EmanuelO on 2009-06-03
I wasn't able to find "Recover X" but I found something called "fixX". It said it would fix graphics problems. So I let it do its thing and I rebooted and went into Normal mode now Ubuntu just boots into a staticy, artifact-filled screen. It doesn't respond and I have to reset. I really don't want to reinstall Ubuntu again. I have done that 4 times already. How can I get a system that works with my gpu? ;_;

---

### Post by EmanuelO on 2009-06-03
BTW this is a "Frankenstein" computer I built myself. All parts are less than a year old in terms of manufacturing date. This is the first version of Ubuntu that has successfully worked in terms of it working Live off the CD. All other versions produced I/O errors. 

My build is based off an Intel E5200 CPU and Gigabyte P45 DS3L motherboard. Could this have any relevance to the issue?

---

### Post by EmanuelO on 2009-06-03
Well thanks so far for your help. I guess I am going to have to go at this alone.

---

### Post by EmanuelO on 2009-06-03
I already asked this but I believe my question was not clear. If you don't mind I am going to ask again.

When I boot into Ubuntu all I get is static and colorful artifacts. It booted normally before I installed ATI drivers for my ATI Radeon 4350. I need these drivers for I hope that they will enable me to have game/video acceleration and the ability to see Ubuntu at my monitors reccommended resolution. Without these drivers I am left without these features. So how can I restore my Ubuntu 9.04 64-bit installation to operating status with functioning drivers? I really need assistance. I've tried fixing it on my own but no success.

---

### Post by VastOne on 2009-06-03
> **EmanuelO said:**
> I already asked this but I believe my question was not clear. If you don't mind I am going to ask again.

When I boot into Ubuntu all I get is static and colorful artifacts. It booted normally before I installed ATI drivers for my ATI Radeon 4350. I need these drivers for I hope that they will enable me to have game/video acceleration and the ability to see Ubuntu at my monitors reccommended resolution. Without these drivers I am left without these features. So how can I restore my Ubuntu 9.04 64-bit installation to operating status with functioning drivers? I really need assistance. I've tried fixing it on my own but no success.

You need to boot into recovery mode (second option on your grub menu). Once it loads, one of the choices is to fix X.  Try that and select boot normal.

See if that corrects it

---

### Post by alphacrucis2 on 2009-06-03
If the previous poster's method doesn't work, then boot into recovery again and select the option to boot into the root prompt and type:

```
aticonfig --initial -f
```

Then try and boot normally.

---

### Post by EmanuelO on 2009-06-03
> **alphacrucis2 said:**
> If the previous poster's method doesn't work, then boot into recovery again and select the option to boot into the root prompt and type:

```
aticonfig --initial -f
```Then try and boot normally.
I've already tried VastOne's method and I did a second time. It did nothing. Your method has gotten me back to my original problem to where the monitor displays out of range. How do I change my resolution/frequency through terminal to correct this.

Gentlemen, thank you both for the help so far. I'm sorry for spamming this three times already.

---

### Post by EmanuelO on 2009-06-03
This thread solved it,

[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

Thank you! I apologize again for my spamming.

---

### Post by porchrat on 2009-06-04
> **EmanuelO said:**
> I already asked this but I believe my question was not clear. If you don't mind I am going to ask again.

When I boot into Ubuntu all I get is static and colorful artifacts. It booted normally before I installed ATI drivers for my ATI Radeon 4350. I need these drivers for I hope that they will enable me to have game/video acceleration and the ability to see Ubuntu at my monitors reccommended resolution. Without these drivers I am left without these features. So how can I restore my Ubuntu 9.04 64-bit installation to operating status with functioning drivers? I really need assistance. I've tried fixing it on my own but no success.

Sorry it took me so long to reply, I needed to go to sleep and I didn't expect you to respond so quickly.

I've been thinking about it and I thought maybe you could use the liveCD to boot and then mount your drive and remove the fglrx drivers thus forcing Jaunty onto the MESA drivers or whatever it defaults to these days, but I doubt that would work as you wouldn't be accessing your drivers, only the default ones on the disk (i.e. you wouldn't be able to reverse the changes you have made automatically, rather you would need to do it manually and that is something I really don't know how to do.

When you boot up and get that artifact-filled screen you could try using the keys "ctrl+al+F1" to get to a good old terminal (no graphics frontend, it is just a simple command line interface). Once you login using your normal username and password you could use apt-get to remove the fglrx driver, to do this type:

```
sudo apt-get remove xorg-driver-fglrx
```

That should remove the fglrx drivers you have installed and force Jaunty back to the original drivers (don't worry you can always put them back on again through the command line instead of through the gnome frontend)

EDIT: Sorry hadn't noticed that you had solved it, I need to learn to read :P
Congratulations on solving it I hope you enjoy Ubuntu as much as we all do.

---

