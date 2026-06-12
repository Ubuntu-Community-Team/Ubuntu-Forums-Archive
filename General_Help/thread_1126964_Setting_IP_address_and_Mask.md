---
title: "Setting IP address and Mask"
date: 2009-04-15
forum: General Help
---

### Post by rick astley on 2009-04-15
How do i set the ip address via terminal.

i know how to view the info via: 
```
ifconfig eth0
```


what is the command for setting the ip thanks all!



rick.

---

### Post by spiderbatdad on 2009-04-16
this gets set in the file /etc/network/interfaces
for example to give your pc a static ip address
```
gksu gedit /etc/network/interfaces
```

Add something like this to the file...to suit your network
```
iface eth0 inet static
address 192.168.15.105
netmask 255.255.255.0
network 192.168.15.1
broadcast 192.168.15.255
gateway 192.168.15.1

```run commands```
sudo ifdown eth0
sudo ifup eth0
```

See here for more: [http://www.youtube.com/watch?v=oHg5SJYRHA0](http://www.youtube.com/watch?v=oHg5SJYRHA0)

---

