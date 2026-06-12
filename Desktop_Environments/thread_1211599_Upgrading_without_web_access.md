---
title: "Upgrading without web access"
date: 2009-07-12
forum: Desktop Environments
---

### Post by caryb on 2009-07-12
I have converted my brother to Linux (Kubuntu) because of where he lives he has 2 options for internet 1) dialup 2)none he opted for dialup access. To help him to upgrade I was going to burn the /var/cache/apt/archives folder from a Kubuntu Jaunty 64bit machine (that is the combo he is running) & get him to run dpkg -i *.deb on the dvd I send him.

Is this the best way to do this? Is there a better alternative?

Any help would be appreciated.

Thanks Cary

---

### Post by LepeKaname on 2009-07-12
If you can download the last version CDROM you can try any of these two alternatives:

Insert the CDROM. I think there is an option to upgrade. If not, type:

**Alternative 1) **

```
gksu “sh /cdrom/cdromupgrade”
```

**Alternative 2) **

comment everything in /etc/apt/sources.lst, then...
```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude dist-upgrade
```

There is other alternative which is explained here:
[http://beans.seartipy.com/2006/05/06/update-or-install-applications-on-debianubuntu-without-an-internet-connection/](http://beans.seartipy.com/2006/05/06/update-or-install-applications-on-debianubuntu-without-an-internet-connection/)

But I haven't tried it.

Hope it helps.

---

### Post by caryb on 2009-07-12
Sorry I wasn't doing this for upgrades it's for programs like firefox, thunderbird, acroread & the myriad of codecs as far as I know they don't exist on any install cd.

Cary

---

### Post by robert shearer on 2009-07-12
aptoncd will handle this. It is in the repos and lets you use your machine to produce an archive cd of apps and upgrades you have installed on your machine.

If he has the same machine and O/S then loading the cd will automagically bring up the option to install the contents.

Otherwise check out Keryx...[http://keryxproject.org/](http://keryxproject.org/)
and their tutorial...[http://crashsystems.net/2009/01/keryx-tutorial/](http://crashsystems.net/2009/01/keryx-tutorial/)

---

### Post by caryb on 2009-07-12
Thanks Robert.


Cary

---

### Post by LepeKaname on 2009-07-12
In the link I posted:

[http://beans.seartipy.com/2006/05/06/update-or-install-applications-on-debianubuntu-without-an-internet-connection/](http://beans.seartipy.com/2006/05/06/update-or-install-applications-on-debianubuntu-without-an-internet-connection/)

Its explained how to generate and get all the .deb dependencies of the software you want to update. I could suggest then, to copy those debs in a USB or CDRW rather than a CDROM, as it will be used once.

---

