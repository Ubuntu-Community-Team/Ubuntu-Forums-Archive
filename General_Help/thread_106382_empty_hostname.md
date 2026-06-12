---
title: "empty hostname"
date: 2005-12-20
forum: General Help
---

### Post by Nickoladze on 2005-12-20
when configuring my network connections i accidently cleared the hostname area and now its blank. basically i cant use the sudo command to become root and fix it, i get:
> sudo: unable to lookup  via gethostbyname()


so am i screwed here?

---

### Post by kaamos on 2005-12-20
You can get root access by choosing "Recovery mode" in grubs menu.

---

### Post by Nickoladze on 2005-12-20
yes but how would i go about changing my hostname?

---

### Post by Dr. Nick on 2005-12-20
run 
sudo nano /etc/hostname
and type a name in. no special syntax needed

---

### Post by Nickoladze on 2005-12-20
yeah that got the hostname but i still get this error when logging in:
> Could not look up internet address for <hostname>.
This will prevent GNOME from operating correctly.
It may be possible to correct the problem by adding
<hostname> to the file /etc/hosts.
where <hostname> is my hostname

i opened the file hosts which says this:
> 127.0.0.1 localhost.localdomain localhost 

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


and changed it to:
> 127.0.0.1 localhost.localdomain localhost 

# The following lines are desirable for IPv6 capable hosts
<hostname>::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


and i still get the error

is that how im supposed to edit it? hmm

---

### Post by Thunk on 2005-12-20
Just enter again the same name you deleted.

---

### Post by schilcha on 2005-12-20
Once had similar troubles... can't really remember the details... however, the first line of my /etc/hosts looks like this:
> 127.0.0.1 smithers.springfield localhost smithers, where "smithers" is the hostname and "springfield" is my private domain.

Hope this helps!

---

### Post by Nickoladze on 2005-12-20
[QUOTE=schilcha]Once had similar troubles... can't really remember the details... however, the first line of my /etc/hosts looks like this:
, where "smithers" is the hostname and "springfield" is my private domain.

Hope this helps![/QUOTE]

aha that worked! thanks :D

---

