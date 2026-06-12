---
title: "automatic shutdown"
date: 2009-10-26
forum: Desktop Environments
---

### Post by leduc900 on 2009-10-26
I would like to shutdown automatically my pc after some inactivity. And later on i use wakeonlan to make it up. 

Problem is that after sleep, wakeonlan does not work but well after complete shut down. 

How can i replace the sleep functionality by a complete shut down? Should i replace the sleep.sh or hibernate.sh scripts ? 

Thank you in advance for any help. 

Benoit.

---

### Post by Keith Hedger on 2009-10-26
I maybe wrong but I don't think you can 'wake on lan' from a complete shutdown only from sleep, as a complete shutdown is a hardware thing whereas sleep is a software thing.
Anyway to do a complete shutdown use```
sudo shutdown -h now
```
see the man pages for the usage for shutdown.

---

### Post by leduc900 on 2009-10-27
Let me explain again. 

What i want to do is not to shutdown manually my pc, but i would like my pc to shutdown automatically after (by ex) 1 hour of inactivity. 

Wakeonlan will only work when my pc is completely shut-down, not when it is in sleep. wakeonlan use a functionality of the BIOS. 

My idea is to use the sleep functionality of ubuntu but to change the scripts so it completely shut down in my pc in place of going to sleep. 

I tried to replace the contents of the scripts /etc/acpi/sleep.sh and /etc/acpi/hibernate.sh by the contents of the script /etc/acpi/powerbtn.sh but it does not work. 

Any idea?

---

