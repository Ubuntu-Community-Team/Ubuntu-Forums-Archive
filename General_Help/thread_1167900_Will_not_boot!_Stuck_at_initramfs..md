---
title: "Will not boot! Stuck at initramfs."
date: 2009-05-23
forum: General Help
---

### Post by redbytex on 2009-05-23
I am running Ubuntu 8.04 64-bit. 
I haven't recently made any changes or stuffed around with any settings, but today  I turned on my machine and it sat at the loading bar for about 5 minutes, then the screen went blank and and it spat me out here:

```
(initramfs)_
```

I booted in recovery mode and it said this:

```
Check root = bootarg cat /proc/cmdline
or missing modules, devices cat /proc/modules ls /dev
ALERT! /dev/disk/by-uuid/(lots of numbers) does not exist. Dropping to a shell.
```

Does anyone know what this means?
Please note, I am only a beginner! If you could explain it carefully I would be very greatful.

Thanks in advance!

---

### Post by gpredrag on 2009-05-23
It means that grub is not able to find your root partition.
How is your disk partitioned?
have you repartitioned it, under different operating system, lately?
Have you installed another operating system lately that may have been partitioned disk?

---

### Post by redbytex on 2009-05-23
[QUOTE=gpredrag]It means that grub is not able to find your root partition.
How is your disk partitioned?
have you repartitioned it, under different operating system, lately?
Have you installed another operating system lately that may have been partitioned disk?[/QUOTE]

Hi gpredrag,
I'm not exactly sure how it is partitioned. I didn't make any custom changes during the installation OS installation, so I assume just the standard way? The only OS installed on this machine is Ubuntu.

I have also not made changes since I last used it, which is why I'm baffled. One day it boots fine, the next day - nothing. :(

---

### Post by gpredrag on 2009-05-23
Can you boot off of a installation CD?
On alternate CD, when you boot, there is an option "Boot from first hard disk". If you only have Ubuntu on a machine, firs partition should be ubuntu.
There is also an option to recover broken system, but let see if it boots at all.
Only time I have seen problems like this, was when partitions were deleted,resized, or corrupted, or hardware problem.

---

### Post by raymondh on 2009-05-23
Hello redbytex,

Another alternative is to download supergrub and have it try to fix the boot problems.  It may be a corrupted grub problem.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

or this link (Herman's) with a nice documentation

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#How_Make_your_Super_Grub_Floppy_Disk](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#How_Make_your_Super_Grub_Floppy_Disk)

Of course, you can also use the liveCD to fix GRUB

Good luck.  Regards

---

### Post by Beacon11 on 2009-05-23
[http://ubuntuforums.org/archive/index.php/t-665643.html](http://ubuntuforums.org/archive/index.php/t-665643.html) might help. Try running blkid and see if the number returned is the one GRUB is looking for. If that's not the case, sounds like you can fix it (from the link).

---

### Post by Beacon11 on 2009-05-23
Another idea: When you get to the Grub menu (on boot) press "e" to edit the default selection. Select the "kernel" line, then press press "e" to edit it, and at the end of the kernel line add "rootdelay=130". Press "enter" to save changes, then press "b" to boot. Blatently plagerized from [http://ubuntuforums.org/showthread.php?t=987243](http://ubuntuforums.org/showthread.php?t=987243)

---

### Post by redbytex on 2009-05-23
> **gpredrag said:**
> Can you boot off of a installation CD?
On alternate CD, when you boot, there is an option "Boot from first hard disk". If you only have Ubuntu on a machine, firs partition should be ubuntu.
There is also an option to recover broken system, but let see if it boots at all.

There are 5 Options:
Try ubuntu without any change to the system
Install ubuntu
Check CD for defects
Test memory
Boot from first hard disk

I have tried the first and last option to no avail: takes me to the initramfs.

Should I try 'Install ubuntu' next or will that stuff up my system?

> **raymondhenson said:**
> 
Another alternative is to download supergrub and have it try to fix the boot problems.  It may be a corrupted grub problem.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)


Hi Raymondhenson,
I can't get into the system (stuck at prompt) so I'm not sure how to install this program. If I download it on a different machine then put it in on USB and plug it into my linux box, what should I type at the initramfs to install it?

Thanks for your help!

> **Beacon11 said:**
> [http://ubuntuforums.org/archive/index.php/t-665643.html](http://ubuntuforums.org/archive/index.php/t-665643.html) might help. Try running blkid and see if the number returned is the one GRUB is looking for. If that's not the case, sounds like you can fix it (from the link).

Hi Beacon,
I took a look at that thread but I can't understand what's going on! Sorry. I can't access my terminal either so I don't think I can do what they are doing.

> **Beacon11 said:**
> Another idea: When you get to the Grub menu (on boot) press "e" to edit the default selection. Select the "kernel" line, then press press "e" to edit it, and at the end of the kernel line add "rootdelay=130". Press "enter" to save changes, then press "b" to boot. Blatently plagerized from [http://ubuntuforums.org/showthread.php?t=987243](http://ubuntuforums.org/showthread.php?t=987243)

Just tried this to no avail unfortunately. Takes me to the initramfs prompt :(

Thanks for talking me through this guys. I really appreciate everyone taking the time to try and help me solve this issue!

---

### Post by raymondh on 2009-05-23
Hello redbytex,

re supergrub

Just boot it (like how you do the liveCD) and follow the prompts.  You will (ultimately) point supergrub to the ubuntu installation.

The second link (users.bigpond....) is a good doc/how to done by Herman, also a forum member.  It has instructions.

Good luck.

---

### Post by redbytex on 2009-05-23
> **raymondhenson said:**
> 
Just boot it (like how you do the liveCD) and follow the prompts.  You will (ultimately) point supergrub to the ubuntu installation.


So are you saying I should try the option 'Install Ubuntu' at the LiveCD prompt?

---

### Post by raymondh on 2009-05-24
> **redbytex said:**
> So are you saying I should try the option 'Install Ubuntu' at the LiveCD prompt?

Hello Redbytex ....

No, I am not saying that.

This was your question to me:

*"...If I download it on a different machine then put it in on USB and plug it into my linux box, what should I type at the initramfs to install it?"*

At which I replied... "just boot it (like how you do the liveCD)...." 

Remember how you installed ubuntu with the liveCD (the first time)?  You "booted" the disk.  

1) Make sure BIOS will load the appropriate drive first 
2) Load the disk or plug the thumb drive  
3) turn on the machine.

Here's the link again if you decide to use supergrubdisk.  Please read as it has instructions on *_how to use supergrubdisk_* (about midway through).

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#How_Make_your_Super_Grub_Floppy_Disk](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#How_Make_your_Super_Grub_Floppy_Disk)

Regards

---

### Post by redbytex on 2009-05-24
> **raymondhenson said:**
> 
At which I replied... "just boot it (like how you do the liveCD)...." 

Remember how you installed ubuntu with the liveCD (the first time)?  You "booted" the disk.  

1) Make sure BIOS will load the appropriate drive first 
2) Load the disk or plug the thumb drive  
3) turn on the machine.

Here's the link again if you decide to use supergrubdisk.  Please read as it has instructions on *_how to use supergrubdisk_* (about midway through).

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#How_Make_your_Super_Grub_Floppy_Disk](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#How_Make_your_Super_Grub_Floppy_Disk)


Hi raymondhenson,
I don't have a floppy disk drive so I will have to use the USB method.

I have set the boot priority to:
[LIST]
[*]CD-ROM
[*]IDE
[*]Floppy
[/LIST]

(like it says to do on the website)

I put SuperGrub on a USB drive, plugged it in and turned on the machine. After 5 minutes of loading bar goodness it goes back to initramfs.

What does SuperGrub do? Because I don't know what I'm looking for. Is it supposed to load up a menu similar to the live CD? Am I supposed to use it in conjunction with the LiveCD?

In the link you posted, it mentions this:
> 
   1. run the mount command without the flash drive pluggedin yet,
   2. then you plug in the USB drive and wait for it to be automatically mounted.
   3. Run the mount command again and compare the results.
   4. It should be obvious which device is the flash memory drive. Let's say it's /dev/hdc.
   5. You tell GRUB that /dev/sdc = (hd3), which would be your fourth hard drive.
   6. You set GRUB's root device as (hd3,0), so you're going to install GRUB from 4th hard disk, 1st partition somewhere.
   7. You install GRUB to the fourth hard drive's MBR, (your USB drive)
   8. That's it, you're finished.

Are these the commands I am supposed to type into initramfs?

Thank you for you help! I really appreciate it.

---

### Post by Beacon11 on 2009-05-24
Alright, when you booted in recovery mode, from the error it tossed you it sounds like it dropped you to a shell. Is that right? If so, from there you should be able to execute the blkid command. Unfortunately, for this to be useful you need to know what your root partition IS. Mine is sda1, and if you only have one hard drive and no other OS on there, yours is probably the same. Anyway, if you can get to the prompt that way, give that a shot. Any luck? If that doesn't work, you can use the Live CD (when you boot from the Live CD, the very top option is the one you want). If you can get to the terminal, I can walk you through the rest :) .

---

### Post by redbytex on 2009-05-24
> **Beacon11 said:**
> Alright, when you booted in recovery mode, from the error it tossed you it sounds like it dropped you to a shell. Is that right? If so, from there you should be able to execute the blkid command. Unfortunately, for this to be useful you need to know what your root partition IS. Mine is sda1, and if you only have one hard drive and no other OS on there, yours is probably the same. Anyway, if you can get to the prompt that way, give that a shot. Any luck? If that doesn't work, you can use the Live CD (when you boot from the Live CD, the very top option is the one you want). If you can get to the terminal, I can walk you through the rest :) .

Hi Beacon11,
I tried running blkid from the prompt but it doesn't seem to be a valid command. Is that all I type? 'blkid'? Do I type anything after it?

The instructions in that thread are a little hard to understand :(

---

### Post by raymondh on 2009-05-24
Did you update recently?  Did you, by chance, do a distribution upgrade?

---

### Post by raymondh on 2009-05-24
> **redbytex said:**
> Hi Beacon11,
I tried running blkid from the prompt but it doesn't seem to be a valid command. Is that all I type? 'blkid'? Do I type anything after it?

The instructions in that thread are a little hard to understand :(

On the terminal, type
```

sudo blkid
```

also type

```
sudo fdisk -l
```

also

cat /etc/fstab

Copy/post back outputs of those commands.  

The reason for this is because (maybe) there is a need to re-mount the drive and the blkid command will output the UUID..... which is helpful to know....and we'll compare with the fstab command.   The other (fdsik) command will tell us what is in your hard drive.

Do you have your files backed-up?

This error maybe because of a corrupted file, corrupted GRUB, or a hard drive that is about to die.  I was thinking of reinstalling GRUB but, let's try to re-mount the drive first. One at a time 'eh :)

Out of curiosity, when you are using the liveCD, do you see your drive in places?  Also, are you using the 8.04 64-bit liveCD? Also, what were you doing prior to receiving the error code?  Were you updating, upgrading, doing a dist-upgrade, etc, anything?

I will be gone for about an 1-3 hrs.  Will check back this thread upon return.

PS.... sometimes (just sometimes), a clean re-install will be faster.  Are you ready for that in case we cannot chase down the problem?

Good luck,

---

### Post by redbytex on 2009-05-24
> **raymondhenson said:**
> On the terminal, type
```

sudo blkid
```

also type

```
sudo fdisk -l
```

also

cat /etc/fstab

Copy/post back outputs of those commands.  


I mustn't be at a proper terminal because none of those commands work.
```

BusyBox v1.1.3 (Debian1:1.1.3 -5ubuntu12) Built-in shell (ash)
Enter 'help' for a full list of commands.

(initramfs)sudo blkid
/bin/sh: sudo: not found
(initramfs)sudo fdisk
/bin/sh: sudo: not found
(initramfs)cat /etc/fstab/
cat: /etc/fstab/: no such file or directory

```

> **raymondhenson said:**
> 
Out of curiosity, when you are using the liveCD, do you see your drive in places?  Also, are you using the 8.04 64-bit liveCD?


Not sure what is meant by 'see my drive in places'? And I am using the CD that I used to install Ubuntu. Is that a LiveCD?

> **raymondhenson said:**
> 
Also, what were you doing prior to receiving the error code?  Were you updating, upgrading, doing a dist-upgrade, etc, anything?

Okay, I turned on my computer 3 days ago and went to the kitchen. My friend was sitting at my computer whilst I wasn't there and when I came back he said, "Your computer stalled for 5 minutes at the 'bios screen' and it said something like 'press F2 to continue' so I did"

Which annoyed me beacause I would have liked to have known what the error message said. But the computer booted so I wasn't too worried. I shut the computer down and then the next time I turned it on, it booted me to the initramfs screen.

I hadn't installed any updates prior or done anything differently than normal. The error message at the "bios screen" is the only information I have to go by.

> **raymondhenson said:**
> 
PS.... sometimes (just sometimes), a clean re-install will be faster.  Are you ready for that in case we cannot chase down the problem?


Not really :(
I've been working on an animated 3d short for the last 8 months and it's all on there. :( I have made a few backups, some are recent, but I haven't backed up everything. So I'd really like to avoid that if possible.

Thanks for helping guys. I know it must be difficult trying to diagnose a problem with someone like me, who doesn't know a lot about Linux. I appreciate your time.

---

### Post by raymondh on 2009-05-24
> **redbytex said:**
> 
not really :(
I've been working on an animated 3d short for the last 8 months and it's all on there. :( I have made a few backups, some are recent, but I haven't backed up everything. So I'd really like to avoid that if possible.


I understand, sir.  OK, let's try to get "GRUB alive and pointing at the right location"..

1.  Boot the liveCD. (the install disc).  Pick the first option "try ubuntu without changes to your system" (something to those words)
2.  Navigate to system > accessories > terminal
3.  Type and enter the following codes (one at a time) ... I will explain in italics.  You will be in the GRUB menu

```
sudo grub
```

*we're asking to go to GRUB which is the bootloader.  we'll try to reinstall grub, hoping this works.*

```
find /boot/grub/stage1
```

*self explanatory.  This will output a location.  Something like (hd0,1).  That is the location we want. Copy that pls. on a piece of paper as you will need it for the next command *. * Using your copied location, X is the number after hd and Y is the number after the comma*

```

root (hdX,y)
```  


```
setup (hdX,y)
```

*we're asking to write the bootloader to the linux root partition.  Some people just use (hd0).  Either is OK since you said there is only one operating system in there.  I just prefer to go direct to the root partition*

```
quit
```

Now, eject the liveCD and restart your computer.  Let me know how it goes.

While you're doing that, I will search with my best google-fu on how to recover and save your data.

Good luck.

---

### Post by raymondh on 2009-05-24
Your comment " stalled at the bios screen ... press F2 to continue" is intriguing me.  Here's an exceprt when I google BIOS ERROR PRESS F2 TO CONTINUE

[I]Does any error accompany the F2 message?

Likely you need replace the cmos battery. If it's dead, or nearly so, it won't hold the settings. Then when you boot up the bios detects that the settings have defaulted and asks if you want to go into cmos/bios setup and correct things. Otherwise, hitting F2 continues the bootup with the default settings. The battery should be silver colored and about the size of a nickel. (You'll need to open the case of course.)

If it's not the battery you may have a bios problem--seems to happen more often with HP's. Sometimes you can correct it by selecting the 'reset configuration data' (I think that's what it says) in cmos.

Other times you can clear the cmos. There should be a 3-pin jumper on the motherboard. It would now be jumpered in the 'normal' position. To clear it you'd move the jumper to the 'clear' position, turn the PC on for a few seconds, turn it off and then return the jumper to the 'normal' position. On next boot you'd be alerted that you need to enter setup.

But it's probably the battery. If you have a DC voltmeter you can check it. A new one would be 3.0 volts. Usually a battery will hold the settings even when it gets down to as low as 1 volt but it'd be a good idea to replace it if it gets lower than 2.8 or so.[/I]

Like I said, one at a time ... we'll see how the GRUB reinstall goes.

Regards,

---

### Post by redbytex on 2009-05-25
IT'S FIXED!! :D

**The solution was to change the hdd type to Raid in BIOS.**

...

Confused?

Well raymondhenson, when you mentioned that the BIOS might have run out of battery it made me remember something: when I first installed Ubuntu I encountered the exact same issue (booting to initramfs). The problem actually lies in the ASUS P5Q motherboard conflicting with Ubuntu and it will not boot unless you change the HDD type from **IDE** to **Raid**. There's more on it [here]("http://ubuntuforums.org/showthread.php?t=933965"). 

So basically I think my friend accidentally cleared my BIOS settings. All I did was change the drive to raid it booted straight away! Woohoo! :D

So a super big thank you to raymondhenson for googling "F2 BIOS ERROR", I probably wouldn't have remembered if it weren't for you.
And thank you to everyone else who gave me their time trying to help a noob like me. It's refreshing to find a community so willing to help others for nothing in return. Thanks! :D

---

### Post by raymondh on 2009-05-25
> **redbytex said:**
> IT'S FIXED!! :D

**The solution was to change the hdd type to Raid in BIOS.**

...

Confused?

Well raymondhenson, when you mentioned that the BIOS might have run out of battery it made me remember something: when I first installed Ubuntu I encountered the exact same issue (booting to initramfs). The problem actually lies in the ASUS P5Q motherboard conflicting with Ubuntu and it will not boot unless you change the HDD type from **IDE** to **Raid**. There's more on it [here]("http://ubuntuforums.org/showthread.php?t=933965"). 

So basically I think my friend accidentally cleared my BIOS settings. All I did was change the drive to raid it booted straight away! Woohoo! :D

So a super big thank you to raymondhenson for googling "F2 BIOS ERROR", I probably wouldn't have remembered if it weren't for you.
And thank you to everyone else who gave me their time trying to help a noob like me. It's refreshing to find a community so willing to help others for nothing in return. Thanks! :D

Am glad you got that fixed.... and you're welcome.

Time to back up that short film 'eh :)  

Also, if you don't mind .... would you mark the thread solved.  Go to your first post > edit > advanced > type solved in front of your thread title > save.  The BIOS setting can help someone should he/she encounter the same issue....and with the same motherboard.


Regards,

---

