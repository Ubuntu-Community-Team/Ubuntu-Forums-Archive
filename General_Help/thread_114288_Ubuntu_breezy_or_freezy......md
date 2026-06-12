---
title: "Ubuntu breezy or freezy....."
date: 2006-01-08
forum: General Help
---

### Post by Red Sand on 2006-01-08
Hi,

I finaly changed my main system to Ubuntu from m$ yesterday.
Got every working (wifi, mail, usb hd, gimping like mad;) ), but every now and again it freezes / hangs. The first two times it happend I was closing or changing a tab in FF and the thirdtime I was downloading packages for xmms install.
Now I have installed Ubuntu and Debian a few times, but I'm still a newb. :p But if I remember correctly I did have a crash with Debian once or twice, but after a hard reboot I got the message check this logfile for details....
Any help on debugging the problem is greatly appriciated.
Thx.
----------------------------
Update:
In the last hour I had 2 more freezes, once while just scrolling down a webpage and once while downloading another package through synaptic. Just a thought, but could it be my wireless nic? It's a Linksys WMP54G, fully Ubuntu compatible.

---

### Post by Red Sand on 2006-01-08
Yeah fixed it....
Turns out that my syslog showed an IRQ conflict.
Turned IRQ resevations for USB of in my stone age BIOS and, running like a charm.
:D :D :D

---

### Post by Iandefor on 2006-01-08
Good deal. I like that... "Freezy" :-D.

I had my first ever freeze on Linux yesterday, after using it for a full year.
Not bad, considering I got a BSOD on Windows once every week.

---

### Post by Thirsteh on 2006-01-08
There's almost always a logical explanation to freezes/hangs in Linux, unlike Windows :) 

<3 <3 <3 hearts <3 <3 <3 Ubuntu

---

### Post by Iandefor on 2006-01-08
[quote=Thirsteh]There's almost always a logical explanation to freezes/hangs in Linux, unlike Windows :) 

<3 <3 <3 hearts <3 <3 <3 Ubuntu[/quote] Yup. In my case, it was the fact that I was playing around with xcompmgr... it crashed and brought my system down with it. Even then, I was able to restart X and it was fine.

---

### Post by hackworth on 2006-01-08
forgive my noobish-ness, but which log files did you check? i have been getting system freezes as well, and i'd love to be able to put a finger on what exactly the problem might be.

thanks.

---

### Post by Red Sand on 2006-01-09
there is a /var/log folder that contains the log u need. Ubuntu has made a really usefull shell around it: applications --> system tools --> systemlog. 
Where the syslog and the messages log the important once are.
Good luck.

It is nice that there is always an logical explanation and that you can debug it yourself most of the time.
However :p ......... when I was researching my problem and going through freeze threads, I must say I found so many of them. That I'm wondering if this release is as stable as many suggest.

---

### Post by Efwis on 2006-01-09
[QUOTE=Red Sand]
However :p ......... when I was researching my problem and going through freeze threads, I must say I found so many of them. That I'm wondering if this release is as stable as many suggest.[/QUOTE]
I have found that most of the time the freezes are caused by hardware not the software itself. unfortunately we live in a world where close to 90% of all the hardware is designed with Windows in mind. until **all**the manufacturers get on the bandwagon and allow more linux compatibility this will probably be the case.

---

### Post by Red Sand on 2006-01-09
[QUOTE=Efwis]I have found that most of the time the freezes are caused by hardware not the software itself. unfortunately we live in a world where close to 90% of all the hardware is designed with Windows in mind. until **all**the manufacturers get on the bandwagon and allow more linux compatibility this will probably be the case.[/QUOTE]

Guess your your right on that one. I have 8 year sysadm in m$ environments experience. The main advantage I see in linux (since in the end you can solve most m$ problems aswell) is that you dont have to depend on m$ patches and so on, but you can configure and troubleshoot all you want to.

---

