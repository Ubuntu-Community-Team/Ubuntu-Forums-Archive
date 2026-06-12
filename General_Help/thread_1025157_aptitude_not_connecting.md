---
title: "aptitude not connecting"
date: 2008-12-29
forum: General Help
---

### Post by zoomiest on 2008-12-29
its a mystery...

I just installed the new Ubuntu server 8.x (LAMP installation) and although I can ping servers, local, and further out, Apt can't seem to connect to any repositories when I try apt-get update or upgrade... (or install lynx, etc.)...

Any suggestions on what to look for?

After putting in a new (Vonage) router I had to Enable IGMP Multicast to get my Ubuntu desktop to connect, but, that hasn't helped the LAMP server... is it typical that the firewall (iptables) block off everything, out of the box?

Summary:
1. I can ping anything
2. /sbin/ifconfig shows my (router-based) dhcp server gives me an IP and everything looks good.
3. Everything else on the network can surf and connect... (linux and windows)

... but I can't get apt to connect to its repositories... (help)

---

### Post by braddcadd on 2008-12-29
Is apt-get trying to access the internet or is it trying to file files on a local repository only? like a cdrom or something?

Have you modified your System->Admin->Software Sources?

Just a couple guesses.

---

### Post by zoomiest on 2008-12-29
It is trying to get access to the Internet. I don't see any play for the CD. There isn't a CD in the drive. The error messages say that it can't connect to the URL for the sources...

Also, I have not modified these sources, in apt (sources.list).

---

### Post by eBoxNet on 2008-12-29
you can try this (if you haven't allready try it)
[http://ubuntuforums.org/archive/index.php/t-618053.html](http://ubuntuforums.org/archive/index.php/t-618053.html)

---

