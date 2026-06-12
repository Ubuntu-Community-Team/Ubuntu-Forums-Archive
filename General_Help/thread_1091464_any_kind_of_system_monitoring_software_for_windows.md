---
title: "any kind of system monitoring software for windows/linux?"
date: 2009-03-09
forum: General Help
---

### Post by pixeldotz on 2009-03-09
a little backinfo:

at work we have a linux server running a vm ESX with like 5 VMs for various virtualized servers we have.

is there any software that runs in linux/ubuntu (im thinking about monitoring my ubuntu box at home the same way from work) that i could see system status in windows?

so basically; if our server or my box goes down; i could tell in XP the moment it went down?

so far all i could find is conky which is (as far as i could tell) local system monitoring.

thanks.

---

### Post by kanikilu on 2009-03-09
See if one of these solutions fits your needs:

[http://ubuntuforums.org/showthread.php?t=953207](http://ubuntuforums.org/showthread.php?t=953207)

(links are in the 2nd post)

I'm considering Nagios for my servers, but it might be overkill to monitor 1 server, as in your case.

---

### Post by pixeldotz on 2009-03-09
thanks for the reply! i'm installing ZABBIX right now through synaptic pkg manager. depending the setup it's a toss up between this and NAGIOS.

thanks for the reply again.

---

### Post by jonobr on 2009-03-09
You could try using SNMP with a freeware application like opmanager and 
cacti...

[here]("http://www.debuntu.org/how-to-monitor-your-servers-with-snmp-and-cacti") is a link using cacti as an example,
also, you can do it via command line also using snmpwalk

Hope this was useful

---

### Post by jjgomera on 2009-03-10
> **pixeldotz said:**
> a little backinfo:

at work we have a linux server running a vm ESX with like 5 VMs for various virtualized servers we have.

is there any software that runs in linux/ubuntu (im thinking about monitoring my ubuntu box at home the same way from work) that i could see system status in windows?

so basically; if our server or my box goes down; i could tell in XP the moment it went down?

so far all i could find is conky which is (as far as i could tell) local system monitoring.

thanks.
 conky can do it, instaling conky in server and using ssh to comunicate, but only not windows :D

Here you have a example: [http://ubuntuforums.org/showpost.php?p=6215178&postcount=4591](http://ubuntuforums.org/showpost.php?p=6215178&postcount=4591)

red is server info, green the normal local info

---

