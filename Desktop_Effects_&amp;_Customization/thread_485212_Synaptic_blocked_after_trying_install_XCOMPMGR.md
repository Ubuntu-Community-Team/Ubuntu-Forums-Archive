---
title: "Synaptic blocked after trying install XCOMPMGR"
date: 2007-06-26
forum: Desktop Effects &amp; Customization
---

### Post by El Viejo Lobo on 2007-06-26
I was trying to install XCOMPMGR gedit did not worked and after that SYNAPTIC was blocked as you can see in the srceenshot attached. I do not know how to get it cleaned up from the source list.
Thanks for any help to come.

---

### Post by RAH66 on 2007-06-26
open
/etc/apt/sources.list
then search for XCOMPMGR and remove the lines that say incomplete

I had the same issue with virtualbox and this method worked for me :D

---

### Post by RAH66 on 2007-06-26
Sorry this is the right method

1) use the following command to open nautilus with root privileges:
sudo nautilus

2) open the file:
/var/lib/dpkg/status

3) search for "XCOMPMGR" you should find the following lines:
Package: XCOMPMGR
Status: install reinstreq half-installed
Priority: optional
Section: misc
Version: 1.3.6_Ubuntu_edgy

4) Remove these lines from the file and save

You should now be able to use synaptic again!

:D

---

### Post by El Viejo Lobo on 2007-06-26
Thanks a lot I did "gksudo gedit /etc/apt/sources.list " then "delete"  and Synaptic  is like new.

It looks that my Laptop will have no XCOMPMGR and no AWM  for the moment. :p

---

### Post by RAH66 on 2007-06-26
Glad your problem is sorted ...

I just reinstalled my virtualbox and the second time around it worked fine so maybe it can work for you dont give up is all I say there is a way through lol enjoy ;)

---

