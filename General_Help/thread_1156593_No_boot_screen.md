---
title: "No boot screen"
date: 2009-05-11
forum: General Help
---

### Post by brandon88tube on 2009-05-11
I've been using Ubuntu 9.04 and Windows XP in a dual boot setup for a while now and after I restarted Windows XP my laptop fails to boot. It comes up with a blank screen and the blinking indicator(underscore). Normally grub would pop up and ask which OS I want to boot, but nothing comes up now. I had this problem before and it seems to randomly happen when I do a restart with XP. To fix it before I had to reinstall Ubuntu completely, which ended up reinstalling grub, but this time I don't want to wipe my Ubuntu partition. As of right now I am unable to boot into any OS and have to use another computer.

---

### Post by spiderbatdad on 2009-05-11
Try removing all power and the battery for 20 minutes or so.

---

### Post by geraldvillorente on 2009-05-11
tell us what exactly happen before that problem...

---

### Post by brandon88tube on 2009-05-11
Prior to the problem nothing was really done. Just did a normal restart from XP and then reboot with a blank screen. I'll try pulling the battery and unplug it, but I doubt that will work.

---

### Post by geraldvillorente on 2009-05-11
Can you still boot on Linux?

---

### Post by brandon88tube on 2009-05-11
No, I can't boot period. The BIOS screen loads then a blank screen and that is it. Just sits there and runs my fan.

---

### Post by gamblor01 on 2009-05-11
You definitely do not need to reinstall Ubuntu to reinstall grub.  Here's a simple method for you -- put in the live CD and open a terminal.  Then run these commands:

```

$ grub
$ find /boot/grub/stage1

```This should return something like (hd0,1).  You will need this output for the next command:

```

$ root (hd0,1)

```Swap out (hd0,1) with whatever was returned in step 2 (the find command).  Now grub is configured and you just need to install grub in the MBR.  You do that like this:

```

setup (hd0)

```That's it...you're done.  Reboot (without the live CD in) and it should work fine.  Sounds like something else is going on with your system though that keeps causing this to happen.    :/

---

### Post by mysoogal on 2009-05-11
maybe your having the same issue, i had about 30 minutes ago,

what i had done was during boot, i was going to start with ubuntu but i mistakenly clicked on xp , i have dual boot with wubi, anyways

soon after during the bootup for xp i pressed reboot button, next i started all over again, and picked ubuntu this time, 

grub showing fine,

ubuntu logo showing fine

then just when ubuntu bar completes i got this colorful messy looking thing like it was pulsating screen or something like on a old tv when you put a magnetic near it changed colors.

so, what i done to fix this, i simply logged back into windows, and shutdown normally and during boot i picked ubuntu and thats about it,

everything back to normal.


in case you removed your ubuntu desktop, you need to reinstall it or, maybe your xserver thing didnt start,


to reinstall ubuntu desktop, sudo apt-get install ubuntu-desktop


to start xserver type in terminal, startx

u have to go into recovery mode to typ these commands,

if you have Ethernet net support, plug it in and follow these commands if nothing works.

---

### Post by brandon88tube on 2009-05-11
Problem, failed to find /boot/grub/stage1

---

### Post by brandon88tube on 2009-05-12
Anyone? I really need to get my laptop back up and working for work and personal reasons.

---

### Post by Amof on 2009-05-12
Is your HDD the first to boot on your BIOS priority list? Is there a CD in the drive? My server does that all the time because when i unplug a USB and then reboot it resets the boot priority in my BIOS.


EDIT:
Ok that doesn't sound like it will help you. Try this. [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by Egi_Power on 2009-05-12
When you installed Ubuntu, did you make a separate partition for /boot?
I have on my laptop the /boot on a separate partition and I got also error for
```
sudo grub
find /boot/grub/stage1
```
However, it worked leaving out /boot from the command
```
sudo grub
find /grub/stage1
```
Give it a try and write any error you get.

Best regards,

Egi_Power

---

### Post by brandon88tube on 2009-05-13
I don't have a separate boot partition. I got the same error for both find /boot/grub/stage1 and find /grub/stage1, which is "Error 15: File Not Found". My problem might be that the LiveCD I am using is 7.04 and the partition is ext4, which I don't think is supported for this old version.

---

### Post by Egi_Power on 2009-05-14
> **brandon88tube said:**
> I got the same error for both find /boot/grub/stage1 and find /grub/stage1, which is "Error 15: File Not Found".
How did you get into Grub in the terminal on the Live CD?
```
grub
```
***or***
```
sudo grub
```
???

I can reproduce your error message using the Live CD, if I get into Grub without *sudo*.
It's important you use *sudo*. Make sure you use it as:
```
**sudo grub**
```
Then
```
find /boot/grub/stage1
```
Try again and write back any errors you may get.

Using the Live CD can you see any files on your old partition?

Egi_Power

---

### Post by petrus4 on 2009-05-14
> **brandon88tube said:**
> Problem, failed to find /boot/grub/stage1

Have you got a Ubuntu LiveCD?  If so, you could copy the files back, assuming you can get write access to your boot drive, that is.

[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

That link might help.

---

### Post by Egi_Power on 2009-05-14
> **petrus4 said:**
> Have you got a Ubuntu LiveCD?
Look in post #13.
> **brandon88tube said:**
> ...the LiveCD I am using is 7.04...
;)

Egi_Power

---

### Post by petrus4 on 2009-05-14
> **Egi_Power said:**
> Look in post #13.

;)

Egi_Power

Sorry. :(

---

### Post by Egi_Power on 2009-05-14
> **petrus4 said:**
> Sorry. :(
Don't be sorry.
It's nice that you try to help a fellow Ubuntu user.

Take care.

Egi_Power

---

### Post by gamblor01 on 2009-05-15
> **brandon88tube said:**
> I don't have a separate boot partition. I got the same error for both find /boot/grub/stage1 and find /grub/stage1, which is "Error 15: File Not Found". My problem might be that the LiveCD I am using is 7.04 and the partition is ext4, which I don't think is supported for this old version.
I suppose it's possible that the 7.04 CD can't read the ext4 partition so that's why it can't find the file, but I can't say this for sure.  Have you tried downloading and burning an iso of 9.04, then starting up that live CD instead?  Ubuntu makes it super easy to burn ISO images to a CD.  Just download the file, then right-click it and select "Write to Disc".  I would think you should be able to do this even in a live session.

The only other reason I can think it might not find the file is that the drive is toast and it can't read the contents of it.  That would be most unfortunate however.  :(

You might to just manually mount the partition and see what happens (again, this might require a newer version than 7.04 -- not sure).

---

### Post by rukiaEnix on 2009-05-15
Try using SuperGrub, it is a boot cd that recovers your GRUB automatically or manually and it also recovers the MBR, is really useful it has help me a lot with this kind of problems.
You can download it from the official website [here]("http://www.supergrubdisk.org/")

---

### Post by brandon88tube on 2009-05-17
I couldn't wait any longer and decided to just wipe it. Don't want to keep repairing it all of the time because this has happened twice already for no apparent reason other than Windows doesn't like Linux. Thanks for the help though. I will keep it in mind if something like this ever happens again.

---

