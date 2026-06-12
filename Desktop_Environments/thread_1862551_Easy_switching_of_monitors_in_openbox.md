---
title: "Easy switching of monitors in openbox?"
date: 2011-10-16
forum: Desktop Environments
---

### Post by HangukMiguk on 2011-10-16
I don't think my previous thread about this posted.

I am looking for a way to easily switch between monitors on Openbox.  I am using only GNOME right now, but am more comfortable with Openbox.  However, at work, I use a monitor at my desk with my laptop, and would like to use ONLY that monitor (because my desk space doesn't allow me to use both), and then I can't have both turned on at the same time mirrored, as the monitor will only display 1280x1024 at that point when it's capable of a much higher resolution.  So basically what I want is to be able to plug in a monitor, then quickly disable my laptop screen, and use the connected monitor at its highest resolution, then just change back to my laptop screen when I go to disconnect the monitor.

Any way to do that?

---

### Post by HangukMiguk on 2011-10-17
Bump

---

### Post by HangukMiguk on 2011-10-17
Bump

---

### Post by HangukMiguk on 2011-10-17
Bump

---

### Post by HangukMiguk on 2011-10-26
Bump, someone gave me this:

[http://shallowsky.com/blog/linux/laptop/docking-resolution.html](http://shallowsky.com/blog/linux/laptop/docking-resolution.html)

Which I tried, to no avail.  Can't seem to get this to work, despite having everything installed that I should.  Where should I be putting this?

---

### Post by aeiah on 2011-10-26
what they gave you is pretty much the way to do it, although your settings will be different.

try and perform all the required actions using xrandr and then put it in a script. put the script in your obmenu or create a keyboard shortcut.

you could use an if/else statement to check whether the screen is already in use, in which case, the script could change back to your laptop screen creating a toggle switch.

---

