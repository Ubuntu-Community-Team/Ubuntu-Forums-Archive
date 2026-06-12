---
title: "Ubuntu randomly freezes at login screen or after logging in"
date: 2009-03-09
forum: General Help
---

### Post by knattlhuber on 2009-03-09
Since a couple of days I am experiencing random freezes on boot. Ubuntu boots fine up until the GDM login window appears. Either then or after entering my username/password, the computer freezes up and needs to be switched off. This happens about half of the times and occurs completely at random.
I looked at /var/log/syslog but I couldn't really see what's wrong. The attached log file has recorded two consecutive freezes (at 16:04:44 and 16:20:14). I'm on Intrepid with kubuntu and xfce installed in addition to GNOME. My kernel version is 2.6.27-11.27. I haven't done any kernel updates or kernel module modifications recently.
Can anybody tell from the attached log what could be the source of the problem?

EDIT: Strange, log file upload didn't work. Here's the link
[http://www.knattlhuber.net/syslog.txt]("http://www.knattlhuber.net/syslog.txt")

---

### Post by mdebusk on 2009-03-10
> **knattlhuber said:**
> Since a couple of days I am experiencing random freezes on boot. Ubuntu boots fine up until the GDM login window appears. Either then or after entering my username/password, the computer freezes up and needs to be switched off.

This happens to mine too. It works fine until it has to change video modes, I think. If I switch to a terminal from the login screen and log in, it's fine. After I let it warm up a while, I can switch back to graphical login.

I'm convinced that it's a bad video card.

---

