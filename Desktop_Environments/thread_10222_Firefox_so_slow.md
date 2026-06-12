---
title: "Firefox so slow"
date: 2005-01-06
forum: Desktop Environments
---

### Post by dwiggy on 2005-01-06
Hello and thanks for considering my problem.

I just loaded Ubuntu on a 400 mHz PC with 192 RAM.   

Firefox takes forever to resolve a webpage then load it.

Per other suggestions in this forum, I turned off IPv6 both in Firefox about:config and in the Aliases file.    No improvement.

Why is this happening?   I loaded the Ubuntu live CD on a computer at my office with a faster CPU and more RAM (512 MB I think), and Firefox worked great.   But it seems that I have enough CPU and RAm and that something else is wrong.

Thanks!

---

### Post by fng on 2005-01-06
Take a look here : [http://ubuntuforums.org/showthread.php?t=8170](http://ubuntuforums.org/showthread.php?t=8170)

It seems firefox doesnt like slow cpu's :(

---

### Post by dwiggy on 2005-01-06
Thanks, FNG.   I've used Firefox under Windows 2000 with a 266 CPU and 256 RAM, and it worked fine.    Is Linux different in that respect?   400 mHz is a fast enough chip in my book, for websurfing and word processing anyway, and while I would like more RAM, the system monitor says I am only using half of the RAM.

Could Gnome be the problem?  Would Firefox work faster under Xfce?

Thanks!

---

### Post by Sensebend on 2005-01-06
Try epiphany, it's package name is epiphany-browser, it is based on mozilla and seems to be faster than firefox in my opinion. Not sure if that is based on fact or perception.

---

### Post by wallijonn on 2005-01-06
what does your /etc/hosts file look like? see those IPv6 entries? rem them out then reboot.

---

### Post by HiddenWolf on 2005-01-06
[QUOTE=wallijonn]what does your /etc/hosts file look like? see those IPv6 entries? rem them out then reboot.[/QUOTE]

A more user-friendly approach would be to check about:config in firefox itself.
The devs really should disable IPv6 by default...

---

### Post by Rancoras on 2005-01-06
[QUOTE=HiddenWolf]A more user-friendly approach would be to check about:config in firefox itself.
The devs really should disable IPv6 by default...[/QUOTE]
He already did that to no effect.

---

### Post by wallijonn on 2005-01-06
[QUOTE=HiddenWolf]The devs really should disable IPv6 by default...[/QUOTE]
uh, now. they're enabled by default. look at what Shorewall, FireStarter and Postfix look for, for example. All the latest distros probably have IPv6 enabled by default.  

[http://www.nanog.org/mtg-0405/pdf/miller.pdf](http://www.nanog.org/mtg-0405/pdf/miller.pdf)

---

