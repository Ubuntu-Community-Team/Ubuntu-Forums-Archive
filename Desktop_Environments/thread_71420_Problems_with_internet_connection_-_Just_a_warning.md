---
title: "Problems with internet connection - Just a warning"
date: 2005-10-03
forum: Desktop Environments
---

### Post by tyttuz on 2005-10-03
Hi, guys,
In last days I had problems with my internet connection...
I tried to see what's happend and I discocover that interface where we configure the network/internet don't save the gateway.
I have to edit /etc/network/interface and add the following line:

gateway (gatewat ip)

maybe this help who add problems with internet connection.

Thanks,
Tito Duarte

---

### Post by smeagol on 2005-10-09
Glad i saw this. I was about to pull my hair out.

So i do a sudo kate /etc/network/interfaces  and i get an error that kate crashed.  I've had Kubuntu 5.10 installed for 10 minutes, I can't get a network connection, and the KDE text editor has crashed already. 

:sigh:

---

### Post by mlomker on 2005-10-09
> So i do a sudo kate /etc/network/interfaces

Kate won't run from sudo.  You can **kdesu kate** if you want.  You can also **sudo kwrite**.

---

