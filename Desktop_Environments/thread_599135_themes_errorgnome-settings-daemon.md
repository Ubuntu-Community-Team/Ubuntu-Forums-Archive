---
title: "themes error??gnome-settings-daemon?"
date: 2007-11-01
forum: Desktop Environments
---

### Post by ixlam on 2007-11-01
I just made a fresh install of Ubuntu Stuido 7.10 and used ENVY to install nVidia drivers , Compiz and the system over-all works fine but I do have this error message at login and my themes do not apply.

Unable to start the settings manager 'gnome-settings-daemon'.
Without the GNOME settings manager running, some preferences may not take effect. This could indicate a problem with Bonobo, or a non-GNOME (e.g. KDE) settings manager may already be active and conflicting with the GNOME settings manager.


and then shortly after starting "sessions" applet i get >

gnome-compiz-preferences --sm-client-id 11c0a80002000119389311800000049200009 --screen 0
No response to the SaveYourself command.
The program may be slow, stopped or broken.
You may wait for it to respond or remove it.

any takers ?

---

### Post by ixlam on 2007-11-01
interestingly enough... after reinstalling drivers etc. in recovery mode, the problem is gone!!

---

### Post by TheWired on 2007-11-02
I have the same error:
```
There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in
```

I have been having sound issues ever since I installed Gutsy. I eventually purged my linux-sound-base, alsa-utils, alsa-base, gdm, and ubuntu-desktop. Upon reboot I heard the little drums for login, but once I logged in all sound was no longer worker. Upon a 2nd reboot it did not come back. 

Seems like something I am starting up is causing the problem. So I turned off everything but Power Management daemon and Volume Control from starting up in my session. Same problems.

If anyone is out there who wants to lend a hand and may need some information from me, please let me know.

---

