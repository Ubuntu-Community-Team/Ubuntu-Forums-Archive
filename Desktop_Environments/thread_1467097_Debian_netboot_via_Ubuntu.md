---
title: "Debian netboot via Ubuntu"
date: 2010-04-30
forum: Desktop Environments
---

### Post by lafrog on 2010-04-30
Hello,
I am trying to boot debian over network using ubuntu desktop.
I've installed tftpd and dhcp3-server and both working well (tried to connect and download file from tftp with success). However it won't boot and load system via ethernet. Can you please tell me what am I doing wrong or is it even possible?

dhcpd.conf
```

default-lease-time 86400;
max-lease-time 604800;

option subnet-mask 255.255.255.0;
option broadcast-address 192.168.1.255;
option routers 192.168.1.254;
option domain-name-servers 192.168.1.1, 192.168.1.2;
option domain-name "whatever.com";

subnet 192.168.51.0 netmask 255.255.255.0 {
       range 192.168.51.64 192.168.51.80;
       filename "pxelinux.0";
       next-server 192.168.51.1;
       option routers 192.168.51.1;
}


```/etc/xinetd.d/tftp 
```

service tftp
{
protocol        = udp
port            = 69
socket_type     = dgram
wait            = yes
user            = nobody
server          = /usr/sbin/in.tftpd
server_args     = /tftpboot
disable         = no
}


```

---

### Post by lafrog on 2010-05-21
bump

---

