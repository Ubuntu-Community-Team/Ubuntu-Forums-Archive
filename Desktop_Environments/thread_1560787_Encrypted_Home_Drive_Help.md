---
title: "Encrypted Home Drive Help"
date: 2010-08-25
forum: Desktop Environments
---

### Post by dmillerct on 2010-08-25
During the OS setup process I chose to have my home drive encrypted (I figured extra security, why not?) Only after the fact did I realize that this prevents the ability for an automatic log on. 

To make a long story short I tried to de-encrypt my home drive and I am now receiving the following two error messages when I log into gnome:

Could not update ICEauthority file /home/dqadmin/.ICEauthority

followed by:

There is a problem with the configuration service. (usr/lib/libgconf2-4/gconf-sanity-check-2 ended with state 256)

I tried to do the following as described in this thread:
[http://ubuntuforums.org/showthread.php?t=949750]("http://ubuntuforums.org/showthread.php?t=949750")

from recovery mode, dropped into root shell:
```
chown dqadmin:dqadmin /home/dqadmin/.ICEauthority
chmod 644 /home/dqadmin/.ICEauthority
exit
```

However this did not work for me. I hope someone out there has a fix for me. :o

---

### Post by tbrminsanity on 2010-08-27
Due to my work's security requirements I had to have my hard drive encrypted.  I got the same error you got when I changed my system password.  These are the steps I took to fix my machine.

[LIST]
[*]CTL + ALT + F1  (or open a terminal instead of Gnome)
[*]ecryptfs-mount-private  (to log into my encrypted hard drive)
[*]ecryptfs-rewrap-passphrase wrapped-passphrase (to reset my password)
[/LIST]

I hope this helps you out.

---

