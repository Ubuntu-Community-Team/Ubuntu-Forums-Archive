---
title: "How To: Task Scheduling"
date: 2009-05-25
forum: General Help
---

### Post by pramathesh on 2009-05-25
Is there any way in Ubuntu wherein I can schedule Bit Torrent to start at 2:15 am and then my laptop to shutdown at 7:45am. Since this is the time frame during which my ISP doesn't charge for downloading. I'm not much into the command line so a GUI if possible will surely go that extra mile.

---

### Post by pramathesh on 2009-05-25
no scheduling apps!!?:(

---

### Post by Girl™ on 2009-05-25
Sure there are. You should read up on cron jobs. I would have given you more help here if I knew what the syntax would look like (for you specific case).

---

### Post by _Purple_ on 2009-05-25
[http://ubuntuforums.org/showthread.php?t=374124](http://ubuntuforums.org/showthread.php?t=374124)

---

### Post by rizman on 2009-05-25
This could be useful:
[http://www.ubuntugeek.com/schedule-tasks-using-gnome-schedule-a-cron-at-gui-in-ubuntu.html](http://www.ubuntugeek.com/schedule-tasks-using-gnome-schedule-a-cron-at-gui-in-ubuntu.html)

---

### Post by pramathesh on 2009-05-25
transmission isn't working whereas shutdown works flawlessly. More so If I manually run the task from the same Gnome-Schedule GUI. Transmission starts off no fuss at all. It's just that it wouldn't work when set to run automatically at a desired time

---

### Post by rizman on 2009-05-25
You could try what is suggested here:
[http://ubuntuforums.org/showthread.php?t=863910](http://ubuntuforums.org/showthread.php?t=863910)
though I don't really know what this DISPLAY thing is doing

---

### Post by kpkeerthi on 2009-05-25
Open your crontab (**not the super-user's**)
```

crontab -e

```

and add these lines:

```

15 02 * * * env DISPLAY=:0.0 /usr/bin/transmission
45 07 * * * env DISPLAY=:0.0 /usr/bin/killall transmission

```

---

### Post by pramathesh on 2009-05-25
I tried the link posted by _Purple_ but I wonder if I'd be getting to see anything when this thing kicks off as per schedule.....

---

### Post by pramathesh on 2009-05-25
Just did wht Mr.kpkeethi said let's wait till 2:15 IST and see what happens I hope I do get to see a GUI at that time.

---

### Post by colau on 2009-05-25
> **rizman said:**
> This could be useful:
[http://www.ubuntugeek.com/schedule-tasks-using-gnome-schedule-a-cron-at-gui-in-ubuntu.html](http://www.ubuntugeek.com/schedule-tasks-using-gnome-schedule-a-cron-at-gui-in-ubuntu.html)
Nice tip.

---

### Post by pramathesh on 2009-05-25
@ kpkeerti
Out of curiousity what entries should be changed if I want utorrent to start in place of Transmission. Everything else remains the same.

---

### Post by XCan on 2009-05-25
Since mutorrent apparently only works for Windows natively I would say

15 02 * * * env DISPLAY=:0.0 wine /path/to/mutorrent
45 07 * * * env DISPLAY=:0.0 /usr/bin/killall mutorrent

Exchange mutorrent with the real filename.

---

### Post by dragos_iliescu_2005 on 2009-05-25
Try scheduling using webmin

---

### Post by kpkeerthi on 2009-05-25
> **pramathesh said:**
> Just did wht Mr.kpkeethi said let's wait till 2:15 IST and see what happens I hope I do get to see a GUI at that time.

You don't have to wait till 2:15 am to check out if it would work. Just set the cron to trigger in about a 2 minutes from now and test it.

---

### Post by kpkeerthi on 2009-05-25
> **pramathesh said:**
> @ kpkeerti
Out of curiousity what entries should be changed if I want utorrent to start in place of Transmission. Everything else remains the same.

Sorry I've never used anything that runs on wine.

---

