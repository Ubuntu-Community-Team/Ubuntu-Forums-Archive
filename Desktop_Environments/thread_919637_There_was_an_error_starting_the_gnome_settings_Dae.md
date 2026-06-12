---
title: "There was an error starting the gnome settings Daemon."
date: 2008-09-14
forum: Desktop Environments
---

### Post by DrSunnysock on 2008-09-14
There is this password protected Windows 2000 computer that I'm trying to overwrite with Ubuntu, but when I try to boot from the disc or install I get the following message:

[I]"There was an error starting the gnome settings Daemon.
The last error message did not receive a reply. Possible causes include the remote application did not send a reply, the reply timeout expired, or the network connection was broken."
[/I]

I also get something about a clock being misconfigured, or something.

What do I do? Please help.

---

### Post by DrSunnysock on 2008-09-15
Bump

---

### Post by DrSunnysock on 2008-09-15
bump

---

### Post by DrSunnysock on 2008-09-16
bump

---

### Post by DrSunnysock on 2008-09-17
bump

---

### Post by DrSunnysock on 2008-09-18
bump

---

### Post by hellion0 on 2008-09-19
I've heard of that bug after install. Never heard of it occuring on the LiveCD, but I guess it's possible.

You might want to try the Alternate CD. It'll install just the same, but hopefully without the nasty errors.

---

### Post by terry_gardener on 2008-10-04
could try the following

quick fix for this is to restart x server, press ctrl+alt+backspace 
then logon. 

if this happens everytime you logon or bootup the system then the instructions in the following link. 

[http://ubuntuforums.org/showthread.php?t=395456](http://ubuntuforums.org/showthread.php?t=395456)

---

### Post by Lou_Cypher on 2008-10-29
As suggested in a forum for another ditro (and what ended up working for me), was to remove the /tmp/gconfd-yourusername/ directory.

---

