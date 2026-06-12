---
title: "File, Folders, programs from Windows?"
date: 2009-03-23
forum: General Help
---

### Post by ckh1 on 2009-03-23
Hello,
I have just gotten UBUNTU 8.10 to work finally after many days. Even got the internet to work
I am using a live user session/cd.
I found out how to transfer some files and folders and applications/programs from windows to ubuntu.
However when I try and open RHAPSODY in ubuntu it doesn't work. 
On the desk top it has a blue square and it says Rhapsody.lnk. When I double click on it is says: Could not display "/home/ubuntu/ Desktop/Rhapsody.lnk".
There is no application installed for this file type.
I have a couple of other programs that say the same thing when I try and start them.

I am afraid to shut down the computer don't want to lose everything in ubuntu.

any suggestions?

---

### Post by oldos2er on 2009-03-23
Here is info on running Win* apps in Ubuntu: [https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

 Not sure what you mean by "I am afraid to shut down the computer don't want to lose everything in ubuntu."

---

### Post by Rallg on 2009-03-23
The reason for shutdown fear, is that olsdos2er is using a live distro, not an installed file system.

In Windows, a *.lnk file is similar to what Linux calls a symbolic link. However, they work differently. In Linux (such as Ubuntu), the system thinks your *.lnk is a file of type lnk, and doesn't know how to open it in an application. You don't want to say that it should open Rhapsody, becuase then all links brought over from Windows would open Rhapsody.

For the moment, try this: Locate the Rhapsody executable file. It is probably in Menu WINE > Browse C Drive. Double-click it to open it in WINE. Does it work?

If it works as expected, then you can create a Linux-type symbolic link to Rhapsody, if you wish. Hoever, since Windows multimedia-type applications sometimes have problems in Linux, you are not there yet.

Ultimately, you should consider installing Ubuntu to the hard drive, if yours is still usable. From your login handle (olsos2er) I suspect that your computer might have hardware problems.

---

### Post by ckh1 on 2009-03-23
thanks for the info.
If I install UBUNTU to my hard drive, will I still be able to access my windows to transfer my files, folders and programs?
And...if and when I do transfer my files, folders, programs etc to ubuntu and they work, I will no longer need anything microsoft/windows. Will I then be able to completely remove windows from my computer and only have Linux/ubuntu?

---

### Post by ckh1 on 2009-03-23
...and how should I partition the drive?...

---

### Post by mocoloco on 2009-03-23
What does this Rhapsody link do under Windows, just take you to their website?  I listen to rhapsody.com on Ubuntu all the time.  Or is there some Windows standalone app that I'm not aware of? (don't see it mention on their site).

---

### Post by bigbencg on 2009-03-23
First, what version of Windows are you using.  If you are using Vista you can open Computer Management and shrink your partition.  If you are using an earlier version the ubuntu installer should give you a guided option to resize the partition and install.  To achieve what you are trying to do, ubuntu needs to first be installed on the computer.

Using a program like WINE does not allow you to run programs installed under a windows installation.  Wine is not an emulator but more of a translator.  It fools the program into thinking it is in a Windows OS.  The applications have to be installed in Wine, you simply cannot run the executable that you copy over.  As for .lnk, ubuntu has no idea what that is.

---

### Post by oldos2er on 2009-03-23
> **Rallg said:**
>  From your login handle (olsos2er) I suspect that your computer might have hardware problems.

 Apparently you have me confused with ckh1, the OP. How you can assume anything by my username is beyond me.

 ckh1, please read [http://psychocats.net/ubuntu/index](http://psychocats.net/ubuntu/index) and [https://help.ubuntu.com/8.10/windows/C/](https://help.ubuntu.com/8.10/windows/C/)

---

### Post by ckh1 on 2009-03-24
Help! nothing is working now?...what am I doing wrong?
How do I get my files,folders and some programs from Windows!
I want to install UBUNTU 100% but need these files,folders and some programs!

I have windows xp home.

In ubuntu, when I try and open the windows volume (158.5 GB Media) I get a statement: "Cannot mount volume. Unable to mount the volume". without touching anything..
another box pops up saying "Opening 158.5 GB Media. You can stop this operation..." without touching anything...
 another box pops up saying: "Unable to mount location".

 I am using the live CD session.
 Yesterday, when UBUNTU finally booted I was able to open the 158.5 GB Media and I "copied/transferred" files and folders to ubuntu. Thinking that the files, folders and programs would stay, I shutdown. I was going to install UBUNTU to the hard drive later.
I started UBUNTU this AM after many many tries and none of my files,folders, programs where in UBUNTU. Now the 158.5 GB Media won't open.
Also, when I click on install I don't get the three options that are talked about.
I get:
Guided - use entire disk
and
SCSI1 (0,0,0) (sda) - 160.0 GB ATA WDC1600BEVE-0
and
Manual
The first to are selected.
The before bar is /dev/sda1 99% and /dev/sda5 0%
The after bar is Ubuntu 8.10 100%

How do I get my files and folders and programs from Windows?
Help!

Thanks

---

### Post by rockstone on 2009-03-24
If your objective is to replace windows with ubuntu the easiest thing to do do would be to copy your files to another drive then have ubuntu install to the entire drive. 

As far as programs go there are linux equivalents to most programs that you would have been using in windows. You should probably figure out what those are and how to use them. Try using add/remove or synaptic package manager. If there are specific windows applications that you need then you will have to configure those with wine. 

Before replacing windows with ubuntu though you might want to get used to it. Play around on the live cd for a while or install it with wubi (this essentially installs ubuntu inside of windows).

---

### Post by ckh1 on 2009-03-24
I can't get to my windows XP...? 
how do I boot windows now?

---

### Post by oldos2er on 2009-03-24
Can you boot the Ubuntu CD again, and post the output of this command:
```
sudo fdisk -l
```
?

---

### Post by ckh1 on 2009-03-25
now I can't even get into ubuntu at all?
I put in the live cd and it brings me to the menu: to load ubuntu without ant changes to my computer and Install ubuntu.
I select one, the ubuntu comes up with the "cylon bar" going back and forth and then eventually i get a screen full of error messages and then everything just stops.
I think the whole thing is toast.
I think I am going to have to reinstall windows and lose everything.
catastrophic!
I'll wait to see if you or anyone else has any suggestions.

---

### Post by oldos2er on 2009-03-25
If you have access to another machine, try burning a copy of System Rescue CD: [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

---

### Post by ckh1 on 2009-03-26
oldos2er

GREAT! saved! got my files and folders and "programs" I needed off the windows.
Installing now....
OK, while installing I got FAILED TO CREATE A FILE SYSTEM  -  The ext3 file system creation in partition #1 of SCS|1 (0,0,0)(sda) failed.

now what?

Thank you so much for your help with all this. You have worked wonders so far! 
Well wonders to someone with my ubuntu/windows experience.

---

### Post by oldos2er on 2009-03-26
Apparently that's a known bug: [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/99908](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/99908)

 It doesn't look like there's any simple solution.

---

### Post by ckh1 on 2009-03-26
to me that is worthless information.
Guess I will just have to go back to "fail-safe, trust worthy" Microsoft Windows XP. I put the Windows XP Reinstall CD in the drive and it worked first time like a charm, no errors, no bugs. It just worked. 
It is unfortunate that LINUX/UBUNTU is not as easy and user friendly as Windows. For people that want to goto LINUX this is a very big turn off, a major deterrant. I will definately not be recommending LINUX to anyone that is thinking of leaving windows. 

Perhaps it is just my Dell Inspiron 2650 that can not handle LINUX OS.

Any other ideas, suggestions, comments? some other form of Linux perhaps?

Again, thank you so much for your help, advice and assistance.
You tried with your knowledege and experience with LINUX/Ubuntu.

If you do not have any other suggestions, advice, assistance or comments for me.

I will move on and forget about my ordeal with Linux/Ubuntu

---

