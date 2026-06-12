---
title: "Mail watch for Gnome panel"
date: 2008-11-28
forum: Desktop Environments
---

### Post by Rmantingh on 2008-11-28
Hi,

I'm looking for a mailwatch utility that I can embed in the Gnome panel and which can keep an eye on POP3 mailboxes. I've already looked at GMailWatch but can't get that to work and I don't like the look of it anyway). I need something similar to the mailwatch plugin for XFCE4 panel (xfce4-mailwatch-plugin). Anybody have any ideas?
I'm not interested in screenlets or similar. It has to be a panel plugin / applet.

Ruud

---

### Post by redDEADresolve on 2009-12-13
just spent the last 40 minutes looking myself. 

this is the closet i've found:
[http://ubuntuforums.org/showthread.php?t=1136699&page=17](http://ubuntuforums.org/showthread.php?t=1136699&page=17)

dont really care for them.

---

### Post by Rmantingh on 2009-12-16
In the end I decided to go for mail-notification.
It's available in the repos and does what I need it to do without too much fuss. The thread you mentioned seems to deal mainly with Google Mail accounts (I didn't read the whole thread) and I need something that can deal with multiple POP and GMail accounts.

---

### Post by redDEADresolve on 2009-12-16
I settled with mail-notification myself, the other choices were sub-par at best. 

A little tip, to get notification working properly,
- delete all entries in /apps/mail-notification/popups/actions in gconf

---

### Post by Rmantingh on 2009-12-17
Can you explain a bit more about mail-notification not working properly?
Where are these 'actions' shown?
I have no problems with the program and don't see any difference if I clear out these actions in gconf.
Am I missing something?

---

