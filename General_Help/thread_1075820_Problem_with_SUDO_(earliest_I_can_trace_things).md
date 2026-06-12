---
title: "Problem with SUDO (earliest I can trace things)"
date: 2009-02-20
forum: General Help
---

### Post by Soarhead on 2009-02-20
The first symptom of my problem is that Update Manager does not go beyond "Install Updates" - if I try to run this it just hangs. 

However I suspect what is at the root of this (sic) is that when I open a terminal and type sudo I get the response "Cannot resolve john-desktop" and it stops there. I wonder if these two are linked! 

Any help needed. If its not a software problem it could be my motherboard is k****ered. :(

---

### Post by jerome1232 on 2009-02-20
Sounds like your hostname doesn't match what /etc/hosts says it is.

You'll need to edit 
/etc/hostname
and
/etc/hosts

for example mine look like this, you just need to make the 127.0.1.1 entry match what's in /etc/hostname


contents of /etc/hostname on this machine
```
direbane

```
contents of /etc/hosts on this machine
```
127.0.0.1	localhost
127.0.1.1	direbane
192.168.1.3	teamspeak

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

---

### Post by Soarhead on 2009-02-24
Thanks for that. Sadly it does not allow me to edit hostname - says I don't have permission to save it. And since I can't persuade sudo to work I can't see a way round this!

---

### Post by mb_webguy on 2009-02-24
Login using the recovery console.  This will drop you into a console login (like the terminal) as root.  Then you can use nano to edit what files you need.

---

