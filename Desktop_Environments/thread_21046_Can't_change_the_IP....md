---
title: "Can't change the IP..."
date: 2005-03-20
forum: Desktop Environments
---

### Post by cyu021 on 2005-03-20
Hi folks,

I am running Hoary 5.04 preview, and there is something bothering me.
I enter the following IP address during the installation:
```

address 192.168.0.18
netmask 255.255.255.0
gateway 192.168.0.1
dns-nameservers 192.168.0.1

```
and everything worked fine.

When I moved back to hostel, I changed the /ect/network/interfaces to:
```

 address 10.0.0.39
netmask 255.255.255.0
gateway 10.0.0.1
dns-nameservers 10.0.0.1 

```
which works fine in Windows XP, but it doesn't seem to work at all in my ubuntu.
/etc/init.d/networking restart returned [ok], however, when I ping to the machine name, the IP is not changed at all.
```

ping ubuntu
ubuntu(192.168.0.18) is unreachable or something similar...

```
but I can certianly ping to the network card itself
```

ping 10.0.0.39
...
returning time latency and other info
works ok

```

This process worked smoothly in my previous Debian environment, I suppose ubuntu is merely a remakeof debian.... or is it ?  :?: 
Please point them out to me if there are more works need to be done.  [-o< 


Thanks in advance,
James

---

### Post by orion_114 on 2005-03-20
Try adding an entry in the windows hosts file ....
C:\WINDOWS\system32\drivers\etc\hosts

something like this ......

10.0.0.39          Ubuntu            #My Ubuntu machine

---

### Post by alastair on 2005-03-20
Check the routing and ifconfig as well i.e.

ifconfig -a
route -n

Also check the /etc/hosts file.

---

