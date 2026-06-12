---
title: "XFCE shutdown problem (not the password one)"
date: 2006-01-01
forum: Desktop Environments
---

### Post by Genesius on 2006-01-01
Started out using Gnome but wanted to play with other window managers and decided I like XFCE. Just one problem - when I shutdown XFCE closes but my system won't power off, it just takes me to a terminal login.

How can I get XFCE to power down my system?

---

### Post by kaamos on 2006-01-01
Well this is not a very elegant solution, but you could edit the menu and add an entry "shut down" that executes the command ```
gksudo "shutdown -h now"
```

---

### Post by vayu on 2006-01-08
My system will shutdown, you just have to wait awhile.  What it does that's annoying is it goes to a login looking prompt (you can't actually login) and waits there without showing the normal shutdown messages.  It will eventually just powerdown.  

Anyone know how to get XFCE to show the shutdown dialog while it's shutting down?

---

### Post by Suger on 2006-01-08
No, same problem here, and it's an Ubuntu problem, I'm also running XFCE on an OpenBSD box and it shuts down like a charm

---

### Post by xenon2000 on 2006-01-17
[QUOTE=vayu]My system will shutdown, you just have to wait awhile.  What it does that's annoying is it goes to a login looking prompt (you can't actually login) and waits there without showing the normal shutdown messages.  It will eventually just powerdown.  

Anyone know how to get XFCE to show the shutdown dialog while it's shutting down?[/QUOTE]

My IBM Thinkpad does the same thing. I choose "shutdown" and it quits Xwindows and goes to a login prompt. I wait about 30 secs and then it shuts off as expected. Would be nice if instead it would act more like Gnome Ubuntu and just show the red text saying that the system is going to shutdown (or reboots as the case my be).

Really I don't care what it looks like or says when I know it's going to shutdown or reboot. But 30sec is kinda slow for shutting down after it's already quit Xwindows session. Doesn't seem to have this long of a pause when normal Ubuntu install does a shutdown/reboot.

---

### Post by kaamos on 2006-01-17
You can press control+alt+f7 to see the shutdown messages. On my machine the shutdown time is the same though.

---

### Post by laffinet on 2008-04-12
I've got the exact same problem.

I'm running hardy (Gnome) on a Lenovo Thinkpad R61i and only recently it's taking a long time to shut down.

After I choose shut down or reboot it goes to the login prompt, then it doesn't seem to be doing anything for a while and then it finally shuts down. Any ideas ?

Thanks.

---

