---
title: "Getting ubuntu networking"
date: 2006-03-14
forum: Desktop Environments
---

### Post by SVwanders on 2006-03-14
I installed ubuntu a few days ago in a 333mhz machine and was fairly quickly able to have it see my D-link router and DSL modem . . . I guess. Anyway, I am able to get online without any problems. However I can't access my machine running XP and my printer. I realize, or at least believe, that the latter is another issue all together but I would like to learn how to network log into my network.

This is all very new to me but I am interested in learning.

Tim

---

### Post by jalm111 on 2006-03-14
Make sure your Samba is configured correctly. Also I believe Samba needs to know if you are on a workgroup or a domain and what the workgroup is. Similar ot setting up a windows LAN. All the pcs that see each other should be on the same workgroup.

---

### Post by skirkpatrick on 2006-03-14
Use **sudo gedit /etc/samba/smb.conf** from a terminal window (Applications->Accessories->Terminal) and look for the line with "workgroup" in it and change it to be the same as your XP machine.  Then you can either reboot your machine or go to System->Administration->Services and uncheck then check the Samba service to restart it.

---

