---
title: "Boot to Ubuntu only if USB stick is in?"
date: 2010-12-09
forum: Desktop Environments
---

### Post by PSUinDC on 2010-12-09
So, I have a dual boot system.  Windows 7 and Ubuntu. I'm not a GRUB expert here, and I want some advice.

What I'd like as an end result is to be able to boot my PC without the USB stick, and have it boot straight to Windows 7. If I boot with the USB stick in, I want it to boot to the Ubuntu partition that is on the hard drive (note: I do not want to boot to a linux distro on the USB stick. I just want to use the USB stick as a "key" to get into my Ubuntu installation).

Is this a feasible request? Is there an easier way to do this? I really just don't want to have 2 operating systems in the GRUB making me choose which one each time... seems like a waste of 30 seconds.

---

### Post by wilee-nilee on 2010-12-09
Yes it's possible, but far from what I would consider a stable setup.

I say this for a couple of reasons #1 your apparent lack of knowledge as far as bootloaders go and the ease of reloading a mbr=master boot record

Now don't take that personally most people have no clue.

#2 Your I'm assuming fear of the grub bootloader.

Grub and the MS bootloader as easily reloaded, as well as there is another linux based bootloader lilo that will act as if it is a MS bootloader.

---

### Post by PhoenixGI on 2010-12-09
First, this is exactly the setup I'm working on. One factor that determins if you can do it, is your system.  As long as BIOS can either detect and let you set USB device as first boot (or 2nd after CD) or, if it still considers it as a HDD that can keep track of it and it's proper order when you remove it, so you can set it before your Hard Drive.  

If you can, I found these directions [http://ubuntuforums.org/showpost.php?p=10117203&postcount=14](http://ubuntuforums.org/showpost.php?p=10117203&postcount=14) I've had 75% success with them, but with that said its the PC that was the problem not the OS.  

If it doesn't work right off the bat, you might want to drop the idea unless your in the mode (and have the time) to fight with it.  The good news is, if you follow the first steps (disabling your Hard drive) you know that it won't break your primary OS.

---

### Post by wilee-nilee on 2010-12-09
> **PhoenixGI said:**
> First, this is exactly the setup I'm working on. One factor that determins if you can do it, is your system.  As long as BIOS can either detect and let you set USB device as first boot (or 2nd after CD) or, if it still considers it as a HDD that can keep track of it and it's proper order when you remove it, so you can set it before your Hard Drive.  

If you can, I found these directions [http://ubuntuforums.org/showpost.php?p=10117203&postcount=14](http://ubuntuforums.org/showpost.php?p=10117203&postcount=14) I've had 75% success with them, but with that said its the PC that was the problem not the OS.  

If it doesn't work right off the bat, you might want to drop the idea unless your in the mode (and have the time) to fight with it.  The good news is, if you follow the first steps (disabling your Hard drive) you know that it won't break your primary OS.

I would just say that grub2 updates are coming through at times, all it will takes is one to install it to the HD which is where it really should be anyway. The update of grub I doubt would even have a sdb=thumb,MBR option even with a loaded thumb plugged in and a grub2 bootloader in its mbr, hard to say really.

I think it would just be helpful if the OP explained why they want this and we can go from there.

If they want easybcd2 no big deal I don't really care but I wont help setup a system with possible failures, when not understood.

---

### Post by PSUinDC on 2010-12-10
> **wilee-nilee said:**
> I would just say that grub2 updates are coming through at times, all it will takes is one to install it to the HD which is where it really should be anyway. The update of grub I doubt would even have a sdb=thumb,MBR option even with a loaded thumb plugged in and a grub2 bootloader in its mbr, hard to say really.

I think it would just be helpful if the OP explained why they want this and we can go from there.

If they want easybcd2 no big deal I don't really care but I wont help setup a system with possible failures, when not understood.

Well, frankly I just wanted to do it because I don't like seeing GRUB pop up and ask what operating system I want to boot to. I thought that including some sort of boot files on a USB stick could tell the PC to boot to Ubuntu, and it would be a hell of a lot sexier solution. 

But like I said, if it's going to be a major hassle, I'll just drop it and stick with GRUB's OS choice menu.

---

### Post by jukingeo on 2010-12-10
Hello All,

Just chiming into this thread since what I would like to do is something similar.   In my case I would like to buy a new computer with Windows 7 on the hard drive.   What I would like to do is put Lucid core files and programs on a memory stick while storing data and files on the hard drive.

So this is what I would like:

When there is no memory stick in the computer, it will normally boot to Windows 7.   If I put the memory stick in the computer then it will boot to grub  in which it will ask me which OS I would like to boot to.

Since my current computer can be set to boot from USB via the Bios, I am going to assume a new computer that  I would buy would have the ability as well.    I do know that I would have to set the new computer's bios to boot from the USB first.

The main reason why I would like to set up Ubuntu Lucid on a USB drive is for two main reasons:

a)   I really do not want to mess with the Master Boot Sector in the event something screws up it would be hard to reinstall everything on the computer again.
b)   Since I have a few computers with boot USB capability, I would like to be able to "move" my Ubuntu OS from machine to machine...something I can't do now with Ubuntu on the main hard drives.

So, am I asking too much?

If No, then could someone link me to a "How To" thread on how to do what I would like to do?

Thank You,

Geo

---

### Post by C.S.Cameron on 2010-12-10
I see the same problem as PhoenixGI, most BIOS I have worked with resets the boot order once the flash drive has been removed.
Some BIOS though will let you boot what device you want by hitting F10, (or whatever). Thus you could insert the flash drive and hit F10 when booting to load Ubuntu.

---

### Post by fr3ak.m3 on 2010-12-11
Of course you can achieve that very easily.

1) Put your USB stick with Ubuntu Live and start setup
2) In the drive selection, install the OS into your USB stick and place the GRUb in your harddisk.. If you see correctly there is a option called "Install GRUB in"
3) Now if you select Ubuntu and haven't installed USB stick then it cannot boot ;)

---

### Post by jukingeo on 2010-12-12
> **fr3ak.m3 said:**
> Of course you can achieve that very easily.

1) Put your USB stick with Ubuntu Live and start setup
2) In the drive selection, install the OS into your USB stick and place the GRUb in your harddisk.. If you see correctly there is a option called "Install GRUB in"
3) Now if you select Ubuntu and haven't installed USB stick then it cannot boot ;)


Question:  For #2 could you have Grub install on the USB drive?   One of my goals is to NOT mess with the hard drive configuration and when the USB memory is not present, then the computer will normally boot to Windows 7.    Now when you boot up with the USB stick in place, THEN you would be presented with the Grub menu asking you what OS you want to boot up (with Ubuntu being the default choice).

Is that doable to boot Grub from the memory stick?

Thanx,

Geo

---

### Post by C.S.Cameron on 2010-12-12
MultiBootUSB has a script that will install grub2 to USB stick, (along with almost any version of Linux you wish):

[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)

If you wish to install grub2 manually see:

[http://www.panticz.de/MultiBootUSB](http://www.panticz.de/MultiBootUSB)

---

### Post by jukingeo on 2010-12-14
> **C.S.Cameron said:**
> MultiBootUSB has a script that will install grub2 to USB stick, (along with almost any version of Linux you wish):

[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)

If you wish to install grub2 manually see:

[http://www.panticz.de/MultiBootUSB](http://www.panticz.de/MultiBootUSB)


Both of those links look like they tell you how to multi boot, like say from a Live CD or an installer program.   What I want to do is RUN from the USB stick as if Ubuntu was installed on a hard drive.  Thus I want to be able to store files on it, read/write...etc.

Thanx,
Geo

---

### Post by C.S.Cameron on 2010-12-14
You can make a grub2 iso install of Ubuntu, or other Debian derivative, persistent by editing the grub.cfg menu entry similar to the following:
"linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/boot/iso/ubuntu-10.04-desktop-i386.iso noeject noprompt -- **persistent**"

Note that persistent has a space before it.

and then create a ext2, 3 or 4 partition named casper-rw.
If you wish a separate home partition name it home-rw.

Some people think that ext2 is best as it is not a journaling FS

---

### Post by C.S.Cameron on 2010-12-14
> **jukingeo said:**
> Question:  For #2 could you have Grub install on the USB drive?   One of my goals is to NOT mess with the hard drive configuration and when the USB memory is not present, then the computer will normally boot to Windows 7.    Now when you boot up with the USB stick in place, THEN you would be presented with the Grub menu asking you what OS you want to boot up (with Ubuntu being the default choice).

Is that doable to boot Grub from the memory stick?

Thanx,

Geo

Oops, now I think I understand???

If you just do a Full install to USB and leave your internal HDD plugged in while doing so you will get a grub menu with options to boot the USB or the internal drive:

Step by step for 10.10:

Insert the flash drive.
Insert the Live CD.
Start the computer, the CD should boot.
Select language
Select install Ubuntu.
Select Download updates while installing and Select Install this third-party software.
Forward
At "Allocate drive space" select "Specify partitions manually (advanced)".
Forward
**Confirm Device is correct.**
(Optional partition for use on Windows machine)
Select "New Partition Table" click Continue on the drop down.
Click "Free space" and "Add".
Select "Primary".
Make "New partition size..." about 4GB.
Location = Beginning.
"Use as:" = "FAT32 file system"
And "Mount point" = windows.
Select "OK"
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 4 to 6 GB, Beginning, Ext4, and Mount point = "/" then OK.
(Optional home partition)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 4 to 8 GB, Beginning, Ext2, and Mount point = "/home" then OK.
(Optional swap space, allows hybernation)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = remaining space, (1 to 2 GB, same size as RAM), Beginning and "Use as" = "swap area" then OK.
**(Important)**
Confirm "Device for boot loader installation" points to the USB drive. Default should be ok if HDD was unplugged.
Click "Install Now".
Select your location.
Forward.
Select Keyboard layout.
Forward.
Insert your name, username, password, computer name and select if you want to log in automatically or require a password.
Selecting "Encrypt my home folder" is a good option if you are worried about loosing your USB drive.
Select forward.
Wait until install is complete.
Turn off computer and plug in the HDD.
Stick the side panel back on.

---

### Post by jukingeo on 2010-12-14
Is there a step by step procedure for doing this somewhere here?

Ok, say I have a 16 gig memory stick and the Ubuntu Studio Lucid iso ready to go.   How do I prepare the memory stick?   As for the install...would I treat it like a hard drive install?

I DO know that the computer has to be set to boot from USB first and my current machine actually can do that already.  (A few years ago I was doing some USB boot tests with Puppy Linux).

In the end my main goal is that I can have my main programs set up on a "portable" drive as I do intend to buy a laptop computer down the road as well and I would like to be able to "Move" my Ubuntu OS.

Thanx,

Geo

---

### Post by oldfred on 2010-12-14
C.S.Cameron's post is good for a full install, he may have posted just as you did.

A couple of more versions:
Some examples of installs and issues:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
Dual drive internal or external
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

It does not have to be encrypted:
Standard full install to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
More discussion Dec 2010
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)

---

