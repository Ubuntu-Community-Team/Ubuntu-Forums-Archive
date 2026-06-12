---
title: "Firefox crashes and lockups - an observation"
date: 2009-03-11
forum: General Help
---

### Post by jlbos83 on 2009-03-11
I have two PC running the latest versions of Intrepid and Firefox.  As nearly as I can tell the software on the two is configured the same.  One system is running am AMD Athlon 1800.  Using this system, I don't think Firefox has ever crashed or locked up.  Ever isn't a long time, three months or so.  About a month ago, I set up the second system.  I acquired it secondhand, and I don't the the details, but it is running a dual core Intel processor at 3.4 GHz.  On this machine, Firefox locks up or crashes regularly, sometimes even on the Google homepage that I've set as the default.

After messing around, and convincing myself that the problem wasn't strictly a plug-in, I decided to think about what was different about the machines.  The second core was an obvious difference.  So, I looked in the BIOS for a way to disable it, and came upon "I/O APIC Mode".  I disabled that, and in a quick test (there's not anything I have found that I can always crash on) the problem seemed to go away.  The I read that if I booted into Windows in this configuration, I would probably be very unhappy with what happened, so I restored it to enabled.

Then I found out about adding "noapic nolapic" to the grub menu.lst, and it seems again that the problem is gone.  That is the good news.  But, if I understand correctly, now I am only using one core of the processor.  For most things I will probably never know the difference, but is is annoying, if nothing else.

Are there any suggestions on where to go from here?  

Thanks!

---

### Post by jlbos83 on 2009-03-11
After some more messing around, I find that I can also just disable multi thread support in the BIOS, and not crash.  Again, now I am only using one core.

Any thoughts?

---

### Post by jlbos83 on 2009-03-17
OK...
After most of a week, the theory has become pretty solid.  I have not had a Firefox crash or lockup since I made the change.  I did go back and put "noapic nolapic" in the menu.lst, and reenabled it in the BIOS, as I don't want to mess up my dual boot.

I think that I also had a few Thunderbird crashes during the time Firefox was crashing.

What I wish I could remember is whether the crashing started at the time of the last kernel update.  I may do a bit of an experiment over the next few days, and run the previous kernel to see if I can tell.

Anyway, I think that there is a bug.  Whether it is an Ubuntu bug, or a Firefox/Mozilla bug is not completely clear just yet.

---

### Post by jlbos83 on 2009-03-20
I ran for a while two nights ago with the previous kernel, and without noapic nolapic.  It seemed that things were better, but eventually I did have a firefox lockup.  I was messing with other things at the time, so it was not a difinitive experiment.

I do think that it is clear that there is a bug which is hard for me to allocate to Ubuntu or Firefox, or even the hardware.  It seems to be mostly the way the three interact.... I guess in the end, I would "blame" the OS, but I'm not hard over on that!

I'm tempted to do a clean install, and see if it might be that something has been corrupted as I've gone through my Ubuntu learning curve.  Thoug the thought of getting things set up again isn't all that attractive!

---

