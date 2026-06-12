---
title: "No space"
date: 2009-03-16
forum: General Help
---

### Post by triplemaya on 2009-03-16
I managed to install home on a separate partition, and allowed 10gb for /. Now I'm running out of space and apps don't work. I've searched the forum and googled, and as a result I've run 
sudo apt-get clean
and
 sudo find / -type f -size +75000k
/proc/kcore
find: ‘/proc/19170/task/19170/fd/5’: No such file or directory
find: ‘/proc/19170/task/19170/fdinfo/5’: No such file or directory
find: ‘/proc/19170/fd/5’: No such file or directory
find: ‘/proc/19170/fdinfo/5’: No such file or directory
find: ‘/home/pc/.gvfs’: Permission denied
/var/log/messages
/var/log/messages.0
/var/log/syslog.0
/var/log/kern.log
/var/log/kern.log.0
/var/log/syslog
/sys/devices/pci0000:00/0000:00:00.0/resource0
/sys/devices/pci0000:00/0000:00:00.0/resource0_wc
/sys/devices/pci0000:00/0000:00:02.0/0000:02:00.0/resource1
/sys/devices/pci0000:00/0000:00:02.0/0000:02:00.0/resource1_wc

The messages.0 file endlessly repeats
Mar 15 02:48:42 pc-2 kernel: [ 1765.405994] irq 155, desc: c04a0b00, depth: 1, count: 0, unhandled: 0
Mar 15 02:48:42 pc-2 kernel: [ 1765.406003] ->handle_irq():  c0177250, handle_bad_irq+0x0/0x2a0
Mar 15 02:48:42 pc-2 kernel: [ 1765.406013] ->chip(): c0477180, no_irq_chip+0x0/0x40
Mar 15 02:48:42 pc-2 kernel: [ 1765.406019] ->action(): 00000000
Mar 15 02:48:42 pc-2 kernel: [ 1765.406022]   IRQ_DISABLED set
which is some consequence of my having got my nvidia graphics card working after a long battle.

If I delete it that naturally makes no difference because it just gets recreated. But it is certainly part of the problem
pc@pc-2:~$ ls -l  /var/log/messages.0
-rw-r----- 1 syslog adm 118039546 2009-03-16 10:00 /var/log/messages.0

I assume I should leave anything in /sys/devices alone.

I've uninstalled Eclipse to get enough working space to use firefox, but I assume it will all just clog up again soon.

I really don't understand where all that 10gb has gone! When I run the excellent disk usage analyser usr is 4.0gb and var is 1.3gb and lib is 301mb and opt is 239mb and everything else listed is trivial.

Please could someone advise me what to do next, I'm trying to use this pc for work! Cheers.

---

### Post by taurus on 2009-03-16
It's safe to remove those backup logs in /var/log/*.0 unless you have a reason to keep the around.

---

### Post by triplemaya on 2009-03-16
Thanks, but won't they all just get big again right away?
/var/log/messages.0 does
Is there a simple script I should use to delete them all once an hour or something?

---

### Post by taurus on 2009-03-16
Yes, you can write a script and use crontab to delete those backup log files at specific time and date.

---

### Post by bumanie on 2009-03-16
Can you post the output of > df -h / and > df -h /home

---

### Post by triplemaya on 2009-03-16
pc@pc-2:~$ df -h / 
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             9.2G  6.3G  2.5G  72% /
pc@pc-2:~$ df -h /home 
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              64G   46G   15G  76% /home

(Clearly this says / has 2.5 gb available, but I got error messages when I tried to send or save an email, or run Synaptic to remove some software to make some space!)

---

### Post by taurus on 2009-03-16
What are the outputs of these commands then?

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by triplemaya on 2009-03-16
pc@pc-2:~$ sudo apt-get update
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid Release.gpg
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/main Translation-en_GB               
Get: 1 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg [307B]                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_GB                      
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release.gpg                            
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Translation-en_GB                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/restricted Translation-en_GB         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/universe Translation-en_GB           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/multiverse Translation-en_GB         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates Release.gpg                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/main Translation-en_GB       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/restricted Translation-en_GB 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/universe Translation-en_GB   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_GB 
Get: 2 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]                          
Ign [http://dl.google.com](http://dl.google.com) stable/non-free Translation-en_GB                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid Release                              
Get: 3 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [46.7kB]                         
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Translation-en_GB             
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_GB        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates Release                      
Get: 4 [http://dl.google.com](http://dl.google.com) stable Release [1300B]                             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_GB  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_GB    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_GB  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release                                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/main Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Packages                          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/restricted Packages                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/main Sources                         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/restricted Sources                   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/universe Packages                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/universe Sources                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages                 
Get: 5 [http://dl.google.com](http://dl.google.com) stable/non-free Packages [954B]                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/multiverse Packages                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid/multiverse Sources                   
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Packages                      
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Sources                           
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Sources                       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/main Packages                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/restricted Packages          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/main Sources                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/restricted Sources           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/universe Packages            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Ign [http://apt.boxee.tv](http://apt.boxee.tv) intrepid Release.gpg                                   
Ign [http://apt.boxee.tv](http://apt.boxee.tv) intrepid/main Translation-en_GB                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/universe Sources             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/multiverse Packages          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) intrepid-updates/multiverse Sources           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources  
Ign [http://apt.pearsoncomputing.net](http://apt.pearsoncomputing.net) intrepid Release.gpg             
Ign [http://apt.pearsoncomputing.net](http://apt.pearsoncomputing.net) intrepid/main Translation-en_GB
Ign [http://apt.boxee.tv](http://apt.boxee.tv) intrepid Release       
Ign [http://apt.pearsoncomputing.net](http://apt.pearsoncomputing.net) intrepid Release
Ign [http://apt.pearsoncomputing.net](http://apt.pearsoncomputing.net) intrepid/main Packages
Ign [http://apt.boxee.tv](http://apt.boxee.tv) intrepid/main Packages
Ign [http://apt.pearsoncomputing.net](http://apt.pearsoncomputing.net) intrepid/main Sources
Err [http://apt.pearsoncomputing.net](http://apt.pearsoncomputing.net) intrepid/main Packages
  404 Not Found
Hit [http://apt.boxee.tv](http://apt.boxee.tv) intrepid/main Packages
Err [http://apt.pearsoncomputing.net](http://apt.pearsoncomputing.net) intrepid/main Sources
  404 Not Found
Fetched 2751B in 0s (2936B/s)
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7D2C7A23BF810CD5
W: Failed to fetch [http://apt.pearsoncomputing.net/dists/intrepid/main/binary-i386/Packages.gz](http://apt.pearsoncomputing.net/dists/intrepid/main/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://apt.pearsoncomputing.net/dists/intrepid/main/source/Sources.gz](http://apt.pearsoncomputing.net/dists/intrepid/main/source/Sources.gz)  404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
pc@pc-2:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by taurus on 2009-03-16
Hey, you are running intrepid but how come you have gutsy and hardy repos in your /etc/apt/sources.list?  Mixing repos (with three different releases) can only bring you trouble.

```
cat /etc/apt/sources.list
```

---

### Post by triplemaya on 2009-03-16
Thanks for that. It updated 50 items once I took them out so it obviously needed doing!

The logs are a serious problem, they grow visibly with additions several times a second. The problem is 

Mar 16 20:28:46 pc-2 kernel: [  290.511377] unexpected IRQ trap at vector 9b
Mar 16 20:28:47 pc-2 kernel: [  291.515515] irq 155, desc: c04a0b00, depth: 1, count: 0, unhandled: 0
Mar 16 20:28:47 pc-2 kernel: [  291.515523] ->handle_irq():  c0177250, handle_bad_irq+0x0/0x2a0
Mar 16 20:28:47 pc-2 kernel: [  291.515535] ->chip(): c0477180, no_irq_chip+0x0/0x40
Mar 16 20:28:47 pc-2 kernel: [  291.515541] ->action(): 00000000
Mar 16 20:28:47 pc-2 kernel: [  291.515543]   IRQ_DISABLED set

I'll start a new thread about this problem.

---

