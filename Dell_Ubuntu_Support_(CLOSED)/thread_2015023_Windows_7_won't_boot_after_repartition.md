---
title: "Windows 7 won't boot after repartition"
date: 2012-07-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by joshmo1 on 2012-07-02
Hi,

I am using a Dell XPS 13 Ultrabook (128GB SSD and i5), and I was trying to repartition it with Ubuntu as well as Windows 7. You probably know that Dell computers come with a RECOVERY partition. I decided that I did not need it so I backed it up on an external drive anyway. Then I booted of my live USB of Ubuntu 11.10 and used GParted to format the recovery partition and move my OS partition to the left, and expand it.

According to GParted it worked fine, but when I restarted, it said "Operation system not found." Next, I decided to try and just make the partition for Ubuntu to the right of the windows partition, thinking that may fix it - because once ubuntu and GRUB are installed, it might fix the bootloader.

Well, GParted got an error when partitioning it, so I tried executing the commands that GParted performed manually in the terminal. I didn't finish executing these commands because I got worried and went to back everything up (it was late and I needed some sleep).

Please can someone help me? Any help is appreciated.

Thank you.

---

### Post by oldfred on 2012-07-02
Welcome to the forums.

Always resize Windows 7 with the partition tools inside Windows. Use gparted to create new partitions or modify Linux partitions.

Windows has info in the PBR - partition boot sector that has to match the partition table including partition start & size. After Windows resizes it will run chkdsk on a reboot to fix itself.

You may need both chkdsk & fixBoot to repair NTFS PBR.

[http://www.sevenforums.com/tutorials/681-startup-repair.html](http://www.sevenforums.com/tutorials/681-startup-repair.html)
[http://www.w7forums.com/startup-repair-t441.html](http://www.w7forums.com/startup-repair-t441.html)
[http://www.bleepingcomputer.com/tutorials/tutorial148.html](http://www.bleepingcomputer.com/tutorials/tutorial148.html)

oldfred's Windows Vista/Win7 repair links posts #7:
[http://ubuntuforums.org/showthread.php?p=9826152](http://ubuntuforums.org/showthread.php?p=9826152)
Make sure boot flag is set for any partition you try to repair.

---

### Post by joshmo1 on 2012-07-02
Thanks for your reply. I cannot run chkdsk though as I can't boot into Windows. (I'm currently on my live USB)

---

### Post by oldfred on 2012-07-02
Do you know someone with the same 32 or 64 bit version of Windows? Always best to have repairCD or USB or liveCD/USB for every system installed.

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

We have a link to a repair ISO, but they now charge $10.

Someone posted this may work.
Also has chkdsk and some other Windows repairs in free version:
[http://www.partitionwizard.com/features.html](http://www.partitionwizard.com/features.html)
[http://www.partitionwizard.com/partitionmanager/partition-fix.html](http://www.partitionwizard.com/partitionmanager/partition-fix.html)

---

### Post by joshmo1 on 2012-07-02
I have the Recovery partition backed up, but that ends up being 15GB when I made it into an iso so I couldn't fit it on my 8GB usb. Should I finish of the commands that I was copying from GParted? because currently it can't even show how much used space there is in GParted.

Also, which of the links that you gave should I use for repairing?

Thanks again.

---

### Post by dave61430 on 2012-07-02
You did a bad thing (I made a similar mistake when I first got the Dell laptop).
The system boots to the recovery partition which is the active partition. Try to restore the system, then you could delete most of the stuff in that recovery partition and shrink it.
Get a hold of mbrwork.exe and a trial version of bootitbm from terabyteunlimited.com and see what you can do with those. Alternatively you could try marking the C (windows) drive as active but there is also a windows boot loader file that the system needs and I'm not sure what you would have to do with that, but it would be doable.

---

### Post by joshmo1 on 2012-07-03
Hi,

Thanks everyone for your help. I ended up getting it working.
For anyone else that needs help I'll just let you know what I did.

I made the bootable recovery disk through Windows on another computer of mine, as suggested. And then copied the files onto a usb. Then I booted from it and it fixed some stuff, and I could boot into Windows.

Then I just made a partition for Ubuntu and installed it.

Thanks again.

---

