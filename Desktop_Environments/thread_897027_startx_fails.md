---
title: "startx fails"
date: 2008-08-21
forum: Desktop Environments
---

### Post by heterosapien on 2008-08-21
Hi,

I have Ubuntu Server installed and I recently installed ubuntu-desktop.  Bet when I try to run it I get this message:

root@tube-it:~# startx


XFree86 Version 3.3.6 / X Window System
(protocol Version 11, revision 0, vendor release 6300)
Release Date: January 8 1999
        If the server is older than 6-12 months, or if your card is newer
        than the above date, look for a newer version before reporting
        problems.  (see [http://www.XFree86.Org/FAQ](http://www.XFree86.Org/FAQ))
Operating System: Linux 2.2.17 i686 [ELF]
Configured drivers:
  VMware: server for VMware graphics adapters (Patchlevel 0)
(using VT number 9)

XF86Config: /etc/XF86Config
(**) stands for supplied, (--) stands for probed/default values
(**) Mouse: type: ps/2, device: /dev/mouse, buttons: 3
(**) VMware: Graphics device ID: "VMware SVGA"
(**) VMware: Monitor ID: "vmware"
Warning: The directory "/usr/X11R6/lib/X11/fonts/misc/" does not exist.
         Entry deleted from font path.
Warning: The directory "/usr/X11R6/lib/X11/fonts/Type1/" does not exist.
         Entry deleted from font path.
Warning: The directory "/usr/X11R6/lib/X11/fonts/Speedo/" does not exist.
         Entry deleted from font path.
Warning: The directory "/usr/X11R6/lib/X11/fonts/75dpi/" does not exist.
         Entry deleted from font path.
Warning: The directory "/usr/X11R6/lib/X11/fonts/100dpi/" does not exist.
         Entry deleted from font path.
Warning: FontPath is completely invalid.  Using compiled-in default.
Warning: The directory "/usr/X11R6/lib/X11/fonts/misc/" does not exist.
         Entry deleted from font path.
Warning: The directory "/usr/X11R6/lib/X11/fonts/Speedo/" does not exist.
         Entry deleted from font path.
Warning: The directory "/usr/X11R6/lib/X11/fonts/Type1/" does not exist.
         Entry deleted from font path.
Warning: The directory "/usr/X11R6/lib/X11/fonts/75dpi/" does not exist.
         Entry deleted from font path.
Warning: The directory "/usr/X11R6/lib/X11/fonts/100dpi/" does not exist.
         Entry deleted from font path.

Fatal server error:
No valid FontPath could be found


When reporting a problem related to a server crash, please send
the full server output, not just the last messages


waiting for X server to begin accepting connections
giving up.
xinit:  Connection reset by peer (errno 104):  unable to connect to X server
xinit:  No such process (errno 3):  Server error.
root@tube-it:~#

Can anyone help me?

Thanks

---

### Post by heterosapien on 2008-08-21
Oh yeah, I tried deleting/renaming the .Xauthority files as well, but still no luck.

---

