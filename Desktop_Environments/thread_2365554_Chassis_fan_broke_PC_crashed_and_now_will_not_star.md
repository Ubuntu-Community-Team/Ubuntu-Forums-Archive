---
title: "Chassis fan broke PC crashed and now will not start"
date: 2017-07-07
forum: Desktop Environments
---

### Post by Jonners59 on 2017-07-07
My PC stopped working, and after I opened it I found that the 2nd fan (chassis) had shattered and the motor had come apart.  I removed it and tried to start the PC.  After a few false starts it starts to boot, but stops after GRUB.  If I try to boot normally it either sticks with the logo after checking hard drives, or it goes in to Recovery mode.  If I select the advanced option it stops at the logo.

It is up to date and I believe on the latest version of xUbuntu.  Any advise, please.  I use this old PC like a storage server and a virtual machine to run the telephone, so quite important to us.

As I can't get in to it, I can only tell you basics
3 x hard drives of which two are 1Tb for starage and 1 x00Gb to run the machine
If I recall 16Gb of DDR3  @ 1600Mhz RAM - Corsair
Asus MB M5A97 LE R2.0
AMD Fx(tm)-8350 eight core processor

---

### Post by Habitual on 2017-07-07
Replace the fan.

---

### Post by Jonners59 on 2017-07-08
> **Habitual said:**
> Replace the fan.
Thank you, but I do not think that is the answer.  The chassis fan is an option, not required and is automatically turned off in the bios.  The OS is booting up past GRUB and has beeen on, stuck in the same place, xUbuntu screen all night, whereas it would have shut down with alarms if the chassis fan was the problem.

I think, when it went the image was damaged in some way.

---

### Post by QIII on 2017-07-08
Hello!

If your fan shattered, there is always the possibility that fragments damaged internal components.  There also may have been a transient short circuit that damaged your power supply.

Start first by really, *really* checking hard for debris from the fan.  If the hub shattered and kicked out even the tiniest bit of metallic shrapnel, any part of your system may have been damaged.  Also check for bulging, burst or burnt capacitors.  A brief short may have ruined one or more of them.  Using your nose helps with the last.  Look very carefully at the board and stick your head in the case and take a few hard sniffs (yes, really.  I have discovered damage that way on several occasions.)

---

### Post by Jonners59 on 2017-07-08
> **QIII said:**
> Hello!

If your fan shattered, there is always the possibility that fragments damaged internal components.  There also may have been a transient short circuit that damaged your power supply.

Start first by really, *really* checking hard for debris from the fan.  If the hub shattered and kicked out even the tiniest bit of metallic shrapnel, any part of your system may have been damaged.  Also check for bulging, burst or burnt capacitors.  A brief short may have ruined one or more of them.  Using your nose helps with the last.  Look very carefully at the board and stick your head in the case and take a few hard sniffs (yes, really.  I have discovered damage that way on several occasions.)

Thanks.
I have had the PC out with the side off and given it a good shaking after a good look round.  No obvious smells.  I was hoping it was not hardware, though will take a closer look again as it won't hurt.  It's been on all night so if it is going to smell it will now.  I was thinking it was more the something wrong in the OS though....  Something curable with a few commands....  Why?  Because it is booting up and I do get past GRUB and it gets to the xUBUNTU logo...

---

### Post by robbie 348 on 2017-07-08
When you gave it a good shaking, did you remove the hard drive first?

---

### Post by QIII on 2017-07-08
> **Jonners59 said:**
> Because it is booting up and I do get past GRUB and it gets to the xUBUNTU logo...

We just need to rule out hardware issues.

---

### Post by kurt18947 on 2017-07-08
Try to boot a live USB or DVD? If a live device will boot wouldn't that help to eliminate hardware issues?  Maybe not hard drive problems but problems with other bits. See if the file system(s) on the hard drive are visible?

---

### Post by Jonners59 on 2017-07-08
> **robbie 348 said:**
> When you gave it a good shaking, did you remove the hard drive first?

:p   EEERRRRR  NO!

Update:
A few minutes ago  I was messing about with the keys before I shut down to give it a nose job and tried F1 (and F2 and so on).  Found it popped in to terminal and just hit return.  It then threw up a warning.  Could not load drive "Backup", press S to skip...  blah, blah...  So I skipped, and it started up normally.

So.  Either I have dislodged the HD "Backup" or some hardware to it, or the MB or HD itself are damaged from some loose stuff when the fan broke.  That is my guess.  Now a possible clue.  When I tried to get it to boot the first couple of times (False starts I mentioned in #1) there was a smell of electrical burning, but was not clear from where as it went I took no notice of it.  So I am wondering, is it, may be that the port it is connected to had burnt out in a short from shrapnel.
,
Task:
[LIST=1]
[*]Double check that the HD is seated and connected properly first
[*]Change port.  I think I have spares.  If not then a new MB.
[*]Does this change fstab???  Not sure it does as the drive is already labelled.
[*]If it still does not work then a new HD for "Backup" and I will have to rebuild the back up from scratch....  not a major problem.
[*]Fingers crossed it stops no further than 2 above.
[/LIST]

Does this sound right?

UPDATE:

Damn Damn Damn!
Checked connections all OK, so didn't knock anything out with the shacking.
Tried gParted and it could see the HD, which is interesting
Shut down and tried disconnecting the HD
Could not get it to boot back in to the OS again, stopped as per previous.  AFter a few retried, inc trying older kernals it still would not work, then started an alarm.  I have shut down now.

Further update:
Tried booting to live CD and it worked great.  Accessed all drives no problem, so it must be that the OS has corrupted somehow, yes, no???  If it boots with the CD and all the HDs work then surely it is the SO that is corrupted in some way????  Is that correct and if so then how to fix?

---

### Post by kurt18947 on 2017-07-08
> **Jonners59 said:**
> :p   EEERRRRR  NO!

[snip]

UPDATE:

Damn Damn Damn!
Checked connections all OK, so didn't knock anything out with the shacking.
Tried gParted and it could see the HD, which is interesting
Shut down and tried disconnecting the HD
Could not get it to boot back in to the OS again, stopped as per previous.  AFter a few retried, inc trying older kernals it still would not work, then started an alarm.  I have shut down now.

Further update:
Tried booting to live CD and it worked great.  Accessed all drives no problem, so it must be that the OS has corrupted somehow, yes, no???  If it boots with the CD and all the HDs work then surely it is the SO that is corrupted in some way????  Is that correct and if so then how to fix?

I'm no expert with this stuff but I'd suspect either a problem with the first few sectors of the hard drive where the boot code lives or a problem with GRUB. You do seem to have eliminated most hardware as the source of your problem. The ability to 'see' a hard drive using a live install probably doesn't mean the code required to boot is intact but I'd think that points to a software problem. Would it be worthwhile to re-install GRUB in case the existing version is at fault? There is a boot rescue .iso around but the last I knew it didn't work with current (16.04 or higher) Ubuntu.

---

### Post by Jonners59 on 2017-07-08
> **kurt18947 said:**
> I'm no expert with this stuff but I'd suspect either a problem with the first few sectors of the hard drive where the boot code lives or a problem with GRUB. You do seem to have eliminated most hardware as the source of your problem. The ability to 'see' a hard drive using a live install probably doesn't mean the code required to boot is intact but I'd think that points to a software problem. Would it be worthwhile to re-install GRUB in case the existing version is at fault? There is a boot rescue .iso around but the last I knew it didn't work with current (16.04 or higher) Ubuntu.
OK, will give it a go....  I have GRUB rescue on CD

---

### Post by Jonners59 on 2017-07-08
No, did not work.  I think the damage is to the installation...  The OS.  If the HW works on the CD and it is getting past GRUB then it has to be the OS...  No?

---

### Post by Jonners59 on 2017-07-09
ANy help please bar trying to rebuild the machine by reinstalling....????????????????

---

### Post by oldfred on 2017-07-09
If fan motor exploded, you must have had a power surge of some type. Even if you can see an mount drives, you may have a damaged sector or two somewhere.
Have you tried running fsck on all ext4 partiitons, and if any NTFS run chkdsk until no errors?
       To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

I had capacitors blow up on my nVidia card (7600 series) years ago. But it damaged motherboard & I also replaced power supply just in case. When odd power events occur who knows what the other impacts may be.

You do have good backups?
If not and you can read drives, back up now.

---

### Post by Jonners59 on 2017-07-09
> **oldfred said:**
> If fan motor exploded, you must have had a power surge of some type. Even if you can see an mount drives, you may have a damaged sector or two somewhere.
Have you tried running fsck on all ext4 partiitons, and if any NTFS run chkdsk until no errors?
       To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

I had capacitors blow up on my nVidia card (7600 series) years ago. But it damaged motherboard & I also replaced power supply just in case. When odd power events occur who knows what the other impacts may be.

You do have good backups?
If not and you can read drives, back up now.

OldFred
THANK YOU for looking in.  My hero strikes again....

No not run check disc.  I can run the live CD and see all the docs etc on all the partitions and drives.  So I know they are there.  I 

Just run the tests and all seem OK.  I am about to reboot to see if anything has changed.

My next option is to copy etc over to my 1Tb backup location and re install...  Unless you have a less brutal method.

---

### Post by Jonners59 on 2017-07-14
OK, update.
I have created a small partition in the backup hard drive (I have 3: 1 for Storage, 1 for backup of storage, 1 for OS and virtual machine directories) and installed a new xUbuntu, and made all config changes and auto-mount changes, blah, blah, blah...  Still got to resolve the directory sharing (SAMBA) always a problem, but otherwise there now.  Just doing an update to 17.04, latest version as I type.


SO:  It seems that there is no apparent HW problem.  This is, as suspected, a system problem, so how do I fix it?

---

### Post by flocculant on 2017-07-14
Did you run the fsck stuff as per oldfred's post?

---

### Post by Jonners59 on 2017-07-15
> **flocculant said:**
> Did you run the fsck stuff as per oldfred's post?
Yes and no errors.

When I boot up I see the text as it loads and I noted a line in RED saying FAILED that may be of interest.
[HTML]FAILED to start load kernel modules[/HTML]

It then carries on and stops at
[HTML]Starting Plymouth boot screen[/HTML]

Thoughts?

I am getting to the point where I am thinking of copying over the directories I have just created to the old, and modifying the fstab and mount points.

---

### Post by oldfred on 2017-07-15
From Boot-Repair's advanced mode, do the total uninstall/reinstall of grub and check to install latest kernel.
If that does not work then full re-install may be required.
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot, only use ppa download into Ubuntu live installer.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by Jonners59 on 2017-07-19
> **oldfred said:**
> From Boot-Repair's advanced mode, do the total uninstall/reinstall of grub and check to install latest kernel.
If that does not work then full re-install may be required.
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot, only use ppa download into Ubuntu live installer.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)
Thanks OldFred
Always have my copy of Boot-Repair.  Great app.  So I tried the full kernel reinstall, but the problem is that the app does not differentiate between the working (temp) install and the broken (trying to repair).  What's more it kept freezing during the process.  So needed to do a little repair job after to get the temp working, and then started to copy directories, though I would like a better way of doing it than opening nautilus in sudo and cutting and pasting!  SO far done USR as it is a separate directory.  Next bits of Home and then the rest: thinking Boot, some from Etc and the img files in root... to start with.

---

### Post by oldfred on 2017-07-19
In advanced options you should be able to select which install to use, and which MBR to install grub2's boot loader into.

---

