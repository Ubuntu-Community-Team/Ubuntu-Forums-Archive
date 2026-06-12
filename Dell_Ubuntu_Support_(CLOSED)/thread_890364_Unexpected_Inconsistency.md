---
title: "Unexpected Inconsistency"
date: 2008-08-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by gabo.cr on 2008-08-15
I have a Dell Latitude, I installed Ubuntu and then Edubuntu desktop.
Everything was fine until I decided to download the codecs for DVD and MP3 player on Synaptic.
Then I get this error booting the computer:

/dev/sda1: UNEXPECTED INCONSISTENCY; RUN fsck manually

So I did, I said yes to all the questions, the I get a message saying:

***** FILE SYSTEM WAS MODIFIED *****

Then I rebooted the system but without being able to load Edubuntu graphics. It is saying that it was not able to load the theme and default theme. I'm getting a window to type the username and password under Gnome but then I get an orange screen and nothing happens.

What should I do now?

---

### Post by jpkotta on 2008-08-15
That sounds like hardware trouble, as in your hard drive is dying.  I would back up any important files immediately, then maybe play around with smartmontools to see if anything is out of order, and probably order a new hard drive.  It sounds like your filesystem was already corrupted, so wiping the hard drive and reinstalling might be a good idea before buying a new drive.

---

### Post by gabo.cr on 2008-08-15
Well, in fact, I do think this computer is dying, it had windows before, and it had all kinds of problems. With Ubuntu it was working like brand new, but then I get this problem.
Also the mousepad goes crazy once in a while.
Fortunately, I backed up all the files before installing Ubuntu.

I will start all over, and see what happens. :(

Thank You !!!

---

### Post by gabo.cr on 2008-08-16
I formated all the partitions and reinstalled Ubuntu and Edubuntu, then I started getting errors again, but like I said before, the mousepad was a little crazy, so I disabled the mousepad from BIOS, and now the computer is working just fine.

I think the problem was a combination between bad partitions (my fault) and a crazy mousepad (hardware).

:)

---

