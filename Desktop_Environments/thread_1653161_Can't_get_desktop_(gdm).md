---
title: "Can't get desktop (gdm)"
date: 2010-12-26
forum: Desktop Environments
---

### Post by AbeJarano on 2010-12-26
(Meerkat) Last night I fixed the xorg.conf to get proper resolution then was installing vlc, mplayer and smplayer.  Then fusion-icon.  I uninstalled *pulseaudio*.  Installed docky, awn and cairo. I rebooted often and everything seemed to be working OK except for the audio (no alsa). Lastly I rebooted, changed the boot drive in BIOS to boot Windows.  Then this morning I rebooted, changed to the Ubuntu drive and surprise, I can't log in.  
It seems I can't log in because gdm is having a problem.  There's no errors in Xorg.X.log but a warning:

(WW) xfCloseConsole:  VT_WAITACTIVE failed:  Interrupted signal call

and in syslog 

WARNING (me: ~something like) Gdm Local Display Failure  maximum number of X display failures reached: check X server log for errors

and in daemon.log

gdm -session-worker[1967]: Glib_GObject_CRITICAL: g_value_get_boolean assertion 'G_VALUE_HOLDS_BOOLEAN (value)' failed
WARNING GdmDisplay: Display lasted 2.2... seconds
and also the warning in syslog from Gdm Local Display Factory

after erasing xorg.conf and rebooting daemon.log changed to

gdm-simple-greeter[1962] Warning default session not available

[nm-manager.c..1317] user_proxy_init(); could not init user settings proxy (3)  Could not get owner of name 'org.freedesktop.Network Manager User Settings': no such name  (I might not have the numbers and puncutation quite right)

I tried making a new user and rebooting there but not much difference and the log messages stayed the same.

Thanks, I would appreciate any help or questions.

---

### Post by sid.mallya on 2010-12-26
Strange .. I am having a similar problem and I had Docky too.

---

