---
title: "[SOLVED] Random restart of Gnome Desktop w/ XMMS"
date: 2008-03-13
forum: Desktop Environments
---

### Post by azimuth on 2008-03-13
The Desktop just restarts and waits for login. This just started yesterday after I installed IcePodder and it uses XMMS for the default player. IcePodder can run and no problem, unless XMMS is playing. I can manually play the podcasts (oggcasts) in VLC w/ IcePodder still open and again no problem. My syslog shows:```
Mar 13 11:00:35 asus gdm[5721]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0
```

I really prefer VLC as the player, but can't find an option in IcePodder to change players. I've used VLC as the player in Juice (on winXP) for some time and prefer to use it here rather than fix the XMMS problem. It's a pain not being able to one click play the unheard podcasts. Anybody know how to force the player in IcePodder or have ideas as to why XMMS crunches my desktop?

---

### Post by azimuth on 2008-03-14
I have more or less solved this myself. The problem appears to be an interaction between XMMS and my screensaver. Simple fix, turn off the screensaver. I don't like XMMS much and would still prefer to replace it as the default for IcePodder But, that's for another thread.

---

