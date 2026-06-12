---
title: "&quot;X&quot; cursor showing up on login"
date: 2005-04-13
forum: Desktop Environments
---

### Post by michwill on 2005-04-13
Apologies if this has been "logged", but I search and haven't seen it.  Anyway, what is the deal with the "X" cursor appearing at login?  It seems to only disappear upon manipulation of a window (e.g. drag the window).  Any ideas?

NOTE: Warty 4.10 and Hoary 5.04

---

### Post by XDevHald on 2005-04-13
If you did the CTRL+ALT+Backspace then yes it will do that because of logging out X, now as far as logging in from boot, then it should only happen once if you just installed Ubuntu.

Probably others could give you more info than this. Sorry :-|

---

### Post by michwill on 2005-04-13
Thanks for the input.  Actually, it occurs every single time I log in.  It just hovers near the center of the desktop.  As I said, it only goes away when a window is moved or an icon is dragged.  I've installed both "Warty" and "Hoary" on multiple systems with the same result.

---

### Post by kamstrup on 2005-04-13
Do you have a Savage graphics card (I bet you do)? If that is the case, addding 

HWCursor "False"

To you Device section in xorg.conf, probably solves the problem. It has is a bug that was also valid in Warty having to do with hardware accelrated cursors in x.org.

Good luck

EDIT:
Resources:
[http://www.ubuntuforums.org/showthread.php?t=26](http://www.ubuntuforums.org/showthread.php?t=26)
[http://www.ubuntuforums.org/showthread.php?t=1100](http://www.ubuntuforums.org/showthread.php?t=1100)

---

### Post by michwill on 2005-04-13
Yes I do have a "Savage" card, but I have no xorg.conf file anywhere.  Any other ideas?

EDIT:
I did, however, add the line to my XF86Config-4 file, but to no avail.

---

### Post by Stormy Eyes on 2005-04-13
[QUOTE=michwill]Apologies if this has been "logged", but I search and haven't seen it.  Anyway, what is the deal with the "X" cursor appearing at login?  It seems to only disappear upon manipulation of a window (e.g. drag the window).  Any ideas?

NOTE: Warty 4.10 and Hoary 5.04[/QUOTE]

Are you getting the X pointer in place of the white arrow? Post the contents of **/usr/share/cursors/xorg-x11/default/index.theme**, please.

---

### Post by Stormy Eyes on 2005-04-13
[QUOTE=michwill]Yes I do have a "Savage" card, but I have no xorg.conf file anywhere.  Any other ideas?[/QUOTE]

Edit /etc/X11/XF86Config-4 if /etc/X11/xorg.conf doesn't exist.

---

### Post by michwill on 2005-04-13
[QUOTE=Stormy Eyes]Are you getting the X pointer in place of the white arrow? Post the contents of **/usr/share/cursors/xorg-x11/default/index.theme**, please.[/QUOTE]

No. I'm just getting an "X" cursor that sits in the middle of the screen.  The "normal" pointer still comes up, however.  So far I have tried each of the following exactly as typed below and nothing has worked:


Option "HWCursor"  "False"
Option "HWCursor False"
Option "SWCursor"  "False"
Option "SWCursor False"
HWCursor  "False"
SWCursor  "False"

Option "HWCursor"  "Off"
Option "HWCursor Off"
Option "SWCursor"  "Off"
Option "SWCursor Off"
HWCursor  "Off"
SWCursor  "Off"

---

### Post by michwill on 2005-04-13
CORRECTION:

The following worked:

Option "HWCursor"  "False"


I was under the mistaken impression that logging out and logging back in was sufficient.  Turns out that a complete reboot is necessary.

Thanks all!!!

---

### Post by kamstrup on 2005-04-15
Logging out and hitting ctrl-alt-backspace is also sufficient. All you have to do is restart the X-server.

Cheers!

---

