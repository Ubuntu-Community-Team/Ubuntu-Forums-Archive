---
title: "How to use host names instead of ip adresses on a home network"
date: 2006-04-15
forum: Desktop Environments
---

### Post by guzzi333 on 2006-04-15
I have a home network with a router that works with DHCP. I have three computers called
guzzi (running linux)
maca (running windows)
pvr17 (running linux)

On the windows machine I can do a ping guzzi or a ping pvr17 and that works. On guzzi and pvr17 that doesn't work. I know I can list the IP addresses in /etc/hosts but then I need to update it whenever my router decides to give different IP addresses to my boxes.

Is there a way that this works out of the box?

---

### Post by bscbrit on 2006-04-15
With only 3 computers it might be simpler to allocate fixed IP addresses.  But I'm currently googling for some answers so I may be back shortly with a fix. :-D

---

### Post by mbeach on 2006-04-15
This may help:
[http://ubuntu.wordpress.com/2006/02/06/fix-hostname-unknown-in-router/](http://ubuntu.wordpress.com/2006/02/06/fix-hostname-unknown-in-router/)

---

### Post by guzzi333 on 2006-04-15
That doesn't fix it. What I want to do is just do a ping <hostname> and ssh <hostname> on to my linux boxes. On the windows PC it recognizes the hostnames

---

### Post by mbeach on 2006-04-15
How about this one - maybe it will shed some light:
[http://www.ubuntuforums.org/archive/index.php/t-88206.html](http://www.ubuntuforums.org/archive/index.php/t-88206.html)

---

### Post by dcstar on 2006-04-15
Install the winbind package.

---

### Post by hentaidan on 2006-04-16
[QUOTE=guzzi333]Is there a way that this works out of the box?[/QUOTE]

What about System > Admin. > Networking > Hosts ?

---

