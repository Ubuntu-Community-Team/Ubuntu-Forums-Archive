---
title: "Gnome desktop gone after last update"
date: 2013-02-25
forum: Desktop Environments
---

### Post by kiwited on 2013-02-25
About two days ago there was a fairly large update, following which my gnome desktop no longer functioned. All I have is the basic gnome classic, and of course the unity desktop which I don't like.
I have tried reinstalling through synaptic, but without success.
Any ideas.

Theo

---

### Post by carl4926 on 2013-02-25
But you have session option for Gnome at login?

Is this 12.04 or 12.10

Test the guest login

---

### Post by kiwited on 2013-02-25
I had a login option for gnome, but it defaulted to the basic gnome classic when started.
Also the fonts were awful.
I have solved the problem, though.
On checking the additional drivers setting I found the monitor was being detected as a laptop with a low resolution setting and no ability to change this.
I removed the fglrx driver, then reinstalled it.
On restarting, everything was back to normal. Rather simple in the end, really, but a couple of days of head-scratching to find it.
:P
Theo

---

