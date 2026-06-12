---
title: "[SOLVED] sudo: unable to resolve host mylaptop?"
date: 2008-12-03
forum: General Help
---

### Post by dougleduck on 2008-12-03
sudo: unable to resolve host mylaptop

I get this error whenever I run sudo, but the command runs. Whats wrong?

---

### Post by Titan8990 on 2008-12-03
You get that error everytime you run sudo? Is mylaptop the name of your local machine?

---

### Post by dougleduck on 2008-12-03
Yes and yes.

---

### Post by adult swim on 2008-12-03
post the results of ```
cat /etc/hosts
```

---

### Post by dougleduck on 2008-12-03
```
#next 2 lines added by me
#127.0.0.1 localhost
#127.0.1.1 mylaptop

# The following lines are desirable for IPv6 capable hosts

::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

I added and commented out the first couple of lines before which didn't fix the problem I seem to remember

---

### Post by adult swim on 2008-12-03
what do you get for ```
cat /etc/hostname
```

---

### Post by bodhi.zazen on 2008-12-03
You have to have the same host name in 

/etc/hosts (under 127.0.0.1 and 127.0.1.1) and /etc/hostname

127.0.0.1 localhost mylaptop
127.0.1.1 mylaptop

---

### Post by dougleduck on 2008-12-03
...I already tried that. But now it worked this time :S. Thanks :)

---

