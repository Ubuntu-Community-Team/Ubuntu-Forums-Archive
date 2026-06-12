---
title: "Lock error in apt-get"
date: 2009-06-07
forum: General Help
---

### Post by Nevart on 2009-06-07
Can somebody please advise on what is the problem that I have encountered here, what might be the cause, and how I can fix it?  

Problem described below:

-------------------

user@machine:~$ sudo apt-get install dia
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  amaya-doc linux-headers-2.6.27-7 libwww-ssl0 python-mysqldb
  linux-headers-2.6.27-7-generic amaya-data
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  dia-common dia-libs gsfonts-x11 xutils-dev
The following NEW packages will be installed:
  dia dia-common dia-libs gsfonts-x11 xutils-dev
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory
user@machine:~$ 

-----------------------

---

### Post by jerrrys on 2009-06-07
have you got two sessions of apt-get open?

---

### Post by Soul-Sing on 2009-06-07
does this helps you?: ```
sudo rm /var/cache/apt/archives/lock
```

---

### Post by jerrrys on 2009-06-07
sudo pkill apt

---

### Post by DeMus on 2009-06-07
> **Nevart said:**
> Can somebody please advise on what is the problem that I have encountered here, what might be the cause, and how I can fix it?  

Problem described below:

-------------------

user@machine:~$ sudo apt-get install dia
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  amaya-doc linux-headers-2.6.27-7 libwww-ssl0 python-mysqldb
  linux-headers-2.6.27-7-generic amaya-data
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  dia-common dia-libs gsfonts-x11 xutils-dev
The following NEW packages will be installed:
  dia dia-common dia-libs gsfonts-x11 xutils-dev
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory
user@machine:~$ 

-----------------------

This means that another installation program (Synaptic, apt-get, aptitude) is running as well. There can be only one program active at one time.

---

### Post by Soul-Sing on 2009-06-07
> This means that another installation program (Synaptic, apt-get, aptitude) is running as well. There can be only one program active at one time

yep.
killall apt-get or aptitude maybe?

---

### Post by jerrrys on 2009-06-07
just do a restart?

---

### Post by Nevart on 2009-06-07
Thanks for all the suggestions.  I will try them in the order that seems least harmful and (if I don't forget) will post back what the result is.

---

### Post by Nevart on 2009-06-07
Well it was not what I expected....

The winning suggestion was leoquant with:

"sudo rm /var/cache/apt/archives/lock"

I tried killing apt first, but it was not a case of there being 2 instances open (I guess that if that had been the case, one of the other remedies might have worked).

What seems to have happened is that an earlier session of apt failed to exit gracefully and left its lock file behind.  Then the new instance of apt could not function.

Thank you for the help. :)

---

