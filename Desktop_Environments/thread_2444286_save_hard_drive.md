---
title: "save hard drive"
date: 2020-05-28
forum: Desktop Environments
---

### Post by jgw on 2020-05-28
My wife uses Windows for her computer.  I really don't use windows/Microsoft anymore.  Anyway, my wife was doing stuff and told me that her keyboard no longer worked.  I attached three different keyboards, that I knew worked but didn't on her windows season.  One of them was a usb keyboard.  Anyway, I then went to the internet to figure out what the problem was.  I found several solutions of one sort or another and tried them all to no avail.  Then I tried chkdsk to check the hard drive.  First I just tried it, with no 'f' and there were problems.  So I figured that /f (fix) would be a good idea.  That ran overnight and never reached the end so I figured I had a real mess on my hands.  I then went to windows support and talked to several of their techs.  They had me download a copy of windows to install as they said what I had was wrecked.  I did that, on an external hard drive and proceeded.  In an attempt to install a new windows, over the old one, the drive was further 'fixed' which really dicked it up (after no less than 4 techs and a day wasted.  At that point I decided to abandon them, get a new drive and put a new copy of windows on it and then deal with the bad disk that has a lot of my wife's stuff on it (she never backed up <sigh>).  I got a copy of windows, signed into my Microsoft account (I was amazed I still had one, and got a copy of windows to install.  I also got that done.  Now I have to try and get something off the drive.  I did another search on what to do to try and get something off of it.  The trick seems to be to, first, run 'no swap'.  My problem with that one is that I can't seem to find the command to run that against a single external usb hard drive (/dev/sdd1) on my linux machine.  After I do that I can, apparently run a program that might be able to restore my missing partition that is no longer there.

I need a couple of things.  I need to know what the command is to run no swap against a single drive.  I would also appreciate any and all suggestions about the best way to try and save whatever I can on the drive I seem to have destroyed following the expert help from the Microsoft techs.    I would be grateful for any help in this regard in this regard.

Thank you........

---

### Post by DuckHook on 2020-05-28
This is not good. Since we have no idea of the "stuff" that the MS techs had you do, there is no possible way to determine how far gone the data is.

[list=1]
[*]***DO NOT*** do anything further on this drive. It's probably already too late, but every attempt to access or write further data on this drive will corrupt it even more. This includes any further attempts to "fix" it.
[*]Your only chance&#8212;slim as it is&#8212;is to make a bit-for-bit copy of the data from the bad drive onto a good one. Then work on the *good* drive.
[*]You must use Windows tools to recover Windows data. Trying to do this with Linux is not a good idea. I am now so removed from Windows that I am a fish out of water. You will get better help from the other gurus on the forum.
[*]If the data is simply irreplaceable, then be prepared to take the drive to a professional data recovery outfit and shell out the bucks for their professional help. They can usually recover some stuff if it's not overwritten, but if the "stuff" that was done to it is too extensive, then don't hold your breath.
[/list]
It's sad that these are the things that have to happen before people learn to back up. Water under the bridge now I suppose.

---

### Post by Autodave on 2020-05-28
For what it is worth, I run into many Win systems that have died or gotten corrupted for many reasons.  I make a copy of the drive to an external drive.  You will need the means to hook the old drive up externally: this usually requires an adapter that is capable of supplying the 12V that is needed to spin-up the drive.  IF the drive is an SSD, then a much simpler and cheaper cable is needed to gain access to the drive.

I have had drives where everything was recoverable and I have had some where nothing was.  And of course, I have had them where some recoverable.

---

### Post by jgw on 2020-05-28
Here is a picture of a wrecked hard drive via the Disks program.  This hard drive is from my wife's Windows machine and is currently an external drive on my ubuntu 18.04.3 machine.[IMG]~/Pictures/wrecked.png[/IMG]  If I try and open it with Gparted I am told it cannot be found and then it goes away from Disks too.  it does not appear in files either.  This is the drive I would like to get data from.  I have been told to copy it.  I have a hard disk, on this system, with enough room to grab whatever might be found but would like to send the data to a file.  

My problem is pretty simple.  How in the world can I copy something that only disks seems to be able to find?

---

### Post by Autodave on 2020-05-29
Can you try and mount that HD to the Win machine?  If you can do that, you then need to turn off *Fast boot* (in the Bios) on the Win machine and then shut Win down with the HD connected.

Windows does not shut down: it merely hibernates.  So, that HD drive is still being held captive by Win. 

After proper shutdown of the drive, you should be able to get to its contents.

---

### Post by DuckHook on 2020-05-29
> **Autodave said:**
> Can you try and mount that HD to the Win machine?  If you can do that, you then need to turn off *Fast boot* (in the Bios) on the Win machine and then shut Win down with the HD connected.

Windows does not shut down: it merely hibernates.  So, that HD drive is still being held captive by Win. 

After proper shutdown of the drive, you should be able to get to its contents.
One assumes that those Windows techs would have been knowledgeable enough to de-hibernate the failed HDD as one of their diagnostic steps, but maybe not.

My concern is that any further monkeying with the HDD only makes things worse.
> **jgw said:**
> …I try and open it with Gparted I am told it cannot be found and then it goes away from Disks too.  it does not appear in files either.  This is the drive I would like to get data from.  I have been told to copy it.  I have a hard disk, on this system, with enough room to grab whatever might be found but would like to send the data to a file.  

My problem is pretty simple.  How in the world can I copy something that only disks seems to be able to find?
My mistake for not being clear enough. If this drive is truly borked, then you won't be able to see it in gparted. Gnome-disks would also only give you rudimentary info. High-level disk utilities like *gparted* or the CLI *cp* can only work with drives that have receptive partition table, MBR, UEFI sectors. If these are too far gone, you can't use high&#8209;level tools.

I did explicitly say: bit-for-bit in my initial post. What this means is *dd*. However, most people will find *dd* overly intimidating. Therefore, I would recommend *gddrescue*.

Instructions for starting the rescue process can be found here: [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

:!:***HUGE WARNING***:!:
I have already warned you that attempting to recover Windows data using Linux tools is a really bad idea. It's like trying to repair a Ford engine using Toyota parts. Since you state that you now have Windows up and running again on your wife's computer, why are you still trying to use Linux? If the data is really important, shell out the money for Windows recovery software and use tools properly made for Windows.

---

### Post by Yellow Pasque on 2020-05-31
If all else fails, try testdisk to fix the partition table before throwing in towel:
```
sudo testdisk
```

---

### Post by jgw on 2020-06-18
My solution was to have my son, who uses windows, to help his mother.  He had a program, from china, that will search for everything on a screwed up drive.  Then you call them, in China, and then they want control of your system.  After several days of the program doing stuff my wife called them, found out where they were, and choose to not give them control of her system.  Basically my wife is now at a standstill but I think she has made up her mind to just live with it.  

That isn't quite what I would have done but its her computer so I backed off.  Since nothing was solved I can't mark this as solved and there is no setting for 'dead' so i am just going to abandon this.

Thank you for all the replies.

---

### Post by GhX6GZMB on 2020-06-18
:shock::shock::shock:

You're having us on, right? April 1st is long past...

---

### Post by jgw on 2020-06-18
Nope - its true.  I also called microsoft support and had their techs 'help' me which further screwed up the drive.  After they did that they bumped to up to another set of tech help which further screwed it up which is when I just stopped due to my wife's insistence (she just wanted her system back which she does now).  She did have a lot of stuff backed up as I had three drives on her system, one of which was sitting there just to back up stuff which she used as just another drive <sigh>  Its just a mess and she was fighting about I know not but know better than indulge that as it can go on for a long time over nothing.  She is back up and running (only cost me another drive <sigh>)

---

### Post by GhX6GZMB on 2020-06-18
In that case, I hope your wife's PC only contains knitting recipes and no online banking information etc. And that it's not networked with the other machines in your house...

---

### Post by jgw on 2020-06-18
she uses it for, basically, email and genealogy.  She found out, after the disaster, that most of her programs were backing up on the cloud automatically so she really didn't lose all that much stuff.  Just took a month to figure that one out.  When I setup her computer I setup and gave her a copy of acronis and it was all automatic.  She cleverly, I guess, stopped that right away and never said a word <sigh>  She is, however, back at it.

---

