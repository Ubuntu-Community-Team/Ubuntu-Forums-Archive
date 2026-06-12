---
title: "There was an error starting the GNOME Settings Daemon."
date: 2007-12-04
forum: Desktop Effects &amp; Customization
---

### Post by decaren on 2007-12-04
Hey guys, I'm having trouble here.  I just installed Ubuntu Studio last night on my new Acer Extensa 4620 Laptop.  Everything went great except it didn't pick up any of my network cards.  So it didn't install networking.  After messing with it until I completely broke it, I had to reinstall which this time I plugged a hard line out of my router and everything went smooth.  I got an error about the GNOME Settings Daemon the first couple times then fine after that.  Then I noticed that plugging my headphones in didn't work, so I had to update the alsa driver.  Reboot after that and I keep gettting

There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Failed to connect to socket /tmp/dbus-UbsILygtoX: Connection refused

GNOME will still try to restart the Settings Daemon next time you log in.

And of course my Ubuntu Studio Theme isn't working.  Here is my ~/.xsessions.error file:

(process:5522): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.

(process:5526): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/dc-subu-m1:/tmp/.ICE-unix/5519
Window manager warning: Failed to read saved session file /home/aydada/.metacity/sessions/default0.ms: Failed to open file '/home/aydada/.metacity/sessions/default0.ms': No such file or directory
** Message: Not starting remote desktop server
libnotify-Message: Unable to get session bus: Failed to connect to socket /tmp/dbus-UbsILygtoX: Connection refused
Initializing nautilus-image-converter extension
Initializing gnome-mount extension
libnotify-Message: Unable to get session bus: Failed to connect to socket /tmp/dbus-UbsILygtoX: Connection refused
system-config-printer-applet: unable to initialize pynotify
system-config-printer-applet: failed to connect to session D-Bus

I'm completely lost now.  Please help

Update:  I can CTRL-ALT-Backspace to restart and it comes up without the error just fine.

---

### Post by dast on 2007-12-06
I just upgraded from 7.04 to 7.10 and I can confirm this bug happened to me

$uname -a
Linux wolf 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux

See the following bugs.

[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/146946](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/146946)
[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/138277](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/138277)

Unlike some people, I found that i could start the daemon from the command line. So... I "fixed" the problem by going under System > Preferences > Sessions (in the main Gnome menu) and adding a startup program entry for the daemon. That does not work for everyone, apparently. Others have hacked up init.d scripts (i believe) to start this daemon, which I opted not to try.

See also
[http://ubuntuforums.org/showthread.php?t=587410&highlight=gnome+settings+daemon](http://ubuntuforums.org/showthread.php?t=587410&highlight=gnome+settings+daemon)

---

