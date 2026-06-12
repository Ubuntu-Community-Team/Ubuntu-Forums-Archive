---
title: "disable screen blanking on 12.10"
date: 2013-04-24
forum: Desktop Environments
---

### Post by xkaliburx on 2013-04-24
Searching gives you 100 + answers / try's with numerous versions, but I am a bit stuck as none have worked.  I have a current up to date lubuntu 12.10 I am using to run a web app, so the config does autostart chrome --kiosk mode as well as unclutter (to hide the mouse).

Problem is after 10 minutes the screen goes black.   I had the default screensaver (xscreensaver) disabled, but it would still take over, so I did remove it via apt.   Same thing, right now there is NO screensaver even installed yet it blacks out.   I read where caffeine can tell if an app is active and force no screensaver, but trying to install fails due to a dependency of a python mod, even trying to re-install xscreensaver I am told it's not available but referenced by another.  I noticed ALL the sources are commented in sources.list, but uncommenting didn't help.  

So, I am not sure how to either fix the sources (I would think xscreensaver is in the defaults since it came with the os), or get caffeine and it's dependencies installed.

Thanks to all read/replies.

---

### Post by rrich1974 on 2013-04-24
why dont you install caffeine and you can disable screensaver when you need it. 

[http://linuxg.net/install-caffeine-in-ubuntu-12-04-and-ubuntu-12-10/](http://linuxg.net/install-caffeine-in-ubuntu-12-04-and-ubuntu-12-10/)

---

