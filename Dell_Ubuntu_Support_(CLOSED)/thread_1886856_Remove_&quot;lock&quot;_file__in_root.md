---
title: "Remove &quot;lock&quot; file  in root"
date: 2011-11-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by capon on 2011-11-25
/var/lib/apt/lists/lock

Ubuntu newbie wants to remove the lock file in the above statement.
Tried (to no avail) going through the Home folder and drilling down in the tree view but don't 
know how to become "root" from there.
What is the proper procedure using the apt command line .
I do understand the "sudo su / password procedure but don't know anything from that point.
am attempting the 1st update/upgrade after installation.
Have did an apt-get update/upgrade/autoclean command but it gives me a "lock' message.

Appreciate any and all help.
Regards:(

---

### Post by matt_symes on 2011-11-25
Hi

> **capon said:**
> /var/lib/apt/lists/lock

Ubuntu newbie wants to remove the lock file in the above statement.
Tried (to no avail) going through the Home folder and drilling down in the tree view but don't 
know how to become "root" from there.
What is the proper procedure using the apt command line .
I do understand the "sudo su / password procedure but don't know anything from that point.
am attempting the 1st update/upgrade after installation.
Have did an apt-get update/upgrade/autoclean command but it gives me a "lock' message.

Appreciate any and all help.
Regards:(

Can i ask why you want to delete it ?

Kind regards

---

### Post by capon on 2011-11-25
In times past I have used that procedure (not on ubuntu) but if there is another way to unlock the "lists" file, please say on.

---

### Post by matt_symes on 2011-11-25
Hi

Let's try to see what is locking it. Open a terminal and type

```
sudo lsof /var/lib/dpkg/lock
```

Post back results.

Kind regards

---

### Post by capon on 2011-11-25
john@Dell-745:~$ sudo lsof /var/lib/dpkg/lock
[sudo] password for john: 
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/john/.gvfs
      Output information may be incomplete.
john@Dell-745:~$ ^C
john@Dell-745:~$

---

### Post by matt_symes on 2011-11-25
Hi

> **capon said:**
> john@Dell-745:~$ sudo lsof /var/lib/dpkg/lock
[sudo] password for john: 
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/john/.gvfs
      Output information may be incomplete.
john@Dell-745:~$ ^C
john@Dell-745:~$

That did not help much. Copy and paste this command into a terminal

```
ps aux | grep -E "apt|synaptic|software-center|update-manager|dpkg|aptitude"
```

Post back results. If it returns nothing we will delete the lock file.

Kind regards

---

### Post by capon on 2011-11-25
john@Dell-745:~$ ps aux | grep -E "apt|synaptic|software-center|update-manager|dpkg|aptitude"
john      2431  0.0  0.0   4444   800 pts/0    S+   16:19   0:00 grep --color=auto -E apt|synaptic|software-center|update-manager|dpkg|aptitude
john@Dell-745:~$

---

### Post by matt_symes on 2011-11-25
Hi

To delete the lock file

```
sudo rm /var/lib/dpkg/lock
```

Enter your password. It will not be echoed to the screen.

What exactly are you trying to do ? It looks like nothing has a lock on it.

Kind regards

---

### Post by capon on 2011-11-25
Honestly Mr.Symes, I am stumbling. For several days I have attemped to finalize this intallation of 11.10 by updating/upgrading something like 104 files. Today (on a whim) I also added apt-get clean and auto clean and received this lock notice. There is a lock file and my thoughts are 'what will it hurt to remove it?'. 
Anyways, I just redid the "sudo rm /var/lib/dpkg/lock" and the lock file remains in the lists file.
Am out of patience with this Dell . 
Regards

---

### Post by capon on 2011-11-25
And I should also add for clarification that this machine will not downloadl any programs from the Ubuntu software downloads. it gives me a "check network connection" . I have been using this Dell on the internet from the get go.

Regards

---

### Post by dinusuresh on 2011-11-25
> **capon said:**
> And I should also add for clarification that this machine will not downloadl any programs from the Ubuntu software downloads. it gives me a "check network connection" . I have been using this Dell on the internet from the get go.

Regards

Hi capon, I think i can help you with the "check network connection". as usual here are a few questions from me for the start,

 - are you able to browse to internet using your browser?
 - do you have a proxy?
         if so, have you specified it system wide?
 - do you use wvdial to connect to the internet or "the network manager"?

---

### Post by capon on 2011-11-26
Thank you for asking: Started this thread yesterday while surfing the web using the dell machine(Dell Optiplex 745 3.4ghz dual core processor,2gig mem). Have switched to my old favorite tower (Pent 4, 2.8ghz)
The connection is straight forward: hard wired to an dish on the roof, to a line of sight connection 10 miles to the east. No wireless, no router, no proxy, network manager gives the addresses etc. In short: the dell 745 will surf but cannot connect with Ubuntu Software Center (gives a 'check connection' msg), 
Installed  Ubuntu 11.10 using a cd purchased from on-Disk. No upgrade from 11.04. Also used that cd to install on this machine.
Regards

---

### Post by matt_symes on 2011-11-26
Hi

For for the delay. Timezones i expect !!

Open a terminal and type

```
sudo apt-get update
```Post the results back here.

Kind regards

---

### Post by capon on 2011-11-26
hn@Dell-745:~$ sudo apt-get update
[sudo] password for john: 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric InRelease                          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security InRelease                      
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg                               
  Connection failed
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates InRelease                     
Err [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release.gpg                    
  Connection failed [IP: 91.189.92.167 80]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release                                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports InRelease                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release                        
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release.gpg                           
  Connection failed [IP: 91.189.92.180 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates Release.gpg                   
  Connection failed [IP: 91.189.92.182 80]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main TranslationIndex                     
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports Release.gpg                 
  Connection failed [IP: 91.189.92.184 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release                               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates Release                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main i386 Packages/DiffIndex   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports Release                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted i386 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main Sources/DiffIndex                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted Sources/DiffIndex          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe Sources/DiffIndex            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main TranslationIndex          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse Sources/DiffIndex          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse TranslationIndex    
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Sources                              
  Connection failed
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main i386 Packages/DiffIndex          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted TranslationIndex    
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main i386 Packages                        
  Connection failed
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted i386 Packages/DiffIndex    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe TranslationIndex      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe i386 Packages/DiffIndex      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse i386 Packages/DiffIndex    
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en_US                    
  Connection failed
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main TranslationIndex                 
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en                       
  Connection failed
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse TranslationIndex           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted TranslationIndex           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe TranslationIndex             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main Sources/DiffIndex        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted Sources/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe Sources/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse Sources/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main i386 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted i386 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe i386 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse i386 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main Sources/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted Sources/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe Sources/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse Sources/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main i386 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted i386 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe i386 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse i386 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe TranslationIndex
Err [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Sources                   
  Connection failed [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Sources            
  Connection failed [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Sources
  Connection failed [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Sources
  Connection failed [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe i386 Packages         
  Connection failed [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse i386 Packages       
  Connection failed [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main i386 Packages             
  Connection failed [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted i386 Packages     
  Connection failed [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Translation-en_US
  Connection failed [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Translation-en
  Connection failed [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Translation-en_US
  Connection failed [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Translation-en
  Connection failed [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Translation-en_US
  Connection failed [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Translation-en
  Connection failed [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Translation-en_US
  Connection failed [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Translation-en
  Connection failed [IP: 91.189.92.167 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main Sources    
  Connection failed [IP: 91.189.88.46 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted Sources
  Connection failed [IP: 91.189.92.170 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe Sources
  Connection failed [IP: 91.189.92.177 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse Sources
  Connection failed [IP: 91.189.92.180 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main i386 Packages
  Connection failed [IP: 91.189.92.182 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted i386 Packages
  Connection failed [IP: 91.189.92.184 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe i386 Packages
  Connection failed [IP: 91.189.88.40 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse i386 Packages
  Connection failed [IP: 91.189.88.46 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main Translation-en_US
  Connection failed [IP: 91.189.92.170 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main Translation-en
  Connection failed [IP: 91.189.92.177 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse Translation-en_US
  Connection failed [IP: 91.189.92.180 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse Translation-en
  Connection failed [IP: 91.189.92.182 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted Translation-en_US
  Connection failed [IP: 91.189.92.184 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted Translation-en
  Connection failed [IP: 91.189.88.40 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe Translation-en_US
  Connection failed [IP: 91.189.88.46 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe Translation-en
  Connection failed [IP: 91.189.92.170 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main Sources
  Connection failed [IP: 91.189.92.177 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted Sources
  Connection failed [IP: 91.189.92.180 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe Sources
  Connection failed [IP: 91.189.92.182 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse Sources
  Connection failed [IP: 91.189.92.184 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main i386 Packages
  Connection failed [IP: 91.189.88.40 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted i386 Packages
  Connection failed [IP: 91.189.88.46 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe i386 Packages
  Connection failed [IP: 91.189.92.170 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse i386 Packages
  Connection failed [IP: 91.189.92.177 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main Translation-en_US
  Connection failed [IP: 91.189.92.180 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main Translation-en
  Connection failed [IP: 91.189.92.182 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse Translation-en_US
  Connection failed [IP: 91.189.92.184 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse Translation-en
  Connection failed [IP: 91.189.88.40 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted Translation-en_US
  Connection failed [IP: 91.189.88.46 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted Translation-en
  Connection failed [IP: 91.189.92.170 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe Translation-en_US
  Connection failed [IP: 91.189.92.177 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe Translation-en
  Connection failed [IP: 91.189.92.180 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main Sources
  Connection failed [IP: 91.189.92.182 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted Sources
  Connection failed [IP: 91.189.92.184 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe Sources
  Connection failed [IP: 91.189.88.40 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse Sources
  Connection failed [IP: 91.189.88.46 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main i386 Packages
  Connection failed [IP: 91.189.92.170 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted i386 Packages
  Connection failed [IP: 91.189.92.177 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe i386 Packages
  Connection failed [IP: 91.189.92.180 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse i386 Packages
  Connection failed [IP: 91.189.92.182 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main Translation-en_US
  Connection failed [IP: 91.189.92.184 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main Translation-en
  Connection failed [IP: 91.189.88.40 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse Translation-en_US
  Connection failed [IP: 91.189.88.46 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse Translation-en
  Connection failed [IP: 91.189.92.170 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted Translation-en_US
  Connection failed [IP: 91.189.92.177 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted Translation-en
  Connection failed [IP: 91.189.92.180 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe Translation-en_US
  Connection failed [IP: 91.189.92.182 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe Translation-en
  Connection failed [IP: 91.189.92.184 80]
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/Release.gpg](http://extras.ubuntu.com/ubuntu/dists/oneiric/Release.gpg)  Connection failed

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/oneiric/Release.gpg)  Connection failed [IP: 91.189.92.180 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/oneiric-security/Release.gpg)  Connection failed [IP: 91.189.92.167 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/Release.gpg)  Connection failed [IP: 91.189.92.182 80]

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/main/source/Sources](http://extras.ubuntu.com/ubuntu/dists/oneiric/main/source/Sources)  Connection failed

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/main/binary-i386/Packages](http://extras.ubuntu.com/ubuntu/dists/oneiric/main/binary-i386/Packages)  Connection failed

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/Release.gpg)  Connection failed [IP: 91.189.92.184 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/main/source/Sources](http://security.ubuntu.com/ubuntu/dists/oneiric-security/main/source/Sources)  Connection failed [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/restricted/source/Sources](http://security.ubuntu.com/ubuntu/dists/oneiric-security/restricted/source/Sources)  Connection failed [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/universe/source/Sources](http://security.ubuntu.com/ubuntu/dists/oneiric-security/universe/source/Sources)  Connection failed [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/multiverse/source/Sources](http://security.ubuntu.com/ubuntu/dists/oneiric-security/multiverse/source/Sources)  Connection failed [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/universe/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/oneiric-security/universe/binary-i386/Packages)  Connection failed [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/multiverse/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/oneiric-security/multiverse/binary-i386/Packages)  Connection failed [IP: 91.189.92.167 80]

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/main/i18n/Translation-en_US](http://extras.ubuntu.com/ubuntu/dists/oneiric/main/i18n/Translation-en_US)  Connection failed

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/main/i18n/Translation-en](http://extras.ubuntu.com/ubuntu/dists/oneiric/main/i18n/Translation-en)  Connection failed

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/main/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/oneiric-security/main/binary-i386/Packages)  Connection failed [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/restricted/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/oneiric-security/restricted/binary-i386/Packages)  Connection failed [IP: 91.189.92.167 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/oneiric/main/source/Sources)  Connection failed [IP: 91.189.88.46 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/oneiric/restricted/source/Sources)  Connection failed [IP: 91.189.92.170 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/oneiric/universe/source/Sources)  Connection failed [IP: 91.189.92.177 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/main/i18n/Translation-en_US](http://security.ubuntu.com/ubuntu/dists/oneiric-security/main/i18n/Translation-en_US)  Connection failed [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/main/i18n/Translation-en](http://security.ubuntu.com/ubuntu/dists/oneiric-security/main/i18n/Translation-en)  Connection failed [IP: 91.189.92.167 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/oneiric/multiverse/source/Sources)  Connection failed [IP: 91.189.92.180 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/multiverse/i18n/Translation-en_US](http://security.ubuntu.com/ubuntu/dists/oneiric-security/multiverse/i18n/Translation-en_US)  Connection failed [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/multiverse/i18n/Translation-en](http://security.ubuntu.com/ubuntu/dists/oneiric-security/multiverse/i18n/Translation-en)  Connection failed [IP: 91.189.92.167 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/oneiric/main/binary-i386/Packages)  Connection failed [IP: 91.189.92.182 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/restricted/i18n/Translation-en_US](http://security.ubuntu.com/ubuntu/dists/oneiric-security/restricted/i18n/Translation-en_US)  Connection failed [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/restricted/i18n/Translation-en](http://security.ubuntu.com/ubuntu/dists/oneiric-security/restricted/i18n/Translation-en)  Connection failed [IP: 91.189.92.167 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/oneiric/restricted/binary-i386/Packages)  Connection failed [IP: 91.189.92.184 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/universe/i18n/Translation-en_US](http://security.ubuntu.com/ubuntu/dists/oneiric-security/universe/i18n/Translation-en_US)  Connection failed [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/universe/i18n/Translation-en](http://security.ubuntu.com/ubuntu/dists/oneiric-security/universe/i18n/Translation-en)  Connection failed [IP: 91.189.92.167 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/oneiric/universe/binary-i386/Packages)  Connection failed [IP: 91.189.88.40 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/oneiric/multiverse/binary-i386/Packages)  Connection failed [IP: 91.189.88.46 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric/main/i18n/Translation-en_US](http://us.archive.ubuntu.com/ubuntu/dists/oneiric/main/i18n/Translation-en_US)  Connection failed [IP: 91.189.92.170 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric/main/i18n/Translation-en](http://us.archive.ubuntu.com/ubuntu/dists/oneiric/main/i18n/Translation-en)  Connection failed [IP: 91.189.92.177 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric/multiverse/i18n/Translation-en_US](http://us.archive.ubuntu.com/ubuntu/dists/oneiric/multiverse/i18n/Translation-en_US)  Connection failed [IP: 91.189.92.180 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric/multiverse/i18n/Translation-en](http://us.archive.ubuntu.com/ubuntu/dists/oneiric/multiverse/i18n/Translation-en)  Connection failed [IP: 91.189.92.182 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric/restricted/i18n/Translation-en_US](http://us.archive.ubuntu.com/ubuntu/dists/oneiric/restricted/i18n/Translation-en_US)  Connection failed [IP: 91.189.92.184 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric/restricted/i18n/Translation-en](http://us.archive.ubuntu.com/ubuntu/dists/oneiric/restricted/i18n/Translation-en)  Connection failed [IP: 91.189.88.40 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric/universe/i18n/Translation-en_US](http://us.archive.ubuntu.com/ubuntu/dists/oneiric/universe/i18n/Translation-en_US)  Connection failed [IP: 91.189.88.46 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric/universe/i18n/Translation-en](http://us.archive.ubuntu.com/ubuntu/dists/oneiric/universe/i18n/Translation-en)  Connection failed [IP: 91.189.92.170 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/main/source/Sources)  Connection failed [IP: 91.189.92.177 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/restricted/source/Sources)  Connection failed [IP: 91.189.92.180 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/universe/source/Sources)  Connection failed [IP: 91.189.92.182 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/multiverse/source/Sources)  Connection failed [IP: 91.189.92.184 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/main/binary-i386/Packages)  Connection failed [IP: 91.189.88.40 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/restricted/binary-i386/Packages)  Connection failed [IP: 91.189.88.46 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/universe/binary-i386/Packages)  Connection failed [IP: 91.189.92.170 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/multiverse/binary-i386/Packages)  Connection failed [IP: 91.189.92.177 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/main/i18n/Translation-en_US](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/main/i18n/Translation-en_US)  Connection failed [IP: 91.189.92.180 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/main/i18n/Translation-en](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/main/i18n/Translation-en)  Connection failed [IP: 91.189.92.182 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/multiverse/i18n/Translation-en_US](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/multiverse/i18n/Translation-en_US)  Connection failed [IP: 91.189.92.184 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/multiverse/i18n/Translation-en](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/multiverse/i18n/Translation-en)  Connection failed [IP: 91.189.88.40 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/restricted/i18n/Translation-en_US](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/restricted/i18n/Translation-en_US)  Connection failed [IP: 91.189.88.46 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/restricted/i18n/Translation-en](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/restricted/i18n/Translation-en)  Connection failed [IP: 91.189.92.170 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/universe/i18n/Translation-en_US](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/universe/i18n/Translation-en_US)  Connection failed [IP: 91.189.92.177 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/universe/i18n/Translation-en](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-updates/universe/i18n/Translation-en)  Connection failed [IP: 91.189.92.180 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/main/source/Sources)  Connection failed [IP: 91.189.92.182 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/restricted/source/Sources)  Connection failed [IP: 91.189.92.184 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/universe/source/Sources)  Connection failed [IP: 91.189.88.40 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/multiverse/source/Sources)  Connection failed [IP: 91.189.88.46 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/main/binary-i386/Packages)  Connection failed [IP: 91.189.92.170 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/restricted/binary-i386/Packages)  Connection failed [IP: 91.189.92.177 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/universe/binary-i386/Packages)  Connection failed [IP: 91.189.92.180 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/multiverse/binary-i386/Packages)  Connection failed [IP: 91.189.92.182 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/main/i18n/Translation-en_US](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/main/i18n/Translation-en_US)  Connection failed [IP: 91.189.92.184 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/main/i18n/Translation-en](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/main/i18n/Translation-en)  Connection failed [IP: 91.189.88.40 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/multiverse/i18n/Translation-en_US](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/multiverse/i18n/Translation-en_US)  Connection failed [IP: 91.189.88.46 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/multiverse/i18n/Translation-en](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/multiverse/i18n/Translation-en)  Connection failed [IP: 91.189.92.170 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/restricted/i18n/Translation-en_US](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/restricted/i18n/Translation-en_US)  Connection failed [IP: 91.189.92.177 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/restricted/i18n/Translation-en](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/restricted/i18n/Translation-en)  Connection failed [IP: 91.189.92.180 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/universe/i18n/Translation-en_US](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/universe/i18n/Translation-en_US)  Connection failed [IP: 91.189.92.182 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/universe/i18n/Translation-en](http://us.archive.ubuntu.com/ubuntu/dists/oneiric-backports/universe/i18n/Translation-en)  Connection failed [IP: 91.189.92.184 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.
john@Dell-745:~$

---

### Post by matt_symes on 2011-11-26
Hi

This is you problem. 

```
Connection failed [IP: 91.189.92.167 80]
```This has nothing to do with your lock file. /var/lib/apt/lists/lock

Have you tried a different mirror ?

Can you see the server ? Can you ping the server ?

```
ping -c3 91.189.92.167
```Post back results.

Kind regards

---

### Post by capon on 2011-11-26
john@Dell-745:~$ ping -c3 91.189.92.167
PING 91.189.92.167 (91.189.92.167) 56(84) bytes of data.
64 bytes from 91.189.92.167: icmp_req=1 ttl=44 time=128 ms
64 bytes from 91.189.92.167: icmp_req=2 ttl=44 time=131 ms
64 bytes from 91.189.92.167: icmp_req=3 ttl=44 time=151 ms

--- 91.189.92.167 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 128.648/137.355/151.468/10.078 ms
john@Dell-745:~$ ^C
john@Dell-745:~$

---

### Post by matt_symes on 2011-11-26
Hi

You can see the server to ping it.

Open a browser and enter

```
91.189.92.177:80
```

I assume you can see the repository ?

As have been asked, are you behind a proxy ? Do you have an invalid proxy set up ?

What's the output of 

```
env | grep proxy
```

and 

```
apt-config dump | grep -i proxy
```

Kind regards

---

### Post by capon on 2011-11-26
john@Dell-745:~$ 91.189.92.177:80
91.189.92.177:80: command not found
john@Dell-745:~$ 91.189.92.167:80
91.189.92.167:80: command not found
john@Dell-745:~$ sudo 91.189.167:80
[sudo] password for john: 
sudo: 91.189.167:80: command not found
john@Dell-745:~$ env | grep proxy
john@Dell-745:~$ apt-config dump | grep -i proxy
john@Dell-745:~$ 

Mr Symes, System settings/Network shows no proxy. 
the only time I have seen the repository is in /sources.list and it appeared all necessay sources were not #. 
I would ask for some assistance to find that file again.
I thought that be a typo on the ip address and did it both ways.
When just now searching for the best connection, the response was Ubuntu.retrosnub.co.uk.
My residence is Fort Worth, Texas.
System Settings/Software Sources/ Download source= Server for the US. (as default)

---

### Post by matt_symes on 2011-11-26
Hi

> **capon said:**
> john@Dell-745:~$ 91.189.92.177:80
91.189.92.177:80: command not found
john@Dell-745:~$ 91.189.92.167:80
91.189.92.167:80: command not found
john@Dell-745:~$ sudo 91.189.167:80
[sudo] password for john: 
Below was meant to be entered into firefox to make sure you could see the page 

```
91.189.92.177:80
```

> sudo: 91.189.167:80: command not found
john@Dell-745:~$ env | grep proxy
john@Dell-745:~$ apt-config dump | grep -i proxy
john@Dell-745:~$
Mr Symes, System settings/Network shows no proxy.  

It looks like you have not proxy defined.

> the only time I have seen the repository is in /sources.list and it appeared all necessay sources were not #. 
I would ask for some assistance to find that file again.
I thought that be a typo on the ip address and did it both ways.

The file is in /etc/apt/sources.list.

> When just now searching for the best connection, the response was Ubuntu.retrosnub.co.uk.
My residence is Fort Worth, Texas.
System Settings/Software Sources/ Download source= Server for the US. (as default)

Did you try the new server (Ubuntu.retrosnub.co.uk) ?

Have you always had trouble with apt-get since you installed Ubuntu ? If not when did it stop working ? Did you change anything ?

I'm at a bit of a loss at the moment unless you are behind a proxy and you have not set up the proxy settings.

Kind regards

---

### Post by Paddy Landau on 2011-11-26
To add to the helpful comments by matt_symes, perhaps we can do it through the GUI (because that's how I know how to do it, not because it's necessarily better).

Try this, please:

[LIST]
[*]Open your Software Sources.
[*]In the Ubuntu Software tab, in "Download from", select Other > Select Best Server (it will take a couple of minutes to run).
[*]Press Choose Server.
[*]Close Software Sources.
[/LIST]
Then:

[LIST]
[*]Open Update Manager.
[*]Press Check.
[*]If you get any errors, post them here. Otherwise:
[*]Press Install Updates.
[*]If you get any errors, post them here.
[/LIST]

---

### Post by capon on 2011-11-27
To matt_symes & Paddy Landau: Thank you much for all the effort. This machine is a reconditioned unit purchased from a small business that offers me a return plan. That option will be exercised. If the current flaw in this machine could be fixed, I would always be anxious when updating. The two gentlemen mentioned above have encouraged me to learn more about Ubuntu. But it will be on a generic machine or maybe something like HPCompaq. See you in a different forum on this web site.
Regards

---

