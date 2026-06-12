---
title: "Dell Precision 490 Freezes after 5 minutes"
date: 2011-01-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by scacinto on 2011-01-21
Hi there,

I have a Dell Precision 490 here with two SAS disks, one with Win7 and the other with Ubuntu 10.10 64-bit.  I have tried to install Ubuntu one both disks and the same problem occurs: after being up and running for 5-10 minutes, the system freezes.  After it freezes, all I can do is hard restart using the power button.

The windows 7 disk partition (disk 1) works like a charm, it is only the disk with Ubuntu on it that freezes up.

I have checked the system hardware including memory and the two hard drives themselves and it all checks out OK.  

Is there something else I can do to troubleshoot this?  Anyone hear of this happening with SAS machines?

Thanks for any and all ideas.

Cheers,

-S

---

### Post by gordintoronto on 2011-01-21
Is there a reason you think this is linked to SAS? What CPU? What video adapter?

---

### Post by scacinto on 2011-01-21
mmm.  i'm really not sure it's a SAS thing, but i have 3 other machines that don't have problems with 10.10 - coincidentally they are all SATA.  That's all i'm going on.

The Precision has a quad-core Intel Xeon processor (5140 2.33GHz ) and an Nvidia Quadro FX 550 graphics card.

thanks,

S

---

### Post by gordintoronto on 2011-01-22
Then again, most computers run 10.10 just fine. The Precision is "unusual" in several ways: CPU, disks, video. I have no idea which one is most likely to be the source of the problem, especially since it runs OK for a while.

---

### Post by scacinto on 2011-01-24
to further add to the confusion, the same thing occurs if I attempt to run a live OS from a USB drive.  the system will run for 5-10 minutes and suddenly freeze.  the freeze occurs even if an operation is in progress (such as software update, etc.)

my next plan is to let the frozen system sit for a while to see if it changes, but i'm not holding my breath.  i wonder if the Dell Precision 490 is Linux resistant...


S

---

### Post by scacinto on 2011-01-24
okay - apparently this was solved by simply turning off the screen saver...

...does that make any sense to anyone?  i also adjusted the power settings to never put the display to sleep.

let me reiterate here that when it froze, the machine froze 5-10 minutes into operations and that (i don't believe) the mouse ever stopped moving for the 5 minutes it would take for the screen saver to activate and kill the system so the screensaver solution doesn't make a lot of sense to me.

let me also reiterate that after the freeze, the system was completely unresponsive in every way and a hard shutdown was necessary via the power button.

after the above changes, the system has been up for a record 39 minutes.

---

### Post by gordintoronto on 2011-01-24
Even if the screensaver doesn't activate, somewhere there is some code saying, "should I activate the screensaver?" -- and that code is not compatible with your computer.

It is possible 32-bit Ubuntu would work better. The Xeon processor has unique features...

---

### Post by superduperlinuxperson on 2011-01-24
sorry for writing that, did it by accident
check for a corrupted screen saver

---

