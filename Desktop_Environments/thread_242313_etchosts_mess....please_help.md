---
title: "/etc/hosts mess....please help"
date: 2006-08-23
forum: Desktop Environments
---

### Post by shagey36 on 2006-08-23
hey i was playing around with my internet and i kinda erased my /etc/hosts file....and maybe some other stuff

anybody know how i can automatically reconfigure this....like how it was after ubuntu installed

---

### Post by ZiZi on 2006-08-23
> **shagey36 said:**
> hey i was playing around with my internet and i kinda erased my /etc/hosts file....and maybe some other stuff

anybody know how i can automatically reconfigure this....like how it was after ubuntu installed

AFAIK there is little to be fixed concerning the /etc/hosts file. Just create the file containing this:
```
127.0.0.1 localhost your_computer_network_name
127.0.1.1 your_computer_network_name

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

This is roughly what it looks like after fresh installation, I don't mess change it very often. If there is anything else you erased, you'll have to figure out what exactly it was :)

---

