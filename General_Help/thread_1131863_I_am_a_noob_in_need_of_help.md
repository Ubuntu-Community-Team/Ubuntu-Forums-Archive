---
title: "I am a noob in need of help"
date: 2009-04-21
forum: General Help
---

### Post by Brudin on 2009-04-21
My problem is that I was under the impression that when I installed Ubuntu, I could also switch back and fourth between normal windows, and Ubuntu. However I cant seem to figure out how to do that. Any help would be appreciated, if you need any specific information just ask I will do my best to give an answer.

---

### Post by bobbob1016 on 2009-04-21
Did you tell Ubuntu to use the whole hard drive when you installed Ubuntu?  

If you didn't tell it to use your whole hard drive, there should be an option when you boot-up to select Windows or Ubuntu, you just press the arrows on your keyboard to select Windows or Ubuntu and then press enter, and boot that OS.

If you did, stop using the drive now, boot the LiveCD and post here again, because you need someone to help you recover your Windows data.

If you don't know, you probably didn't change the setting, and probably just have to select Windows on boot.

---

### Post by Brudin on 2009-04-21
> **bobbob1016 said:**
> Did you tell Ubuntu to use the whole hard drive when you installed Ubuntu?  

If you didn't tell it to use your whole hard drive, there should be an option when you boot-up to select Windows or Ubuntu, you just press the arrows on your keyboard to select Windows or Ubuntu and then press enter, and boot that OS.

If you did, stop using the drive now, boot the LiveCD and post here again, because you need someone to help you recover your Windows data.

If you don't know, you probably didn't change the setting, and probably just have to select Windows on boot.

I apparently told it to use the whole hard drive :(, when I was just using the demo I had the option of going between windows and ubuntu. I just put in the LiveCD and restarted my computer.

---

### Post by James_Lochhead on 2009-04-21
> **Brudin said:**
> My problem is that I was under the impression that when I installed Ubuntu, I could also switch back and fourth between normal windows, and Ubuntu. However I cant seem to figure out how to do that. Any help would be appreciated, if you need any specific information just ask I will do my best to give an answer.

You can. If everything went according to plan. If it did restart your computer: a black and white menu should pop up (time limit of 10s then it boots automatically) asking you whether you want to load Ubuntu (various options) or Windows (at the bottom).

If this screen does not pop then something along the way has gone wrong. Most likely you have written over Windows or Windows has not been detected by the boot loader (the black menu) for some reason.

---

### Post by Brudin on 2009-04-21
> **James_Lochhead said:**
> You can. If everything went according to plan. If it did restart your computer: a black and white menu should pop up (time limit of 10s then it boots automatically) asking you whether you want to load Ubuntu (various options) or Windows (at the bottom).

If this screen does not pop then something along the way has gone wrong. Most likely you have written over Windows or Windows has not been detected by the boot loader (the black menu) for some reason.

I am really banking on it not being detected, me writing over windows would be a huge mistake on my part and I am not that skilled in computer knowledge to know how to fix it. I guess thats why I get trying to install ubuntu after being awake for 30 hours.

---

### Post by James_Lochhead on 2009-04-21
Could you please open a terminal (Applications > Accessories > Terminal) and give us the output from the following command:

```

sudo fdisk -l

```

---

### Post by Brudin on 2009-04-21
> **James_Lochhead said:**
> Could you please open a terminal (Applications > Accessories > Terminal) and give us the output from the following command:

```

sudo fdisk -l

```

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x89ae89ae

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9635    77393106   83  Linux
/dev/sda2            9636       10011     3020220    5  Extended
/dev/sda5            9636       10011     3020188+  82  Linux swap / Solaris

---

### Post by James_Lochhead on 2009-04-21
Yea, your Windows has been written over.

---

### Post by gali98 on 2009-04-21
Oops. That's bad news. You must have told the installer to use the whole disk. There is no windows partition. :( Sorry.
Kory

---

### Post by Brudin on 2009-04-21
Yikes! Is there anything that can be done?

---

### Post by James_Lochhead on 2009-04-21
There might be. There are data recovery tools out there. It is actually extremely difficult to 100% get rid of data. I do not have enough experience with this kind of thing to point you in the right direction though.

There are lots of techies around though, so hopefully someone will point you in the right direction.

---

### Post by Brudin on 2009-04-21
> **James_Lochhead said:**
> There might be. There are data recovery tools out there. It is actually extremely difficult to 100% get rid of data. I do not have enough experience with this kind of thing to point you in the right direction though.

There are lots of techies around though, so hopefully someone will point you in the right direction.

Alright, to be honest it is really not that big of a deal I had so many problems with windows anyways. Guess the biggest bummer is now I cant play any of my video games, namely WoW.

---

### Post by James_Lochhead on 2009-04-21
I think (pretty sure) you can get WoW working on Linux through WINE (a compatibility layer).

---

### Post by Brudin on 2009-04-21
> **James_Lochhead said:**
> I think (pretty sure) you can get WoW working on Linux through WINE (a compatibility layer).

You've just made my day, I will look into tomorrow have school and need to catch up on some much needed beauty sleep. I appreciate you taking the time to respond you have been helpful, I will just feel like a moron for the rest of the day that's all.

---

### Post by hyperdude111 on 2009-04-21
If you want to use windows again you will need to get hold of a windows disk and re-install.
For help with dual booting (this allows you to switch between ubuntu ad windows) use these guides:

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm) (If ubuntu is already installed)

[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first) (If win XP is already installed)

Or as an alternative just install windows and pop your ubuntu cd in the drive, a little application should pop up called wubi, this is ideal for windows users as it allows you to dual boot a full version of ubuntu without removing windows or partitioning your hard drive. Wubi is also very user friendly, it is how i first got into ubuntu.

---

### Post by rastro123 on 2009-04-21
do it all again mate, but install windows first

---

### Post by Brudin on 2009-04-21
> **hyperdude111 said:**
> If you want to use windows again you will need to get hold of a windows disk and re-install.
For help with dual booting (this allows you to switch between ubuntu ad windows) use these guides:

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm) (If ubuntu is already installed)

[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first) (If win XP is already installed)

Or as an alternative just install windows and pop your ubuntu cd in the drive, a little application should pop up called wubi, this is ideal for windows users as it allows you to dual boot a full version of ubuntu without removing windows or partitioning your hard drive. Wubi is also very user friendly, it is how i first got into ubuntu.

Thanks, I will try this out at a later time, I think I am going to use ubuntu exclusively for a while, who knows I may not even want windows back.

---

### Post by Michael.Godawski on 2009-04-21
hi,

do not be afraid. We are with you. Although you had a bad start ;) the end result may be great.

WoW is one of the games which run pretty well with Wine:

[LIST]
[*][http://www.winehq.org/](http://www.winehq.org/)
[/LIST]
When you do not have any problems with your Internet connection, your sound and video card than you have experienced a real blessing in disguise.

Next time before playing around with installing new operating system please safe your important data to external sources, like CDs, DVDs, usb stick or even external hard-drives.

Saves you a lot of troubles.

---

### Post by Brudin on 2009-04-21
> **Michael.Godawski said:**
> hi,

do not be afraid. We are with you. Although you had a bad start ;) the end result may be great.

WoW is one of the games which run pretty well with Wine:

[LIST]
[*][http://www.winehq.org/](http://www.winehq.org/)
[/LIST]
When you do not have any problems with your Internet connection, your sound and video card than you have experienced a real blessing in disguise.

Next time before playing around with installing new operating system please safe your important data to external sources, like CDs, DVDs, usb stick or even external hard-drives.

Saves you a lot of troubles.

I dont want to turn this into a rant on how to get WoW up and running but, I have installed wine and followed the instructions off of: [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

However, I recieve this error when trying to run InstallWoW.exe:"[/home/*******/Desktop/InstallWoW.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/*******/Desktop/InstallWoW.exe or
          /home/*******/Desktop/InstallWoW.exe.zip, and cannot find /home/*******/Desktop/InstallWoW.exe.ZIP, period." That is the command line output, you most likely know this haha. The actual error says: "An error occured while loading the archive." (null)

---

