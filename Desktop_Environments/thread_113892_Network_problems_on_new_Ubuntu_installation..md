---
title: "Network problems on new Ubuntu installation."
date: 2006-01-07
forum: Desktop Environments
---

### Post by Boopop on 2006-01-07
When I was installing the breezy 64bit edition of ubuntu, I got an error saying DCHP failed to configure. "Simple" I thought," I'll just do it manually" this is exactly what I did. Now it's installed I can't connect to the network. I've tried configuring DHCP again, and using a different Static IP. I found the subnet mask was incorrect, I fixed that but I still cannot connect to my network. I have a ASRock Dual939 motherboard with an ALI Network port.

Any help would be greatly appreciated :)

---

### Post by zappa86 on 2006-01-07
How much functionality do you have on your network? can you even ping anyone? Also sometimes it just wont bring up the adaptor try doing an ifup eth0 (or whatever your card is called).

---

### Post by Boopop on 2006-01-07
[QUOTE=zappa86]How much functionality do you have on your network? can you even ping anyone? Also sometimes it just wont bring up the adaptor try doing an ifup eth0 (or whatever your card is called).[/QUOTE]

Don't know how to ping someone......I can't connect to the interface on my router anyway. I can see the adaptor if I go on network settings.

---

### Post by Peter76 on 2006-01-07
[QUOTE=Boopop]Don't know how to ping someone......I can't connect to the interface on my router anyway. I can see the adaptor if I go on network settings.[/QUOTE]
 If you can see your adaptor ( probably eth0 ) in the network settings, at leat it's recognized... Good. In network settings, highlight it and go to properties. Set it to DHCP ( versus ) manual. Now activate it ( Activate button; duh:-) ), or if it was already active, deactivate it and then reactivate it. Does this help?

---

### Post by Boopop on 2006-01-07
[QUOTE=Peter76]If you can see your adaptor ( probably eth0 ) in the network settings, at leat it's recognized... Good. In network settings, highlight it and go to properties. Set it to DHCP ( versus ) manual. Now activate it ( Activate button; duh:-) ), or if it was already active, deactivate it and then reactivate it. Does this help?[/QUOTE]

Tried that already - no luck.

---

### Post by Peter76 on 2006-01-07
[QUOTE=Boopop]Tried that already - no luck.[/QUOTE]

Ok, we'll go for the ping option...
Open a terminal and type: ping -c 5 [www.ubuntu.com](www.ubuntu.com)
and when that has finished: ping -c 5 82.211.81.166
Can you post the output from these commands?
If you know your router's ip, can you try to ping that as well??? ( ping -c 5 routerip ) And post?
and (actually first ): ifconfig eth0

---

### Post by Boopop on 2006-01-07
For the first I get the error message " Unknown host" and for the other to i get something along the lines of " the network address is unreachable "

---

### Post by Peter76 on 2006-01-07
[QUOTE=Boopop]For the first I get the error message " Unknown host" and for the other to i get something along the lines of " the network address is unreachable "[/QUOTE]
Did you do the ifconfig as well? ( Sorry, that should have been the first thing ) So:

ifconfig eth0

Check if you see an ip address in there; or post output

---

### Post by Boopop on 2006-01-07
This is what I got.

[[IMG]http://img411.imageshack.us/img411/338/screenshot8rg.th.png[/IMG]](http://img411.imageshack.us/my.php?image=screenshot8rg.png)

---

### Post by Boopop on 2006-01-07
Bump, i really need help with this >.<

---

### Post by cwaldbieser on 2006-01-07
[QUOTE=Boopop]Bump, i really need help with this >.<[/QUOTE]
Well, from the screenshot, it appears as though you have no IP address.

I am not familiar with what an "ALI Network Port" is-- is it just an ethernet port?  You could try the wired ethernet troubleshooter and post the outputs you get, though it looks like you have already done some of the steps:
[http://ubuntuforums.org/showthread.php?t=87643]("http://ubuntuforums.org/showthread.php?t=87643")
Also, if you could tell us how your computer is physically connected the Internet (direct, router, etc.), that would also help.

---

### Post by Boopop on 2006-01-08
I think [http://www.ocworkbench.com/ocwb/ultimatebb.php?/topic/30/4876.html#000010]("http://www.ocworkbench.com/ocwb/ultimatebb.php?/topic/30/4876.html#000010")
specifies the problem. Any ideas how I can fix it?

---

### Post by hone on 2006-01-08
try this thread: [http://www.ubuntuforums.org/showthread.php?t=83710](http://www.ubuntuforums.org/showthread.php?t=83710).  But, I'm having problems compiling a custom kernel b/c of my lvm2 shares and software raid I guess.  Is there a way to compile a module for the default ubuntu kernels?

EDIT: Actually I found this on the forums, it should get you running until dapper.
[http://www.ubuntuforums.org/showthread.php?t=106117&highlight=asrock](http://www.ubuntuforums.org/showthread.php?t=106117&highlight=asrock)

---

### Post by GameManK on 2006-01-11
[QUOTE=Boopop]When I was installing the breezy 64bit edition of ubuntu, I got an error saying DCHP failed to configure. "Simple" I thought," I'll just do it manually" this is exactly what I did. Now it's installed I can't connect to the network. I've tried configuring DHCP again, and using a different Static IP. I found the subnet mask was incorrect, I fixed that but I still cannot connect to my network. I have a ASRock Dual939 motherboard with an ALI Network port.

Any help would be greatly appreciated :)[/QUOTE]
how did you do that manually during install?
I'm trying to install dapper, where the driver is supposed to be fixed, but can't get through the install.  See my thread here: 
[http://www.ubuntuforums.org/showthread.php?p=649243#post649243](http://www.ubuntuforums.org/showthread.php?p=649243#post649243)
And I even filed a bug report: [http://bugzilla.ubuntu.com/show_bug.cgi?id=22132](http://bugzilla.ubuntu.com/show_bug.cgi?id=22132)

---

