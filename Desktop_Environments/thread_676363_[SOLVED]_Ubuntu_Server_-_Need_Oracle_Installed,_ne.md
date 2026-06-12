---
title: "[SOLVED] Ubuntu Server - Need Oracle Installed, need X11 installed?"
date: 2008-01-23
forum: Desktop Environments
---

### Post by jumping_snake on 2008-01-23
Ok, hang in there, this is a little bit of a scenario mixed with a Linux n00b:

We need to install the Oracle 10g client on an Ubuntu server setup (6.06) **REMOTELY**. I was thinking that this ([https://help.ubuntu.com/community/Oracle10g](https://help.ubuntu.com/community/Oracle10g))
would be all that I need. Yet, someone with more knowledge of the workings of servers told me that I needed to install X11 and then do the install remotely. They said that a GUI install was needed to run the Oracle install.

I'm not sure if they're correct, but I figure it'd be good to know anyways. So, here's my *questions*:
1) Do I need X11 installed or is the link all that I need?
2) If I do need X11, how do I install it? I'd like to do packages if possible, because as soon as we have Oracle installed, I'd like to get X11 off.


I've looked everywhere for a solution (google, forums, more google, etc.) but I have yet to come up with any answers other then "Install Xubuntu" which is the last thing that I want to do.

---

### Post by Waappu on 2008-02-04
Hi

XE installation works without X11
[http://www.debian-administration.org/articles/430](http://www.debian-administration.org/articles/430)

---

### Post by jumping_snake on 2008-02-13
COOL LINK! Thanks for the advise, but we decided to change our approach and use PHP instead of our older Perl scripts. Either way, our situation is solved, thanks!

---

