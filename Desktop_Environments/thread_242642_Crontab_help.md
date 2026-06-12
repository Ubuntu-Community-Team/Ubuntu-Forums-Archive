---
title: "Crontab help"
date: 2006-08-23
forum: Desktop Environments
---

### Post by bruenig on 2006-08-23
Alright, new to using crontab. I added my username to /etc/cron.allow, and then did crontab -e, my crontab looks like this
```
# m h  dom mon dow   command
* * * * * /usr/bin/nautilus

```

My thought is that every minute nautilus should launch. But it never does. Mind you that is the entire crontab. There is nothing else. Someone suggested I add a "DISPLAY=something or other" in the file but I am not certain what that means. I tried the same thing except using totem instead of nautilus and it did the same. Also when I used ```
* * * * * rm /home/bruenig/Desktop/test
``` it worked and deleted the test document I had put up so it does do stuff. I think it might be because I am asking it to launch a graphical app. But again I am totally lost here. Any help is greatly appreciated.

---

### Post by johnsd8 on 2006-08-24
A cron job doesn't inherit your environment settings. Your friend is right - you'll need to set the DISPLAY variable for a graphical app to know where to put itself. Try this instead:

* * * * * DISPLAY=:0 /usr/bin/nautilus



Or, you should have it execute a script, where you can set more complex parameters first.

---

### Post by bruenig on 2006-08-24
yeah my intent is to put the tasks in scripts. This was more a concept question than anything else. Your advice works though, thanks.

---

