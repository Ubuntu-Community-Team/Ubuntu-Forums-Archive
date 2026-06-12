---
title: "Problem with Synaptic and Proxy"
date: 2006-06-23
forum: Desktop Environments
---

### Post by DavidCar on 2006-06-23
Hi!
I've been using Ubuntu a while in dual-boot with windows in home and office and it works great (although I always change that "Chocolate" look):mrgreen:D .
Recently I used the Alternate Install image to upgrade my ubuntu from breezy to dapper in my office PC but now I'm having problems with Synaptic and the proxy I use to get access to internet; the funny thing is that the only that isn't working is APT and, of course, Synaptic; Firefox and even GAIM used their proxy settings from breezy, even Synaptic in its Network Configuration shows me the correct proxy (username:pass@myproxy:port) but when I try anything it just says

"http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz: 407 Proxy Authentication Required"

Please if someone could spare some valuable knowledge with me...:)

---

### Post by aysiu on 2006-06-23
Maybe [this](http://ubuntuforums.org/showthread.php?t=42946) might help?

---

### Post by DavidCar on 2006-06-23
Hi!!

It didn't work, I still get the same errors ](*,) ](*,) ](*,) :confused: :confused: 
"http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz: 407 Proxy Authentication Required
[http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz:) 407 Proxy Authentication Required
[http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz:) 407 Proxy Authentication Required"

---

### Post by aysiu on 2006-06-23
How about [this](http://www.ubuntuforums.org/showpost.php?p=1071942&postcount=10)?

---

### Post by DavidCar on 2006-06-23
HI!!!:) 

The problem has been fixed!! Thanx!!!
It seems that my menu entry for Synaptic was wrong!!

Thank you very much for your help, I've even used some strange python script to emulate NTLM authentication with the proxy; I never thought it was something this simple!!:-D

---

