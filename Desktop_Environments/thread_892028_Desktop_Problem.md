---
title: "Desktop Problem"
date: 2008-08-16
forum: Desktop Environments
---

### Post by pdadad on 2008-08-16
My desktop no longer allows right clicks and the icons are no longer visible.  I've tried reseting the desktop in gconf-editor to show the desktop but this had no effect - changed the settings and rebooted each time.  The only other issues I could find were a usb connected drive, turned it off, and a message about Opera, stopped it from starting on boot.

I have 2 panels and they work as they are supposed to.  Compiz is running and everything with it seems to be working fine.  I tried turning off compiz and rebooting, it made no difference.

I set up another user to see if the desktop was active.  It was.

I've been running Ubuntu since v7.04 but I feel like a total noob when I run across this kind of issue.  If anyone can point me in a productive direction I would very much appreciate it.

---

### Post by mr.moch on 2008-08-16
OK.  Try a couple of things:

1.  If you have a login screen, check the session type.  You should be under "GNOME", "X Window Client".  Pick one of the two.

2.  If they're doing a file scan, skip it and see what happens.  Not sure how to turn it off.

3.  Try turning off desktop effects if on.

---

### Post by pdadad on 2008-08-17
mr. moch - Thank you for your assistance.  I rebooted and could not find a reference to "GNOME" or "X Window Client" on the login options.  The scan did not occur but it's easy enough to cancel if it would have.  I had already tried to turn off the compiz desktop effects.  Well long story short.  My desktop came back and I don't know why.  I changed no settings after reading your post.  Must have been the result of your good will. :-)

---

### Post by swisscow on 2008-08-18
Mine has also done this as well, seemingly at random.

so you are not alone.............

---

### Post by pdadad on 2008-08-18
swisscow - Did you try going to the gconf-editor to show the desktop?

---

### Post by swisscow on 2008-08-18
> **pdadad said:**
> swisscow - Did you try going to the gconf-editor to show the desktop?

If you mean show trash, home folder etc then yes, I like to see them. When it happens it's like the icons and right click menu are invisible. A reboot usually seems to fix it. Hasn't happened recently come to think of it.

---

### Post by pdadad on 2008-08-18
Yes, that is exactly what I experienced.  It's like the icons and right click menu are invisible.

I would have liked to figure out what caused it but it was just such a productivity killer having it fixed is a big relief.

---

