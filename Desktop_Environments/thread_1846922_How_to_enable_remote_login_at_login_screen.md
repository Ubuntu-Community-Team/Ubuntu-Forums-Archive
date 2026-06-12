---
title: "How to enable remote login at login screen?"
date: 2011-09-19
forum: Desktop Environments
---

### Post by Higgs1 on 2011-09-19
Hello,
My goal is to go to the login screen and log in to an account on another computer as if I was logging in to a local account. XDMCP sounds good, but how do I enable the remote login selection at the login screen?
Many of the guides I found basically followed this procedure: [http://www.idevelopment.info/data/Unix/Linux/LINUX_ConfiguringXDMCPRedHatLinux.shtml#Granting%20Remote%20Access%20to%20the%20Login%20Manager]("http://www.idevelopment.info/data/Unix/Linux/LINUX_ConfiguringXDMCPRedHatLinux.shtml#Granting%20Remote%20Access%20to%20the%20Login%20Manager")
I'm using Ubuntu 11.04 as the computer I want to sit at.

---

### Post by Higgs1 on 2011-09-21
Bump

---

### Post by mister_p_1998 on 2011-09-22
I just make the station autologin, then go in via putty.

---

### Post by pavi_elex on 2011-11-04
use sftp for this.
install this on your system as well as on system which you want to access.
sudo apt-get install openssh-server openssh-client

now places--> connect to server
select service type ssh, type ip address of system (which you want to access) in the field server.
click on connect.
fill username password of that system.
Now you can access that system.

---

