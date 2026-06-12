---
title: "Connecting to Win via Linux"
date: 2006-09-25
forum: Desktop Environments
---

### Post by crossedout on 2006-09-25
Hi folks,
I have family members that are mostly pc-challenged.  So I usually connect via remote assistance through windows to fix/correct/install etc, anything they may need.
My questions are: 
1. Has anyone used linux to connect to a windows xp home user via a similar fashion to that of remote assistance?
2. If so could you point me in the right direction as far as programs/connectivity issues to investigate?

Notes: 
I am not using VMWare or the like atm.
Desktop: Gnome.

-Xout

---

### Post by reacocard on 2006-09-25
take a look at [VNC]("http://www.realvnc.com/")

---

### Post by civic_si on 2006-09-25
you can also use a terminal server client. dapper has one built in its under internet. just make sure that on your windows box that you right click my computer, properties, remote, check the box allow user to connect remotely to this computer. then you should be able to use the term serv client to connect to the windows box. you can use the computer name or the IP address. if you cant find the term serv client you can install krdc and then type rdp:/192.168.x.x the ip address or computer name. hope this helps.

---

### Post by crossedout on 2006-09-26
Thanks for the suggestions.  I'll look into both.

-Xout

---

