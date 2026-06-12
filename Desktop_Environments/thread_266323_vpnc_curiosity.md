---
title: "vpnc curiosity"
date: 2006-09-27
forum: Desktop Environments
---

### Post by moaxey on 2006-09-27
I was stumped for three months trying to get kvpn to work, found a great simple way to use vpnc in terminal here in forums somewhere... setting up a somple configuration file.

Only it wont work on my main laptop machinem, the one i really need to be able to vpn from.

Other machines work, so i must have configuration correct, but main laptop always says:
```
vpnc: binding to port 500: Address already in use

```

i do it with sudo, su root, gksu but it never works.

does that mean i have some other flaky piece of software binding to port 500?

how can i find out what it is?

do i have to remove every package one-by-one and see what works?

this is really silly and frustrating, help appreciated!

---

### Post by moaxey on 2006-09-27
brainwave time, straight after i post...

i can start in recovery mode, 
start vpn connection, 
logout and 
log in through gui as myself
and connect successfully

but thats still a bit messy!

---

### Post by Thav on 2006-12-05
The only times I've gotten that error with vpnc, I just do vpnc-disconnect and then connect as normal, in fact I have vpnc-disconnect at the beginning of my vpn script just for that reason. Hope this helped any.

---

### Post by marianom on 2007-02-20
Other option to skip port in use error, in case everything else fails, is to use --local-port=0 as additional parameter when you're starting it.

```
mariano@mishima:~$ sudo vpnc --local-port=0
```

The option = 0 will make vpnc pick a random port, hopefully available.

---

### Post by Michl on 2008-01-10
> **Thav said:**
> The only times I've gotten that error with vpnc, I just do vpnc-disconnect and then connect as normal, in fact I have vpnc-disconnect at the beginning of my vpn script just for that reason. Hope this helped any.

Would you be willing share your script?  I can get vpnc to work if I use
sudo vpnc
and enter the info command line by command line.

but nothing else works for me.

Thanks,
Michael
Michael

---

### Post by tamasgal on 2008-01-23
If vpnc is not working, try this:
vpnc --natt-mode cisco-udp your_config.conf

---

