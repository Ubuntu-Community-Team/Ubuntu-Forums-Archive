---
title: "Command &quot;init 2&quot; does not work?"
date: 2006-08-14
forum: Desktop Environments
---

### Post by lagagnon on 2006-08-14
Yesterday I wanted to drop into single user mode console from X so I typed "sudo init 2" . Nothing happened other than being asked for the password. 

What gives? How do I drop to runlevel 2???

---

### Post by kaamos on 2006-08-14
Debian uses different runlevels..

[quote=http://www.debian-administration.org/articles/212]
 * 0		System Halt
 * 1		Single user
 * 2		Full multi-user mode (Default)
 * 3-5		Same as 2
 * 6		System Reboot
[/quote]

---

### Post by lagagnon on 2006-08-14
Doh! Thanks, I come from the Slackware world so I guess I still have a lot to learn!

---

