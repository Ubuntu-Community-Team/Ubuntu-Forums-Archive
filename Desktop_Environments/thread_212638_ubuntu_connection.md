---
title: "ubuntu connection"
date: 2006-07-10
forum: Desktop Environments
---

### Post by davebradford on 2006-07-10
this morning i went to do an apt-get and for some reason nothing would connect? i though this was strange as i use using the internet at the time to connect the machine from a remote location, i then performed a wget on a tarball only to get this message.

dave@brads:~/noip$ wget [http://www.no-ip.com/client/linux/noip-duc-linux.tar.gz](http://www.no-ip.com/client/linux/noip-duc-linux.tar.gz)
--10:18:14--  [http://www.no-ip.com/client/linux/noip-duc-linux.tar.gz](http://www.no-ip.com/client/linux/noip-duc-linux.tar.gz)
           => `noip-duc-linux.tar.gz'
Resolving [www.no-ip.com](www.no-ip.com)... failed: Temporary failure in name resolution.
dave@brads:~/noip$

I also cannot ping amazon.co.uk, i dunno what to do from here? the internet must be working in order for me to be able2 remote in?

any ideas? cheers..

---

### Post by davebradford on 2006-07-10
bump!

---

### Post by Crosbie on 2006-07-10
Sounds like a probem with your internet connection rather than Ubuntu.

Um, or firewalling?

---

### Post by Tux+ on 2006-07-10
dns problem. If you have a D-Link router you need to set the DNS in /etc/resolv.conf and point it to a different server.

---

### Post by apoth on 2006-07-10
Put a working nameserver entry into /etc/resolf.conf

eg.

nameserver 4.2.2.2

---

### Post by davebradford on 2006-07-24
problem sorted! for some reason the dns keeps resetting after a re-boot. any idea on how to stop the script from auto detecting?

---

### Post by davebradford on 2006-07-25
bump!

---

### Post by Tux+ on 2006-08-05
Try making the resolv.conf read only AFTER you have entered the dns and in theory the os can't write to the file

---

### Post by davebradford on 2006-08-05
sounds good will try that.. thanks special friend

---

