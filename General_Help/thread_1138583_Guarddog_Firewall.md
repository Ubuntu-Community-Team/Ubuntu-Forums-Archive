---
title: "Guarddog Firewall"
date: 2009-04-26
forum: General Help
---

### Post by MFinkel on 2009-04-26
I am running Ubuntu 8.04.1 LTS Desktop Edition and am trying to fully configure Guarddog firewall. I am getting a message: Since you do not have superuser privileges, Guarddog is running with reduced functionality. Firewall scripts may be Imported/Exported, but the system's firewall settings may not be changed. So what I want to do is at least see what the settings are in case there is in fact something that I want or need to change. Thanks in advance everyone out there in Ubuntu Forum land!

---

### Post by newboyo on 2010-06-04
> **MFinkel said:**
> I am running Ubuntu 8.04.1 LTS Desktop Edition and am trying to fully configure Guarddog firewall. I am getting a message: Since you do not have superuser privileges, Guarddog is running with reduced functionality. Firewall scripts may be Imported/Exported, but the system's firewall settings may not be changed. So what I want to do is at least see what the settings are in case there is in fact something that I want or need to change. Thanks in advance everyone out there in Ubuntu Forum land!
 
 
Hi,
 
Dunno if you've solved the problem, but open a terminal and type gksudo guarddog. That'll get your guarddog working.
 
Alternatively, if you have a launcher on your panel, rightclick for properties and change the command to gksudo guarddog.
 
good luck.

---

