---
title: "Can't login -- user/pass doesn't work"
date: 2007-11-09
forum: Dell  Ubuntu Support
---

### Post by Joe_CoT on 2007-11-09
After upgrading to Gutsy on my friend's Inspiron 1420, video didn't work (I fixed this by reconfiguring xorg). However, after that, the login screen will not allow me to login. I type in username/password, which doesn't seem to have any effect, and I'm prompted for username again. Nothing in /var/log/messages, auth.log, or gdm logs. Auth.log shows the login working! Logging in from a tty works fine. Keyboard layout is fine. Further more, logging into gnome intermittently works! Any ideas?

**Solved**: I found this in /var/log/syslog:
```
Nov  9 17:23:13 dell gdm[5251]: WARNING: gdm_slave_session_start: Execution of PostLogin script returned > 0. Aborting.
```
I found this in /etc/gdm/PostLogin
```

synclient TapButton1=0 TapButton2=0 TapButton3=0 RTCornerButton=0 RBCornerButton=0
```

Apparently a friend had added this to disable touch tapping. This caused a problem, as SHMConfig was now disabled in xorg.conf (because i reconfigured it!). In other words, completely isolated, and nothing to do with Dell. Please move this out of the Dell support forum.

---

