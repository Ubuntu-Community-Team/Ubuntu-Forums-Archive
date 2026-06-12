---
title: "Server Apps, on desktop Ubuntu"
date: 2008-12-17
forum: General Help
---

### Post by Tom_T on 2008-12-17
Hi
I'm new to Linux.. be kind :)


I've installed the following on to Ubuntu 8.10 following these guides:

tftpd
[http://www.davidsudjiman.info/2006/03/27/installing-and-setting-tftpd-in-ubuntu/](http://www.davidsudjiman.info/2006/03/27/installing-and-setting-tftpd-in-ubuntu/)

Dhcp3-Server
[http://www.linuxtopia.org/online_books/system_administration_books/ubuntu_starter_guide/ch07s04.html](http://www.linuxtopia.org/online_books/system_administration_books/ubuntu_starter_guide/ch07s04.html)

Proftpd
[http://www.linuxtopia.org/online_books/linux_beginner_books/unofficial_ubuntu_starter_guide/index_204.html](http://www.linuxtopia.org/online_books/linux_beginner_books/unofficial_ubuntu_starter_guide/index_204.html)

All this seems to be working as I would expect..

What I would like to do is have these disabled by default and then only enable them when needed.  Is that possible ??  How ??

Is it possible to create desktop shortcuts that could be used to start and stop these applications ??

Thanks

---

### Post by binbash on 2008-12-17
yes you can start and stop via shortcut (just make a shortcut to /etc/init.d/proftpd start for example)

for making services stop or start at startup : 

System > Administration > Services

---

### Post by Tom_T on 2008-12-18
Thanks for the reply.

Do you know how I can disable them by default and only start / stop them when I need to ??

Regards

---

### Post by Tom_T on 2008-12-18
Anyone any ideas on this ??
Thanks :)

---

### Post by kanikilu on 2008-12-18
It might be overkill for what you want to do, but I use webmin (sudo apt-get install webmin) to do these system administration type things.

---

### Post by clw3388 on 2008-12-18
wouldnt u have to edit the rc.d to ensure it dont start on boot??

---

### Post by Tom_T on 2008-12-19
Thanks.

I've sorted teh stop, start and restart commands..  Just need to stop them starting at boot.

---

### Post by hyper_ch on 2008-12-19
in /etc/init.d you will find all the service that are started/stopped during boot and shutdown. Find the according application names you need for the services you want to deactivate. Then run for each:

```

sudo update-rc.d -f SCRIPTNAME remove

```

---

### Post by Tom_T on 2008-12-19
Thanks.

What about apps started via xinetd ??

---

### Post by hyper_ch on 2008-12-19
are there still any?

---

### Post by Tom_T on 2008-12-19
tftpd is using it !!
[http://www.davidsudjiman.info/2006/03/27/installing-and-setting-tftpd-in-ubuntu/](http://www.davidsudjiman.info/2006/03/27/installing-and-setting-tftpd-in-ubuntu/)

---

