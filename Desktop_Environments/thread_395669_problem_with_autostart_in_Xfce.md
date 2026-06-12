---
title: "problem with autostart in Xfce"
date: 2007-03-28
forum: Desktop Environments
---

### Post by Lord Darth Vader on 2007-03-28
I recently installed Xfce in my Ubuntu. I had quite a few applications in autostart in Ubuntu. 

Now whenever  Xfce starts I have at least two and instances of Gaim! Gaim is not listed in my autostart apps.

How can I fix this problem?

---

### Post by x1a4 on 2007-03-28
Hi,

See if you have a Gaim _.desktop_ file in _~/.config/autostart/_.  If so, remove it.  Then/Or, set-up Xfce the way you want and quit Xfce.  When quitting, tick the 'Save session for future logins' checkbox.  Log back in.

---

### Post by Lord Darth Vader on 2007-03-28
I deleted everything in ~/.config/autostart/

and it fixed multiple GAIMs on startup but I still have one GAIM when Xfce starts. practically speaking, this is what I want but I am just curious to know why I have one when it is not listed in "autostarted applications" nor it has file in ~/.config/autostart/. .

Thanks.

---

### Post by x1a4 on 2007-03-28
It's probably saved as part of the session.  Configure Xfce the way you want it to start, logout--remember to tick the 'Save session...' checkbox--then log back in, and all will be well.  

It's also a good idea to upgrade to the latest release of Xfce.  Add the following repositories to _/etc/apt/sources.list_

[B]deb [http://ubuntu.tolero.org/](http://ubuntu.tolero.org/) edgy xfce-4-4-0 main
deb-src [http://ubuntu.tolero.org](http://ubuntu.tolero.org) edgy main[/B]

---

