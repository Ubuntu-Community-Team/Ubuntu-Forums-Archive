---
title: "System crashed, log files??"
date: 2005-05-24
forum: Desktop Environments
---

### Post by feralert on 2005-05-24
Hi people,

My system crashed this morning and i dont know where to look for information about what happened.
I have search in /var/log/messages but this is all i see:   :?

May 24 11:35:28 deathstar -- MARK --
May 24 11:55:29 deathstar -- MARK --
May 24 12:15:29 deathstar -- MARK --
May 24 12:35:29 deathstar -- MARK --


Any more log files where i can find out where the problem came from?

Thanks!

---

### Post by dataw0lf on 2005-05-24
/var/log/Xorg.0.log
/var/log/syslog
/var/log/kern.log
/var/log/debug
/var/log/dmesg

---

### Post by Cantabile on 2007-11-20
Did Feisty also log the messages relevant to crashes in these log files? If I did a reboot after the crash, these log files are not overwritten with new messages? 

Just had the very first crash of my Feisty, trying to figure out what's the problem. Thanks.

---

