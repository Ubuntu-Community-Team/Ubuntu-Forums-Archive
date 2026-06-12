---
title: "Not resolving DNS causing internet to act slow?"
date: 2006-09-01
forum: Desktop Environments
---

### Post by SvanteH on 2006-09-01
Currently I can't access Google.com but I can access the IP of it, 66.102.9.104 (Swedish) and then it works perfect, high speed and all. Any ideas what has gone wrong? I have turned of IPv6 in Firefox but it's not really only firefox.

I got a D-Link router and I can't go direct connection to the internet to try for a diffence since it's located to far from the computer.

---

### Post by FuriousLettuce on 2006-09-01
If you find you are having trouble in other programs, do the following:

```
sudo nano -w /etc/modprobe.d/blacklist-ipv6
```

and in the file insert the following code:

```
blacklist ipv6
```

Reboot, then check it hasn't been loaded by doing

```
lsmod | grep ipv6
```

That should sort out your issues :-)

---

### Post by SvanteH on 2006-09-01
I'll try as soon as I get home, thanks! :)

---

### Post by kerry_s on 2006-09-01
I just had issues with a new modem/router that had crapy dns. I changed my system to use open dns. It's really easy just go to /etc/dhcp3/dhcient.conf and add this line> prepend domain-name-servers 208.67.222.222, 208.67.220.220;   <you must do this as root, than check if it worked here> [http://www.opendns.com/start/unix.php](http://www.opendns.com/start/unix.php)

---

### Post by SvanteH on 2006-09-01
Question ~~
Is there a server in Europe there already? I didn't see one and if not is there a Europe comparision.

---

