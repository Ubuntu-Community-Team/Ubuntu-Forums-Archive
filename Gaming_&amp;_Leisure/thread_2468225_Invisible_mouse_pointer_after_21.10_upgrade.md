---
title: "Invisible mouse pointer after 21.10 upgrade"
date: 2021-10-21
forum: Gaming &amp; Leisure
---

### Post by brunolabs on 2021-10-21
After upgrading from 21.04 to 21.10 the mouse pointer became invisible in some games.
A bug has already been opened in [https://bugs.launchpad.net/ubuntu/+source/xwayland/+bug/1947516]("https://bugs.launchpad.net/ubuntu/+source/xwayland/+bug/1947516")

Has anyone ran into this problem?
Have you found a solution/workaround?

---

### Post by marcosdipaolo on 2021-11-25
Yes, I ran into the same issue, still waiting for an aswer

---

### Post by Dennis N on 2021-12-18
> **albert902 said:**
> Yes, I am having the same problem. The mouse pointer is invisible and I have to guess where it is on the screen. Sometimes it works and sometimes it doesn't. Very frustrating!

I would suggest logging in to Xorg session at the login screen and see it that makes a difference. I believe 21.10 now uses Wayland for the default. My notes for Ubuntu 21.10 say "..the updater changed my display manager from Xorg to Wayland without asking." Until I changed back to Xorg, I also had some cursor misbehavior.

---

