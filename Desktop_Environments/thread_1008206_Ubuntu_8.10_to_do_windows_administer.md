---
title: "Ubuntu 8.10 to do windows administer"
date: 2008-12-11
forum: Desktop Environments
---

### Post by xacker on 2008-12-11
I am not sure if i post it at the correct place as i tried to google for solution to my concern of running and administer 2003 Active directory from Ubuntu 8.10

I would like some advice if i am able to install the AD in ubuntu or a way to access the AD from ubuntu so that if i am required to administer the AD( add new domain user, Configure the computers from AD) just like i could administer the AD with windowz itself.:confused:

---

### Post by AndyCee on 2008-12-11
Um, no. Active Directory does not run natively on Ubuntu.

Enterprise Likewise may help you out, but if you want to administer AD you can not run it on Ubuntu without using Windows in a virtual machine.

---

### Post by tbg58 on 2008-12-11
Actually you can do this quite simply.  Although the utilities used to administer Active Directory and other Windows functions do not run natively in Ubuntu, you can use Applications, Internet, Terminal Server Client to log into a Windows server with Terminal Services installed.  This could easily be a domain controller - you don't have to have a server with TS installed in application mode; the administrator mode will work nicely.

Now you have the admin console up from your domain controller or other server (where you have conveniently installed adminpak.msi and your other utilities).  Your desktop runs Ubuntu and you can administer your domain and other Windows functions.

The default protocol for the Ubuntu Terminal Server client is RDPv5, and it is part of the default Ubuntu desktop install, so you don't even need to load any new Synaptic packages.

Hope this helps.  Good luck!
Rob

---

