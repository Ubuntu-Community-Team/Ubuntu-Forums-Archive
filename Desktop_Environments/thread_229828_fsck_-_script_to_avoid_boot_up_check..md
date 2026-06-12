---
title: "fsck - script to avoid boot up check."
date: 2006-08-05
forum: Desktop Environments
---

### Post by musther on 2006-08-05
Ok, here's the thing.  I don't like having to sit through the forced fsck every 30 mounts, so I was about to write a script to set the partitions to check at the next boot and then restart the system.  It would work like this.

1   Set all partitions to be checked next boot
2   Restart computer

Then I though, hey, with the help of the people on the forums, we can do better than this.  What would be great is a script (or set of scripts), called on boot (or on user login) that would do this:

1   Check disk mount counters, if any disk is nearing 30, alert user (notification area would be great)
2   When the user decides to check disks, provide two options.

   Option 1 - check and then turn of computer
      
      1   Set partitions to check at next boot
      2   Restart computer to allow fsck to occur
      3   After booting completed, shut down and halt

   Option 2 - check and return to OS

      1   Set partitions to check at next boot
      2   Restart computer to allow fsck

That's it, quite simple in theory, but it would be good to have some graphical interface so that it's user friendly.

What do you think, anyone fancy working on this?

-----EDIT-----
Actually, there's no need to reboot at all is there, just unmount FS and then check, then either shutdown or just sit there.

---

### Post by maniacmusician on 2006-08-05
Having no idea how to do it, I can't really help, but I have a request, sort of...if this does get worked on, could you do it in a public environment like a thread, where everyone can see your work and progress? Because though I have no idea how to write scripts of any kind, I want to start learning stuff like that so that I can do more things myself, learn more, etc.

---

### Post by musther on 2006-08-05
Well I know how to do some basic scripting, I know how to do a string of commands and use zenity for basic graphics.  I could write a script to check the partitions of my PC, but it would be ugly and would only work for my PC (have no ability to do all partitions, it would just do what I told it) so I thought I'd post here and see what happened.

After thinking about it a bit more I think it should 

1  check the counter to see if it's near 30
2  offer to do check now
---when commanded to do check---
3  remount partitions as read only
4  check partitions
5  either shutdown and halt, or simply exit the script

A nice zenity (or similar) percentage progress bar would be very nice, then more advanced things like estimated time remaining (if it's possible).

---

