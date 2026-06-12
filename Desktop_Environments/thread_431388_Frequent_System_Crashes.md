---
title: "Frequent System Crashes"
date: 2007-05-03
forum: Desktop Environments
---

### Post by andyt05 on 2007-05-03
I recently installed Feisty, and I've been having frequent total system crashes - both the keyboard and the mouse are completely unresponsive and the screen freezes.  It happens at random times, and I can't seem to replicate the behavior.  This would occasionally happen to me in Edgy too, but it was only when I experimented with Beryl, so I thought that was the cause of it.  In Feisty, it happens all the time and I'm NOT using Beryl or Compiz.  How would I go about diagnosing this problem and figure out what is causing this?

thanks

---

### Post by tgalati4 on 2007-05-03
run memtest overnight.  You may have questionable RAM.  It's located on the Live CD  under one of the options.

Have you cleaned out your machine recently?  Try reseating the RAM and blowing the dust out.  

Check /var/log for errors.  There are several files so go through them and see if anything comes up.

Something like:

tail -n 30 /var/log/messages

Some errors are normal (part of hardware detection algorithm--like SCSI disks that don't exist).  Other errors could help isolate the problem.  If it is a hardware problem, such as RAM, sometimes the system messages are not helpful  because the system is responding to machine states that are not normal.

Post some more details about your system.  Video RAM can also cause system lockups.  If you have a separate video card, try reseating it.

If this is a laptop, hook up an external monitor and see if the behavior changes.

Good luck.

---

### Post by rysh on 2007-05-03
Hi

Of course it would help when you post some relevant info about what kind of hardware you use, which drivers and so on. Is it maybe so that you are using an ATI video card?

---

### Post by Steve H on 2007-05-03
I had similar problem not so long ago, and I did everything to work it out.

It turned out to be dust clogging up the CPU fan and heatsink. Once I cleaned out the case everything has been fine since. Might be worth opening your case and having a look, just as tgalati4 suggests. Its always the simple stuff that takes the most effort to solve...

:)

---

### Post by orb9220 on 2007-05-03
Read about multiple issue's with Feisty.
Just search the forums on lockup.

I have also had this in feisty after the final release and upgrades. Not in any of the herds or beta.

This happen's whether you are nvidia or ati.

Two issue's with workarounds are 

1) wireless networking cause
3) scrolling in firefox locking it up.

I have had the system sitting there no activity while I slept. Come back and it is sitting there No mouse,keyboard,clock,conky activity all Hard Lock. Not even a ctrl-alt-backspace would reset.

Another time was scrolling in firefox all of a sudden total lockup again.

4 lockups in last 2 weeks. Alot of user's have alot more.
Had to hard boot.

---

### Post by andyt05 on 2007-05-03
Ok, well I opened the case and cleaned everything out, reseated my video card and made sure my memory was nice and snug, performed the memtest - everything passed, checked the logs - nothing unusual, i think...
I just rebooted into Feisty and so far no crashes, yet... I neglected to mention that I had searched the forums and found other users that had lock up problems due to firefox that were fixed when they switched to swiftfox.  I tried that and it did not help.

My hardware:
Athlon XP 2400+
256MB ram
ATI Radeon 9200 (open source driver)
Netgear MA111v1 usb wireless (prism2)
Leadtek WinfastXP TV tuner (bttv bt878 )

Thanks for the help everyone.  I'll let you know if the crashes start happening again.

---

### Post by whayong on 2007-05-03
Based on my personal experience, I'd say, try booting without the wireless card installed.  Should be a no brainer since it's usb.

---

### Post by andyt05 on 2007-05-03
Seems like everything is fixed! All it took was cleaning out all of the dust inside the case and reseating the video card.  I can even run beryl now with my computer dying in a horrible flaming crash!  Thanks for the suggestions.

---

### Post by Steve H on 2007-05-04
It's always the simple things that'll get ya in the end!!

Glad t' help

:)

---

### Post by tgalati4 on 2007-05-05
Penguin bowing gracefully.

---

