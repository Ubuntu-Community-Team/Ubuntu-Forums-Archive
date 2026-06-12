---
title: "Cannot connect with XDMCP"
date: 2008-11-07
forum: Desktop Environments
---

### Post by angel6700 on 2008-11-07
Hello,

I recently installed kubuntu 8.10 and I find it really nice and usable. The only small problem is that I cannot configure a wired network card with knetworkmanager because I need static ip, but I work just fine with:
ifconfig eth0 192.168.2.1 netmask 255.255.255.0 up

I have to computers PC1 and PC2.

PC1 has one wireless card (ath0) which connect it to internet and another card (eth0) which I use to connect to another linux box PC2 with a crossover ethernet cable. (This one has static IP as explained above).

I used always XDMCP to connect from PC2 to my kubuntu on PC1 and works just fine. But some days ago, I installed kubuntu 8.10 and XDMCP does not work anymore.

I edited as it was before (except for kde3 instead of kde4)
/etc/kde4/kdm/kdmrc

...
[XDMCP]

enable=True
...


and 
/etc/kde4/kdm/Xaccess

*


I can see the machine in the chooser of PC2 but if I try to connect to it I just get a black screen with a mouse pointer with a X sign shape.

Any clue or advise??

Thanks a lot in advance.

---

### Post by angel6700 on 2008-11-09
Please, any advise?

---

### Post by leofiska on 2008-11-09
same problem with ubuntu/Gnome 8.10. :(

Cannot connect using remote login or Xnest, just a black window with the X cursor.

---

### Post by bford16 on 2008-11-14
I had the same problem (Xubuntu to Ubuntu, both 8.10).  On both machines, XDMCP was enabled, but still no connection.  Then just for fun, I decided to check if I had enabled the firewall.```
sudo ufw status
```Nope.  The firewall wasn't running.  So I decided to run Firestarter.  After installing with```
sudo apt-get install firestarter
```I set a policy to enable incoming connections on port 177.

Now XDMCP works again, although it seems a bit slower.  I still cannot start a nested X-session with gdmflexiserver.```
gdmflixiserver -n
```returns "Cannot start new display.  Perhaps the X server is not configured correctly," or something similar.
UPDATE: solved gdmflexiserver problem by installing Xnest,  Apparently it is not installed by default. (sudo apt-get install xnest)

---

