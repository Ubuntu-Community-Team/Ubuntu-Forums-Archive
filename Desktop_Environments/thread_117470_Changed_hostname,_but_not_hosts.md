---
title: "Changed hostname, but not hosts"
date: 2006-01-14
forum: Desktop Environments
---

### Post by Roy Collins on 2006-01-14
Yes, I know, stupid mistake. :( 

I edited /etc/hostname to change my computer name.  Didn't even think about needing to make the same change in /etc/hosts.

Now - I can't su, and the files in question are owned by root.

Any suggestions on how I might recover from this?

Oh yeah - I'm running 5.10, Gnome.

Thanks! 

Roy

---

### Post by 23meg on 2006-01-15
Can you boot into recovery mode? If you can, type ```
nano /etc/hosts
```and make your /etc/hosts look like this```

127.0.0.1 localhost.localdomain localhost HOSTNAME

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```
replacing HOSTNAME with your hostname.

---

### Post by Roy Collins on 2006-01-15
Thank you so VERY much, sir!

Now I can stop sweating.....

Roy

---

### Post by 23meg on 2006-01-15
Glad I could help; recovery mode is your friend in such situations.

---

