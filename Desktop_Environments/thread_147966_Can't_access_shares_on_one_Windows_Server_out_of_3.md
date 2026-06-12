---
title: "Can't access shares on one Windows Server out of 3"
date: 2006-03-21
forum: Desktop Environments
---

### Post by darf681 on 2006-03-21
I couldn't get an answer on the beginners forum, so i am faux pasin' and posting it here too...

I just reinstalled Breezy on my main desktop, and now, after installing samba, and now I am having these two problems:

1) I can access all of my windows shares, except shares on one windows computer.

2) Clicking on Network Servers under Places shows all machines in the network, as well as the icon for WORKGROUP, which the servers are in also... That wasn't there before I did the reinstall..

For the first one, I think I may have a different configuration on that one windows box, or may have inadvertently setup samba with wierd connection properties for that one box. (I remember it asking for passwords and such for a couple of boxes the first time I tried to access them, and it hasn't happened again after I tinkered with samba... is there a place to access specific settings per server in samba, or is there a way to start over with samba without reinstalling Breezy?)

thanks!

---

### Post by dcstar on 2006-03-22
[QUOTE=darf681]
.....or is there a way to start over with samba without reinstalling Breezy?)

thanks![/QUOTE]
Just remove you Samba packages (including configuration) and re-install them in Synaptic.

---

