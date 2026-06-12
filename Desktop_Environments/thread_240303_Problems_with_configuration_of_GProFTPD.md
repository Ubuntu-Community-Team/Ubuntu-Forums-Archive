---
title: "Problems with configuration of GProFTPD"
date: 2006-08-20
forum: Desktop Environments
---

### Post by Mark_V on 2006-08-20
I've installed GProFTPD through the add/remove software gui without a problem.

Now when i startup GProFTPD i get the question if i want to overwrite the proftpd.conf with the default configuration, but when i press yes it return the message:

Can't write the new proftpd.conf here:
/etc/proftpd.conf
Run GPRoFTPD as root

When i tried to change the file through the terminal screen ( gedit /etc/proftpd.conf it stil gives this message.

When i press No it returns the message:
Cant open shells for writing /bin/false here:
/etc/shells

How can i start this program up as root, so i can configure it proberly??

Please in newbee step by step language...


:neutral:

---

### Post by em3raldxiii on 2006-08-21
Open up a terminal, as you did, but change your command to include **sudo** first, so you have **sudo gproftpd**.
 
That should work ... if not, let me know and I will install it at home and muck about so I can see what's going on :D

---

