---
title: "panel using high cpu"
date: 2007-07-31
forum: Desktop Environments
---

### Post by 043087m135 on 2007-07-31
Hey All

I'm running Xubuntu Feisty, and I've got a problem with the panel.

On a fresh install it was working fine, but I was dinking around with desktop-effects and I guess I must have messed something up.

Now when the panel loads it uses 80-99% of my CPU at all times, and exhibits strange behaviors. For instance, the lower bar is almost completely nonresponsive. I cannot click windows there and have them pop up - new windows aren't even reported there as menu items. The top bar is also unresponsive except for the applications menu, which works perfectly. You know how normally when you hover on an icon on the top menu it changes the way it looks to seem as if you are hovering over it? Well that doesn't happen. Sometimes if I click anyway it will respond (like 2 minutes later, literally) but usually there's absolutely no response.

Here's some output when I run and kill the panel from a terminal

```
~$ sudo xfce4-panel
Password:
** Message: Trash Applet: screen changed: 0

** Message: No valid plug window.

(xfce4-panel:5241): Gtk-CRITICAL **: gtk_socket_get_id: assertion `GTK_WIDGET_ANCHORED (socket)' failed

** (xfce4-panel:5241): CRITICAL **: An item was unexpectedly removed: "Trash Applet".

```

Could this all be a problem with my trash applet?

Thanks!

~043087m135

---

