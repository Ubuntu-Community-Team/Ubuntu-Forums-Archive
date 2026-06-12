---
title: "Desktops crash after login"
date: 2007-02-08
forum: Desktop Environments
---

### Post by HeyGabe on 2007-02-08
I've been slowly rebuilding a frankenbuntu system in my basement. I'm having some troubles with the Desktop, though.  The desktop crashes after the login screen. Sometimes GNOME will get the panels up and running, sometimes it won't. Regardless, after a few seconds of gnomey desktop goodness the whole thing flakes out and dumps me back to the login screen. 

It did this with Ubuntu 6.10, Kbuntu 6.10 and Xbuntu 6.10 live CDs. 

I was finally able to install Ubuntu 6.10  with the alternative install cd.  It's installed now, but I still have the same problem. Afer a few seconds of desktop, I get dumped back into the login screen. *sigh*

I tried logging in via failsafe gnome and the same thing happened, although this time, I got an error message:  "There was an error starting the GNOME settings daemon."

[IMG]http://static.flickr.com/168/383882689_7d0a182bfb_m.jpg[/IMG]

The Good News is that the system appears to be running fine on the backend. I used the failsafe terminal to install and execute openssh so I can work on the machine remotely. I can interact with the machine via the command line all day long. Unfortunately, the person I'm planning to give this machine to probably will expect some kind of functioning desktop.  

Here's the .xsession-error log: 
```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "gabe"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/basement:/tmp/.ICE-unix/3991
Gnome-Message: gnome_execute_async_with_env_fds: returning -1
evolution-alarm-notify-Message: Setting timeout for 17569 1170979200 1170961631
evolution-alarm-notify-Message:  Thu Feb  8 18:00:00 2007

evolution-alarm-notify-Message:  Thu Feb  8 13:07:11 2007


(gnome-panel:4060): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -3 and height 24
nautilus: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
Window manager warning: Lost connection to the display ':0.0';
most likely the X server was shut down or you killed/destroyed
the window manager.
The application 'gnome-cups-icon' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.
The application 'gnome-panel' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.

** (gnome-panel:4060): WARNING **: FIXME: wait for completion unimplemented

** (gnome-panel:4060): WARNING **: panel-applet-frame.c:1267: failed to load applet OAFIID:GNOME_MixerApplet:
Unknown CORBA exception id: 'IDL:omg.org/CORBA/COMM_FAILURE:1.0'
Xlib: sequence lost (0x10000 > 0x766) in reply type 0xe0!
```


Is that helpful?
Any suggestions?

---

### Post by shareMenaPeace on 2007-02-08
Maybe this related topic helps
[http://www.ubuntuforums.org/showthread.php?t=222747](http://www.ubuntuforums.org/showthread.php?t=222747)

---

### Post by everdred on 2007-05-09
I seem to be experiencing something very similar:

[http://ubuntuforums.org/showthread.php?t=437531](http://ubuntuforums.org/showthread.php?t=437531)

Did you ever resolve your problem? And if so, how? :)

---

