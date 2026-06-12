---
title: "ifdown ifup at startup"
date: 2006-07-12
forum: Desktop Environments
---

### Post by Thorndeux on 2006-07-12
Hello everyone,

after startup I always have to deactivate and reactivate my eth0 before i can access the internet. I remember having read something about it in this forum before, but I wasn't able to find it again. Is there a easy way out?

I was thinking of having that done at startup manually, but how do I do that? Do I just produce a file with gedit that says:

ifdown eth0
ifup eth0

and run it at startup (which I'd do via System>Preferences>Sessions)? I mean, wouldn't that just be a textfile and not do anything?

I other words:
1. How do I get to execute commands in the terminal at startup?
2. Shouldn't there be a more elegant solution to the problem in the first place?

Thanks, Thorn

---

### Post by mogelhead on 2006-07-12
Try [this]("https://wiki.ubuntu.com/NetworkNotEnabled") article.

The key is to set eth0 to auto in the file /etc/network/interfaces.

"auto eth0"

---

### Post by Thorndeux on 2006-07-12
Sorry, didn't search properly earlier. Now I find millions of posts about problems like that.
Thanks for your help, though.


EDIT: Unfortunately, it still doesn't work. My interfaces file says:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.

# The primary network interface
auto eth0
iface eth0 inet dhcp
```

So, it doesn't seem to be connected to the auto eth0 setting. Any other ideas?

---

### Post by Thorndeux on 2006-08-06
Bump

---

### Post by Del Pede on 2006-10-19
A quick solution would be to add 
ifdown eth0
ifup eth0

to /etc/rc.local. The two commands would be run at start up

---

