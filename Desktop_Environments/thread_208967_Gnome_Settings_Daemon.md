---
title: "Gnome Settings Daemon"
date: 2006-07-04
forum: Desktop Environments
---

### Post by kob0724 on 2006-07-04
Allright. So when ever I log on as a user in ubuntu I keep getting this error message.
```

There was and error starting the Gnome settings daemon Some things such as themes,
sounds, or backgroung settings may not work correctly. The settings daemon restarted too 
many times. The last error message was 
System exception:IDL:omg.org/CORBA/COMM_FAILURE: 1.0 
GNOME will try to restart the Settings Daemon next time you log in

```

I literally just installed ubuntu. This was my first time trying to log in as a user. I burned the CD myself (made sure to burn it at x4) and checked the md5 before hand. I've been in the mIrc channles both for ubuntu and gnome. Nobody seems to know whats going on. I've also tried going into the terminal and typing gnome-settings-daemon and that doesn't work. Whats going on here? I'm on a mac G4 and I installed ubuntu with the alternate CD.

---

### Post by eternalsword on 2006-07-15
try installing all updates via Synaptic.  make sure all of the ubuntu repositories are selected.

---

### Post by kob0724 on 2006-07-16
I solved the problem. Turns out my Mac was set to March 7 1907. This is before Unix Epoch so the Unix timestamping was getting screwed up.

---

