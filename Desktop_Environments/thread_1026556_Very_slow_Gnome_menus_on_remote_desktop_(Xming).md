---
title: "Very slow Gnome menus on remote desktop (Xming)"
date: 2008-12-31
forum: Desktop Environments
---

### Post by jherold on 2008-12-31
I am using Xming to use a PC with Ubuntu 8.10 remotely as desktop. The Gnome menu bar is excruciatingly slow. I need to keep the mouse over a menu item for quite a while to have the pull-down menu appear.

If I use Xfce as window manager this problem disappears for the system menus.

What makes the interaction with the Gnome system menus so slow on a remote desktop, but does not seem to affect Xfce?

I use Xming on my PC to display the remote desktop. The network connection itself does not seem to be the bottleneck.

Any help or suggestions?

thanks!

---

### Post by moejuda on 2009-01-26
I am experiencing the same issue.  Did you ever come across a fix?  There doesn't seem to be much documentation on this problem.

---

### Post by jherold on 2009-01-26
No, I did not receive any response.

I have switched to Xfce when I use a remote desktop connection.

---

### Post by minnow on 2009-07-19
Hi Guys....

This was the first forum i found with the same problem i was expierenceing, So in hopes to help others.....

I was using SNAT to share my internet connection to my client systems....
The SNAT rule had no  output interface specified,
So in turn i assume it was attempting to SNAT my X11 forwarding and failing...causing the delay.

My fix was to simply specify the output interface for my SNAT rule.
This fixed it perfectly.

---

