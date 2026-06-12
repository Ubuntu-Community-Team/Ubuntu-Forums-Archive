---
title: "Newbie in FVWM, have a question"
date: 2009-07-25
forum: Desktop Environments
---

### Post by dustin.xu on 2009-07-25
Hi, 

   I just start to learn fvwm, I installed it from APT->log out from current GNOME->select session, fvwm->login, but then I found I could not connect to Internet? Why? 


   Is there any steps incorrect above?


   Thanks, ;)

---

### Post by jpkotta on 2009-12-06
It is almost certainly not a window manager problem, but more likely something that has to do with the network that usually gets run in a Gnome session is not being run in the Fvwm session.  You can see if your network is up with ```
ifconfig
```

More recent versions of Ubuntu have changed the way the network is configured.  I've never had good luck with network-manager (outside of Gnome at least), but [wicd]("http://wicd.sourceforge.net/") works well.

---

