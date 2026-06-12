---
title: "unexpected Beryl/X problem"
date: 2007-05-03
forum: Desktop Effects &amp; Customization
---

### Post by melat0nin on 2007-05-03
Hi all

I was working away fine, Beryl was looking fantastic and working great, then I ran Azureus but it would disappear after running for about a second.  So I restarted my comp, tried to login, and received a message saying that my **"session lasted 10 seconds"**.

Here is the output of the error message:

```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /user/X11R6/bin/sessreg -a -w /var/log/wtmp -n /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "laurie"
/etc/gdm/Xsession: Beginning session setup...
Warning: Only changing the first 7 of 9 buttons...
Xlib: extension "XFree86-DRI" missing on display ":0.0".

Fatal Server Error:
no screens found
```

I'm guessing it's something to do with DRI, hence why the Beryl session won't load by the normal Gnome one will.  But I've no idea why it suddenly b0rked -- I did nothing to get rid of or uninstall DRI/ATi/flgrx/whatever that I'm aware of.

Any ideas?  At the moment I'm running the standard Gnome session with mesa (again, I've no idea why it's not in fglrx).

Any help would be much appreciated!  I did a search but couldn't find anything related to this specific problem.

---

