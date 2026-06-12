---
title: "Need XPS m1330 interfaces file"
date: 2007-11-20
forum: Dell  Ubuntu Support
---

### Post by Pod_Man on 2007-11-20
well silly me, i managed to bugger up my /etc/networking/interfaces file trying to do some vitual machine stuff. and because i am a n00b, i did not back it up. Can someone help me out by pasting in the contents of that file from a working 1330? i was using all default dhcp settings and whatnot. its weird, i was able to get my net up and running, but the manager is still all screwy. Thanks much!

-Pod_Man

---

### Post by robdudley on 2007-11-21
Taken from a Gutsy m1330. 

Cheers, 

Rob

---

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

---

### Post by Pod_Man on 2007-11-21
Thanks Much! still not quite back to normal though... its weird, all that shows up are wireless networks, even though it is plugged in. so i flipped the wireless switch off and rebooted. now no wireless comes up, but the wired still doesnt either. it still works though (the wired) because im online now. just doesnt show up in the manager. :confused:

---

