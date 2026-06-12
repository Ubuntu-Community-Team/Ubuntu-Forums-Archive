---
title: "&quot;su returned with an error&quot; - missing/wrong hostname?"
date: 2005-12-06
forum: Desktop Environments
---

### Post by lodp on 2005-12-06
hi,

i appear to be locked out in kubuntu breezy...
i can't change system settings anymore (e.g. , when i hit the "administrator mode" in the network settings, it returns "su returned with an error"). when i try sudo -s in the terminal, it says "unable to lookup  via gethostbyname()".

now after reading up a bit i'm pretty sure it's something with the hostname. trying to get wifi running (and not really knowing what i was doing) i changed the hostname from "ubuntu" to just nothing (i did this in gnome, which i run parallel to kde). the thing is now that i can't get into root mode, i can't change the hostname back. so i'm all caught up it seems... any ideas how i could get out of this?

it IS the missing / wrong hostname, right? when i enter "hostname" in the terminal, i get an empty line. also, there's nothing in the "hostname" and the "domain" fields in the "domain name system"-tab of the network settings.

---

### Post by lodp on 2005-12-06
jus thought it would be usefull to post the content of some of those files...

/etc/hosts
```

127.0.0.1 localhost.localdomain localhost 

# The following lines are desirable for IPv6 capable hosts
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
::1 ip6-localhost ip6-loopback
```

/etc/hostname

```
 
```

yes, right, there's nothing in that file...

now i read that when i get into recovering mode, i'm root automatically - i just wonder which files i need to edit and how, to get it to work again... just enter "ubuntu" in etc/hostname and in the place of "localhost" in the etc/hosts ?

---

### Post by lodp on 2005-12-06
ok, i solved the problem. i hereby reprimand myself for not having done a more extensive search in the forums. bad boy.

so for all the fellow newbies who might run across this post looking for a solution to the same problem sometime, heres what i did:

i went into recovery mode in grub and, having root access, changed /etc/hostname to contain "ubuntu" (nothing else in there) and changed the first line of /etc/hosts from

```
127.0.0.1 localhost.localdomain localhost
```

to

```
127.0.0.1 localhost.localdomain localhost ubuntu
```

that did it, i got root access back now in kde

---

