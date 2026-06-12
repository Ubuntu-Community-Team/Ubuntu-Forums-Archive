---
title: "The need of Firewall&amp;Antivirus"
date: 2006-02-02
forum: Desktop Environments
---

### Post by ipp3l1 on 2006-02-02
Is firewall neccesary while using ubuntu? What about Antivirus software? Cuz I dont have either of them and no problems has appeared yet :mrgreen: 

Is Ubuntu safe enough without fw/av ? thanks

\\:D/

---

### Post by Jonne on 2006-02-02
There is a firewall in Ubuntu (or you can install it, I'm not sure), It's called iptables. I don't know if there are any good front-ends for it, but chances are you already have iptables running.

Antivirus won't do you a lot of good, as there's only a limited number of Linux viruses. There is a free antivirus called ClamAv, but that's mainly used to scan e-mail on mail servers.

---

### Post by Klaidas on 2006-02-02
The front-end for iptables could be *Firestarter* (Search in synaptic), for antivirus - you don't really need it, unless there are other operating systems on the computer. 

Some useful threads:
[http://ubuntuforums.org/showthread.php?t=123230](http://ubuntuforums.org/showthread.php?t=123230)
[http://www.ubuntuforums.org/showthread.php?t=88357&highlight=install+f-prot](http://www.ubuntuforums.org/showthread.php?t=88357&highlight=install+f-prot)
[http://www.ubuntuforums.org/showthread.php?t=104001&highlight=install+clamav](http://www.ubuntuforums.org/showthread.php?t=104001&highlight=install+clamav)

---

### Post by Jonne on 2006-02-02
just to add to my post:
If you keep your install updated, and don't run any services that might be vulnerable (ssh with a weak password, anonymous ftp server with upload privs, apache+php+vulnerable php scripts on a priviledged account, ...), you probably won't need any of those.

Those situations I mentioned above are not part of a normal setup, so if you didn't enable those situations, you're not vulnerable. Ubuntu ships in a pretty safe default configuration, so any security holes you open up yourself are ultimately your own fault.

---

### Post by ipp3l1 on 2006-02-02
[QUOTE=Klaidas]The front-end for iptables could be *Firestarter* (Search in synaptic), for antivirus - you don't really need it, unless there are other operating systems on the computer. [/QUOTE]

So, does that mean, that if I install WindowsXP as a dual-boot, I will have to use firewall software on ubuntu too? :eek:

---

### Post by madmetal on 2006-02-02
yes, install firestarter (firewall) and install clam antivirus if the computer is connected  
 with windows pc (lan) or has shared files with windows at the same system, in order to protect other users.

---

### Post by Jonne on 2006-02-02
It's not as critical as when you're using Windows, as Windows has many more vulnerable services running by default. If you have no services listening to outside connections (which is the way it's set up by default, i think), you don't really need one.

---

### Post by WinCtrlAltDel on 2006-02-02
Firehol is a good Firewall also.

---

### Post by Thulemanden on 2006-02-03
[quote=ipp3l1]Is firewall neccesary while using ubuntu? What about Antivirus software? Cuz I dont have either of them and no problems has appeared yet :mrgreen: 

Is Ubuntu safe enough without fw/av ? thanks

\\:D/[/quote]

Firestarter doesn't have the great gui as Guarddog has. Firestarter only allows you to stop and start a non-configurable firewall. Guarddog lets you select the protocols via easily understood menues and icons.

You'll want a firewall but an anti-virus isn't critical yet.

---

