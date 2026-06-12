---
title: "Ubuntu newbie broke boot loader?"
date: 2009-01-27
forum: General Help
---

### Post by waxBall on 2009-01-27
After a rather painful, but ultimately successful, install of 8.10 on my newly built box (with Vista and XP already happily installed), I'm finding my Ubuntu experience to be less than satisfying.  These are my current issues:

A) Graphics card performance less than stellar - I have an ATI Radeon 4670 and after installing the proprietary driver I have ample screen resolution.  Though in order to view video without a horrible seizure-inducing flicker, I must turn off all video enhancements (in appearance menu). While this isn't tremendously important, it's disappointing because I'm quite used to my Mac's pretty UI.

So in the quest for a different driver I stumbled across instructions for uninstalling the proprietary driver and replacing it with Envy.  In the directions it mentioned the **ctrl + alt + F1** shortcut.  So with out thinking, I hit it!  That of course took me to the console...  Which I didn't know how to get out of using any of my DOS cmd's.  No surprise there.  Haha!  (Now I know it's ctrl + alt + F7, right?)  So I just hit the reset button my case.  That brings me to the **major issue at hand**:

B) _**Cannot boot to HDD!!**_ - When I try to boot up normally, I'm given the prompt to boot from CD and the computer complains there is no media in the drive with no other options available!  So I tried inserting my Ubuntu 8.10 disc and it booted to the LiveCD just fine.  I thought perhaps everything is OK so took the disc out and rebooted normally.  Same boot problem!  It will not boot to my SATA drive.  Then I tried the option "Boot to first HDD" from the Ubuntu CD.  It complained there was nothing to boot (can't remember the exact error, sorry).

Next I went into my BIOS and checked that the boot order hadn't been messed up and of course it had.  For some reason it no longer seems to recognize my (main) SATA drive.  The boot order reads:

1: CD/DVD
2: Maxtor IDE
3: FD

I don't think I even have a Maxtor installed!!  I do have 1 SATA and two IDE drives installed but I'm certain the SATA is Seagate and I thought the others were WD and Seagate.  Any way, neither of the IDE's have ANY form of OS on them.  And when I try to change the boot order, my SATA drive is not even listed!

How could I have possibly broken my boot order/BIOS with a few simple commands in the console, none of which worked anyway!  (Except 'shutdown' which I couldn't get the correct operators to make it work any way).

Please help me fix my boot issues!

Intel E8500 3.16ghz
Asus P5Q mobo - most recent BIOS already flashed
4gb DDR2 Geil RAM
Seagate 500gb SATA
HIS ATI Radeon 4670

Thank you so much in advance for your help!

---

### Post by sowelie on 2009-01-27
None of the commands would have messed up your bios settings.  I would venture to guess that the ubuntu install removed the MBR.  I'm surprised that it doesn't at least boot into ubuntu.

I'd check out THE SECOND post here:

[http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)


To figure out which partition to use (the hda0,6 part), do sudo fdisk -l.  Pick your main ubuntu partition (most likely the only linux ext3 partition you have).  Then you'll at least be able to get back into Ubuntu.

---

### Post by waxBall on 2009-01-27
Thank you very much for the speedy reply!  I'll try this when I get home (in 5 hours) and post the result.

---

### Post by sowelie on 2009-01-27
Yeah do all of that from the live cd.  That should at least get you back into Ubuntu.  Then you can add your windows partitions to your grub menu later.

---

### Post by waxBall on 2009-01-27
Yeah I should have looked at your link before thinking about replying...  Silly.

Setting up windows partitions is the same as an ext3, right?

> 4. Type "root (hd0,6)", or whatever your harddisk + boot partition numbers are (my /boot is at /dev/sda7, which translates to hd0,6 for grub).
5. Type "setup (hd0)", ot whatever your harddisk nr is.

Replacing the correct names where appropriate, of course.

---

### Post by sowelie on 2009-01-29
Yeah, grub doesn't care what type of partition you're setting up.

---

### Post by waxBall on 2009-01-29
I did finally get the boot issue fixed, thank you for your help.  But after a few days of virtually non-stop struggling with Ubunut 8.10, I've decided to give up.  It's just not worth fighting with my OS.  

I consider myself primarily a Mac user, but just recently built an Intel system.  Although Vista is mess of buggy, unsecure spaghetti, it's better than having to struggle with your OS to accomplish basic computing funtions.  One day I may go back to Ubuntu but for now the video driver, boot problems, general incombatability and other issues will keep me away.  Sad too because there is a lot I like about Ubuntu....

I think I'll give iDeneb a shot next.  ;)

Cheers all!

---

### Post by jerome1232 on 2009-01-29
> **waxBall said:**
> 

1: CD/DVD
2: Maxtor IDE
3: FD

I don't think I even have a Maxtor installed!!  I do have 1 SATA and two IDE drives installed but I'm certain the SATA is Seagate and I thought the others were WD and Seagate.  Any way, neither of the IDE's have ANY form of OS on them.  And when I try to change the boot order, my SATA drive is not even listed!

Not that it matters but seagate IS maxtor.

---

### Post by waxBall on 2009-01-29
Interesting.  I never knew.  I guess it might be more correct to say, "Maxtor is Seagate".

[Seagate acquires Maxtor]("http://arstechnica.com/old/content/2005/12/5816.ars")

---

### Post by sowelie on 2009-01-29
> **waxBall said:**
> I did finally get the boot issue fixed, thank you for your help.  But after a few days of virtually non-stop struggling with Ubunut 8.10, I've decided to give up.  It's just not worth fighting with my OS.  

I consider myself primarily a Mac user, but just recently built an Intel system.  Although Vista is mess of buggy, unsecure spaghetti, it's better than having to struggle with your OS to accomplish basic computing funtions.  One day I may go back to Ubuntu but for now the video driver, boot problems, general incombatability and other issues will keep me away.  Sad too because there is a lot I like about Ubuntu....

I think I'll give iDeneb a shot next.  ;)

Cheers all!

Don't give up!  If you had an nvidia card your experience would be much better.  Honestly, it's a much butter OS than Windows.  Compared to Mac, it's not as easy to use, but it's much more customizable.  Ubuntu is IDEAL for development, not sure if you do any programming though.

---

