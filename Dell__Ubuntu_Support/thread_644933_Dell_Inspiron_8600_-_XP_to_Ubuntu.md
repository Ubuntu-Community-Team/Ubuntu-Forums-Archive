---
title: "Dell Inspiron 8600 - XP to Ubuntu"
date: 2007-12-19
forum: Dell  Ubuntu Support
---

### Post by zhang2 on 2007-12-19
I'm not very good with computers, and after hearing about problems some users had with their computers crashing and hard drives not being found, I'm hesitant to try to install Ubuntu on my own. So far I have burned the ISO (version 7.10 i386) and been to the boot menu.

Can someone guide me through what I need to do to install it on my computer? When I go into my boot menu and boot from CD, do I choose the first option to install Ubuntu, or the second option that allows me to partition everything? Will I have hardware and wireless internet problems, and if I will, how do I fix these? Basically I'm looking for a simple step-by-step instructional for installing Ubuntu and getting it to run with no problems. Thanks for the help!

---

### Post by zhang2 on 2007-12-19
I'm also wondering...is it necessary to go into the partitioning menu and partition everything? I didn't even know what partitioning was until today, so if I can avoid doing this I'll be very happy. If it;s necessary, and not that complicated, could someone tell me how I should partition and what I need to do?

---

### Post by randomnote1 on 2007-12-19
Welcome to the wide world of Linux.

The first thing is, make sure, if you have any information on your computer currently, that it is backed up.  That way when you format your hard drive it won't kill your information.

If you are looking to completely wipe XP off of your computer, then just put in the CD and boot it up.  When it is completely booted, you should have a desktop screen with an icon to install.  This is known as running off of the Live cd.  From there you can test how your system will run Ubuntu without erasing any data on your hard drive.  Keep in mind that running from the CD will be slower than it will actually be when you install it.  As far as installing it, just follow the installer guide.  You do not need to worry about partitioning because Ubuntu will do it automatically for you if you select that option. 

Unfortunately, I do not know of any step-by-step tutorial for installation.  The best way to do it is to just do it.  

Good Luck!

---

### Post by zhang2 on 2007-12-19
That's a little more comforting to know. Well, I've put in the CD, restarted windows, gone into the boot menu, and booted off the CD. I got a black screen with "Ubuntu" with a bunch of options. I clicked the first option which said to Install Ubuntu, and a small window popped up that said something about a Linux Kernel. Then my screen turned black, and I just got a blinking white line on the top left of the screen that seemed to prompt me to type something. After waiting 10 minutes, nothing happened so I turned off the computer and rebooted in XP. 

Shouldn't something happen when I click install? Like a screen that tells me that it's actually installing and replacing XP? The black screen tells me nothing. I don't need to download Linux do I? Sorry if this is a stupid question...like I said I'm not too good with computers. If you can help me out I'd really appreciate it.

---

### Post by brett_baudin on 2007-12-19
I just did the following on my Inspirion 8600 which has XP on it.
Put Ubuntu CD in computer.
Reboot if computer is running.
Select install from text menu.
Ubuntu logo for a minute or two.
Flashing cursor in top left for less than minute.
Numerous text lines on screen.
Solid brown color for about a minute.
Linux desktop shows up in less than minute.
If you like what you see double click on the Install icon on the Linux desktop.
Installer starts.
Click forward on step 1 of 7
Select timezone on step 2 of 7
Click forward on step 3 of 7
On step 4 of 7 you can use the default which will set up a dual boot with XP or use the "Guided - use entire disk" if you want to wipe out XP. Probably not what you want to do.
Select continue to write changes to disk.
Step 5 of 7 will migrate any XP accounts you have. Probably best to just press forward.
Step 6 of 7 fill in the information and press forward.
Setp 7 of 7 press install

---

### Post by zhang2 on 2007-12-19
hmm, I seem to be stuck at the flashing cursor Brett. I 

-load the CD
-restart the computer
-press F12 to get to the boot menu
-boot from CD
-get the orange Ubuntu logo on a black screen and some options
-choose the first option to Start/Install
-get the black screen with cursor for 40 minutes this time and nothing

Are you using the i386 version? I tried the 64 version mistakenly the first time, and my computer wouldn't do anything with it. I'm not sure what I'm doing wrong. You did nothing before you burned the CD right? I checked the CD with that hash comparer and everything matched.

---

### Post by brett_baudin on 2007-12-19
Not really sure but I would say you Inspiron is different in some way from mine. Possibly your bios is not up to date. You should compare your bios version with the latest from Dell.

---

### Post by brett_baudin on 2007-12-19
You should also try the Check CD for defects option that is on the same initial install menu.

---

### Post by nick_h on 2007-12-19
> You should also try the Check CD for defects option that is on the same initial install menu.
Good idea.  This is the first thing to do.

Did the 8600 have different graphics card options?  Perhaps this might be a difference between your 2 machines.  If this is the case then maybe installing from the alternate image might work.

---

### Post by zhang2 on 2007-12-19
I checked for a newer BIOS and one couldn't be found. I also checked the hash and it compared to the one Ubuntu had on its site. It's very strange...maybe I'll bring it to a friend who knows much more about computers than me. It's easier to fix when you have the actual computer in front of you. Well, I'm also getting an Asus eeePC in a couple months which I think comes with Ubuntu already installed, so it's not a big deal. In the mean time, I might try that alternate CD idea.

---

