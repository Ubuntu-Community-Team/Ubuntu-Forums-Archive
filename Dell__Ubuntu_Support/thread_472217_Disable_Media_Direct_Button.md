---
title: "Disable Media Direct Button?"
date: 2007-06-12
forum: Dell  Ubuntu Support
---

### Post by rwfilice on 2007-06-12
I have a Dell 640m which I got just before Dell started offering Ubuntu - wiped out everything on the hard drive including Media Direct, and installed Ubuntu.  Everything worked great - but when I accidentally press the Media Direct button when the computer is off, it still tries to start the Media Direct software and then crashes - kind of annoying.

Is there a way to disable that button or change what it does?

thanks.

---

### Post by angryfirelord on 2007-06-20
Not sure how to do that, but you can fiddle with the settings in System-->Preferences-->Keyboard Shortcuts

---

### Post by NBGeekGuy on 2007-06-20
Comments removed

---

### Post by HotShotDJ on 2007-06-20
> **NBGeekGuy said:**
> What would be really interesting to see is if the Linux community can write a driver that allows this button to function and open a Linux media center such as MythTV.If your employer will release the specifications and protocols (perhaps they have already?) then the Linux community would have drivers in short order.

---

### Post by nickless on 2007-06-21
I think I pushed the button last night :D
It was kind of dark so I am not 100% shure, but I saw the dell Media Direct Loading Screen, but after that Ubuntu booted as usual, so I guess it doesn't matter? :D
As well I guess one could install windows on a partition again and reinstall DellMediaDirect via the recovery disk to get it to work correctly again. Never tried it thought, because I don't use this feature :)

EDIT: Found this thread just now, [Dual boot vista with ubuntu + mediadirect + restore files]("http://ubuntuforums.org/showthread.php?t=469370")

---

### Post by neptho on 2007-06-21
As a person who is not a Dell Employee, but someone who's had his trusty 6400 for nearly a year, I can tell you:

[list][*] The MediaDirect Button is hardwired to the system.  What happens is: You press the button,
[*] The machine begins to boot, with a flag set in BIOS,
[*] machine boots, with *a custom bootloader with MD3*, which tests for this BIOS flag, and
[*] chains to the FAT32 partition (relabeled and hidden with both MD2 and MD3),
[*] loading a minimal version of XP, which opens directly into the MD software interface.[/list]

Basically, if you want to get rid of it, the easiest way is to rebuild your system's MBR.  If you are using Vista or XP, you can do this from booting from your install CD, loading to 'Repair' mode, and running 'fixmbr'.  If you are using Grub, you still have remnants of this partition (load fdisk and look at the tags by pressing 'p': )

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7        1312    10490445   83  Linux
/dev/sda3            1313        1513     1614532+  82  Linux swap / Solaris
/dev/sda4            1514       12161    85530060   83  Linux
```

Note that Dell Utility is *NOT* the MediaDirect software.  It's the BIOS 'Diagnostics' partition.

I've bound mine (in Linux) to load Totem.  :)

---

### Post by mike999999 on 2007-06-21
That media direct button can also give you a grub error 17 if you use it to boot, the error goes away if you use it a second time. :?

---

### Post by Artemis3 on 2007-08-03
I have two of these machines Inspiron (640m). Using Debian Etch, if the machine is suspended when you open the lid (and accidentally touch the too close buttons) you will see a mysterious "Media Direct" screen, by the time you see this, the machine has modified the partition table and grub fails to boot with error 17.

This is seriously annoying to say the least...
I'm doing tests with ubuntu now.

---

### Post by Artemis3 on 2007-08-03
With kubuntu pushing the buttons made grub report error 24, rebooting starts a test suite.

This was on a fresh install consisting of 2 partitions: 1 for the system (/dev/sda1) another for swap (/dev/sda6)

Now the disk has an additional fat32 partition at the end of the disk, type c (fat32), but the partition table is rearranged to make this partition /dev/sda1 with the bootable flag.

Funny how Dell put an easy system disabling button in front where you can accidentally touch it; ¡Do not suspend/hibernate!

BTW: if you push the button while the system is on, it does load amarok etc. The danger is pushing the button when the system is sleeping, you know, like, when carrying the machine with the lid closed...

Now ill try installing leaving the fat32 partition intact to see if at least an easier recovery is possible...

---

### Post by Artemis3 on 2007-08-16
To avoid the temptation (or accident) i disabled suspend/hibernate in gnome using this guide: [http://jeremy.sunriseroad.net/2007/02/how-to-disable-suspend-and-hibernate-for-all-users-in-ubuntu/](http://jeremy.sunriseroad.net/2007/02/how-to-disable-suspend-and-hibernate-for-all-users-in-ubuntu/)

---

### Post by mike999999 on 2007-08-16
[QUOTE=NBGeekGuy]What would be really interesting to see is if the Linux community can write a driver that allows this button to function and open a Linux media center such as MythTV.[/QUOTE]

Actually, this is a lot easier than it seems. All the button does is flip on a partition and sets it bootable. 

If grub is configured properly (and you have boot files on that partition), you can tap it all you want and it'll flip back and forth. 

:):)

---

### Post by HokeyFry on 2007-10-03
haha i just got done talking to dell about how to disable it, since it somehow trashed all of my partitions beyond recovery

they said since i deleted the partition the button shouldnt be working

makes me wonder why im not in customer service, id go all the way to  upper (if not middle) management :lolflag:


but in all seriousness, would installing grub to the MBR stop the button from working?

---

### Post by keithlommel on 2007-11-18
No, deleting all partitions (i.e. the Dell Utility and MediaDirect partitions), formatting the entire drive, and then installing GRUB to MBR will not stop this Dell Self-Destruct-Direct button from working. 

Believe it or not, the Dell Self-Destruct-Direct button will still trash your partition table and make the system unbootable even after all that. When I recently installed Gutsy on my laptop, I used a gparted live CD to delete and reformat all partitions on the hard disk. Imagine my surprise then, when I accidentally hit the Self-Destruct button and it rendered my entire system unbootable. Booting with the Gutsy Live CD showed that there were now a couple of new partitions on the hard disk for Dell Utility and MediaDirect -- how did these things come back to life?

The answer is that MediaDirect hides a small chunk of boot code in a hidden partition called a "Host Protected Area" or HPA, which most partition editors (included gparted) cannot see or touch. The button apparently enables this partition for booting, and whatever sloppy code is in there trashes your partition table and/or MBR if it does not find things the way it expects them.

Naturally, I was not pleased with the knowledge that after re-installing everything I'd always have this Sword of Damocles hanging over my head -- one false button press in the dark or a careless nudge in the briefcase and my computer would be rendered inoperable and all the data only recoverable with significant effort.

Long story short, here's what you can do to erase the code in this hidden partition and render the Self-Destruct button harmless. A word of warning, however. The following command will PERMANENTLY ERASE ALL DATA off your ENTIRE HARD DISK. Only perform the following command after backing up all important data, and in preparation for a fresh, clean install of all operating systems on your system.

Run the following command from a terminal in a live cd (I used my gparted live cd, which conveniently let me create new partitions after everything was wiped.)

SECOND WARNING: This command will erase all data on your hard drive!
```
dd if=/dev/zero of=/dev/sda
```

After running this and reinstalling your OS, pressing the MediaDirect button will do nothing more than show a special splash screen (stored in BIOS, it seems) before booting to your normal GRUB loader.

Hope it helps.
--Keith

---

### Post by MEB202073 on 2007-11-19
sounds like what I been having lately.

What is it exactly do if you erase media direct but still have it in BIOS?

---

### Post by starkawa on 2007-12-16
> **keithlommel said:**
> 
The answer is that MediaDirect hides a small chunk of boot code in a hidden partition called a "Host Protected Area" or HPA, which most partition editors (included gparted) cannot see or touch. The button apparently enables this partition for booting, and whatever sloppy code is in there trashes your partition table and/or MBR if it does not find things the way it expects them.

After running this and reinstalling your OS, pressing the MediaDirect button will do nothing more than show a special splash screen (stored in BIOS, it seems) before booting to your normal GRUB loader.


Thank you for the advice with strong warning. Is this method going to work with Media Direct 3 as I read other threads stating that it is stored on logical partition on this new version. Or is the boot code still on HPA as I've read quite a few experiences of dealing with MD3 but still experiencing weird behavior when pressing the button?

I almost give up installing ubuntu on my dell but rather on my mac; it's just after reading so many articles I kind of want to win against Dell on this :)

Thanks again!

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

### Post by JimGoose on 2007-12-28
EDIT:

I think I got it, here's what I did:

Using some help from Dan Goodell and ubuntu forums:

[B]1. Run Windows XP Recovery Console, type "fixmbr"
2. immediately Run Hitachi Feature Tool boot disk after your restart, using the change capacity feature, set it to Max
3. Use Gparted Live Boot CD, get into GUI, bring up terminal/command line, use "dd if=/dev/zero of=/dev/sda" to zero fill drive.  If it seems like it zero filled instantly, it didn't, let it wait a while (5 min for every GB of your drive). You might be able to use Windows XP boot disk to format, but i wanted to be safe and went for zero fill.
4. turn off PC after zero fill, try the media direct button, it should just show the splash screen that is stored in BIOS, then it should give you "No boot sector on internal drive"
5. boot from your chosen OS boot disk to create partitions/format/install etc.[/B]

The sequence is important

...now i'm going to try and reassign the media direct button for something useful...

---

### Post by chokas on 2008-01-30
I don't know why this !$"#$ button has to re-write the partition table, I almost fainted this morning when I accidentally pushed it and I couln't boot windows or Ubuntu :(, I got some "grub error 2"...

So... from my own experience.. if this happens to you, dont panic

I followed the step 2 in this post
[http://ubuntuforums.org/showpost.php?p=4030564&postcount=16](http://ubuntuforums.org/showpost.php?p=4030564&postcount=16)

and I could rescue Windows ... ¡Great! ¿isn't it ?:-x

Anyways... had to re-install ubuntu..etc...etc... but for those who haven't clicked yet and haven't formatted the whole drive and don't want to go through this whole thing... here's a link showing some steps to "re-map" the button to load something else, so you can load Linux with the power button and ... linux with the media direct button, or something different :)..

[http://forum.notebookreview.com/showthread.php?t=182495](http://forum.notebookreview.com/showthread.php?t=182495)

Note: I haven't done it yet, I'm planning to do it this weekend..

---

### Post by syxbit on 2008-01-30
running 
dd if=/dev/zero of=/dev/sda
from gparted live disc
I have the m1330 with a 250GB drive, and it's been going for almost 3 hours already!
I'm assuming this is normal....
how long has it taken you lot?

edit: Took a little over 3 hours

---

### Post by neonard0 on 2008-03-10
Hey!!!!  I found something really cool, I have not tried this again but worked perfect for me.
The stage was this:
First I installed Xp (c:/), then Installed Vista(d:/), then installed ubuntu (Other partition and other for swap)
Everything was perfect, but one night trying to start my xp1330 accidentally I push the HOME KEY. :(, the logo of dell media direct appear and then and BLUE error screen with message (common functionally of windows) told that there was a mess with the system. I could not restart the pc, it was blocked, so I kept the start button pushed to restart, the grub appear, but when I selected the menu for booting on vista or Xp, the system showed the same error, fortunatelly i could boot from ubuntu, but once in it the partitions were not mounted, after checking with fdisk from a booting cd, It showed that the C:/ partition was moved, now for a emty partition with just like 2Gigs, the d was there but not mounted too, and the format was not showed.
Well I was about to format everything but then a friend of mine appear, so to show him what no to do (I mean if you have a shutdown dell notebook YOU CANT PRESS THE HOME KEY) so as the system was messed up, I press the key once again, The direct media logo appear ( as If I have started the pc with the power on button, and select the vista option to boot) and the It show me the grub menu, it was strange because the the graphics was ugly, so I select the Vista option to boot.  MIRACOULUS AND HIBERNATING XP WAS STARTING  and then i was on XP, I restarted the machine and select the vista option again, then appear normally the next boot menu (the vista menu, to select vista or XP start), everything worked fine, then I restart and go into ubuntu and the partitions were mounted normally.

So I dont know If you people tried to start the pc with the home button, that was my case and know I'm writing this down in case someone want to try this. I dont want to test that, maybe i just was lucky

---

### Post by MikeyMike01 on 2008-04-11
Fixing the Grub boot errors from pushing the MediaDirect Button is quite simple:

1. Push MediaDirect Button (Again)
2. As soon as the Loading screen appears do a hard shutdown.

Problem fixed. 

And since I know most of you are probably to scared to try it (no offense) I will be making a YouTube video later.

---

### Post by MikeyMike01 on 2008-04-11
[http://youtube.com/watch?v=GjzFU6rXwLo](http://youtube.com/watch?v=GjzFU6rXwLo)

---

