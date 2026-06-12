---
title: "Boot Log"
date: 2006-09-09
forum: Desktop Environments
---

### Post by Ziggy72 on 2006-09-09
My /var/log/boot (monitored) - System Log viewer looks like this:

Sat Sep  9 08:29:18 2006: ^[[74G[ ok ]
Sat Sep  9 08:29:18 2006: dirname: missing operand
Sat Sep  9 08:29:18 2006: Try `dirname --help' for more information.
Sat Sep  9 08:29:18 2006: chown: missing operand after `clamav'
Sat Sep  9 08:29:18 2006: Try `chown --help' for more information.
Sat Sep  9 08:29:18 2006: ^[[74G[ ok ]ClamAV daemon clamd       ^[[80G 
Sat Sep  9 08:29:22 2006: ^[[74G[ ok ]ClamAV virus database updater freshclam       ^[[80G 
Sat Sep  9 08:29:22 2006: ^[[74G[ ok ]system message bus dbus       ^[[80G 
Sat Sep  9 08:29:22 2006: ^[[74G[ ok ]Hardware abstraction layer hald       ^[[80G 
Sat Sep  9 08:29:26 2006: ^[[74G[ ok ]the Firestarter firewall...       ^[[80G 
Sat Sep  9 08:29:29 2006: Starting filtering proxy server: privoxy.

Where can I look to to find the commands referred to by the log? I would like to correct the so-called "missing operands".
Thanks for any help...

---

### Post by zek725 on 2006-10-19
i do not have that folder. how do you 'enable' it?

---

### Post by wHEREiSmYcAPSlOCKkEY on 2007-06-21
instructions to enable logs here: [http://ubuntuforums.org/showthread.php?t=49925]("http://ubuntuforums.org/showthread.php?t=49925")

---

### Post by singh.gurjeet on 2008-04-07
> **zek725 said:**
> i do not have that folder. how do you 'enable' it?

edit /etc/default/bootlogd and replace No with Yes

---

