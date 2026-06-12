---
title: "Gparted froze up during partition resize - will my files be lost if I reboot?"
date: 2009-04-02
forum: General Help
---

### Post by sofasurfer on 2009-04-02
My Ubuntu system is on drive SDA. I have a secondary drive mounted to my file system for backups and stuff. It is partitioned with SDB1, SDB5 and SDB2.

I was resizing (shrinking) SDB5 (gparted was run in terminal) and when nearly done it froze up (or seems to be froze up. The gparted window went dim). I ran "top" and I see that gparted is using 98.2% of CPU.

If I reboot I expect that SDB5 will be shot. But will I still be able to access SDB2, which is my important backup files?

---

### Post by Cybie257 on 2009-04-02
I would try killing the Gparted process before rebooting and see if that helps. Either way, you risk your data, but killing the process while the other volume is mounted gives you that extra chance to copy the data off from it before rebooting and finding out the none of them will remount.

Or just wait it out a while and see if it ever fixes itself. It could just need the extra time.

-Cybie

---

### Post by sofasurfer on 2009-04-02
In the last hour nothing has happened. The window is still dark and the progress bar has not moved. Xorg is using 2% of CPU, firefox 3% and gparted about 85-95%. Is there a way to tell if the process is actually working or if it is really dead in its tracks? This is a bad thing.

---

### Post by Cybie257 on 2009-04-02
Well, if it's using that much CPU, then it's doing something. What it's doing is unknown, but with that much CPU usage for that long, I'm guess it's looping the code (bug), or some sort of memory leak that isn't going to let it go. 

If it were me, I'd call it a night, let it run and hope it's done in the morning. If not, you're going to have to kill it. Either by killing the process, or rebooting. 

-Cybie

---

### Post by Elfy on 2009-04-02
Not sure what is going on - but gparted can look as though it has hung and is actually doing something.

It is possible that stopping it could cause issues with the other partition - but I couldn't say for sure.

How long has it actually been running - and what size partition are you working with?

---

### Post by sofasurfer on 2009-04-02
Ok, I think I'm gonna survive.
I opened a terminal and started copying my files over to the main drive. I copied some and some more are still working. All that is left now is the multimedia files which will probably take a long time. But if I lose them its not the end of the world.

So tell me, is the problem that I used gparted from within my system? Before this I always used gparted from a live gparted cd and never had a problem.

Anyway, thanks for the replies. I will post about how it turns out. I'm sure someone will learn a lesson from my mistake.

---

### Post by Elfy on 2009-04-02
I have had gparted take hours to move and resize partitions before now - I prefer partedmagic as a livecd - not that it's any quicker, just more available on the livecd:)

If you did it from the system then I assume it was just a partition - so no it shouldn't make a difference. I have used gparted from within ubuntu without problem - hope all goes well :)

---

### Post by sofasurfer on 2009-04-02
Well, everything turned out alright. I copied all of my important file from the backup drive to the main drive. Then I went ahead and killed gparted. I was still able to access all my data with no trouble. I rebooted and it was still ok. So apparently the freeze-up occurred at the end of the process.

In case anyone has this same issue, here is the messages that were in my terminal at the time gparted froze up. I don't know what they mean...

```

======================
libparted : 1.8.9
======================

** (gpartedbin:8333): CRITICAL **: atk_object_get_parent: assertion `ATK_IS_OBJECT (accessible)' failed

** (gpartedbin:8333): CRITICAL **: atk_state_set_contains_state: assertion `ATK_IS_STATE_SET (set)' failed

```

---

