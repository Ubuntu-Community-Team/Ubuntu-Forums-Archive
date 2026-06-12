---
title: "switching users broken?"
date: 2016-06-26
forum: Desktop Environments
---

### Post by courtney2 on 2016-06-26
I have found over the last year that with kde plasma 5, switching users is just an absolute mess. On my school's computer science labs (which have been running kubuntu 15.04 and 15.10 since I started attendance) switching users, or "sessions" is a complete mess and involves hard shutting down the computer more often than not. I recently installed Kubuntu 16.04 on my personal machine and attempted to create a new user and switch users rather than log out and it appears to be direly broken on plasma 5.6 (from the backports). Is there something I'm missing? User switching has never been an issue on other desktops like GNOME, MATE, Cinnamon or XFCE. The attachment shows the error I get (hopefully I loaded it up right)

---

### Post by squirrel3 on 2016-06-28
I would try the prompt on the screen. Press Ctrl+Alt+F2, then in the terminal type, > logintcl unlock-sessions

Then, press Ctrl+Alt+F7. Perhaps write the steps down on a pad to avoid confusion. After that you can go into your control panel and tweak some settings so it does not lock your sessions.

---

### Post by courtney2 on 2016-06-29
I've done all that before, I just want to avoid the issue so I'm not having to drop into different TTYs each time I want to switch a user. I find that rather insecure preventing sessions from locking when switching user, wouldn't that mean switching back wouldn't require authentication?

---

