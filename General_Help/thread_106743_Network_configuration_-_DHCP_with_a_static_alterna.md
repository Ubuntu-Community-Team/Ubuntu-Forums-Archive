---
title: "Network configuration - DHCP with a static alternative"
date: 2005-12-21
forum: General Help
---

### Post by Adam Atlas on 2005-12-21
I have a rackmount server which I'm soon going to be coloing, and I've installed the server version of Breezy on it. Currently it's connected to my home network, configured using DHCP, and I'm working on it from my personal computer over SSH. But once it's at the colo facility, of course, it's going to have a static IP. So that the transition will be painless, and so that it'll be less convenient if I ever need to have them ship it back so I can work on it at home, is there a way for me to have it try to configure by DHCP by default, but fall back onto a static configuration (the static IP, subnet, and gateway, which the colo company has provided to me) if no DHCP server is present?

---

### Post by Masteroc on 2005-12-21
i know that in the regular version of breezy, there is a network manager that will allow u to have profiles with different settings, but im not sure if the same is true for the server edition.

---

### Post by localzuk on 2005-12-21
You might like to look at having multiple IP addresses assigned to one network card. Eg. You could have eth0:0 set to use DHCP and eth0:1 set to use static. There is some information about doing this at [http://www.yolinux.com/TUTORIALS/LinuxTutorialNetworking.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialNetworking.html) Bear in mind that the instructions there are for fedora (it appears).

I will take a look when I get home from work at doing this on my test box and post how I did it (I have done it before...)

---

### Post by Adam Atlas on 2005-12-21
[QUOTE=localzuk]You might like to look at having multiple IP addresses assigned to one network card. Eg. You could have eth0:0 set to use DHCP and eth0:1 set to use static. There is some information about doing this at [http://www.yolinux.com/TUTORIALS/LinuxTutorialNetworking.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialNetworking.html) Bear in mind that the instructions there are for fedora (it appears).

I will take a look when I get home from work at doing this on my test box and post how I did it (I have done it before...)[/QUOTE]

That seems to work. Now, how would I configure it to use the right gateway address? `route` seems to ignore eth0:0, just assigning the gateway to eth0 instead.

---

### Post by Adam Atlas on 2005-12-21
I'm trying to use /etc/network/interfaces instead, with its mapping feature. I have two questions about this: [LIST]
[*]It needs a script to choose which interface to bring up. How would I do that? I need some way to detect if there's a DHCP server on the local network. What would be the best way to do that, without automatically using it for configuration?
[*]What would be the best way to set resolve.conf when it is using the static interface? dhclient apparently edits that file automatically. Perhaps in /etc/network/interfaces, should I have a "post-up" script that overwrites resolve.conf?
[/LIST]

---

### Post by localzuk on 2005-12-21
I'm at home now so give me a few hours and I will have a mess...

---

