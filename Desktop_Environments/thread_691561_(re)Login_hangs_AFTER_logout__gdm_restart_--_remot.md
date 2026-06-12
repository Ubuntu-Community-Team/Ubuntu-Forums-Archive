---
title: "(re)Login hangs AFTER logout / gdm restart -- remote desktop to blame?"
date: 2008-02-08
forum: Desktop Environments
---

### Post by sir_blargh on 2008-02-08
Hi,

My initial login works great -- in fact it's super speedy thanks to the readahead cache tip found in these forums!  However, if I ever logout, or need to restart gdm (sudo /etc/init.d/gdm restart OR <CTRL><ALT><BACKSPACE>), I can never log back in.  I enter my credentials, the screen turns to the normal brownish color and I hear the login sound.  However the panels do not load and it just hangs there at that brown screen.

If I look at my .xsessions-errors file from a console window, I see an identical file to what a normal one looks like, except that it is truncated.  Here's the .xsessions-errors file from a failed login:  

```
(process:7716): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    http://www.gtk.org/setuid.html

Refusing to initialize GTK+.

(process:7720): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    http://www.gtk.org/setuid.html

Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/blargh-htpc:/tmp/.ICE-unix/7713
```

A normal login includes ALL of the above, but continues on:

```
Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/blargh-htpc:/tmp/.ICE-unix/6213
** Message: Starting remote desktop server
Checking for Xgl:
```

So I noticed that the first thing that happens in a successful login is the starting of the remote desktop server, but apparently that's not happening in a non-successful login.  As a temporary solution, I disabled the remote desktop server by System --> Preferences --> Remote Desktop unchecking the "Allow other users to view your desktop" option.

By doing this, then hitting <CTRL> <ALT> <BACKSPACE>, I was then able to log right back in successfully.

So seems to me like there's a problem with my remote desktop server?  Does anyone have any ideas about this?

Thanks...

---

### Post by tcommbee on 2008-02-09
you could check the xsession-errors after logging out (but before logging in again), to see if anything related to rdp didn't shut down properly

---

### Post by sir_blargh on 2008-02-12
Good call, I will try that.  Out of curiousity though, is hitting the Log Out button equivalent to CTRL ALT BACKSPACE, or is the keyboard shortcut more of a forced quit?

---

### Post by Tiede on 2008-03-29
I am having the same problem also, and I just remembered that  I was fiddling with remote-desktop earlier. I will try to disable it and see what happens...

Should we fill a launchpad bug, or it is related to [*this old one*](https://bugs.launchpad.net/ubuntu/+source/meta-gnome2/+bug/158755)?

---

### Post by Tiede on 2008-03-29
Confirming that going to System->Preferences->Remote Desktop and disabling remote users from login in fixes the issue.
Filling a bug against Remote Desktop.

---

### Post by Tiede on 2008-03-29
Done!
This is now [Bug #208942](https://bugs.launchpad.net/ubuntu/+source/rdesktop/+bug/208942)

---

