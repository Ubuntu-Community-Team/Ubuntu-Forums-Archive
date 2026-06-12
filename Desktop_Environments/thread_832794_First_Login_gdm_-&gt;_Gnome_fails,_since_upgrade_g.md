---
title: "First Login gdm -&gt; Gnome fails, since upgrade gutsy -&gt; hardy"
date: 2008-06-18
forum: Desktop Environments
---

### Post by Lenz Moser on 2008-06-18
I've done an upgrade from gutsy to hardy. The system was originally installed with kubuntu gutsy discs, later I've added all the packages for gnome stuff.

The system is running on an Dell notebook. When I first login to my account after system start, the first login fails. I instantly see the Nvidia logo again and I return to the gdm login.

After that I can logout logon as often as I like, it always works at the first time.

When I change the session to KDE (within gdm), it works at the first try and even there, a following Gnome login works.

I cannot see any hints in the Xorg.n.log or /var/log/gdm/* 
~/.xsession-errors is untouched when it happens.

---

### Post by stek79 on 2008-06-30
I have the exact same problem.

Anyone has resolved this issue?

Thanks

---

### Post by stek79 on 2008-07-01
Hi,
   I solved this issue.

I was having problems with gdm, check your daemon.log.

I solved by going back to the default gdm login theme.

---

