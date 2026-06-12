---
title: "Question about Netbook Remix top panel"
date: 2009-07-24
forum: Desktop Environments
---

### Post by cotocoto on 2009-07-24
I've installed ubuntu 9.04 NBR on my netbook for couple of months. So far I'm liking it and I intend to install a normal version of ubuntu or even xubuntu for my desktop pc. Now, one feature that I like the most in NBR is how the active window's top bar (the one with window's title and min/max/close buttons) is integrated into the top panel. Hence, giving us a bit more height for viewing the window's content.

So how do i put this feature into normal ubuntu/xubuntu desktop? I'm still quite new with linux having played around with it on for a few months. Thank you in advance.

---

### Post by Brandon Williams on 2009-07-24
That behavior is handled by maximus. You will have to configure maximus as one of your startup applications, and then, using gconf-editor, you can configure maximus to undecorate maximized windows. The key in gconf-editor is /apps/maximus/undecorate.

If you just want you maximized windows undecorated, but you don't want windows to be automatically maximized, then enable /apps/maximus/no_maximize.

---

### Post by cotocoto on 2009-07-24
Brandon, thank you for the direction.

However that solves only half of the problem. With undecorated, the top bar go away and the top panel untouched. If you take a look at NBR, the window's top bar title and close button are actually being placed right in the middle of the top panel. So how do we achieve this effect?

---

### Post by Brandon Williams on 2009-07-25
Oops ... I forgot to mention that you need to add the 'window picker' applet to the tob bar. That's what provides the pseudo-titlebar.

---

### Post by cotocoto on 2009-07-26
ok thank you

---

