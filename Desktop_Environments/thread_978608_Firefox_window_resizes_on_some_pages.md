---
title: "Firefox window resizes on some pages"
date: 2008-11-11
forum: Desktop Environments
---

### Post by cdillard-hsp on 2008-11-11
After visiting a banking site yesterday firefox now opens in a semi-fullscreen view where the top title bar is missing.  I can correct this by hitting the F11 key twice.  Also on some pages (like Yahoo Mail) Firefox resizes again to the same semi-fullscreen state.  I have looked in the Prefs but don't see an option to stop this from happening.

I'm running:
8.10
Compiz
Nvidia
HP 8510w

Thanks for any help from the community!

- Clay

---

### Post by Gausian on 2008-11-11
try setting "dom.disable_window_move_resize" to "true" in **about:config**

---

### Post by pholden on 2008-11-11
You can control how Javascript behaves in the browser by going to *Edit -> Preferences -> Content -> Enable Javascript -> Advanced*. The popup that follows contains options to limit what scripts can do, one of which is change the window size.

---

### Post by seanksg on 2008-11-11
> **Gausian said:**
> try setting "dom.disable_window_move_resize" to "true" in **about:config**

I'm having the same problem.  I'm also new to Ubuntu and Linux.  So how do I get to about:config?

---

### Post by keithld on 2008-11-11
> **seanksg said:**
> I'm having the same problem.  I'm also new to Ubuntu and Linux.  So how do I get to about:config?

Type about:config in the address field and hit enter.

---

