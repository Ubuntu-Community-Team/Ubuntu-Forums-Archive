---
title: "Dual floppy drives both come up as &quot;Floppy disk&quot;"
date: 2010-02-16
forum: Desktop Environments
---

### Post by hbquikcomjamesl on 2010-02-16
With no media mounted, both(!) of my floppy drives come up as "Floppy disk" in the "Removable media" menu.

Anybody know of a way, in Ubuntu 8.04LTS, to have two separate not-yet-mounted floppy drives come up with different names (e.g., "Floppy A" and "Floppy B," or "Floppy 3.5" and "Floppy 5.25,"  or "Floppy 1.44" and "Floppy 360" in the "Removable media" menu?

Yes, I know empirically that the one on top is the 3.5, and the one on the bottom is the 5.25 (in spite of the fact that they're physically arranged exactly the opposite in the case), but having them both show up as "Floppy disk" is inelegant.

Having separate icons would be even better.

---

### Post by warp99 on 2010-02-17
On the menu go to Places > Computer, highlight the drive then right mouse click and choose "Rename". BTW with *nix it's normal behavior for the drives to show up without being mounted.

---

### Post by hbquikcomjamesl on 2010-02-17
Wow. Just right-click and rename, right on the menu? That easy?!? I'll try it at my first opportunity.

---

### Post by warp99 on 2010-02-17
Oh and if you want different icons then right mouse click and choose properties then click on the icon. In the dialog box move to the /usr/share/pixmaps or the /usr/share/icons folder to choose a different icon.

---

### Post by hbquikcomjamesl on 2010-02-17
Uh, it doesn't work.

Right-clicking on "Floppy disk" in the Places > Removable Media submenu just tries to mount it, the same as left.

Right-clicking on it in the drive list on the left of a Nautilus window produces a right-click menu with "Rename" disabled.

Attempting to rename the drive in a Nautilus window opened to "Computer" produces an error message:
> **This item could not be renamed**
Sorry, couldn't rename "Floppy Drive" to "Floppy A": Operation not supported by backendThe last two are also true if I open the Nautilus window with a "sudo nautilus" in a terminal, and in such a case, a message appears in the terminal window, "**(nautilus:6709): WARNING **:Hit unhandled case g-io-error-quark:15 in fm_report_error_renaming_file."

Also, while I can change the icon for the drive in Properties on that drive, it doesn't affect the sidebar or the Places > Removable Media menu.

Version is 8.04LTS

Going home; it's my laundry night, and I've just installed a new sign-on screen theme, and a few new icons.

---

### Post by warp99 on 2010-02-17
I did a little more digging and found out this is a known Gnome bug:

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/388207](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/388207)

I just figured it was the same as in KDE, which does work properly. Sorry about that.

---

### Post by hbquikcomjamesl on 2010-02-17
That bug, and its friend, both appear to be connected with *volume labels*. The problem here is with how empty floppy *drives* show up in the Nautilus sidebar and the Places > Removable Media submenu.

On a lark, I dug up both fstab and mtab, hoping I'd find something relevant, but no joy there, either.

---

### Post by hbquikcomjamesl on 2010-02-24
Sticking "Disk Mounter" in the top Panel seems to have helped: even if nothing else seems able to indicate which floppy drive is which, it can.

But I'd still like to get them coming up as, say, their DOS names, or their drive types, when unmounted.

---

