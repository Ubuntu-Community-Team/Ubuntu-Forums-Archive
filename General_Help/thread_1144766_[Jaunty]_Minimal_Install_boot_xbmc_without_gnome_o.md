---
title: "[Jaunty] Minimal Install: boot xbmc without gnome or fxce or kde"
date: 2009-05-01
forum: General Help
---

### Post by Tasu on 2009-05-01
Hi all,
I'm looking for a way to setup my eeebox b206 as a standalone set top box, I'm trying to install a minimal system, via ubuntu minimal cd [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD) .
The Asus box comes with an integrated ATI Radeon Mobility HD3450, I would like not to have to install a full desktop, even mminimal, to start the xbmc in full screen/standalone mode.

The steps taken so far (that leaded to just a system that tries to run the Xserver, but revert to shell due to errors), are:

1) Installed the ubuntu minimal
2) apt-get install xorg-driver-fglrx fglrx-modelines
3) added the ppa for xbmc 
4) apt-get install xbmc
5) Write a custom init.d script to start the server

The init script is this:

```

#!/bin/sh
#/etc/init.d/xbmc

# export set __GL_SYNC_TO_VBLANK=1
export set DISPLAY=:0


# starting Xorg and XBMC For Linux
case "$1" in
  start)
        exec /usr/bin/startx # > /dev/null 2>&1 &
        sleep 2
        exec /usr/bin/xbmc --standalone #> /dev/null 2>&1 &
        ;;
  stop)
        killall Xorg
	killall xbmc
        ;;

esac

exit 0

```

Anytime I reboot, I just see the x server try to run, but falling down to the shell with errors like: "swlDalGetDisplayIndex:ERROR: The number of Active Displays is 0".

Is there a way to boot into a graphic mode, with just the xbmc without having the complete i.e. Gnome desktop (autostarting from there the xbmc)?

Thank you.

---

### Post by Tasu on 2009-05-01
Some more insight:

After the nth fail during the boot, I tried to ssh into the box and manually startx (sudo startx), this time the server looks like it's started, in fact the screen became black, hiding the shell (why it happens if I start it by hand and not via the init script? do I have to be logged in to run startx? Can't it be done by an init script?
But as soon as I try to run xbmc it won't start with this error:

```

$ sudo xbmc
[sudo] password for administrator: 
/var/lib/python-support/python2.6/gtk-2.0/gtk/__init__.py:72: GtkWarning: could not open display
  warnings.warn(str(e), _gtk.Warning)
Error: unable to open display 
FEH.py: cannot connect to X server 

```

Looks like it's not started this X server... how comes? If it's not started, what is that black layer that blanks my screen?

I'm almost sure the X server is there, infact:

```

$ ps aux | grep X
root      3777  0.0  0.0   2908   824 pts/0    S<+  08:33   0:00 xinit /etc/X11/xinit/xinitrc -- /etc/X11/xinit/xserverrc :0 -auth /tmp/serverauth.dtcUdNtgJq
root      3778  0.4  3.2  51336 33372 tty9     S<s+ 08:33   0:02 /usr/bin/X11/X -nolisten tcp

```

Thanks again.

---

### Post by Tasu on 2009-05-01
It looks like I solved (almost, it's strange I have to use the --no-test switch, since xbmc complains about not finding the hardware acceleration, but as it starts is not slow at all, all the effects are good.. anyway)

Thanks to this post: [http://ubuntuforums.org/showthread.php?t=1125476](http://ubuntuforums.org/showthread.php?t=1125476) I tried to change my init script to this:

```

#!/bin/sh
#/etc/init.d/xbmc

# starting Xorg and XBMC For Linux
case "$1" in
  start)
        xinit /usr/bin/xbmc --standalone --no-test
        ;;
  stop)
	killall xbmc
        ;;

esac

exit 0

```

And now the system works! ^_^

---

