---
title: "e17 system tray?"
date: 2006-04-03
forum: Desktop Environments
---

### Post by drotter on 2006-04-03
is there a system tray for e17?  When i have a deamon running the background like gaim or limewire i cant tell if its running or not without running top or something.

If there is one does anyone know how to install a module in e17?  I'm not sure how to do that.

thanks for the help

---

### Post by nlogax on 2007-04-28
You can always use a standalone SysTray, such as Trayer or Docker.  They seem to work okay if you use the right command line parameters, e.g.:

 trayer --edge bottom --align right --distance 41 --widthtype request --heighttype request

 (I use '--distance 41' to place it directly above the shelf at the bottom of my screen)

---

### Post by sachetto on 2007-06-18
Awesome  :popcorn:

Thank you very much for the tip. I was searching for a system tray on e17 :D

---

### Post by nlogax on 2007-09-16
If you are using Ubuntu Gutsy (7.04), you can now install 'stalonetray' which is a lot prettier than trayer.

However, if you're using an earlier version of Ubuntu I DO NOT recommend you upgrade to Gutsy until it has been released, because it still has many rough edges and many things may be broken for you.

---

### Post by octoberdan on 2007-10-29
[http://www0.get-e.org/Main/FAQs/#57](http://www0.get-e.org/Main/FAQs/#57)

> **nlogax said:**
> If you are using Ubuntu Gutsy (7.04), you can now install 'stalonetray' which is a lot prettier than trayer.

Thanks for the stalonetray tip, I worked it into my Elbuntu tutorial. 
and Ubuntu Gutsty (7.10) has been released! Make sure you upgrade.

---

### Post by octoberdan on 2007-10-29
I ended up writing how to have the systray start when you start e. You have to create a .desktop file and then tell e17 to run it at startup. I go over [the details]("http://octoberdan.wordpress.com/2007/10/29/installing-elbuntu-e17-for-ubuntu/") on my blog

---

