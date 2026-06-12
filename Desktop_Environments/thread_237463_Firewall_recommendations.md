---
title: "Firewall recommendations?"
date: 2006-08-16
forum: Desktop Environments
---

### Post by Robert Leithe on 2006-08-16
Hi,

Are there any recommendations regarding firewall settings? Any default and/or (officially) public file available for download?

Or would the default simply do?

(I'm running Ubuntu 6.06 LTS)

Sincerely
Robert Leithe

---

### Post by Lunar_Lamp on 2006-08-16
The default is very secure from a firewall perspective.  If you want to change it's settings in any way (usually not required) you can install a graphical front to it called Firestarter.

---

### Post by ardchoille on 2006-08-16
> **Lunar_Lamp said:**
> The default is very secure from a firewall perspective.  If you want to change it's settings in any way (usually not required) you can install a graphical front to it called Firestarter.

Ubuntu ships with an empty iptables configuration, so it is not secure at all. Type "sudo iptables --list" on a new install and you'll se that the firewall isn't even working. One of the first things I do on a new install is install and set up Firestarter.

---

### Post by az on 2006-08-16
> **Robert Leithe said:**
> Hi,

Are there any recommendations regarding firewall settings? Any default and/or (officially) public file available for download?

Or would the default simply do?

(I'm running Ubuntu 6.06 LTS)

Sincerely
Robert Leithe
You do not need a firewall on a desktop system, unless you run software that does stuff behind your back.  If you stick with the software from the ubuntu repositories, you are safe - it would be quite a feat for someone to upload malware into the archive.

By default, no services are listening.  If you install software that listens, you will need to open up your firewall anyway.

---

### Post by hecato on 2006-08-16
I have used one time knoppix, I have liked the firewall look that have the firewall there (I guess other application that isnt firestart)...

You know hte name of that firewall program [for reference, it have 3 displays of "complexity" or something like simple/intermediate/complex look]? (perhaps is only a front end).



Also I ask if there exist a program that integrate with firewall that let me set or see per application bandwitch usage???



By the way, for firestarter, you need to change the edit->configure->interface for being able to use the icon in the panel... because the default behaviour is close the application (tought the firewall will continue is execution I guess).

---

### Post by hecato on 2006-08-16
I have finded a place where there are some screenshoots of the firewall I say (of knoppix)... [http://doc.linucie.net/Admin/KnoppixFirewall](http://doc.linucie.net/Admin/KnoppixFirewall).

Also searching in synaptic, I have liked guarddog and guidedog... what do you think? (when I start guarddog it complain about /etc/rc.firewall not finded?... is that fine for first time use?)

---

### Post by vincentb on 2006-08-16
I also use 'firestarter' which is a very simple GUI for iptable. It is really worth a try

---

