---
title: "after online updates root account doesn't work"
date: 2006-09-17
forum: Desktop Environments
---

### Post by cccc on 2006-09-17
hi

I have dapper drake.
after online updates **sudo** doesn't work.```

ubuntu@(none):/$ sudo
sudo: unable to lookup (none) via gethostbyname()

ubuntu@(none):~$ sudo root passwd
sudo: unable to lookup (none) via gethostbyname()

```
```

ubuntu@(none):/$ cat /etc/hosts
127.0.0.1       localhost
127.0.1.1       ubuntu

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

---

