---
title: "host not recognised?"
date: 2009-05-23
forum: General Help
---

### Post by abhilashm86 on 2009-05-23
I'd changed my terminal name in /etc/hostname, from then on terminal treats me like unable to resolve kinda thing, so where actually i need to edit the information of hosts.
I changed the hostname because,it was too lenghty n kinda abhilash@Desktop~,
so please help to resolve...........


```
abhilash@abhilash:~$ sudo su
sudo: unable to resolve host abhilash
[sudo] password for abhilash: 

```

---

### Post by capscrew on 2009-05-23
Did you reboot the system?  The system reads the /etc/hostname upon startup.

---

### Post by abhilashm86 on 2009-05-23
yea i did reboot, well this shows the file,
```

abhilash@abhilash:~$ cat /etc/hostname
abhilash

```
why does shell prompt the error, i've no idea. Which file should i change......

---

### Post by abhilashm86 on 2009-05-23
hey i just figured out the error, there's a file in /etc/hosts which read before.......
```

abhilash@abhilash:~$ cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	abhilash@Desktop

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

then i edited as,
```
abhilash@abhilash:~$ cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	abhilash

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```
so now there's no error by the shell,
```
abhilash@abhilash:~$ sudo su
[sudo] password for abhilash: 

```

---

