---
title: "weird gdm failure"
date: 2007-10-02
forum: Desktop Environments
---

### Post by noknyc on 2007-10-02
Hi folks, really hoping someone can help me.

I'm still pretty much a beginner, but I've been fairly successful at figuring things out on my own.  This one has me stumped, though.

Here's the problem.  Ever since I installed another hard drive, GDM fails to start.  The machine boots just fine and I get all the way through to the end of the Ubuntu loading screen (with the progress bar).  Then the screen goes almost black.  I say almost, because there is actually one single pixel in the mid left of the screen that remains lit and seems to flicker. (!)

I'm 99% sure the machine is hung up at this point since I can't ssh to it or do anything else remotely.

Using GRUB, I was able to boot into recovery mode.  Everything seems okay.  But as soon as I run 'gdm' or 'startx', the same thing happens.

I don't think it's an error in xorg.conf since I tried using a backup copy of it that I made a few days ago.

I don't even understand how changing HDD's could affect how X runs...  but maybe I'm missing something.

Here's exactly what I did right before the problem started:

I have been using a fresh install of Fiesty on this box for about a week with no issues at all.  It's an older machine, and I was using a 12gig master with an 8gig slave on the primary IDE chain.  Today I added a new HDD as a slave on the secondary chain, along with the CD drive.

The HDD was detected just fine by the BIOS.  And I can even boot to a LiveCD and mount it and see the files on it.  (it's an older FAT32 drive).  So I'm pretty darn sure it's installed properly.

Any help would be greatly appreciated!
Thanks!

---

### Post by noknyc on 2007-10-02
Okay, I should have thought to try this sooner.  I just unplugged the new HDD and everything booted up normally.

So what am I doing wrong?

Why is this new drive mucking up the works?

---

### Post by noknyc on 2007-10-02
Okay... just to make matters even stranger.

I tried swapping the new harddrive from slave to master.  And It booted up just fine.  I could mount it browse files, etc.  Everything was great.

I made no changes to xorg.conf or anything else (that I'm aware of),

Then I rebooted, and now I'm back to the original blank screen on bootup.

What is going on??!?

---

