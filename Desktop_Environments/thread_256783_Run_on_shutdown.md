---
title: "Run on shutdown"
date: 2006-09-13
forum: Desktop Environments
---

### Post by amsch on 2006-09-13
Hello!

I have a small backupscript and I want to run it everytime I shutdown (or reboot) my computer. How can I do this?

Thanks!

---

### Post by Jussi Kukkonen on 2006-09-13
You can do that with init-scripts -- /etc/rc.local is probably the place to add stuff like that. 

If you just want to run a script once a day, take a look at anacron (*man anacron*), that might be a good solution.

---

### Post by amsch on 2006-09-14
Thanks for your answer - I want to run the script to run every time I shut my computer down! Isnt rc.local executed on start-up?

Gentoo had the /etc/conf.d/local.stop script - is there no script in ubuntu?

Thank you!

---

### Post by Jussi Kukkonen on 2006-09-15
Weird, /etc/rc.local is referenced in /etc/init.d/rc.local, which in turn is symlinked to /etc/rcX.d/ for X runlevels, just as I thought. But now that I read /etc/init.d/rc.local, it only supports starting services and it is not run for runlevel 6... I have no idea what that is about.

I guess you could just put your own script as the first script in /etc/init.d/rc6.d, but I have a feeling there's a right way to do this also...

---

### Post by amsch on 2006-10-05
I have added a symbolic link in /etc/rc6.d but it does not work - the script is not executed!

---

### Post by clarknova on 2006-10-05
I know you're not an idiot, but I'm an idiot, so if I were you, I would:

1. run the script manually to make sure it works
2. **ls -l /etc/init.d/rc6.d** to make sure your link is valid and correct
3. try adding a symbolic link to your script in /etc/init.d/rc0.d

---

### Post by amsch on 2006-10-07
I have found the problem: Runlevel 6 is reboot not sutdown - I have linked it now to Runlevel 0 (shutdown) and now it works!

Thanks very much!

---

