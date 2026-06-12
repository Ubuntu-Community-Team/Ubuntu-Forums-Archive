---
title: "Firewall inUbuntu?!"
date: 2005-12-11
forum: General Help
---

### Post by Thunk on 2005-12-11
So I wasn't going to use a firewall after installing Ubuntu on my machine because it's Linux and it's Ubuntu and that's part of why I switched to it in the first place, but then I read a little about Firestarter and a few threads about firewalls in Ubuntu in general and now I don't know what I should do.

What do you think? Is a firewall necesary in Ubuntu or should the lack of open ports as a default be enough? And what about Firestarter, is it doing the job?

---

### Post by psusi on 2005-12-11
In a typical ubuntu install, it is completely unnessesary.  

If you still want to play with it because you like tweeking things though, go for it.

---

### Post by rykel on 2005-12-11
[QUOTE=psusi]In a typical ubuntu install, it is completely unnessesary. [/QUOTE]

hiii, how do you uninstall the firewall (i believe it's either an ipv6 or firestarter service tat runs in the background) in a stock ubuntu breezy install?

i want to do tis becoz my bittornado seems to hang forever...

thanks!!

---

### Post by psusi on 2005-12-11
[QUOTE=rykel]hiii, how do you uninstall the firewall (i believe it's either an ipv6 or firestarter service tat runs in the background) in a stock ubuntu breezy install?

i want to do tis becoz my bittornado seems to hang forever...

thanks!![/QUOTE]

There isn't one by default, which is why the original poster was asking if he should install one.

---

### Post by Gray. on 2005-12-11
Maybe you should check your router to see if it's forwarding ports 6881-6889. That solved it for me.

---

### Post by rykel on 2005-12-13
[QUOTE=psusi]There isn't one by default, which is why the original poster was asking if he should install one.[/QUOTE]

hi, i believe tat ubuntu breezy is installed with firestarter as a background service, because when i shut down the system, i see "shutting down firestarter" as one of the shutdown lines.

as for iptables, i have uninstalled it from synaptic. is this a good idea?

not sure if i actually still have any firewall on... how can i check?

---

### Post by matthewv on 2005-12-13
If you install firestarter, it runs as a service. Don't know if it does if it isn't installed. I think every linux system has the routing tables (whatever that is) but firewalls like firestarter are extra. I've got firestarter installed, but only because I like tweaking things... otherwise I wouldn't have installed it.

---

### Post by rykel on 2005-12-13
[QUOTE=matthewv]If you install firestarter, it runs as a service. Don't know if it does if it isn't installed. I think every linux system has the routing tables (whatever that is) but firewalls like firestarter are extra. I've got firestarter installed, but only because I like tweaking things... otherwise I wouldn't have installed it.[/QUOTE]

well, tat is correct. the only thing is, i did not install firestarter, but it was being "shut down" whenever i shut down ubuntu breezy. do a stock installation and take a close look.

a lot of thanks for ur message!!   :)

---

### Post by kosmic on 2005-12-13
just a sugestion never, ever remove iptables

---

### Post by rykel on 2005-12-13
[QUOTE=kosmic]just a sugestion never, ever remove iptables[/QUOTE]

oops! i have been surfing the net etc. without iptables... but anyway, i have reinstalled it in synaptic. does it need to be reconfigured?

btw, if iptables is installed, will it interfere with bittornado as a firewall?

---

