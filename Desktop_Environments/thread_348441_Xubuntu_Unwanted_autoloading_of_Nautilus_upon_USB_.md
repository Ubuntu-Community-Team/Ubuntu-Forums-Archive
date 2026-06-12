---
title: "Xubuntu: Unwanted autoloading of Nautilus upon USB memory key insert"
date: 2007-01-28
forum: Desktop Environments
---

### Post by afoglia on 2007-01-28
Somehow my preferences got corrupted and now when I insert a usb memory key, Nautilus autoloads.  Oddly the first time, only one Nautilus window opens, but my desktop is unchanged.  The second time, five windows open (one to the memory key and 4 to my hom directory) and my desktop background and icons change to the Nautilus ones.  If anything were to open, I'd like it to be Thunar.

This also happens if I log out and then back in between the two insertions.  (And a 'pgrep nautilus' showed no instances running immediately after the second login.)


I don't care what originally caused the problem, just how to fix it.  But if it helps, the only likely initial causes of the problem were either (1) when I logged in via NX recently and because I apparently can't log into as an XFCE session when I'm already on an XFCE session locally, I had to use Gnome, or a time soon after when the laptop appeared to hang during a NX XFCE session and I had to reset or (2) when I restarted everything looked okay, except my Applications menu was gone (which I simply rebuilt using the "add new item" option to the panel).

---

### Post by Pobega on 2007-01-28
Are you using the Xfce mounting tool? That's the only thing I know of that supports running a command after mounting an external device.

---

### Post by afoglia on 2007-01-29
> **Pobega said:**
> Are you using the Xfce mounting tool? That's the only thing I know of that supports running a command after mounting an external device.

Which Xfce mount tool are you talking about?  I just ran a pgrep for automount and udev.  The former is not running, but udevd is.  And according to the man page it can be configured to "run additional programs as part of the device event handling.".

I don't remember setting up any automounting programs when I installed Xubuntu.  And I think I installed dapper and then upgraded to edgy, if that matters.

---

### Post by afoglia on 2007-01-29
You encouraged me to do more digging.  Apparently gnome-volume-manager was running (probably configured with ubuntu-desktop package), and that appeared to be calling nautilus.  Unchecking the "Browse removable media when inserted" solved the problem.  (That doesn't explain why it would launch multiple copies, though.)

Is there a standard xubuntu way of doing the automounting?

Now there is another (possibly related) problem, when I try to open the USB flash drive by double clicking, Thunar does not run.  The .xsession-error line is: ** (xfdesktop:6149): CRITICAL **: xfdesktop_file_icon_activated: assertion `info' failed

Any ideas on that one?

---

### Post by afoglia on 2007-01-29
> **afoglia said:**
> Now there is another (possibly related) problem, when I try to open the USB flash drive by double clicking, Thunar does not run.  The .xsession-error line is: ** (xfdesktop:6149): CRITICAL **: xfdesktop_file_icon_activated: assertion `info' failed

Any ideas on that one?

A perusal of the one google result for that error gave me the idea to uncheck the firts two check boxes in gnome-volume-properties: "Mount removable drives when hot-plugged" and "Mount remocable media when inserted".  (I was uncertain which one it was.)  No the icon appears, but the drive is unmounted.  Double-clicking then gets (i assume) xfdesktop to mount the device and open Thunar.

So I guess my question is now: Should gnome-volume-manager even be running?  What about the other gnome stuff I have running: gnome-keyring-daemon, gnome-power-manager, gnome-pty-helper, and gnome-vfs-daemon?

---

### Post by kerry_s on 2007-01-29
If you don't use gnome stuff just uncheck the "launch gnome services on startup" in > menu> settings> sessions and startup

It won't stop you from using gnome apps, they just start a little slower, when it has to start other needed apps. Just try and see if there's a difference.

---

