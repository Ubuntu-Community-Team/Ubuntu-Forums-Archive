---
title: "Replacing Ubuntu with Windows"
date: 2009-04-09
forum: General Help
---

### Post by Sgtblades275 on 2009-04-09
I had Windows on this comp a while back. But I got it rid of it for some stupid reason. Now I have Ubuntu and just want to scrap it. Here's the deal, both of my drives still think there's a windows partition when there's not. I can't boot from cd or usb or floppy. can only boot to currently installed OSs. I've tried replacing GRUB with MSDOS but it hasn't been working. I've done the dd command where it erases all data including partitions on the drive. All this and still can't get to booting another OS. Even one that erases everything on the drives like DBK.
Any help will be very much appreciated.

(I'm trying to replace Ubuntu with Windows XP Pro)

---

### Post by Pasdar on 2009-04-09
You've erased windows and now you want it back? Why don't you just put in your Windows CD and install? Or are all your drives in linux filesystems?

---

### Post by paradigm2 on 2009-04-09
> **Sgtblades275 said:**
> I had Windows on this comp a while back. But I got it rid of it for some stupid reason. Now I have Ubuntu and just want to scrap it. Here's the deal, both of my drives still think there's a windows partition when there's not. I can't boot from cd or usb or floppy. can only boot to currently installed OSs. I've tried replacing GRUB with MSDOS but it hasn't been working. I've done the dd command where it erases all data including partitions on the drive. All this and still can't get to booting another OS. Even one that erases everything on the drives like DBK.
Any help will be very much appreciated.

(I'm trying to replace Ubuntu with Windows XP Pro)

You probably should go to a windows forum for this.  If you've done the "dd command" to zero out all the data, Ubuntu is no longer on that drive.

Traditionally the windows installer would be all you need.

---

### Post by Slim Odds on 2009-04-09
> **paradigm2 said:**
> You probably should go to a windows forum for this.  If you've done the "dd command" to zero out all the data, Ubuntu is no longer on that drive.

Traditionally the windows installer would be all you need.

LOL

I've been thinking about this for a while and I think that when people ask this question (which is the TOTALLY wrong place to ask it) I'm just going to tell them to go to the Winbuntu forum!!

---

### Post by paradigm2 on 2009-04-09
> **Slim Odds said:**
> LOL

I've been thinking about this for a while and I think that when people ask this question (which is the TOTALLY wrong place to ask it) I'm just going to tell them to go to the Winbuntu forum!!

:) lol

If they still had Ubuntu installed at all I might understand it.  But this person has stated that they erased it using multiple methods.

I don't how we could help explain why the windows installer won't work!

[nice guy mode]
I guess to be nice and the most likely thing I can think of is that the boot order in the BIOS has the hard drive booting before the CD rom.  The Poster should check that and change it, usually by hitting a certain key (such as F2. F10, or DEL) on startup.

Good luck.

---

### Post by Sgtblades275 on 2009-04-09
I've posted it in Windows help forums and waiting replies and on multiple sites. The boot order: I've checked that loads of times and have done it many different ways. The only thing that happens every time is it either: completely skips boot from cd/usb/floppy and goes straight to GRUB OS menu or it gives me error 21. This happens randomly and a lot. I can't even get rid of Ubuntu without doing it manually. Manually, I'd kill it before I even finished. The files would still be there and I wouldn't be able to do anything else.

---

### Post by Sgtblades275 on 2009-04-09
> **Pasdar said:**
> You've erased windows and now you want it back? Why don't you just put in your Windows CD and install? Or are all your drives in linux filesystems?

Yes, because I was very computer illiterate back then. Can't because it won't freaking let me boot from anything but current;y installed OSs. One drive is ext3 and the other is, currently, empty of all data including partition data and has not been formatted, yet still does not allow me to boot.
My guess is that I need to flash my bios with an older version and then update it again with the newest version to clean out whatever is causing the problem. But, I'm having trouble flashing the bios because they're windows installers and WINE goes about halfway through then it just shuts off without any error or warning message.

---

### Post by Pasdar on 2009-04-10
You don't need to flash anything. Even some of the oldest PC BIOS has the ability to select CD in boot priority. You just to select it in Bios.

---

### Post by acreech on 2009-04-10
If your partitions are still in the Linux format (ext3, extended, Linux-swap) then I would use the Ubuntu Live CD, go to System>Administration>Partition Editor (gparted). Then reformat the drive partition to a nfts or what ever format that windows will take. 

I don't know why you would go back to Windows. I just setup a Windows XP drive for my mife to use on a rare occasion and that was enough to remind me why I hate Windows!

Good luck

---

### Post by Slim Odds on 2009-04-10
The bottom line here is that it does not matter what is currently on your computer.

You need to boot an install CD (windows in your case).

To do this, your BIOS must be setup to:
1) Boot from CD.
2) Boot from CD First.

That's really all there is to it.

Once the install CD boots, you partition, format, install....

---

### Post by Sgtblades275 on 2009-04-10
... I already said this...
I can't boot from cd/usb/floppy. I've switched the order of which boots first and GRUB IS THE PROBLEM. It either gives me error 21 on random occasions or completely skips it goes to select OS to boot or gives me the options of "Press F1 to retry or F2 to go to setup". It completely skips the error 21 message when both drives are powered on. When one drive is powered on it always gives me error 21 and locks the computer up

---

### Post by Sgtblades275 on 2009-04-10
> **acreech said:**
> If your partitions are still in the Linux format (ext3, extended, Linux-swap) then I would use the Ubuntu Live CD, go to System>Administration>Partition Editor (gparted). Then reformat the drive partition to a nfts or what ever format that windows will take. 

I don't know why you would go back to Windows. I just setup a Windows XP drive for my mife to use on a rare occasion and that was enough to remind me why I hate Windows!

Good luck

I wish I could do that, but, as I said, it doesn't allow me to boot from CD or USB. I have the options but it either skips it or gives me error 21.

I want to go back to windows because I'm a classic gamer and Ubuntu jsut doesn't like windows programs (ex: pj64, psx, dolphin) or older games that run from D3D only.

---

### Post by _khAttAm_ on 2009-04-10
> **Sgtblades275 said:**
> I wish I could do that, but, as I said, it doesn't allow me to boot from CD or USB. I have the options but it either skips it or gives me error 21.

I want to go back to windows because I'm a classic gamer and Ubuntu jsut doesn't like windows programs (ex: pj64, psx, dolphin) or older games that run from D3D only.

did you try PCSx (available via synaptic)? it works file. Also ePSx is available for linux too (haven't tried it).
I also tried [mupen64](http://mupen64.emulation64.com/) in ubuntu but got poor results than "Project 64 on windows". May be that was because of my old computer with graphics without 3d. I haven't tried it on my new pc.

Also, gamecube emulator is available for Linux. It is called Tuxcube but I have never tried it.

Also have a look at this:
[http://www.usinglinux.org/emulators/](http://www.usinglinux.org/emulators/)

Anyways, getting back to your problem. How did you change the boot order?? via BIOS I guess. You should be able to go into bios (by pressing DEL or F2 or some other key) and change the boot priority. 
Error 21 is after the CD fails to boot.
Are you sure that the CD you are using is bootable?

---

### Post by Sgtblades275 on 2009-04-11
> **_khAttAm_ said:**
> did you try PCSx (available via synaptic)? it works file. Also ePSx is available for linux too (haven't tried it).
I also tried [mupen64](http://mupen64.emulation64.com/) in ubuntu but got poor results than "Project 64 on windows". May be that was because of my old computer with graphics without 3d. I haven't tried it on my new pc.

Also, gamecube emulator is available for Linux. It is called Tuxcube but I have never tried it.

Also have a look at this:
[http://www.usinglinux.org/emulators/](http://www.usinglinux.org/emulators/)

Anyways, getting back to your problem. How did you change the boot order?? via BIOS I guess. You should be able to go into bios (by pressing DEL or F2 or some other key) and change the boot priority. 
Error 21 is after the CD fails to boot.
Are you sure that the CD you are using is bootable?

Oh dude, I can get PSX and PJ64 working but WINE kills like 50% of my grfx card so that when I play it runs slow. Like: I have an nvidia geforce fx 5200 and through wine it runs like an early mx series.

Yes through bios. Correct. Yes bootable dude. I've also researched the error 21 problem but people that get this error all have raid drivers and link it to that then just boot directly from motherboard sata/ide cable to single drive and the problem is fixed. I don't have a raid driver, but I do have two hard drives connected directly to the motherboard via IDE.
I suspect that GRUB wrote itself to both drives as software to boot with. If only I could overwrite GRUB with MSDOS it would be fixed (though GRUB is much better, I'd prefer to keep GRUB but be able to have Windows)

---

### Post by callie510 on 2009-04-11
I don't think you're understanding what people are telling you... 

**If you're seeing GRUB, your computer is already booting from the hard drive.** You have to get to the CD before this happens.

Try holding down F keys during the bootup (BEFORE grub, during your manufacturer display ...) until you get an option to choose where to boot - CD, Hard drive, etc. Select CD.

I don't know why, but setting CD to boot first in the BIOS doesn't always work. Sometimes you have to select it by hand.

edit: I am a video gamer and I keep a little 40GB partition of Windows at the start of my drive for games. Doesn't interfere with me using Ubuntu the other 90% of the time. :) Just saying...

edit2: If you like grub, try googling "Wingrub" or "Windows Grub" - there is in fact a way to make Grub work with Windows (or other non Linux operating systems) to manage multiple boots.

Hope I have helped.

---

### Post by Slim Odds on 2009-04-11
> **Sgtblades275 said:**
> ... I already said this...
I can't boot from cd/usb/floppy. I've switched the order of which boots first and GRUB IS THE PROBLEM.

As others have said, and I will say: GRUB is not your problem. You need to BOOT FROM ANOTHER DEVICE (like a CD). If you can't figure out how to do that, then you'll have to get a friend who does.

Your OS install has to run FIRST! Once you're already booting from the hard drive (which is what is happening if you get to GRUB), then it's already too late.

---

### Post by lolol i r linux noob on 2009-04-11
grub can load a floppy disk so if u have a floppy disk with fdisk.exe boot tht with grub and formatt the disk to fat 32 then insert exp cd and install like normal.

try fdisk/mbr this should fix the MBR (master boot record)

Hope this was what u were looking for.

---

### Post by Sgtblades275 on 2009-04-13
... ehem: For me to change the boot order I must go into BIOS to do this. Now, when I press the power button on the computer, it turns on. understand? then I hit my setup menu button: F2. understand so far? Then, I go down to BOOT ORDER and move IDE CD DRIVE to the top as 1. For me, it goes: 1 IDE CD DRIVE 2 FLOPPY DRIVE 3 HARD DRIVE C:
My computer is a Dell Dimension 8300 with BIOS revision AO7.
Now, when I hit save changes and exit, it restarts with those settings and turns on, it takes a few extra seconds to start AFTER the screen with the DELL logo on it disappears. Then, it just says: Loading grub stage 1.5... loading, please wait... The bios, for some stupid reason, completely skips over the CD AND floppy boot.
Also, here's something else, drive C: for the BIOS would be the first hard drive (the one connected to IDE #1 cord), but, the first hard drive is the UNPARTITIONED UNFORMATTED EMPTY hard drive. The 2nd is not recognised until AFTER it tries booting from C:. Another reason why I have a strong mind to think that the BIOS is the issue.
If you STILL do not understand, I'll post a video on youtube showing y'all what the exact issue is.

---

### Post by TenPlus1 on 2009-04-13
Can you try something...  Insert your ubuntu install CD and see if it lets you BOOT from the CD...  If it does then it may be that something is wrong with your actual Windows XP Install CD if it refuses to boot straight from it...

Also, If you can somehow boot from the Ubuntu CD (or Ubuntu flash-device) then you can use Gparted to remove all partitions and start with an empty drive again...

---

### Post by AntiBodies on 2009-04-13
yeah it is possible there is something wrong with your XP cd (or possibly cdrom drive).. so check a bootable cd you know works, such as the ubuntu cd you used to install ubuntu

if the cd is not bootable it will just skip to the next bootable device (floppy then hard drive).. the XP install cd will also say "press any key to boot from cd" you have to press the any key (jk) or it will just continue to boot from the hard drive

also try pressing F9 or F12 when you start up (when the dell screen is up).. just keep pressing the button over again until hopefully you get a screen to give you a choice of what device you want to boot from.. pick CD

GRUB is on the hard drive (which ever one) so it has no effect on what device you are booting from.. you want to boot from the windows setup cd (or dell restore cd) and basically blow away all the partitions you can see and create a new windows partition.. windows will see it as unknown partition or something as it is ext3 formatted

hope this helps.. if it dont, dude i dont know what is wrong.. maybe bios problem but i doubt it.. i wouldn't go flashing your bios unless you were safely booting from a flashing floppy\cd (provided by dell) or using the windows utility from within windows.. how long ago did you install ubuntu? you would have had to boot from cd to get that installed

---

### Post by Sgtblades275 on 2009-04-19
This info may also help: drive #1 (so called because it is connected to IDE1) is sda1 (and only sda1 no other sda#) and has nothing on it whatsoever. It is empty, unpartitioned, and not flagged as anything. (I use GPARTED for partitioning). Drive #2 (so called because it is connected to IDE2) is sdb1 and sdb2 and sdb5. sdb1 is formatted as ext3 and is the Linux filesystem. sdb2 is a small 6gb partition that is in extended format. sdb5 is the extended 6gb partition, which is formatted as a Linux swap (but in the terminal command fdisk -l, it appears as Linux swap / Solaris. (the swap is currently active)

Even when having just the first hard drive powered on and even the only hard drive connected to the IDE cable, it still will not let me boot from IDE CD Device, or USB Device. (I now have floppy disks so if anyone has any idea for some mbr fixer that would fit in a floppy please, do tell.) And it gives me a message saying that I can't boot from this device press F1 to retry or F2 to return to System Setup. Sometimes I don't hear the computer attempting to access those drives.

edit: would erasing or formatting the extended partition (actually reformatting the linux swap partition which is inside the extended partition) to fat32/ntfs allow me to boot from the Ubuntu LIVE CD? or not... probably not because for that partition to be even seen it has to go through GRUB first right...

---

### Post by Sgtblades275 on 2009-04-19
> **AntiBodies said:**
> yeah it is possible there is something wrong with your XP cd (or possibly cdrom drive).. so check a bootable cd you know works, such as the ubuntu cd you used to install ubuntu

if the cd is not bootable it will just skip to the next bootable device (floppy then hard drive).. the XP install cd will also say "press any key to boot from cd" you have to press the any key (jk) or it will just continue to boot from the hard drive

also try pressing F9 or F12 when you start up (when the dell screen is up).. just keep pressing the button over again until hopefully you get a screen to give you a choice of what device you want to boot from.. pick CD

GRUB is on the hard drive (which ever one) so it has no effect on what device you are booting from.. you want to boot from the windows setup cd (or dell restore cd) and basically blow away all the partitions you can see and create a new windows partition.. windows will see it as unknown partition or something as it is ext3 formatted

hope this helps.. if it dont, dude i dont know what is wrong.. maybe bios problem but i doubt it.. i wouldn't go flashing your bios unless you were safely booting from a flashing floppy\cd (provided by dell) or using the windows utility from within windows.. how long ago did you install ubuntu? you would have had to boot from cd to get that installed

That does help dude. I understand GRUB is on the hard disk. I installed Ubuntu around late January this year and about the third time I tried dual booting it wouldn't let me boot from the stated mediums. I want to be able to boot from the Ubuntu 8.10 LIVE CD and repartition the ext3 drive to NTFS or fat32 or jsut completely erase the drive. (oh yeah, screw grub, I'm fed up with it. If I end up with MSDOS boot, I'll just go with it.)

---

### Post by Sgtblades275 on 2009-04-20
bump
any other informative help would be gladly appreciated

---

### Post by MartyBuntu on 2009-04-20
If you have a *real* Windows disk that won't boot, or any other Linux disk won't boot, I would consider swapping the CDROM drive at least temporarily for an install.

---

### Post by Slim Odds on 2009-04-20
> **Sgtblades275 said:**
> That does help dude. I understand GRUB is on the hard disk. I installed Ubuntu around late January this year and about the third time I tried dual booting it wouldn't let me boot from the stated mediums. I want to be able to boot from the Ubuntu 8.10 LIVE CD and repartition the ext3 drive to NTFS or fat32 or jsut completely erase the drive. (oh yeah, screw grub, I'm fed up with it. If I end up with MSDOS boot, I'll just go with it.)

I can't believe that you're still bad mouthing GRUB when it has nothing to do with your problem. Once again, **you should never be getting to GRUB!**

Try this:
1) Disconnect every IDE device except the CD ROM drive.
2) Boot from CD ROM drive.

If you can't get that to work, pour gasoline on the machine and toss a lit match on it. ;)

But, seriously, get your boot order fixed. It's NOT a GRUB problem.

---

### Post by lisati on 2009-04-20
I offer these thoughts in the hope that they might provide a clue for something else to check.

I once had problems temporarily reinstalling Windows on the machine I'm using at the moment, using the recovery DVD that came with it - it's one of the Toshiba A100 range of laptops. Even though I did everything "correctly" according to the brochure that came with the machine (press F12 at startup, selecting the appropriate "boot from CD/DVD, etc) it just didn't seem to work. Turns out that the recovery DVD was set to check the volume label on the hard drive. Out with the Ubuntu Live CD, a quick bit of tinkering with the copy of gParted on it renaming the volume, and the Windows recovery DVD worked. (I was able to learn the proper volume label by inspecting the files on the rec.overy DVD's root folder using another machine.)

---

### Post by Sgtblades275 on 2009-04-22
> **Slim Odds said:**
> I can't believe that you're still bad mouthing GRUB when it has nothing to do with your problem. Once again, **you should never be getting to GRUB!**

Try this:
1) Disconnect every IDE device except the CD ROM drive.
2) Boot from CD ROM drive.

If you can't get that to work, pour gasoline on the machine and toss a lit match on it. ;)

But, seriously, get your boot order fixed. It's NOT a GRUB problem.

... I know GRUB ain't the problem. It's just not responding to commands any more.
Also, you can't boot from CD ROM if there's no hard disk installed. That would eliminate the point of having the ability to fix the problem. Which I have finally solved is drive #2s problem or sdb's problem. I'll erase it when I get a hold of a computer for at least a week so I can have enough time to fix this piece of crap when I erase everything.

---

### Post by MC_Sketch on 2010-05-24
why do you even want to switch to Windows? i used Windows for 8 years before i switched to Ubuntu 2 years ago, and i've never had any desire to switch back :confused:

---

### Post by lisati on 2010-05-24
I think this old thread should be allowed to rest in peace.

(BTW, I no longer have that laptop I mentioned a few posts back, I gave it to a nephew)

---

