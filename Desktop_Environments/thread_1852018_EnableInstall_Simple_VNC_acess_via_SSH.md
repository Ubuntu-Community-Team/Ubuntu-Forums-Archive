---
title: "Enable/Install Simple VNC acess via SSH?"
date: 2011-09-29
forum: Desktop Environments
---

### Post by g{Lv$qjC8w2 on 2011-09-29
Hello, 

i just bought a ubuntu vps and cannot access via vnc, i tried service vncserver start and it says cannot find a service called that? Im stuck, any simple tutorials?

Cheers

george
i have ssh acess


edit, heres what it throws at me

Last login: Thu Sep 29 17:07:05 2011 from host-92-6-203-178.as43234.net
Starting PowerConsole v1.1 <> (c)2010 soluslabs ltd.
please wait...
successfully logged in.
entered into CT 12774
root@skydive:/# service vncserver start
vncserver: unrecognized service
root@skydive:/#

---

### Post by pavi_elex on 2011-11-04
This the way of accessing other system of a LAN. but not exact like "remote desktop" function of windows. There, you can see mouse activity on other system done by you.
Here, the way is different but functionality is same.

use sftp for this.
install this on your system as well as on system which you want to access.
sudo apt-get install openssh-server openssh-client

now places--> connect to server
select service type ssh, type ip address of system (which you want to access) in the field server.
click on connect.
fill username password of that system.
Now you can access that system.

---

