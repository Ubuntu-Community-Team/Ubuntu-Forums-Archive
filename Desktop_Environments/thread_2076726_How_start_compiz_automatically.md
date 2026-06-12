---
title: "How start compiz automatically?"
date: 2012-10-26
forum: Desktop Environments
---

### Post by christian.convey on 2012-10-26
I'm running a fresh install of Ubuntu 12.10 64-bit, and I've installed the legacy, closed-source ATI graphics driver.  I've also installed compiz and ccsm.

What's the best way to have compiz automatically running when I log into my desktop environment (currently Gnome Classic)?

As things currently stand, each time I log in I have to go to a terminal and manually run "compiz --replace &".  I'd like to not have to do that.

---

### Post by Ninja Sticker on 2012-10-26
You have installed the compiz settings manager?

---

### Post by christian.convey on 2012-10-26
> **Ninja Sticker said:**
> You have installed the compiz settings manager?
Yup, I've installed CCSM.

---

### Post by ajgreeny on 2012-10-26
Go to the menu entry for "Startup applications" and add the command ```
compiz --replace
``` there.

---

### Post by christian.convey on 2012-10-26
> **ajgreeny said:**
> Go to the menu entry for "Startup applications" and add the command ```
compiz --replace
``` there.
Thanks.  That sounds like a decent solution, but is there a well-known approach that causes "compiz" to run from the get-go, rather than having to replace whatever it is that it replaces?  I would expect that to result in smoother graphics during login.

---

### Post by stinkeye on 2012-10-26
Don't you have the the 2 sessions at login...
# **Gnome Classic**....uses compiz
and
# **Gnome Classic (No Effects)**....uses metacity

---

### Post by christian.convey on 2012-10-27
Awesome, that did it.  Thanks.

---

