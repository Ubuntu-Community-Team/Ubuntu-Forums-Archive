---
title: "my firefox is choosing..."
date: 2009-01-05
forum: General Help
---

### Post by superpink99 on 2009-01-05
ok recently i observed that my firefox in ubuntu is not working properly, it always says error when i open other sites, but the other sites it can open it

i tried to open same sites in my firefox in xp and it works......

can someone tell me whats wrong please.............

---

### Post by howefield on 2009-01-05
Is that it ?

What is the error that you are getting, is there more to it than simply the one word ?

---

### Post by 73ckn797 on 2009-01-05
> **superpink99 said:**
> ok recently i observed that my firefox in ubuntu is not working properly, it always says error when i open other sites, but the other sites it can open it

i tried to open same sites in my firefox in xp and it works......

can someone tell me whats wrong please.............


I was having similar problems after importing bookmarks into a new Firefox installation. I found that the last letter of the links had been cut off.

Example being that if the link had "aspx" or anything else on the end, the "x", or whatever was the case, was missing. See if that could be your issue. Not all of the links were bad. You could shorten the address to end at the ".com" or whatever.

---

### Post by superpink99 on 2009-01-05
It tell me "Page Load Error" address not found........this is weird........

for example when i type "google earth" and press enter it shows a list of where to choose, but when i click on one it says address not found, now i tot maybe its just for this site but then i observed its the same with others.

---

### Post by blazemore on 2009-01-05
How are you accessing the Internet?

---

### Post by superpink99 on 2009-01-05
to make things clear, my firefox is still working but its kinda choosing the ones its opening.....i made some comparison with my firefox in xp on the same laptop the one in xp works just fine it can open the sites firefox in ubuntu cannot.

---

### Post by blazemore on 2009-01-05
Look at the sites it's not loading.
do
```
ping www.**sitename**.com
```
Does the ping work (Press CTRL+C after a few seconds to end the pinging)

---

### Post by superpink99 on 2009-01-05
ok i tried pinging several sites, it shows the same problem "unknown host", but the ones i pinged were sites i used to go to like eHow.com

---

### Post by blazemore on 2009-01-05
```
gedit /etc/hosts
```
I have a hunch...

Is this file long?
Paste the results here (If it's not really long)

---

### Post by superpink99 on 2009-01-05
127.0.0.1	localhost
127.0.1.1	eric-laptop

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

this is the code, and oh did i paste it correctly?

---

