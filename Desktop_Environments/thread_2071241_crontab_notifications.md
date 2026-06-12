---
title: "crontab notifications"
date: 2012-10-14
forum: Desktop Environments
---

### Post by dexter197 on 2012-10-14
I want to use a crontab to send a notification every day at 9 pm. I have the following "crob tab job" :

00 21 * * * notify-send 'Title of the message' 'Text of the message'

According to me, it should work, however nothing happens... Does anybody know why and how can I solve it.

I am using ubuntu precise pangolin 32 bits.

Thanks in advance :)

---

### Post by Cheesemill on 2012-10-15
You probably need to tell crontab which display to use (crontab doesn't know if the X server is running or not).

Try this instead:
```
00 21 * * * env DISPLAY=:0 && notify-send 'Title of the message' 'Text of the message'
```

---

### Post by dexter197 on 2012-10-15
Thanks, however it didn't work either. Is there a way to check if the cron process is running at the time? This way I could determine if the cron job is actually working or not (so i can focus on the real problem.

---

### Post by steeldriver on 2012-10-15
Is this a system crontab, or a crontab belonging to the user who currently 'owns' the display? if it's a system crontab then you may need to fix the Xauthority as well as setting the DISPLAY variable - see this similar thread: [http://ubuntuforums.org/showthread.php?p=12248336](http://ubuntuforums.org/showthread.php?p=12248336)

---

