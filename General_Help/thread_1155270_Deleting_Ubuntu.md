---
title: "Deleting Ubuntu"
date: 2009-05-10
forum: General Help
---

### Post by redemptionx9 on 2009-05-10
Hey, I'm attempting to delete Ubuntu and go back to XP but I've hit a few snags

Firstly, I can't restore the MBR with the fixmbr command on the recovery console - Nothing at all happens, and all of the "uninstall ubuntu" guides seem to be based off this. CHKDSK returns me with the disk has unresolvable errors and nothing else seems to do... anything except create partiton - Which bluescreens me

Secondly, if i need to just completely erase the whole drive of any data to restore the MBR, i need some way of backing up drivers, I've tried to find the DRIVERS folder in the WINDOWS folder in program folders, but I don't quite know what I'm looking for - Is there any way i can find driver information via Ubuntu?

---

### Post by gradysghost on 2009-05-10
While I'm fairly sure this is not the place to ask how to install Windows XP, I suppose I'll assist you.  There is no such thing as "uninstalling" any operating system.  It doesn't exist.

Your best bet is to simply reinstall XP from a disk, which, if you don't already have it, will run you a fair amount of money.  Looks like you can buy the cheapest version of XP for about [175 bucks]("http://www.newegg.com/Product/Product.aspx?Item=N82E16837116193").  Refer to that user guide to get it installed, but do it quick.  Support runs out very soon.  Then try to get an internet connection.  When that fails, use a different computer to download your NIC drivers, transfer them over on a flash drive (assuming WinXP can handle your mass storage controller out of the box), and install it.  Then get your other drivers downloaded and your 1 GB+ of updates (which won't be lasting much longer, since support won't exist anymore).

The fixmbr thing also requires a Windows disk.  It overwrites the master boot record of your hard drive, making NTLDR take the place of GRUB.  This should fix it, provided fixmbr can find your Windows installation.

For what it's worth, fixmbr will do nothing that GRUB doesn't already do for you.  It just prevents you from having the option to boot into Ubuntu.  It does nothing to remove Ubuntu from your system whatsoever.  To do that, you must actually do a full install of WinXP, repartitioning your hard drive in the process, or use WinXP's Drive Management tools to format those partitions.  This will result in your hard drive still having two partitions, and may affect your ability to boot to XP.  Your best bet is to do a clean install of XP.

---

### Post by redemptionx9 on 2009-05-10
I have an XP disk, fixmbr does not do anything at the recover console

I can't boot into my windows partition from GRUB, if i try, it'll just crash :/ It worked fine before i installed linux

I'm guessing the XP partition is corrupted? I can still access the system files and program files etc from the computer window 

Is there no way i can see what drivers i have from ubuntu so i can attempt to find an XP verison before i completely clear everything?

---

### Post by jimbob on 2009-05-10
I think you also have to do a fixboot in conjunction with fixmbr.  Google it - there are several guides to follow.

As I recall the drivers are in C:\WINDOWS\SYSTEM32\DRIVERS but if you do a new install you will get them back unless you are using some special drivers
in which case you should have the CD's that came with the devices.

---

### Post by spiderbatdad on 2009-05-10
when booting from your windows disk, do you get the option to install or repair? You should choose repair.
> next screen will have a 1 and some question, enter 1
now there should be a prompt c:\
enter help
a long list of activities should show, move to the end of the list and at the prompt enter help diskpart
you should get a report on your hard drive and some info what you can do, delete partitions is one of those.

if you like you can delete the Linux partitions, that will get rid of Ubuntu

then if you want to clean the disk off completely you can at the prompt enter help once again and find the format activity, enter that at the prompt and your disk will be formatted and no more ubuntu nor anything else.

If you want to keep whatever else is on the disk , find fixmbr and enter that at the prompt, and you next boot will be Windows if it was on the disk  [https://answers.launchpad.net/ubuntu-doc/+question/61701](https://answers.launchpad.net/ubuntu-doc/+question/61701)
Hope this helps you.

---

### Post by redemptionx9 on 2009-05-10
> I think you also have to do a fixboot in conjunction with fixmbr.  Google it - there are several guides to follow.

Fixboot does nothing, I'v already looked over guides on how to uninstall ubuntu, they all rely on fixmbr and fixboot which don't do anything for me

> As I recall the drivers are in C:\WINDOWS\SYSTEM32\DRIVERS but if you do a new install you will get them back unless you are using some special drivers

Thanks, I'll have a look in the morning

> in which case you should have the CD's that came with the devices

I took the computer off somebody that was just going to chuck it and thought I'd have a look at what all the fuss was about Linux

spiderbatdad, I was on the repair console thing while attempting to do all this fixmbr shizzle, I'll have another look at it in the morning with that little guide next to me (The two computers are next to each other)

Thanks everyone, I'll post back tomorrow with updates

---

### Post by gradysghost on 2009-05-10
Question: When you installed Ubuntu, did you choose to resize your WinXP partition?  If so, this could explain the corruption, especially if you didn't run three or four degrag attempts beforehand.  Not that it matters now, but it could help explain things.

---

### Post by gradysghost on 2009-05-10
If you can't get fixmbr and fixboot to work, I'd suggest backing up your data before continuing with this fix.  It could save you a ton of headaches in the future.

---

### Post by redemptionx9 on 2009-05-11
I did resize the partition without defragging, I didn't know that'd be an issue

Once I delete the partitions, will I then be able to fixmbr etc?

---

### Post by jimbob on 2009-05-11
If all the partitions are gone you won't have to worry about it because your next installation will write a new mbr.

(Unless of course you have some sort of hardware problem).

---

### Post by redemptionx9 on 2009-05-11
Right I'v got the drivers i want - Thanks to whoever suggested the windows32 folder, was there all along :)

Now i'm not exactly sure about how to go and format the disk

the format command in the recovery console keeps returning me with a sort of 'incorrect syntax' error, what exactly shall i put? "Format c"?

If i attempt to install windows it cannot locate a disk at all

Perhaps a hardware error?

---

### Post by mistypotato on 2009-05-11
So, there's nothing on the drive that you want?  I thought you said you wanted to do a backup?  If you've deleted the partitions, all data on the disk is basically inaccessible....outside of sophisticated recovery programs.

In essence, you are starting fresh.  New, empty Windows XP install.

If so, all you should have to do is insert the WindowsXP CD, start your computer and follow the easy Windows prompts.

If you're getting other problems, you'll need to get a disk tool (I use Acronis) to go in and clean things up.  Depending on the Manufacturer and whether it was an OEM drive or not, it MIGHT have a recovery partition.  If so, try a recovery first, (see documentation that come with the computer).

Otherwise, go to the website of the harddrive manufacturer and download their TOOLS disk.   You will be able to properly format the drive with that regardless....(unless the drive has gone bad, and the manufacturers software will sometimes tell you that too).

---

### Post by redemptionx9 on 2009-05-11
> So, there's nothing on the drive that you want?

In previous post: Right I'v got the drivers i want - Thanks to whoever suggested the windows32 folder, was there all along

> If you've deleted the partitions

I can't delete anything, from the XP setup thing I can't create a new partition or delete one because it doesn't detect a HDD

Stated also in a previous post, i do not have any disks because the computer was given to me because it was just going to be scrapped, i didn't get anything with it

I'll give Acronis a look

---

### Post by xx58 on 2009-05-11
):P Dear Friend,
You have 2 choices only.
1. Make clean ANY Windows installation. Again you need know what kind Hard Drive you have. If you have SATA Hard Drive, then you need make customer Windows DVD Disk use nLite. If you have any kind Windows Vista, then original install disk are good. YOU need make clean install to install Windows XP.
2. You can install (my recondation) Linux Ubuntu 8.04 witch one is very good. Don't install Linux Ubuntu 9.04, because you will have much problems to put all programs work. Ubuntu 9.04 is supported only one year, but Ubuntu 8.04 to year 2011. Beleive me you will have first much problems, but at Linux Ubuntu Forums will help you. If you learn at Ubuntu Forums, then some 6 month later everything will be easy and you will be love it.
If you want be with Windows XP, then my recondations is go to Windows Vista, because Windows XP support will be very soon over too. Good luck. I love Linux.

---

### Post by jimbob on 2009-05-11
I'm thoroughly confused. If you tried the XP setup you must have an XP install CD, right?

Please give us a list of exactly what CD's you have and we can go from there.

---

### Post by xx58 on 2009-05-11
):PIf Windows XP cannot detect Hard Drive , then you have SATA Hard Drive and you need make customer DVD. Good Luck.

---

### Post by redemptionx9 on 2009-05-11
> then you have SATA Hard Drive

SATA doesn't have the 80 or whatever pin connectors with that massive ribbon cable, so no - My drive isn't SATA, its PATA

> Please give us a list of exactly what CD's you have

All I have is an XP disk

I have backed up drivers from the PC

I need to now format the drive 

The windows XP disk is not recognizing a HDD when i go into setup

If I CHKDSK in recovery mode, it does find a disk but states that it has unresolvable problems

Is it possible that bad partitioning etc has damaged the drive?

---

### Post by jimbob on 2009-05-11
> If Windows XP cannot detect Hard Drive , then you have SATA Hard Drive 
I don't think this is true.  I have only a single SATA drive in my system and I took my old XP install disk, booted it and it found my drive just fine and listed the (2) Ubuntu and (1) swap partition just fine.

> I need to now format the drive  No you don't.  Forget about recovery console, etc. and just start a new install.
The new install should read the CD and put a bunch of stuff into memory before it begins to look at your disk partitions.  (that's what mine did).

---

### Post by xx58 on 2009-05-11
):PYou have only one choice, need make at your Windows XP DVD OR CD customer DVD to reformat Hard Drive. ATA or SATA all are same. Command format C was used only for Windows 95 or Wndows 98. You will see, you can do what you want, you cannot  format Hard Drive useing Windows XP Disk, before you will make customer DVD useing nLite program. How it do, better place is Windows XP support web page. I fixing computers for living, so I know it and I had same problem what you have right now, before.

---

### Post by redemptionx9 on 2009-05-11
> **jimbob said:**
> just start a new install.

Alright :P Trying the setup thing yields nothing, it cannot detect a HDD to create a partition on

Shall i try that cleaning tool thing?

---

### Post by x12796 on 2009-05-11
I was experimenting with dual booting XP and Ubuntu after having a single boot Ubuntu system.  In order to both successfully and easily install XP I had to completely wipe the drive by booting into gwscan from a CD.  This course of action was a lot easier than trying to fix the MBR going from Grub to the Windows loader.  Before I wiped the drive I'd install XP but it wouldn't load as Grub didn't recognize it, but after the drive was wiped then XP installed as expected as Ubuntu installed in a snap too.

Tim

---

### Post by theozzlives on 2009-05-11
Boot up the Ubuntu cd and go to partition editor, if you have Linux or swap partitions delete them. If you have NTFS, resise it to take up your whole drive. If you have nothing, create an NTFS and use the whole drive. That should fix you to re install.

---

### Post by jimbob on 2009-05-11
He said above that all he has is an XP CD.

You need to download and burn an Ubuntu Live CD and proceed as in post #22.

---

### Post by gradysghost on 2009-05-11
> **jimbob said:**
> He said above that all he has is an XP CD.

You need to download and burn an Ubuntu Live CD and proceed as in post #22.

Agreed.  And if that fails, then you may have a hard drive problem.  Still, gparted sees all, and should help your dilemma.

---

### Post by redemptionx9 on 2009-05-11
I have the ubuntu .iso still, so i can just burn another - I'll give it a try

---

### Post by redemptionx9 on 2009-05-11
I can't find my ubuntu iso but i do have a gparted.rar on my desktop - Verison 0.4.2

Can i just burn this onto a disk and use that?

There isnt a specific iso or whatever, will it be alright to simply burn all the files/folders to disk or is there something different i have to do - Boot disks always seem to give me trouble

---

### Post by jimbob on 2009-05-11
No, you need to burn the .iso of Gparted or it won't boot.

---

### Post by redemptionx9 on 2009-05-11
I have Gparted  up on my second computer but I'm not too sure where to go from there? The help command spews out alot of stuff but it's all abit much - Any suggestions?

---

### Post by M4rotku on 2009-05-11
Gparted has a GUI, you don't have to use it in the terminal (which I assumed you were from the '--help' command)

To use Gparted, go to 
Sytem -> Administration -> Partition Editor

It will give you a nice GUI which should be decently intuitive.

Good luck

---

### Post by jimbob on 2009-05-11
I have no idea what your "second computer" is.

You need to do what I suggested in post #27 and boot the standalone Gparted CD on the computer with the apparent disk problem.

As mentioned above it has a nice GUI to use.

---

