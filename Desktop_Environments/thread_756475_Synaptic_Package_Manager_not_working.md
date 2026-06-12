---
title: "Synaptic Package Manager not working"
date: 2008-04-15
forum: Desktop Environments
---

### Post by tambidude on 2008-04-15
I screwed up in installing a product and now apt-get, dpkg is dying on me with
the message 
'E:The package db2exc needs to be reinstalled, but I can't find an archive for it.'

I googled for it and saw this

"http://ubuntuforums.org/archive/index.php/t-398709.html"

I tried every option but could not get it work. 

what options are left for me now?

---

### Post by kerry_s on 2008-04-15
did you try->
sudo apt-get -f install
or
sudo apt-get remove --purge db2exc

---

### Post by tambidude on 2008-04-16
ravi@ravi-laptop:~$ sudo apt-get remove --purge db2exc
[sudo] password for ravi:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package db2exc needs to be reinstalled, but I can't find an archive for it.
 


ravi@ravi-laptop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree        
Reading state information... Done
E: The package db2exc needs to be reinstalled, but I can't find an archive for it.

---

### Post by tambidude on 2008-04-16
Ok found the solution finally.

I edited the file /var/lib/dpkg/status and removed the lines about package
db2exc. This got synaptic working and then I resinstalled it.

thanks all for their time.

---

