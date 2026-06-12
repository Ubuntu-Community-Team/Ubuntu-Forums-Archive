---
title: "PC wants the user to be root"
date: 2005-04-21
forum: Desktop Environments
---

### Post by sonny on 2005-04-21
I 'm having some problems with Kubuntu, whenever I start my PC and get to the splash screen it complains about not having write acces to /home/.ICEauthority and can't load the X session. I do a console login and type:

sudo chmod 775 .ICEauthority                and then
sudo startx

If I reboot the PC, again it complains about the ICEauthority write permissions, do the console loging and the stuff above. It loads as user.. but if I had left some programs opened the last session (usually kopete, superkaramba, bittornado), it asks for root permission... and open those programs as root... 

How can I fix this problem???...

Some background: It happened while I was editing my Xorg.conf file to enable the twinview (got that working); some where between the tests the write permissions got ereased or messed up... but as I've said, everytime I reboot the permissions are erease...

well... I'll appreciate any comments on that.

---

### Post by gunnyman on 2005-04-21
I had this happen to me and chown -R myusername:myusername /home/myusername  fixed it for me.

---

### Post by sonny on 2005-04-21
Thanks gunnyman it really help me... now everything is back to normal.

---

### Post by gunnyman on 2005-04-22
good :)

---

