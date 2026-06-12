---
title: "changing the desktop name on ubuntu 9.04"
date: 2009-10-19
forum: Desktop Environments
---

### Post by g_lev on 2009-10-19
hello, I would like to change the desktop name on ubuntu 9.04. I read that it can be done by 'system > administration > network' from here: [http://ubuntuforums.org/showthread.php?p=4516606](http://ubuntuforums.org/showthread.php?p=4516606) however there is no 'system > administration > network' on ubuntu 9.04.  any idea ?

---

### Post by mac9416 on 2009-10-19
You have to edit /etc/hostname and /etc/hosts.

**/etc/hostname** is pretty straightforward. Run this command, change the hostname, and save the file.

```
$ sudo gedit /etc/hostname
```

**/etc/hosts** is a little more tricky, but not bad. Run the following command, then change edit the hostname following "127.0.1.1".

```
$ sudo gedit /etc/hosts
```

This:

> 127.0.0.1    localhost
127.0.1.1    old_hostname

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

Should now look like this:

> 127.0.0.1    localhost
127.0.1.1    new_hostname

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

**Remember** no spaces are allowed in the hostname! Good luck.

Source: [http://www.rebelzero.com/fixes/changing-your-computers-hostname/60](http://www.rebelzero.com/fixes/changing-your-computers-hostname/60)

---

### Post by g_lev on 2009-10-20
worked great. thank you : )

---

