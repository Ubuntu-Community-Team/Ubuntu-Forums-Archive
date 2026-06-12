---
title: "Please help"
date: 2009-03-09
forum: General Help
---

### Post by newb_nate_08 on 2009-03-09
Now to start off with, ive been foolin around with linux and xp for the past week trying to get what i want accomplished but am just a novice to installing 2 OS's on the same hard drive. point is, i have tried my best before asking for help.

What i want to do is have windows xp 64 bit and linux ubuntu installed. 

Somehow i installed linux inside of windows and the end result was before either OS booted when i restarted the whole comp, it would ask me which OS i wanted to run (XP or Ubuntu).

That was cool. 

But I wanted to run the linux with the Cube thing (compiz fusion). Ended up trying to delete ubuntu from windows and screwed it all up. 

If someone could please show me a step by step tutorial (which i have spent last couple days trying to find and piece together through several tutorials) how to dual boot that would be so friggin awesome. 

As we speak, im using PartitionMagic to clean up ALL the partitions ive somehow made (lol as you can tell im new to all this but really giving it my all to try to learn).

Like i said, my desired end result is to be able to do the Cube thing and be able to choose which os i want to use: ubuntu or windows.

thanks alot for those who read this and try to help me.

---

### Post by Rocket2DMn on 2009-03-09
Moved to General Help - please don't post support requests in Tutorials & Tips, that area requires staff approval and is for guide and HowTos only :)
Good luck, the community here will be glad to help.

---

### Post by C-- on 2009-03-09
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty)

---

### Post by hyper_ch on 2009-03-09
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

See the forums policy, especially section II.2: [http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by hatrack on 2009-03-09
Hi there!

I too am very much a newbie (I only started with Ubuntu in the autumn) but I have been through a similar exercise to that which you describe, so perhaps the following comments will be helpful.

I will assume that you have the original Windows XP DVD and also a live CD for Ubuntu.

First of all, start off making a completely new installation of Win XP. This will format the HD, probably to NTFS. Once this installation is complete, fire up the computer and test that it is working OK in Win XP. Do not install any windows apps at this stage.

Now you are ready to begin the installation of Ubuntu. Insert the Ubuntu DVD. This should auto-start. Select "Install Linux" (or Ubuntu ... I can't remember the exact wording here). After a short while, you will reach the stage where the partitioner starts up. Select the "Manual ... Guided" options.  This will present a diagram showing how much of the disk is being used by Windows and how much is available for Linux to use.
There is a slider which you can drag to vary the size of the Linux partition. Let us say you decide to give Linux half the disk space ... you will, of course, choose an actual amount.  

After you have selected this size, Linux will go ahead and format the new partition and set up swap space, etc. In due course, the installation will finish and you will remove the DVD and re-boot. The start menu should now give you the options to boot into Linux or Windows XP. Test that both work.

Now, you can install your Windows apps by booting into this partition and installing as usual. Again ... test that all is OK.

What you call "the spinning cube thing" is a Compiz function and ONLY is available in Linux. There are helpful posts on this forum re Compiz, which is only a display manager.

Please note and follow the sequence I have described ... install Win XP FIRST and make sure it is working. THEN think about installing Linux. Linux will "play nicely" with Windows but if you try to do the installation the other way around, Windows gets all huffy and can turn you HD into a dog's breakfast ... or so I am told. I was warned about this potential problem right at the start and have followed the above sequence ever since ... (I have gone through several install cycles until I finally got the configuration I want ... two computers networked together ... one runs Linux, one runs Windows 2000 and I can hot-switch between them onto one monitor. (I initially went down the dual-boot route but then decided that my present confguration better suited my particular needs).

I hope you find this helpful. Best regards and Good Luck !

---

### Post by oldos2er on 2009-03-09
[http://psychocats.net/ubuntu/iso](http://psychocats.net/ubuntu/iso)

---

