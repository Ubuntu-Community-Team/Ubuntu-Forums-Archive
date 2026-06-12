---
title: "Mouse busy cursor"
date: 2007-11-30
forum: Desktop Environments
---

### Post by msromike on 2007-11-30
Just installed Gutsy and have noticed a mouse cursor problem.  the mouse, while pointed over an open desktop area, animates in "busy" mode. I have variously tried disabling/killing services one by one to isolate what I thought was a hung service in the background ...but this doesn't appear to be the ticket.

Over any running application the mouse cursor behaves as expected.

However - minimizing applications, or over the open desktop, the mouse "busy" animation just spins and spins.

Again - over an opened program the mouse is normal. Over the desktop (wallpaper area or no wallpaper, no difference) the mouse icon remains animated and spinning.

Any ideas?  I have seen this same problem posted three times in the past 2 years in this forum with no solution posted.

---

### Post by IanB2 on 2008-02-06
I'm having the same problem with the busy mouse cursor.

This is only affecting one login session ..... other users are not seeing the same problem on this PC.

Anyone know what is going on? Is this linked to compiz in some way?

---

### Post by IanB2 on 2008-02-08
I've reported this as a new bug in launchpad see:

[Bug 190248] [NEW] while pointed over an open desktop area, animates in "busy" mode

---

### Post by tcommbee on 2008-02-08
i think this is caused by nautilus, which renders the desktop by default. so if you move the mouse over the desktop, you move it effectively over a nautilus window. you could start gconf-editor, go to /apps/nautilus/preferences and disable show_desktop there (obviously this will temporarily remove icons from screen until reactivated). if the hourglass disappears then, your problem definitely has to do with nautilus.
maybe ~/.xsession-errors tells anything useful

---

### Post by IanB2 on 2008-02-09
> **tcommbee said:**
> i think this is caused by nautilus, which renders the desktop by default. so if you move the mouse over the desktop, you move it effectively over a nautilus window. you could start gconf-editor, go to /apps/nautilus/preferences and disable show_desktop there (obviously this will temporarily remove icons from screen until reactivated). if the hourglass disappears then, your problem definitely has to do with nautilus.
maybe ~/.xsession-errors tells anything useful

Thanks for the suggestions which I've tried.
Changing the settings in gconf-editor has made no apparent difference (tried a reboot).
I don't think that xsession-errors has anything useful but here are the contents of the last entry:

[I](process:5974): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.[/I]

Any other ideas what to do try next?
Cheers!

---

### Post by tcommbee on 2008-02-09
Check under System>Administration>System Monitor if any process eats much more CPU than what it's supposed to.

---

### Post by IanB2 on 2008-02-10
The only process that is showing any cpu usage (single percentage points only) is 'Xgl'

---

### Post by NiceGuy on 2008-02-27
I had this problem but I managed to fix it by editing my .gtk-bookmarks file in my home folder. There was an entry in there pointing to a network folder which no longer existed, removing this entry fixed the problem.

See: [http://ubuntuforums.org/showpost.php?p=4414151&postcount=5](http://ubuntuforums.org/showpost.php?p=4414151&postcount=5)

---

