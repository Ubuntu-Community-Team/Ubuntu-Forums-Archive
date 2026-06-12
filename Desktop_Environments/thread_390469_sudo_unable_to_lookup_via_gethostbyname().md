---
title: "sudo: unable to lookup via gethostbyname()"
date: 2007-03-22
forum: Desktop Environments
---

### Post by johnbl on 2007-03-22
My etc/hostname was missing.
So created hostname file with sole line " interserve"

edited etc/hosts

and inserted as first line interserve

now reads;

interserve
127.0.0.1 localhost.localdomain localhost 

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

However;

sudo: unable to lookup interserve via gethostbyname()

So no password input, no admin capability!

The screw up occurred on an aircraft - a wireless mouse isn't a good thing to use  I figure, well now <G>

Any ideas as to where else I can poke around to ge this system back up fully would be most appreciated.

Johnbl

---

### Post by dfreer on 2007-03-22
Try rebooting and use recovery mode: That will give you root access. 

```

**[B]interserve**[/B]
127.0.0.1 localhost.localdomain localhost

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```
The line in bold should not be in there, I should think. it should be like this:
```
127.0.0.1 localhost.localdomain localhost interserve

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

---

### Post by johnbl on 2007-03-22
Genius! Worked a treat. Had tried before after instead of but not following.

Thankyou for your help.

Johnbl

---

### Post by kgr132 on 2007-03-31
Thanks a bunch. I'd previously tried to change the name of my computer and somehow ended up with different names in the /etc/hostname and /etc/hosts files. This caused the "unable to lookup via gethostbyname()" problem. Making both files have the same name fixed that problem, but I lost all internet connectivity until I had my old computer name (that I'd chosen during installation) in both files, instead of the new name I wanted to change to. Oh well. Thanks to these tips and recovery mode, at least it's back the way it was and everything works again.

---

### Post by dfreer on 2007-04-01
Welcome :D

---

