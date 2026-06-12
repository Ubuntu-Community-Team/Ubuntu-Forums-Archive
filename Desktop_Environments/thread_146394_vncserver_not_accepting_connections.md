---
title: "vncserver not accepting connections"
date: 2006-03-18
forum: Desktop Environments
---

### Post by madubuntuer on 2006-03-18
I have a vnc server running on breezy which was installed via apt-get. apt-get install vncserver. The server starts up fine but when I try locally connecting to it it refuses the connection. I have tried via local loopback and it's actual ip address and machine name too. 

 vncviewer 192.168.0.7:1

---

### Post by localzuk on 2006-03-18
Hi, are you sure it is :1 and not :0? Also, do you have a firewall installed?

---

