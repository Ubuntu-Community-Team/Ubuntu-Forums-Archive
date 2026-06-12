---
title: "samba woes"
date: 2005-06-06
forum: Desktop Environments
---

### Post by not_yet on 2005-06-06
hello,

it was working but now its not :???: 

have xp and ubuntu connected

when I go to /etc/samba and run testparm I get 

> "Can't find include file /etc/samba/dhcp.conf"

how do I fix this

thanks

---

### Post by jjross on 2005-06-07
I am not really up on this, but try from a terminal and just type in testparm and see what it says

---

### Post by dierre on 2005-06-07
It sounds like you have a 
```
include = dhcp.conf
```
line in the global section of your /etc/samba/smb.conf  ....

Could you have a look and check whether it is there? But, in case it is, I really don't know what it should mean, so try to comment it and see if everything gets fixed. :-)

F.

---

