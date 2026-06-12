---
title: "Unreal Tournament 2004 minimizing every 5 minutes"
date: 2008-03-25
forum: Gaming &amp; Leisure
---

### Post by dboot on 2008-03-25
I don't mean to hog your thread...but good UT2k4 support has been hard to find and you guys might have an answer to my question.

I have the full game, installed it without a problem on my 64-bit system and it runs perfectly except it minimizes EXACTLY every 5 minutes (I timed it). The game goes from full screen to a window that fits bellow my taskbar. Any ideas?

Terminal output:
```
nick@udesk:~$ ut2004 
Exporting ONS-Urban.....Successful!
Exporting ONS-Adara.....Successful!
Exporting ONS-Tricky.....Successful!
Exporting ONS-IslandHop.....Successful!
WARNING: ALC_EXT_capture is subject to change!
Defaulting to false
Defaulting to false
Resolved ut2004master1.epicgames.com -> 216.27.56.6
Connection established.
Resolved ut2004master2.epicgames.com -> 216.27.56.6
Connection established.
```

Thanks for any help!

---

### Post by Lord Illidan on 2008-03-25
I moved the post to a separate thread. Please don't hijack other threads.

As regards your problem, perhaps every 5 minutes some application is taking focus? Or a notification of some sort? Try exiting every application, then play the game.

If all else fails, from the loginscreen, chose a Failsafe Terminal session, and start ut2004 from the command line.

---

### Post by dboot on 2008-03-25
Thanks for the tips. I have nothing running except for the terminal that I used to launch the game. I've even looked at my cron jobs.

---

### Post by dboot on 2008-03-25
Screen saver!!! It's supposed to only start when idle...

---

### Post by Cappy on 2008-03-25
Solutions:
[http://ubuntuforums.org/showthread.php?t=656720](http://ubuntuforums.org/showthread.php?t=656720)

---

