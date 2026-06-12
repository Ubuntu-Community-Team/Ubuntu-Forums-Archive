---
title: "Ubuntu Server edition help?"
date: 2009-04-05
forum: General Help
---

### Post by Thyssenkrupp on 2009-04-05
Hey, i recently installed Ubuntu Server edition 8.10 on a VM,and chose LAMP to be included in the installation.

What commands do i use to start the server, edit it, and find out how people in the outside world can connect to it?

Help would be greatly appreciated, 

thanks in advance,

Jak

---

### Post by Peter09 on 2009-04-05
If I remember correctly installing LAMP should have started Apache.
Try

<webserver IP>

in a browser. You may get the Apache default page.

However to go further than this you really need to understand Apache and generate a website.

---

### Post by wineman on 2009-04-05
> **Thyssenkrupp said:**
> 
What commands do i use to start the server, edit it, and find out how people in the outside world can connect to it?


**start the server: **start your VM
**edit it:** VMware( or Qemu or etc)'s options panel
**find out how people on the outside can connect to it:**
ok this is a tricky one. on the actual 810 VM, in command line, ping google.com .if you get a response, that means that you can connect out (and theoretically connect in). Then on your host system (the PC that the VM is on) setup the appropriate firewall, routing etc. rules to get outside clients to connect to the VM **through** your pc. This can be achieved in linux with the iptables command (here's the basic script:
```


#!/bin/sh

echo 1 > /proc/sys/net/ipv4/ip_forward

iptables="/sbin/iptables"

# '--dport 80' is the incoming port, 10.0.0.1:80 is the VM's ip, # eth0 is your external (web) interface.
$ iptables -t nat -A PREROUTING -p tcp --dport 80 -i eth0 -j REDIRECT --to-destination 10.0.0.1:80

```
In windows, you can setup a simple config in your windows firewall to route port 80's traffic to your VM via a NAT connection in the VM.

Hope this helps:p:D

---

### Post by albinootje on 2009-04-05
> **Thyssenkrupp said:**
>  What commands do i use to start the server, edit it, and find out how people in the outside world can connect to it?

All services are probably running, try :
```

ps auxw|grep apache
ps auxw|grep mysql

```
To restart apache and mysql
```

/etc/init.d/apache2 restart
/etc/init.d/mysql restart

```
To edit the apache2 config files, take a look in /etc/apache2/ and do some more reading online about it.

The people in the outside world would browse to the ip address of your VM guest.
The ip address of that depends on how you configured it.
VirtualBox and Qemu use 10.0.2.2 for the host system, and if you've chosen NAT for your guest VM then I think only your host system can reach it by default, not anyone else in your LAN.
If you have chosen "host interface" in the newer VirtualBox (started somewhere with 2.x), then your guest VM probably has gotten an ip address via DHCP.
Just check for the ip address in the Ubuntu VM :
```

ifconfig

```

---

