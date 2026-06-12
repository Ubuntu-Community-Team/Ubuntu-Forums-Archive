---
title: "Net"
date: 2005-12-03
forum: Desktop Environments
---

### Post by digitalice on 2005-12-03
Hi, my name is Digital Ice... and im a new UBUNTU user....:KS 

I used ubuntu 5.10 LIVE version....
When i was going to a URL....i discovered that my net conection wasn´t working...:confused: 

i cheked my IP and my GATEWAY by doing IFCONFIG..and all was ok....
:confused: 
HELP PLZ...



PD: SORRY ABOUT MY ENGLISH

---

### Post by invalid on 2005-12-03
We will need a little more details. Is it just through a browser that you can not connect? Try opening a terminal and typing:```
ping -c 5 google.com
```and```
ping -c 5 72.14.207.99
```and see what happens. 

Cb

---

### Post by digitalice on 2005-12-03
yes...ping works... :rolleyes: 
but slow....
and if i put a URL in the firefox it says....looking......
and then....timeout...:confused:

---

### Post by invalid on 2005-12-03
If you can ping the domain with no problems, you should be able to visit it with a browser. Do you have a proxy enabled, or something that reroutes your traffic perhaps by mistake?

Cb

---

### Post by cwaldbieser on 2005-12-03
[QUOTE=digitalice]yes...ping works... :rolleyes: 
but slow....
and if i put a URL in the firefox it says....looking......
and then....timeout...:confused:[/QUOTE]
This sticky should help walk you through the common problems.  Sounds like you might just have to turn off ipv6.

[http://ubuntuforums.org/showthread.php?t=87643]("http://ubuntuforums.org/showthread.php?t=87643")

---

