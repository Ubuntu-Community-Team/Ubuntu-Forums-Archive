---
title: "Clonezilla Workstation Hostname"
date: 2008-08-30
forum: Desktop Environments
---

### Post by OfMacandMen on 2008-08-30
Here is the scenario:

* Clonezilla server up and running. 
* 50 new workstations 
* 1 cloned workstation with all the setting, programs and devices installed. 

The ISSUE is when I push the image out to 50 workstation. After the machines reboot I now have 50 workstation with the same HOSTNAME ! 

How can I set the host names to change to wkXXX (XXX being sequential numbers) after being restored?

---

### Post by erwall on 2008-08-31
What OS are the workstations running?

---

### Post by Cato2 on 2008-08-31
Can't give a full answer but in Ubuntu / Debian you simply need to edit the /etc/hostname file on each PC.  

Not sure about how you can automate this, but if you are going to check each workstation boots OK, you could simply edit the hostname using ALT-F2 "gksu gedit /etc/hostname" on each machine.

---

### Post by nsche on 2008-09-04
I am not familiar with clonezilla but I have done what sounds like a similar operation on a bunch (hundreds) of solaris systems using jumpstart.  I assume:
1 - Somewhere there must be a dhcp server that  is handing out ip addresses for these clones. 
2 - Somewhere in "clonezilla" there is a script that runs on the clone that configures it and puts it in running order.
  
In our case we had a script that was run when the clone initially started up which used the ip address given to derive a hostname which was then put in /etc/hostname.  To make this deterministic the dhcp server was giving out specific addresses to each host based on the ethernet address.  Therefore the first task after we determined which system would be which (based on how it was equipped and where it was installed) would be to gather the ethernet addresses and edit them into the file driving the dhcp process and turn it loose.

---

### Post by bigc on 2008-09-11
I'm having the same problem. Have you found a solution?

---

