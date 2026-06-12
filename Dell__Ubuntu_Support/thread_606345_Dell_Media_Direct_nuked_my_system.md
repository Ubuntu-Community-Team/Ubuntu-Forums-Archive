---
title: "Dell Media Direct nuked my system"
date: 2007-11-07
forum: Dell  Ubuntu Support
---

### Post by vonHumboldtFleischer on 2007-11-07
Hi,

I accidentally pushed the Media Direct button instead of Power on my brand-new xps m1330 and it messed up the boot loader (grub error 17) -- apparently it repartitioned the drive.

Since it's been only 12hrs from a fresh gutsy install, I opted for the easy solution and reinstalled the system; however, I abhor the idea of carrying a "nuke-your-system" button around. 

Any ideas on how to permanently disable it (w/o using concrete)?

Thanks,

vHF

---

### Post by groovete on 2007-11-08
Hi,

perhaps it's only a problem with the bootloader? Did you try to repair grub by using ubuntu in recovery mode?

I repartioned my drive with "gparted", so I got rid of that DellUtility.

---

### Post by vonHumboldtFleischer on 2007-11-08
Hi,

Thanks for your reply.
I booted Ubuntu from LiveCD and tried to mount my hard drive to have a look at it, but I failed:/dev/sda1 was a strange windows-like partition, sda5 was swap and sda2 was unbootable.
OK, now I think I see everything: sda2 must have been bootable, only I was too dumb. Dell Media Direct has probably created one small partition as sda1 and grub tried to boot from there (because it become the first partition). Is this plausible?

The question remains about how to disable the MediaDirect button. I don't fancy verifying my theory the hard way.

vHF

---

### Post by tturrisi on 2007-11-08
> The question remains about how to disable the MediaDirect button. I don't fancy verifying my theory the hard way.
Delete the partition.  The button can only "do something" IF the partition exists.  Rule of thumb is always nuke the Dell hidden partition if have os install cds.  And there may even be a bios setting for it.

---

### Post by vonHumboldtFleischer on 2007-11-08
> **tturrisi said:**
> The button can only "do something" IF the partition exists.  

Are you sure about it? I did a clean install of gusty and when asked by partitioner, I said "use whole disk", so I would expect all strange partitions to have been removed, and yet MediaDirect button did what it did.
 
Right now I seem to have three partitions: sda1 is main, sda5 is swap and sda2 is mbr (this info is according to `disktype'). Do you think this makes me safe from MediaDirect?

Thanks,

vHF

---

### Post by Linicks on 2007-11-08
This post maybe of help here:

[http://www.goodells.net/dellrestore/mediadirect.htm](http://www.goodells.net/dellrestore/mediadirect.htm)

Nick

---

### Post by b4d on 2007-11-08
I pressed media direct again to boot system, and from that boot after I could boot with power button again normally.

---

### Post by vonHumboldtFleischer on 2007-11-08
OK, thanks everyone, I guess I will leave everything as it is ;-)

vHF

---

### Post by drakonte on 2007-11-15
Hi there. Same problem in a Dell XPS M1210, and no: a clean disk will also be damaged by pressing mediadirect button. Apparently, if original partition is missing, this button simply writes on any non-(ntfs or fatXX) partition it finds (some program in rom?), and guess what... yes, neither ext3 nor swap are recognized so they must be useless!!! partition table of extended partitions with alien formats are overwritten with a win95-XX file system. I couldn't recover any linux data after this, so I guess not only partition table is damaged. I would also appreciate info to disable this button.

Thanks in advance       :popcorn:

---

### Post by Lacrimstein on 2007-11-15
open up the laptop, remove the button contact :) kind of drastic, but it works!

---

### Post by keithlommel on 2007-11-18
The Dell Self-Destruct-Direct button will trash your partition table and make the system unbootable even if you get rid of the extra partitions. When I recently installed Gutsy on my laptop, I used a gparted live CD to delete and reformat all partitions on the hard disk. Imagine my surprise then, when I accidentally hit the Self-Destruct button and it rendered my entire system unbootable. Booting with the Gutsy Live CD showed that there were now a couple of new partitions on the hard disk for Dell Utility and MediaDirect -- where did these come from?

The answer is that MediaDirect hides a small chunk of boot code in a hidden partition called a "Host Protected Area" or HPA, which most partition editors (included gparted) cannot see or touch. The button apparently enables this partition for booting, and whatever sloppy code is in there trashes your partition table and/or MBR if it does not find things the way it expects them.

Naturally, I was not pleased with the knowledge that after re-installing everything I'd always have this Sword of Damocles hanging over my head -- one false button press in the dark or a careless nudge in the briefcase and my computer would be rendered inoperable and all the data  only recoverable with significant effort.

Long story short, here's what you can do to erase the code in this hidden partition and render the Self-Destruct button harmless. A word of warning, however. The following command will PERMANENTLY ERASE ALL DATA off your ENTIRE HARD DISK. Only perform the following command after backing up all important data, and in preparation for a fresh, clean install.

Run the following command from a terminal in a live cd (I used my gparted live cd, which conveniently let me create new partitions after everything was wiped.

SECOND WARNING: This command will erase all data on your hard drive:
```
dd if=/dev/zero of=/dev/sda
```
 
After running this and reinstalling your OS, pressing the MediaDirect button will do nothing more than show a special splash screen (stored in BIOS, it seems) before booting to your normal GRUB loader.

Hope it helps.
--Keith

---

### Post by vcallaway on 2007-11-26
Well it happened to me this morning.

I don't know how it was pressed but I came in and had the Dell Media direct logo on the screen and my partitions were gone!

I am REALLY annoyed.

---

### Post by deserthowler on 2007-11-27
I don't know if this will help or not.:confused:

I have a 1420n with Ubuntu pre-installed.  Upon getting the machine and after the first boot, I pushed the media direct button to see what happens.  (I pushed a lot of buttons just to see what would break before I did a lot of work on the system.)

I got the media direct splash screen and the computer went directly into grub.  sda3 is the boot partition and sda6 is root on this machine if that helps.  The first 2 partitions are the Dell test utility and the Dell reinstall utility.

So far I've hit the media direct button by accident a couple of times with no problem. 

Earl

---

### Post by cendant on 2007-11-28
> **keithlommel said:**
> The Dell Self-Destruct-Direct button will trash your partition table and make the system unbootable even if you get rid of the extra partitions. When I recently installed Gutsy on my laptop, I used a gparted live CD to delete and reformat all partitions on the hard disk. Imagine my surprise then, when I accidentally hit the Self-Destruct button and it rendered my entire system unbootable. Booting with the Gutsy Live CD showed that there were now a couple of new partitions on the hard disk for Dell Utility and MediaDirect -- where did these come from?

The answer is that MediaDirect hides a small chunk of boot code in a hidden partition called a "Host Protected Area" or HPA, which most partition editors (included gparted) cannot see or touch. The button apparently enables this partition for booting, and whatever sloppy code is in there trashes your partition table and/or MBR if it does not find things the way it expects them.

Naturally, I was not pleased with the knowledge that after re-installing everything I'd always have this Sword of Damocles hanging over my head -- one false button press in the dark or a careless nudge in the briefcase and my computer would be rendered inoperable and all the data  only recoverable with significant effort.

Long story short, here's what you can do to erase the code in this hidden partition and render the Self-Destruct button harmless. A word of warning, however. The following command will PERMANENTLY ERASE ALL DATA off your ENTIRE HARD DISK. Only perform the following command after backing up all important data, and in preparation for a fresh, clean install.

Run the following command from a terminal in a live cd (I used my gparted live cd, which conveniently let me create new partitions after everything was wiped.

SECOND WARNING: This command will erase all data on your hard drive:
```
dd if=/dev/zero of=/dev/sda
```
 
After running this and reinstalling your OS, pressing the MediaDirect button will do nothing more than show a special splash screen (stored in BIOS, it seems) before booting to your normal GRUB loader.

Hope it helps.
--Keith

Thank you - it worked beatifully

If only Windows is installed, pressing the MediaDirect button boots into Windows

If Linux is installed, pressing the MediaDirect button boots into GRUB

---

### Post by tochi on 2007-11-28
Hi guys,
   I am new to ubuntu. I recently installed ubuntu on my dell 1505. I got everything working except for my wireless. I was told i needed ndiswrapper to get it to work. I downloaded and was installing the application when my computer froze. I had to reboot manually but i am not sure if i hit the media direct button. Anyway, i go reboot and it gets stuck on the screen GRUB loading.. please wait. Error 16. I cant get past that screen. I tried reinstalling from the dvd but it just gives me so many errors and wont let me install it.

I tried using a windows cd to reformat the disk but here is the message i get.

IDE status : failed
Status Byte = 64
Control Code = 1
Msg = No additional sense info.
Error code: 10000-0141
Msg: No drive detected.

What do i do? How do i get my ubuntu back on? Its not a dual boot system just a single ubuntu installation. Thanks

---

### Post by alfredska on 2007-11-28
> **tochi said:**
> What do i do? How do i get my ubuntu back on? Its not a dual boot system just a single ubuntu installation.
Boot from the Ubuntu CD and follow one of the many guides on the net about restoring GRUB.

Or, if you want to start fresh (as you implied when you tried to boot from your Windows CD), boot from the MediaDirect CD and let it partition your drive (and overwrite the MBR) [THIS WILL DESTROY ALL DATA ON YOUR HD].  Then if you plan to have only ubuntu, boot from your Ubuntu disc and go from there.  If you're interested in dual booting, consider referencing a post I recently put up: [here]("http://ubuntuforums.org/showpost.php?p=3855904&postcount=81").

---

### Post by tochi on 2007-11-28
its not letting me boot from either the windows or ubuntu cd.

> **alfredska said:**
> Boot from the Ubuntu CD and follow one of the many guides on the net about restoring GRUB.

Or, if you want to start fresh (as you implied when you tried to boot from your Windows CD), boot from the MediaDirect CD and let it partition your drive (and overwrite the MBR) [THIS WILL DESTROY ALL DATA ON YOUR HD].  Then if you plan to have only ubuntu, boot from your Ubuntu disc and go from there.  If you're interested in dual booting, consider referencing a post I recently put up: [here]("http://ubuntuforums.org/showpost.php?p=3855904&postcount=81").

---

### Post by alfredska on 2007-11-28
> **tochi said:**
> its not letting me boot from either the windows or ubuntu cd.

Are you pressing F12 at the DELL Splash screen to boot from an alternate drive?  You should be.

If the DELL Splash screen isn't showing up: shut down, press media direct button, let it fail.  Shut it down, press power button.

If you cannot boot from the same Ubuntu disc which you originally installed from, it may be scratched/corrupted.  Burn a new copy.

---

### Post by tochi on 2007-11-28
its not the ubuntu disk because it does it with windows too.. i did press f12.. it boots the cd but when i go to start or install ubuntu, thats where the problems start it shows busybox 13... 
buffer I/O error on device sda, logical block 111298329 
buffer I/O error on device sda, logical block 111298330 
buffer I/O error on device sda, logical block 111298331 
buffer I/O error on device sda, logical block 111298332 
buffer I/O error on device sda, logical block 111298333 

then it shows a whole bunch of memory addresses



> **alfredska said:**
> Are you pressing F12 at the DELL Splash screen to boot from an alternate drive?  You should be.

If the DELL Splash screen isn't showing up: shut down, press media direct button, let it fail.  Shut it down, press power button.

If you cannot boot from the same Ubuntu disc which you originally installed from, it may be scratched/corrupted.  Burn a new copy.

---

### Post by alfredska on 2007-11-28
> **tochi said:**
> its not the ubuntu disk because it does it with windows too.. i did press f12.. it boots the cd but when i go to start or install ubuntu, thats where the problems start it shows busybox 13... 
buffer I/O error on device sda, logical block 111298329 
buffer I/O error on device sda, logical block 111298330 
buffer I/O error on device sda, logical block 111298331 
buffer I/O error on device sda, logical block 111298332 
buffer I/O error on device sda, logical block 111298333 

then it shows a whole bunch of memory addresses

I see you've started an entirely new thread.  I'll let you work it out with the other member helping you.

---

### Post by tochi on 2007-11-28
no luck there either... do you mind contributing your ideas in that thread?

> **alfredska said:**
> I see you've started an entirely new 
thread.  I'll let you work it out with the other member helping you.

---

### Post by gerd_m1330 on 2007-12-05
> **cendant said:**
> Thank you - it worked beatifully

If only Windows is installed, pressing the MediaDirect button boots into Windows

If Linux is installed, pressing the MediaDirect button boots into GRUB

Hey there! This is my first post here. Hope you can help me :)

I´ve got two questions:

1) Did you let the "dd"-command finish and how long did it take to overwirite the whole HDD with zero´s?!

2) Wikipedia (and other sources) say: The unix dd command is NOT able to erase the HPA areas of a hard disk!

So, I wonder why it worked out for at least two users of this forum by now!


Anny help appreciated. Btw: I´ve got an M1330 with a 160GH Sata HDD...

---

### Post by MRAB54 on 2007-12-07
I'll chime in with my experiences with this terrible idea that is MediaDirect.  I don't know when or how I pressed the MediaDirect button on my Dell Vostro 1500, I've got a dual boot Ubuntu 7.10/ Win XP pro.  The media direct splash screen showed up when I tried to boot then took me to grub, I tried to boot Windows and it hung at "System starting..."

Restarted, in Ubuntu, my old Windows partition now was not mounted, instead there was a MediaDirect partition but I could still see the actual disk of my old Windows in the device manager.

I shut off, pressed the media direct button, now I know where it is, it gave the splash screen, I choose windows and it booted...  Now I can boot either OS from the normal power button with no problem.

Very frustrating, I don't want this crap on my system but I don't feel like reinstalling everything all over again.  And I'm assuming getting rid of the MediaDirect at this point will render my Windows partition useless.  What a great "feature".

---

### Post by bimargulies on 2007-12-27
Forcing a clean mbr with grub-install seems to prevent the partition-table smashing behavior. I didn't leave the media direct splash up indefinitely to find out, however.

There are a number of posting about how to make this thing due devious dual boots.

---

### Post by bimargulies on 2007-12-27
There are some remarks here which I believe to be counterfactual.

You can't get rid of HPA with the DD command. You can get rid of the MBR. 

I think that the reason that the poster's life got better was because the procedure provoked ubuntu into overwriting the MBR.

If you rewrite the MBR (perhaps with grub-install /dev/sda) you SHOULD have the same effect. Someone should try this.

This leaves the rest of your hard drive alone and eliminates the Dell MBR that is, apparently, a critical part of the self-destruct process.

---

### Post by nealron on 2007-12-28
**[SIZE="3"]I found a fix for the Dell Self-destruct-direct (MediaDirect) button problem.[/SIZE]** 

A little background info might be in order though. What the Dell MediaDirect button (next to the power button and has a house icon on it similar to an internet browsers "Home" button) does when the hard drive is partitioned in a way that it does not expect (aka, linux installed) it rewrites the partition table that it thinks it should have. Your partition table is essentially like the table of contents pages in a book with 100 billion pages, without it your screwed. 

What we're going to do here is offer a way to disable the button if you don't care about the data on the drive (like right after a fresh install) OR a way to recover your partition table with a nifty program called [testdisk]("http://www.cgsecurity.org/wiki/TestDisk").

**[SIZE="3"]Plan A - Disable Destruct Button[/SIZE]**
You can low-level format your hard drive to permanently remove the danger the button poses to your future data, because you _will_ loose ALL data currently on your drive. Issue the following command from a live CD/DVD booted system.

[B][SIZE="2"]****WARNING USE ONLY FROM LIVE CD/DVD******
****WARNING WILL DESTORY ALL DATA ON DISK*******[/SIZE][/B]
```
sudo dd if=/dev/zero of=/dev/sda
```

The above command writes zeros in every sector of your hard drive, aka "Zeroing the drive". Zeroing the drive has been known to overwrite the HPA (Host Protected Area) of the hard drive where the MediaDirect partition is hidden on the drive. Afterwards, pressing the self-destruct button will harmlessly show the MediaDirect splash screen and then boot GRUB.

[_The above came from Skuzniak here_]("http://ubuntuforums.org/showpost.php?p=3870754&postcount=2")

**[SIZE="3"]Plan B - RECOVER YOUR DATA[/SIZE]**.
If you have pressed the dreaded MediaDirect button and now have a very expensive paper weight for a laptop, FEAR NOT! testdisk to the rescue!

1) Boot up your live CD/DVD (like the one you used to install from).

2) Copy the additional repositories to your /etc/apt/sources.list file on your live CD/DVD session. The live CD isn't mean to install packages/programs to since it is erased when your reboot, however, if needed you can install a small amount of extra data. Like repair utilities. You can find instructions on how to do this [HERE]("http://kubuntuguide.org/Gutsy#Add_Extra_Kubuntu_Repositories").

3) Issue the following command to update your repository list after you changed your sources.list file and also install the precious data recovery utility "testdisk", as well as run testdisk after it's installed creating a testdisk.log file of all it's actions in the directory you issue the following command from.
```
sudo apt-get update && sudo apt-get install testdisk && sudo testdisk /log
```

4) Use the arrow keys to select your laptop hard drive. If you are using the live CD/DVD you should see two hard drives. 

**/dev/hda** (the live CD virtual drive) and **/dev/sda** (your laptop hard drive)

To "Proceed", tap the "Enter/Return" key when you've selected the appropriate hard drive.

5) Tap the "Enter/Return" key again on the next screen to select "Intel/PC" partition type.

6) Tap the "Enter/Return" key again on the next screen to "Analyse" (spelled the way it is in the program) your hard disk and search for your lost partitions.

7) This screen shows the screwed up partition table.. just tap the "Enter/Return" key again to "Proceed"

8) If you're lucky you'll see two or three partitions (If you let Ubuntu install configure your disk for you). Something like what you see below:
```
* Linux 0 1 1 18752 254 63 301266882
L Linux Swap 18753 0 1 19456 254 63 11309760
```
Tap the "Enter/Return" key again to "Proceed"

9) Now tap the right arrow key twice and tap the "Enter/Return" key to write the recovered partition table. Confirm it by taping the "Y" key and then the "Enter/Return" key.

10) Reboot your computer and take the live CD/DVD out. :)

NOTE: I had to do this twice for it to work for some reason, but after that, my precious Kubuntu booted up normal just like it used to without one file missing!

THANK YOU [_NICOLAE_]("http://ubuntuforums.org/showpost.php?p=3878125&postcount=7") and [_PSEUDOMANCER_]("http://ubuntuforums.org/showpost.php?p=3885747&postcount=8")!

---

### Post by abrahm on 2007-12-30
I would like to thank nealron for making my recovery process so easy! His instructions worked well.

I'm _very_ happy that I didn't lose weeks of coding.

---

### Post by meateater on 2007-12-30
you guys might want to try this guide on how to boot a linux distro using media direct
[http://forum.notebookreview.com/showthread.php?t=182495](http://forum.notebookreview.com/showthread.php?t=182495)

this involves using the executable to edit the mbr from the media direct cd.

I haven't had the chance to try this out as my laptop has not arrived yet. 

But if this works, then we do not need to overwrite the HPA.

---

### Post by rhonaldmoses on 2008-01-07
Check out the article on [http://linuxevangelist.blogspot.com/2007/10/dual-boot-in-dell-xps-m1330-with.html](http://linuxevangelist.blogspot.com/2007/10/dual-boot-in-dell-xps-m1330-with.html) for using MediaDirect safely with Windows & Ubuntu dual boot.

---

### Post by yesint on 2008-01-08
It was a surprice for me that there is such hidden thing as HPA on my hard drive. 
Is it possible spmehow to get rid of HPA completely (not just disable the destructive behavior of MD)?

---

### Post by rhonaldmoses on 2008-02-02
Hi [nealron]("http://ubuntu.ubuntuforums.org/member.php?u=464224"),

Your suggestion to zero the drive didn't work out for me as I tried that (the command didnt give any output nor return the control back to the terminal and leaving the command run for almost 3 hours, i closed the terminal) by issuing it first, leave it for 3 hours, come back, install windows, shut down, press the MediaDirect butto which erased the partition as before.

Now I am going to re-install the whole laptop again. I desperately want to remove windows, but there seems to be no working way to make MediaDirect button stop doing anything.

Anyway, I can't experiment right now since I have deadlines on my work so I better do the known way.

---

### Post by Chua-Chua on 2008-02-04
Hrmmm...I just found out about this the hard way.

Previously on my new 1420 laptop::
-45GB FAT32 partition containing torrents, files for both linux/windows
-35GB reiserfs mounted as /
-22GB unformatted for windows install (i will do it when i have free time)


Now:
-1GB mediadirect NTFS partition
-35GB reiser
-22GB unformatted


The mediadirect overwrote and repartitioned my hard drive, taking out the FAT32 partition. It left my 22GB unformatted free space alone, though.

I'm PISSED about this, because the 45GB partition had backup files like drivers and i use it to store files that can be read by both the linux and windows partitions.

GOOD JOB, DELL!
Dell's not getting my recommendations anymore.

So sorry for the rant.
~C-C

---

### Post by RetiredInMaine on 2008-02-06
I found this thread while browsing the Dell Ubuntu forum. I have a Dell Inspiron 1420 laptop as my travel machine so I read through it. Mine came with Ubuntu 7.04 preinstalled. But I have a (probably) dumb question. What is a "media direct" button and where is it?  I don't want to experiment and wreak my machine .

---

### Post by RetiredInMaine on 2008-02-06
I apologise to all for my prior post. All I had to do was read the manual. My fingers were faster than my brain cells.

Prior to reading the manual I thought the button was to bring up my home page on a browser (it is a home icon) and would only work in windows. When I tied it out it did not destroy my system but I thought that under Linux it was reconfigured. Anyway for what it's worth it did not destroy my system when I tried it out, maybe because Linux was preinstalled.

---

### Post by PsychedelicReaction on 2008-02-06
noob question: maybe if someone make an image (i.e. with clonezilla) of the media direct partition from an ubuntu preinstalled we could replace it to the windows-compatible one?

---

### Post by moleculeman on 2008-02-07
This just happened to me. I'll make sure I'm awake before I try and boot in future!

Thanks to nealron. The solution he posted worked (heavens be praised). I had horrific visions of losing everything from the last 3 months.

The media direct button is a little piece of insanity.

---

### Post by baxeico on 2008-02-18
This is my case:

- I completely removed all visible partition with Kubuntu installer, then installed Kubuntu as usual.
- I pressed accidentally the "media direct" button.
- Media direct tries to start, but then it complains of not finding a disk (of course, I formatted everything!) and then it turns off.
- If i try to boot normally (with the "power on" button), grub gives an "error 17".
- I boot again using "media direct" button.
- I see media direct splash screen, but then I see grub messages, and Kubuntu boots normally.
- After this I can again boot Kubuntu normally with "power on" button.

I cannot explain why this happens to me!!!

But _for me_ the easy solution is:
If you press media "direct button" accidentally, the only thing you have to do is to wait media direct turn off complaining, and then to press "media direct" button again. :)

Someone can reproduce this? Someone understands WHY this happens?

---

### Post by seaq on 2008-02-24
Yes i can reproduce that behaviour, let the media button do it's thingy let it turn it off and then push it again. it would solve the Grub 17 problem by itself.

However it seems that it really could destroy your system, at least your partition table. In my specific case with 2 diferent systems it created an sda1 partition with 2G at the end of the disk, in both systems i could restore by pushing the button again or manually reconstructing the partition table.

But i'm a bit confused because i could swear that some months ago i tested that button on poweron and it didn't do any damage.. but now it trashed a new system. anyway I'm  making some research i want to put a geekbox instead of MD...

---

### Post by new2GNU on 2008-02-29
> **nealron said:**
> **[SIZE="3"]I found a fix for the Dell Self-destruct-direct (MediaDirect) button problem.[/SIZE]** 

A little background info might be in order though. What the Dell MediaDirect button (next to the power button and has a house icon on it similar to an internet browsers "Home" button) does when the hard drive is partitioned in a way that it does not expect (aka, linux installed) it rewrites the partition table that it thinks it should have. Your partition table is essentially like the table of contents pages in a book with 100 billion pages, without it your screwed. 

What we're going to do here is offer a way to disable the button if you don't care about the data on the drive (like right after a fresh install) OR a way to recover your partition table with a nifty program called [testdisk]("http://www.cgsecurity.org/wiki/TestDisk").

**[SIZE="3"]Plan A - Disable Destruct Button[/SIZE]**
You can low-level format your hard drive to permanently remove the danger the button poses to your future data, because you _will_ loose ALL data currently on your drive. Issue the following command from a live CD/DVD booted system.

[B][SIZE="2"]****WARNING USE ONLY FROM LIVE CD/DVD******
****WARNING WILL DESTORY ALL DATA ON DISK*******[/SIZE][/B]
```
sudo dd if=/dev/zero of=/dev/sda
```

The above command writes zeros in every sector of your hard drive, aka "Zeroing the drive". Zeroing the drive has been known to overwrite the HPA (Host Protected Area) of the hard drive where the MediaDirect partition is hidden on the drive. Afterwards, pressing the self-destruct button will harmlessly show the MediaDirect splash screen and then boot GRUB.

[_The above came from Skuzniak here_]("http://ubuntuforums.org/showpost.php?p=3870754&postcount=2")

**[SIZE="3"]Plan B - RECOVER YOUR DATA[/SIZE]**.
If you have pressed the dreaded MediaDirect button and now have a very expensive paper weight for a laptop, FEAR NOT! testdisk to the rescue!

1) Boot up your live CD/DVD (like the one you used to install from).

2) Copy the additional repositories to your /etc/apt/sources.list file on your live CD/DVD session. The live CD isn't mean to install packages/programs to since it is erased when your reboot, however, if needed you can install a small amount of extra data. Like repair utilities. You can find instructions on how to do this [HERE]("http://kubuntuguide.org/Gutsy#Add_Extra_Kubuntu_Repositories").

3) Issue the following command to update your repository list after you changed your sources.list file and also install the precious data recovery utility "testdisk", as well as run testdisk after it's installed creating a testdisk.log file of all it's actions in the directory you issue the following command from.
```
sudo apt-get update && sudo apt-get install testdisk && sudo testdisk /log
```

4) Use the arrow keys to select your laptop hard drive. If you are using the live CD/DVD you should see two hard drives. 

**/dev/hda** (the live CD virtual drive) and **/dev/sda** (your laptop hard drive)

To "Proceed", tap the "Enter/Return" key when you've selected the appropriate hard drive.

5) Tap the "Enter/Return" key again on the next screen to select "Intel/PC" partition type.

6) Tap the "Enter/Return" key again on the next screen to "Analyse" (spelled the way it is in the program) your hard disk and search for your lost partitions.

7) This screen shows the screwed up partition table.. just tap the "Enter/Return" key again to "Proceed"

8) If you're lucky you'll see two or three partitions (If you let Ubuntu install configure your disk for you). Something like what you see below:
```
* Linux 0 1 1 18752 254 63 301266882
L Linux Swap 18753 0 1 19456 254 63 11309760
```
Tap the "Enter/Return" key again to "Proceed"

9) Now tap the right arrow key twice and tap the "Enter/Return" key to write the recovered partition table. Confirm it by taping the "Y" key and then the "Enter/Return" key.

10) Reboot your computer and take the live CD/DVD out. :)

NOTE: I had to do this twice for it to work for some reason, but after that, my precious Kubuntu booted up normal just like it used to without one file missing!

THANK YOU [_NICOLAE_]("http://ubuntuforums.org/showpost.php?p=3878125&postcount=7") and [_PSEUDOMANCER_]("http://ubuntuforums.org/showpost.php?p=3885747&postcount=8")!


THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU!

It worked like a charm, exactly as you described it. I was back up and running in 10 minutes. It is frustrating that this can happen at any time but at least I know there is an easy solution to resolve it.

---

### Post by gtspaulding on 2008-03-06
The (undocumented) fix for the self-destruct button is found in a program called RMBR found on the Media Direct Reinstall CD.  It's best run in a DOS environment (boot up from the MD CD and then quit).

Syntax:  RMBR DELL [partition to use for power button] [partition to use for Media Direct button]

eg RMBR DELL 3 1 will cause the power button to boot partition 3 and the Media Direct button to boot partition 1.  I guess these settings are saved in NVR somewhere.  The process appears to be non-destructive.

Note that the Media Direct button will always display a splash screen.

Your partition table will only get trashed if the partition set up for the Media Direct button is not a bootable one.

Why Dell don't tell people this is a mystery.

---

### Post by orangek3nny on 2008-03-06
> **gtspaulding said:**
> The (undocumented) fix for the self-destruct button is found in a program called RMBR found on the Media Direct Reinstall CD.  It's best run in a DOS environment (boot up from the MD CD and then quit).

Syntax:  RMBR DELL [partition to use for power button] [partition to use for Media Direct button]

eg RMBR DELL 3 1 will cause the power button to boot partition 3 and the Media Direct button to boot partition 1.  I guess these settings are saved in NVR somewhere.  The process appears to be non-destructive.

Note that the Media Direct button will always display a splash screen.

Your partition table will only get trashed if the partition set up for the Media Direct button is not a bootable one.

Why Dell don't tell people this is a mystery.

Thanks for the small guide, this is exactly what i need!

When i start rmbr.exe though, it tells me that the possible values are 1,2,3,4. Does that mean if you have got MediaDirect (or any other OS) on partition nr.5, it will not work?

---

### Post by gtspaulding on 2008-03-09
There are four possible primary partitions on a disk; as far as I knowm rmbr can only boot from one of those primary partitions, not from any extended ones.  You could experiment, but be prepared for it to trash the partition table,

---

### Post by knic on 2008-03-09
I confirm: **DO NOT EXPERIMENT "rmbr"** command **on an extended partition**, it will crash your whole filesystem leaving you with a blank hardrive without the possibility to restore anything.
I tryed to assign this f...g button to my kubuntu grub which was on the sda5 (primary partition on the sda3 extended partition) and this blasted a one full day work over my xps1530 laptop! fortunately there was no sensitive datas, just a wonderful system working perfectly with all the drivers and personnal setups :(
I am now trying to map my drive differently.

what I had before the crash:
sda1: NTFS (XP) 40GB
sda2: FAT32 (recovery images) 10GB
sda3: Extended
---sda5: EXT3 (Kubuntu) 20GB
---sda6: SWAP (swap) 4GB
---sda7: EXT3 (geexbox) 50MB
sda4: FAT32 (shared partition) 40GB
at this point the triple boot was working perfectly using grub.

What I did with rmbr.exe and which screwed my drive:
"rmbr DELL 1 5"... burp!! didn't like it... :mad:

I am now trying:
sda1: NTFS (XP) 40GB
sda2: EXT3 (geexbox) 50MB
sda3: Extended
---sda5: EXT3 (Kubuntu) 20GB
---sda6: SWAP (swap) 4GB
---sda7: FAT32 (recovery images) 10GB
sda4: FAT32 (shared partition) 40GB

in such case, and if "rmbr DELL 1 2" command works, I will have the windows bootloader pointing on the ubuntu grub menu when pressing the power button, and the geexbox media player when pressing the mediadirect button which is not that bad finally.

I originaly wanted to start windows from the power button, and all other OS with mediadirect button leading to the grub's list, which is doable if considering the primary partitions assignement with mediadirect button and a correct partition map, but the 4 primary limitation is not really helpful with my disk partitioning method.

If anyone has an idea to make things more flexible, I will be glad to have some feedback. :KS

---

### Post by knic on 2008-03-09
hi! I just tryed this new drive map with XP on sda1 and geexbox on sda2 and the "rmbr 1 2" worked fine. I now have XP on power button, and geexbox on mediadirect button. I need now to reinstall all xp drivers and kubuntu. cheers!!!

---

### Post by knic on 2008-03-11
Hi,
as stated in my previous post, "rmbr 1 2" command did work using dell mediadirect 3.3 install disc on an xps1530 with xpsp2 installed on sda1 and geexbox on sda2. This did not hurt the drive nor additionnal extended partitions (up to sda7).
I finally reinstalled kubuntu on sda5 (swap on sda6) and the restore partition on sda7.
This restore partition includes bootable PING backup and recovery tool with sda1 (xp), sda4 (shared datas) and sda5 (linux) compressed partition images. sda7 was formatted in ext3 to prevent writtings from windose.
some lines were added in the linux grub to choose between linux, windows, geexbox or ping restore process, this allowing a fast embedded restoration without the need for external sources like CDs, DVDs or usb drives.
Now considering the space lost on the hard drive and probably very little use of sda7, I am thinking about backing up system partitions on DVDs which is not as hard to carry when travelling, and leaves 10GB free space for the data partition or even system files. In such case, sda7 will be removed and other partitions extended to fill the gap.

Conclusion:
the dell rmbr tool just writes some bytes in the hard drive's mbr to assign power and mediadirect buttons on selected primary partitions (switching 1 to 4), whatever these partitions datas are (bootable or not). the rmbr process does not destroy datas if applied on the four primary partitions only, it can be launched before or after the system install when run in dos mode after partitionning the drive, but I suggest to do it before setting up the whole system in case of a wrong partition switch.
Finally, this mediadirect button is useful as it can be used to launch any OS, could be xp, vista, linux, geexbox, mediadirect, gparted or any bootable tool installed on the harddrive.
hope my story helped you in your quest.
cheers! :popcorn:

---

### Post by daw3b on 2008-03-11
hi all, please let me understand if my only choice is a suicide...
I've just bought a Dell Inspiron 1525 and without know this huge issue
of the autodistructive button I leave factory partitions except for
the extended one with three logical inside I created between the
Vista-one and the Media Direct one, so now I have (if I remember well):

primary hidden dell utility partition
primary dell recovery partition
primary vista partition
extended ubuntu with
-logical \
-swap
-\home
-media trash directly partition

how many things could I do except cry?
is there some software more stable than gparted to move md partition
before the extended one so I can use rmbr from Dell?

---

### Post by daw3b on 2008-03-11
> **knic said:**
> I confirm: **DO NOT EXPERIMENT "rmbr"** 
---sda7: EXT3 (geexbox) 50MB


Hi, just for curiosity... does the tv out works with geexbox?
I could resize Vista and create 50 mb partition and then associate
the button to geexbox to solve my above problem

---

### Post by lrich28 on 2008-03-11
So I have an 8 month old Inspiron 1420n that came with vista.  I have since reformatted and now have XP on one partition, a swap partition, and an Ubuntu partition.  I have never heard of this until now.  I do have a media direct button, and I just discovered that when I press it in Ubuntu it starts Rhythm Box.  I don't know why.  I have formatted the drive about three times.  Could there be any harm?

---

### Post by GrandpaLeaman on 2008-03-15
I'm a little confused as many of the posters above do not clarify whether they are talking about a single or dual boot configuration. I can infer in many instances that the individual is running either one or the other. But since they don't say this, I fear I may misunderstand and later have problems with the MediaDirect button.

I have a Dell Inspiron E1505/6400 which I purchased pre-installed with Vista. After discovering Ubuntu I decided to reformat my entire HD and install it as my only OS. Now I understand that I still have a hidden partition on the HD with MediaDirect installed on it and that if I punch that button all hell could break loose. And yet I see some posts that say all they had to do was to wait for MediaDirect to error out and then push the button again and it will fix itself. I just need clarification on a few issues and then I will know what to do in case someone, like my granddaughter, were to punch this button.[LIST]
[*]If you are running a single boot configuration, was it pre-installed by Dell or by you?
[*]Did the problem arise from mashing the button to start up the computer?
[*]What happens when you hit this button while Ubuntu is running?[/LIST]I have never touched this button, even in the short period in which I had Vista, so I have never had any problems. But young fingers are curious and I would like to be able to recover from any possible  mis-steps in the future.

---

### Post by baxeico on 2008-03-17
> **GrandpaLeaman said:**
> 
[LIST]
[*]If you are running a single boot configuration, was it pre-installed by Dell or by you?
[*]Did the problem arise from mashing the button to start up the computer?
[*]What happens when you hit this button while Ubuntu is running?[/LIST]I have never touched this button, even in the short period in which I had Vista, so I have never had any problems. But young fingers are curious and I would like to be able to recover from any possible  mis-steps in the future.

[LIST]
[*]I'm running a single boot Kubuntu installed by me
[*]Yes, if I press the button to start the computer, something bad happens to the partition table, but if I turn off and turn on again with the evil button, everything is ok again!
[*]I associated the button (which has an home icon on it) to my home folder. So when I hit the button while Kubuntu is running, the file manager shows my home dir.
[/LIST]

---

### Post by GrandpaLeaman on 2008-03-18
> **baxeico said:**
> [LIST]
[*]I'm running a single boot Kubuntu installed by me
[*]Yes, if I press the button to start the computer, something bad happens to the partition table, but if I turn off and turn on again with the evil button, everything is ok again!
[*]I associated the button (which has an home icon on it) to my home folder. So when I hit the button while Kubuntu is running, the file manager shows my home dir.[/LIST]
Wow, that's great! Can you teach me how to do that last item? I'm running Ubuntu Gutsy. Will the process be pretty much the same? I would appreciate any help you can give me!

---

### Post by baxeico on 2008-03-20
> **GrandpaLeaman said:**
> Wow, that's great! Can you teach me how to do that last item? I'm running Ubuntu Gutsy. Will the process be pretty much the same? I would appreciate any help you can give me!

In KDE is quite trivial. I have an "Home folder" entry in KDE launch menu, and I can associate a keyboard shortcut to it.

When I've to choose which button associate to the menu entry, I simply press the "evil" home button on the laptop. The button code appears to me as: XF86AudioMedia.

I'm sure that in Gnome there is a similar simple procedure to assign a keyboard shortcut to the home folder, but I'm not a Gnome user.

---

### Post by sdennie on 2008-03-20
For me the Key of Death actually brings up Rythmbox when the machine is booted.  I don't recall making that change but, it's possible that I did.  Navigating to System->Preferences->Keyboard Shortcuts shows that the media player is mapped to 0xed so I assume that's what the key identifies itself as.  The key generally makes me quite nervous but, it seems that it can be safely remapped to do useful things while the machine is booted.

---

### Post by buzz91 on 2008-03-29
Hello,

after I hit the self-destruct button today I read all the things and I'm really angry about DELLs self-destruct button. Well but fortunately I figured out the problem before I format my old PC.

So in the moment I'm Zeroing my harddrive ... 1 3/4 hours gone :mad:

And then I want to Install Vista on a 25GB-partition and Ubuntu etc, aftwrwards. So that i can boot Ubuntu and Vista with GRUB.

Is the problem with the MediaDirect-Button after Zeroing really gone? I hope so ... I'm really unhappy ... hours of time wasting ith such a sh**

And when its gone both Buttons will Boot up normally GRUB and nothing wil happen to my Partitions?

gretz

P.S.: Is there a way to make GRUB check, wether the FLAG of the MediaDirect-Button is set? Then for example GRUB could check wether the Flag is that and if do it could wait only 1sec instead of normally 5secs or something like this?

---

### Post by marteus on 2008-04-09
I just wiped the whole boot sector with dd if=/dev/zero of=/dev/sda bs=512 count=1 before installing (the partition table was wiped too, but I didn't want the preloaded stuff anyway). It took less than a second.

Now Button of Doom harmlessly calls grub.

---

### Post by argoo on 2008-04-11
[http://www.goodells.net/dellrestore/hpa-issues.htm]("http://www.goodells.net/dellrestore/hpa-issues.htm")

According to the Dell MBR description on the site above, it should be possible to wipe the mediadirect code from the drive w/o destroying all the HD's data or the MBR.  These cmds should do the trick, but I haven't tested them.  The cmds must be run on the live CD of your choice.  Please note, according to the site, these cmds should only be used on mediadirect versions 1 and 2.  I have version 3 so I will never be able to test this. :)

Backup sector 4 (LBA 3 = sector 4):
dd if=/dev/sda of=<filename> bs=512 count=1 skip=3

Clear sector 4 (LBA 3 = sector 4):
dd if=/dev/zero of=/dev/sda bs=512 count=1 seek=3 conv=notrunc

---

### Post by baxeico on 2008-05-07
Hi, I'm tryng to use RMBR.exe tool to remap the media direct button to GEEXBOX.

I booted from the media direct reinstallation CD provided by DELL, the label of CD says: "For reinstalling mediadirect 3.5 on dell XPS computers".
After boot I have three choices: 1, 2 and Q. Of course I choose Q (Quit) because I do not want to reinstall media dircet or change partition table in any way.

Then I get a DOS prompt A:, but I can't find RMBR.exe tool. Loading the CD in Kubuntu, I saw that RMBR.exe is in dellkit/ folder in the CD, but when I booted from the CD itself that folder is not present under A: neither C:, I tried also D: (E:, and so on), but those devices are not available.

Can someone precisely explain me how to use RMBR.exe booting from media direct reinstall CD?

---

### Post by mgc8 on 2008-05-12
It seems there are different versions of the software installed on various machines (or maybe just various behaviours of the same program? maybe differences between MD 2.x, 3.3, 3.5) -- I have a new XPS m1530 and it came with the usual partitions (Dell Utility, etc.) which I promptly erased and installed Linux before reading about this. Fortunately, I left a small NTFS partition for win* as the first one, and when I pressed the MD button (out of curiosity, really) it mangled that one but left the rest alone. It showed the splash screen and screeched the HDD for a while before erroring out, but afterwards grub loaded just fine (Linux on /dev/sda2). Fdisk revealed that /dev/sda1 was erased and replaced by a large FAT32 partition that was overlapping the other ones, fortunately not much was written to it... This is strange since I did clean the /dev/sda1 partition with "dd if=/dev/zero" beforehand, so the code must have come from somewhere else (BIOS?! MBR? some fixed location on disk?)

I also am unable to use RMBR.exe, because in their extreme benevolence, Dell removed the EXTCD.SYS driver from the MD boot CD (the blue one) so it is unable to mount itself (it only mounts a ramdisk as C, but no CD -- you can see the driver line commented out in config.sys). It would be useless anyway I think because I tried copying the rmbr.exe file from /dellkit to a FreeDOS USB stick, and it barfed with "This program cannot be run in DOS mode" -- meaning it's probably a win* application.

So from what I can infer right now, in order to kill the button one needs to have a win* install to run rmbr.exe from, right? I'll get around to doing that soon, hopefully I don't kill it by pressing the button too soon. Frankly I believe the engineer(s) resposible for such a fiasco should be fired (or at least demoted to chair-movers).

Best regards,
Mihnea

---

### Post by TimDaniels on 2008-05-24
> **knic said:**
> I confirm: **DO NOT EXPERIMENT "rmbr"** command **on an extended partition**, it will crash your whole filesystem leaving you with a blank hardrive without the possibility to restore anything.
I tryed to assign this f...g button to my kubuntu grub which was on the sda5 (primary partition on the sda3 extended partition) and this blasted a one full day work over my xps1530 laptop! [.....]

what I had before the crash:

sda1: NTFS (XP) 40GB
sda2: FAT32 (recovery images) 10GB
sda3: Extended
---sda5: EXT3 (Kubuntu) 20GB
---sda6: SWAP (swap) 4GB
---sda7: EXT3 (geexbox) 50MB
sda4: FAT32 (shared partition) 40GB

at this point the triple boot was working perfectly using grub.

What I did with rmbr.exe and which screwed my drive:
"rmbr DELL 1 5"... burp!! didn't like it... :mad:


I suspect that "rmbr DELL 1 5" set the MediaDirect button for the SWAP partition.  Remember that the MediaDirect partition is a logical drive in an Extended partition, so it isn't required to be a Primary partition.  And since rmbr is a command for a DOS environment, it probably follows Microsoft's method for numbering partitions - first the Primary partitions, then the logical drives - excluding (unlike Linux) the Extended partition.  So for rmbr in the above partition order:
"1" => sda1 1st Primary (Windows XP),
"2" => sda2 2nd Primary (recovery images),
"3" => sda4 3rd Primary (shared),
"4" => sda5 1st logical (Kubuntu),
"5" => sda6 2nd logical (Swap)
"6" => sda7 3rd logical (GeexBox).

In other words, when you pressed the "House" button, control was passed to the Swap file.  Wanna test it for us?  :-)

TimDaniels

---

### Post by TimDaniels on 2008-05-25
Ooops.  I just read the "rmbr /?" output from running the MediaDirect reinstallation DVD on my XP system, and it says that the permissable values for the 2nd and 3rd arguments are 1,2,3 and 4.  This is puzzling because the 4th partition on my laptop's hard drive is an Extended partition with just one logical drive that contains MediaDirect.  Apparently, the MD button doesn't distinguish between Primary and Extended partitions, and it seems to expect that if MediaDirect is in an Extended partition, it will be in the first logical drive in that partition.

TimDaniels

---

### Post by happy-and-lost on 2008-05-26
I've just ordered a 1525, [http://www.goodells.net/dellrestore/mediadirect.htm](http://www.goodells.net/dellrestore/mediadirect.htm) says that MediaDirect 3 won't kill your partition table. Does anyone happen to know if recently built Dells come with MD2 or MD3?  No use in blanking my new drive if there's no danger. ;)

---

### Post by TimDaniels on 2008-05-26
> **happy-and-lost said:**
> Does anyone happen to know if recently built Dells come with MD2 or MD3?

My XPS M1330, ordered in early February, came with MediaDirect 3.5 .  It makes the system very inflexible and fragile.  If it gets hosed for some reason, reinstallation of MediaDirect requires wiping the entire hard drive and using the MediaDirect reinstallation CD to re-partition the hard drive.  Then one has to reinstall Vista, and THEN one can reinstall MediaDirect.  Don't expect Dell Tech Support to know any more than that about MediaDirect.

The MediaDirect partition (which is really a logical partition within an Extended partition - contrary to Vista's Disk Management) makes installing Linux or any other OS very difficult if you intend to keep the MediaDirect functionality.  If you intend to do any dual-booting, I advise you to just save yourself the headache and get rid of MediaDirect.

TimDaniels

---

### Post by TimDaniels on 2008-05-27
I've been experimenting with my MediaDirect re-installation disk today, and  I ran rmbr from the disk's DellKit folder using the command prompt window in Vista's Repair Environment.  I found that the 2nd and 3rd args of rmbr set the "active" flag in the indicated partitions when the Power button and the MD button were pressed, respectively.  This was regardless of whether the partition was Primary or Extended.  Apparently, something puts a boot record in the Extended partition in the same way that a boot record is put in a Primary partition, and the MBR passes control to it when the MD button is pressed.  Whether the boot record knows which logical partition the MediaDirect loader is or whether it just assumes it's in the 1st logical partition, I don't know.

But I also accidentally hosed out all the partitions except for the Vista partition.  I tried running the MediaDirect re-installation disk from within Vista - just as one is supposed to in the normal 3-step re-installation process - but without steps 1 and 2 which involve wiping the hard drive and re-installing Vista.  Now the only partition with a name, a file system, and contents is the Vista partition.  In other words, the MediaDirect re-installation disk nuked 'em.  Praise Dell.

TimDaniels

---

### Post by TimDaniels on 2008-05-28
New Version 4.0 of MediaDirect

People have apparently given Dell so much negative feedback
about having to wipe out the hard drive and having to re-
install Windows in the process of re-installing MediaDirect,
that Dell has a new MediaDirect - version 4.0 - that runs
under Vista as an application.  By pressing the "house" button,
Vista will load and run without asking for a password, and
MediaDirect will startup automatically as an application.
That sounds like a security hole to me, but Dell (or Cyberlink,
the creator) apparently thinks it will be more acceptable -
or less obnoxiaous - to users than the current "embedded OS"
kludge that causes so much pain.  If you're a recent buyer of
a laptop that has MediaDirect, you can ask (or pester) Dell
for a free MediaDirect 4.0 installation CD.

By making MediaDirect an application running under Vista, one
should be able to keep the MediaDirect functionality while
still being able to create multiple partitions for Linux by
making multiple "logical drives" within an Extended partition.

TimDaniels

---

### Post by kamiokande on 2008-06-13
Does this problem only crop up with dual boot systems? I have an XPS m1330 pre-installed (by Dell) with Ubuntu, and I was wondering if I should be aware of this problem. Thanks!

---

### Post by TimDaniels on 2008-06-20
> **kamiokande said:**
> Does this problem only crop up with dual boot systems? I have an XPS m1330 pre-installed (by Dell) with Ubuntu, and I was wondering if I should be aware of this problem. Thanks!

I'm not sure which problem you mean.  Since the Ubuntu-loaded laptops don't have MediaDirect, there is no contention for partitions between MediaDirect and any other OS which may be added as a dual-boot OS.  (But if your Ubuntu laptop DOES have MediaDirect, please let me know.)  :-)

TimDaniels

---

### Post by TimDaniels on 2008-06-20
> **TimDaniels said:**
> Dell has a new MediaDirect - version 4.0 - that runs under Vista as an application.

As of yesterday, June 18, Dell was still beta testing version 4.0 of MediaDirect.  There was no estimate on when it will be out of beta test, and no one that I've been able to speak with at Dell knows how it will work.  Way to go, Dell!

TimDaniels

---

