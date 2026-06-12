---
title: "ssh connection port 22/webmin port 10000"
date: 2006-02-17
forum: Desktop Environments
---

### Post by Hotchilli on 2006-02-17
I can connect to ssh on port 22 from my box and also to webmin web interface on port 10000/ but not from outside

here is what netstat says

Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address Foreign Address State
tcp 0 0 localhost:10000 localhost:32822 TIME_WAIT
tcp 0 0 localhost:10000 localhost:32827 ESTABLISHED
tcp 0 0 localhost:10000 localhost:32826 ESTABLISHED
tcp 0 0 localhost:ssh localhost:32821 ESTABLISHED
tcp 0 0 localhost:32827 localhost:10000 ESTABLISHED
tcp 0 0 localhost:32826 localhost:10000 ESTABLISHED
tcp 0 0 localhost:32821 localhost:ssh ESTABLISHED
Active UNIX domain sockets (w/o servers)

when I type

netstat -at | grep 22

i am just returned to the comand prompt

when I tpye netstat -at | grep 10000 i get

tcp 0 0 *:10000 *:* LISTEN


any ideas how to establish a connection from outside my box

here is what netstat -tln  lokks like
root@4096:~# netstat -tln
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 0.0.0.0:20000           0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:8002            0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:70              0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:11372           0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:10000           0.0.0.0:*               LISTEN
tcp        0      0 192.168.1.64:53         0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:119             0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN


hc :???: :???:

---

### Post by jinacio on 2006-02-17
if you are connected to internet behind a router, you need to set up the router to forward those ports (tcp 22 and 10000) to the local ip address.

also, if you are using dhcp on your ethernet card you should probaly use a static ip address.

check out [http://www.portforward.com](http://www.portforward.com)

---

### Post by Hotchilli on 2006-02-18
thanks for your post

I am not set up behind a router I do have dhcp And the router has a static ip
address.

thanks for url

hc:)

---

