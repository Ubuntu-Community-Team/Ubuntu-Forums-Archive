---
title: "Disfunctional User Account and ATI"
date: 2006-06-13
forum: Desktop Environments
---

### Post by RudolfMDLT on 2006-06-13
Hi,
I had trouble installing ATI drivers, finally got them installed. Now when I log into my account, the desktop appears, icons start popping up and gaim  starts connecting and suddenly, the screen goes black, TTY1 appears and I'm back at the login screen. I can log into root, or any other account(including my own) on the system, but only my account bombs out. I found a hidden error log in my home folder .xsession-errors:
> 
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "rudolf"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/rudolf:/tmp/.ICE-unix/5368
Gnome-Message: gnome_execute_async_with_env_fds: returning -1
gaim: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
update-notifier: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
Window manager warning: Lost connection to the display ':0.0';
most likely the X server was shut down or you killed/destroyed
the window manager.
The application 'gnome-panel' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.
The application 'gnome-session' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.
1150186023.547900 Session manager: gsm-remote-desktop.c:107: remote desktop server died, restarting
1150186023.548330 Session manager: gsm-remote-desktop.c:130: activation of OAFIID:GNOME_RemoteDesktopServer failed: System exception: IDL:omg.org/CORBA/COMM_FAILURE:1.0
The application 'nautilus' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.

The first time this happened installing the ATI drivers got me back in my account but with NO graphics acceleration(glxgears -printfs runs at 250fps). Currently in my other accounts, glxgears runs at 1800fps. 

I tried to create a new account for myself but the option is not available in ROOT or any other account under System => System Administration.

Can some one please tell me how to fix my account or how to create a new account either in one of the text shell modes or in Gnome.

Thank you!

EDIT: I found away to creat user accounts. Upon creatin the new account my drivers where reverted back to Mesa. Does anybody know what the above error means?

---

