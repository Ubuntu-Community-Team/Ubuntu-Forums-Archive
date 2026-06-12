---
title: "Unexpected remote arg @root centos 7"
date: 2016-05-20
forum: Fedora/RedHat and derivatives
---

### Post by Doyet on 2016-05-20
can someone help me..
i already create a SSH passwordless at root but when i use rsync via SSH it appears like this:
[HR][/HR][root@localhost Desktop]# su -
Last login: Fri May 20 15:58:22 PHT 2016 on pts/3
[root@localhost ~]# rsync -avzh -e --progress ssh
root@192.168.12.3:/home/drives/shares/utils/ /samba/utilities/
Unexpected remote arg: root@192.168.12.3:/home/drives/shares/utils/
rsync error: syntax or usage error (code 1) at main.c(1214) [sender=3.0.9]
[root@localhost ~]#
[HR][/HR]i should install passwordless SHH on the source server or something to do in firewall? can someone explain me why.. Newbie here.. so be gentle on me.. :)
thanks..

---

### Post by ajgreeny on 2016-05-20
*Thread moved to **Fedora/RedHat and derivatives**.*

I am not sure whether or not this is a server query from what you have asked.
If it is please say so.

---

### Post by Doyet on 2016-05-20
im a newbie admin .. and i really dont know what i'm doing, where to properly post a thread ... sorry for the mistake... :D

---

