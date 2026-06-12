---
title: "ssh -X is notsending me the signal"
date: 2013-01-12
forum: Desktop Environments
---

### Post by Synoc on 2013-01-12
I ssh into my server with "ssh -X servername" the user names are identical. I type in anything say "dolphin" to open up the file manager I get 
```

Cannot find the D-Bus session server:  "/bin/dbus-launch terminated abnormally with the following error: Autolaunch error: X11 initialization failed.

```
why? This was after a recent update. I do no know if this matters

---

### Post by tgalati4 on 2013-01-12
ssh -2 -Y username@servername dolphin

---

### Post by Synoc on 2013-01-13
if that does work (suddenly started working again over here) why does or did -X fail all of the sudden. If I do not know why it happened, I can't figure out how to fix it.

---

### Post by tgalati4 on 2013-01-13
man ssh

The -Y switch assumes "trusted" forwarding of the X-session, where -X requires going through an xsession security/authority check.  If this fails, then no session.

Check your log files (/var/log) on both machines to get the details.  Most likely auth.log.

Depending on what you updated, you may need to reboot to allow the new code to work correctly.

---

