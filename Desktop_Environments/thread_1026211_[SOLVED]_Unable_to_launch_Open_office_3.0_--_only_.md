---
title: "[SOLVED] Unable to launch Open office 3.0 -- only in KDE"
date: 2008-12-30
forum: Desktop Environments
---

### Post by binukavumkal on 2008-12-30
Hi,

I installed the Open office 3.0.0 in Ubuntu 8.10. When I use KDE, none of the Open office applications is launched.

It shows the initial flash screen for a couple of seconds and then shows a application screen for a split  of a second then nothing. No application  icon even in the task panle.

Please help to resolve this. I think in KDE, some configuration is missing.

In GNOME all these open office applications are working fine.

Thank you.

---

### Post by ajmorris on 2008-12-30
hi there,
can you please open up a terminal, and load one of the OOo applications.
for example, to load the writer component, just type ```
oowriter
``` into the terminal.
Then wait for it to crash, and paste here any output, (if it is large output, please use the [CODE] envelops around it.)


AJ

---

### Post by binukavumkal on 2008-12-31
Thanks ajmorris.

The error i am getting is similar to the following


[https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/306908](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/306908)

As per the work around suggested I removed the following package

 sudo apt-get remove openoffice.org-kde

It is working fine now.

---

### Post by lolwhites on 2009-01-03
I tried this solution and OpenOffice does now open, but the toolbar buttons have vanished. They only appear when I hoverthe mouse over them.

---

