---
title: "help!"
date: 2009-06-06
forum: General Help
---

### Post by batsmj65 on 2009-06-06
Have a new Dell notebook with ubuntu 8.04. Bought to take on travels to check e-mail, book flights etc. Clicked to install updates,but  got following msg;
 
ERROR dpkg was interupted you must manually run dpkg configure-a to correct
 
E;_cache open failed please report.
 
Now i have following;
 
Failed to check for installed and available applications'
this is a major failure of your software management system. Please check for broken packages with synaptic, check the file prmissions and correctness of the file '/etc/apt/sources.list' and reload the software information with; 'sudo apt-get update' and 'sudo apt-get install-f'.
 
Any help appreciated, thanks.

---

### Post by madmaxou on 2009-06-06
Have you typed in the commands??

---

### Post by lindsay7 on 2009-06-06
type the following in the terminal

sudo dpkg --configure -a 

then go to Synapic package manager and click edit, then choose fix broken packages.  After that type in the terminal 

Then make sure your system is up to date:

sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade

---

