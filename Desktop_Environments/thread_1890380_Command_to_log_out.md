---
title: "Command to log out"
date: 2011-12-03
forum: Desktop Environments
---

### Post by jimmydean886-2 on 2011-12-03
Hello, all!

I've run into a bit of a problem. When I try to run gnome-session-save, it says "command not found"

This is probably a GNOME3 thing, but what would I run through the command line to log out?

I would like it to be something without a confirmation dialog. The gtk-logout-helper in /usr/lib/indicator-session has no disable function for this (or at least no working one)


I'm running Ubuntu 11.10 and unity.

Thanks in advance!

--Jimmydean886-2--

---

### Post by Lars Noodén on 2011-12-03
Wouldn't that be [font=Courier New]/usr/bin/gnome-session-quit --no-prompt[/font]?

---

### Post by jimmydean886-2 on 2011-12-03
Jeez, I feel stupid.

Thanks a ton!

--jimmydean886-2--

---

