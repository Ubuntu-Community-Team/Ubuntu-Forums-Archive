---
title: "Auto poweroff / shutdown"
date: 2008-12-15
forum: General Help
---

### Post by havencruise on 2008-12-15
Hey all :).. Was wondering if there's a way to poweroff my computer at a desired time of the day. I tried searching all the threads on this topic, and did try all the suggestions applicable to me.. But none seem to actually work. There's one thing i didn't try, and thats using a script. I'm sure there other ways apart from running a script to poweroff. Can anyone please suggest me a working solution?

---

### Post by havencruise on 2008-12-15
Any body have any ideas?

---

### Post by SoCalChris on 2008-12-15
Create a cron job to turn the computer off at a certain time. We'll create it using sudo since a shutdown requires admin privileges.

From a console, type
```
sudo crontab -e
```

In the file that opens, insert a line saying
```
0 1 * * * halt
```

This will shut down your computer at 1am every day. Check out the [crontab syntax]("http://en.wikipedia.org/wiki/Cron#crontab_syntax") to change the time/days that the shutdown occurs on.

---

