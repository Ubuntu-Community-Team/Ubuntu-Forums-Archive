---
title: "Lock screen on startup?"
date: 2006-08-23
forum: Desktop Environments
---

### Post by sizzam on 2006-08-23
I have the GDM Login Window set up to automatically log my account when Ubuntu boots up.  I do this so that I can reboot my machine remotely and have VNC access to the :0 display.   I know there are other ways to set up VNC to correct this, etc, there are lots of threads about that.

[B]Here is exactly what I want to know:

What can I put into System > Preferences > Sessions > Startup Programs so that the screensaver will lock itself automatically when my account logs in?[/B]

In Breezy, I used to use:

```
xscreensaver-command --lock
```

However, in Dapper, xscreensaver was replaced with gnome-screensaver.  I tried adding this to the Startup Programs:

```
gnome-screensaver-command --lock
```
But, that doesn't seem to work from Startup Programs.  It works fine from a regular terminal, but just doesn't seem to execute from Startup Programs.   I haven't been able to capture any error output as to what's happening when it tries to run.

So, can I write some sort of batch script to do this, or do you have some other way to get the screensaver to lock from Startup Programs?   Can we leverage Ctrl+Alt+L somehow, or can I write a script that runs /etc/acpi/lockbtn.sh as SUDO somehow without me having to type in a password?

---

### Post by mlind on 2006-08-23
Misread your post earlier. Does ~/.xsession-errors contain any info why this fails?

---

### Post by sizzam on 2006-08-24
> **mlind said:**
> Misread your post earlier. Does ~/.xsession-errors contain any info why this fails?


Yes, I get a line that says:
**gnome-screensaver-Message: Screensaver is not running!**

Here is a log of everything that happens during my boot process (edited username and machine name):

```

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "MYUSERNAME"
/etc/gdm/Xsession: Beginning session setup...
INFO: imwheel started (pid=23195)
imwheel(17894): Operation not permitted
xmodmap:  commandline:1:  bad number of buttons, must have 11 instead of 7
xmodmap:  1 error encountered, aborting.
imwheel: the -p option is deprecated.
WARNING: kill imwheel(pid=17894) failed: Operation not permitted
INFO: imwheel started (pid=23201)
Bonobo accessibility support initialized
GTK Accessibility Module initialized
SESSION_MANAGER=local/MYMACHINENAME:/tmp/.ICE-unix/23151
GTK Accessibility Module initialized
GTK Accessibility Module initialized
GTK Accessibility Module initialized
Bonobo accessibility support initialized
Bonobo accessibility support initialized

(gnome-panel:23229): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `dest_width > 0' failed
Initializing nautilus-open-terminal extension
GTK Accessibility Module initialized
Gnome-Message: gnome_execute_async_with_env_fds: returning -1
Bonobo accessibility support initialized
GTK Accessibility Module initialized
GTK Accessibility Module initialized
Bonobo accessibility support initialized
Bonobo accessibility support initialized
GTK Accessibility Module initialized
GTK Accessibility Module initialized
Bonobo accessibility support initialized
GTK Accessibility Module initialized
Bonobo accessibility support initialized
gnome-screensaver-Message: Screensaver is not running!
GTK Accessibility Module initialized
Bonobo accessibility support initialized
GTK Accessibility Module initialized
Bonobo accessibility support initialized

```

---

### Post by mlind on 2006-08-24
I'm not sure what's the easiest way to accomplish this. gnome-screensaver doesn't seem to have a daemon process, so it's harder to determine when it's running or not.

It does register itself to D-BUS though, and you can query D-BUS when this registration has happened, then launch gnome-screensaver-command.
```

http://cvs.gnome.org/viewcvs/*checkout*/gnome-screensaver/doc/gnome-screensaver.html?rev=1.1

```

---

### Post by steve.horsley on 2006-08-24
Maybe it's a timing issue. How about launching a script that goes something like:
#!/bin/sh
sleep 10
gnome-screensaver-command --lock

---

### Post by mlind on 2006-08-24
> **steve.horsley said:**
> Maybe it's a timing issue. How about launching a script that goes something like:
#!/bin/sh
sleep 10
gnome-screensaver-command --lock

That's probably the easiest way to do it. Although querying DBUS on certain intervals allows you to re-activate screensaver when it's not active, like desktop environment does when system has been idle for certain time.

---

### Post by mccann on 2006-08-24
The reason it isn't working is because gnome-settings-daemon starts the screensaver 25 seconds after login:

[http://cvs.gnome.org/viewcvs/gnome-control-center/gnome-settings-daemon/gnome-settings-screensaver.c?view=markup](http://cvs.gnome.org/viewcvs/gnome-control-center/gnome-settings-daemon/gnome-settings-screensaver.c?view=markup)

---

### Post by sizzam on 2006-09-15
Hmm, that explains it.

The move to gnome-screensaver from xscreensaver really confuses me.  We've really lost a whole lot of functionality and were better off before IMHO.  I know you can switch back, I just think it was an odd decision.

---

