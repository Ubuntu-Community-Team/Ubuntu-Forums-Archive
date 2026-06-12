---
title: "Unable to lock the administration directory (/var/lib/dpkg/)"
date: 2008-12-09
forum: General Help
---

### Post by K_K on 2008-12-09
Kk... so im a newbie migrated from windows on my server caus its cheaper (who hasnt heard that story before im sure). I'm trying to install mobloquer (GUI for moblock). Moblock and moblock-control are successfully installed (i checked this and it blocks all internet access when turned on (i have turned it off to run this as i know how to sort that problem out later. I'm running ubuntu 8.04 (hardy)with Gnome 2.22.1 . I believe the problem is something to do with apt-get (but havent a clue how to solve it). Heres the complete terminal error report:

```
admin@ks363480:~$ sudo apt-get update
Hit http://archive.canonical.com hardy Release.gpg
Ign http://archive.canonical.com hardy/partner Translation-en_GB
Hit http://archive.ubuntu.com hardy Release.gpg                                
Hit http://archive.ubuntu.com hardy/main Translation-en_GB                     
Hit http://security.ubuntu.com hardy-security Release.gpg                      
Ign http://security.ubuntu.com hardy-security/universe Translation-en_GB       
Hit http://archive.ubuntu.com hardy/universe Translation-en_GB                 
Hit http://archive.ubuntu.com hardy/restricted Translation-en_GB               
Hit http://archive.ubuntu.com hardy/multiverse Translation-en_GB               
Hit http://archive.ubuntu.com hardy-updates Release.gpg                        
Ign http://archive.ubuntu.com hardy-updates/universe Translation-en_GB         
Ign http://archive.ubuntu.com hardy-updates/main Translation-en_GB             
Ign http://archive.ubuntu.com hardy-updates/multiverse Translation-en_GB       
Ign http://archive.ubuntu.com hardy-updates/restricted Translation-en_GB       
Hit http://archive.canonical.com hardy Release                                 
Hit http://archive.ubuntu.com hardy Release                                    
Ign http://security.ubuntu.com hardy-security/main Translation-en_GB           
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_GB     
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_GB     
Hit http://security.ubuntu.com hardy-security Release                          
Hit http://archive.ubuntu.com hardy-updates Release                            
Hit http://archive.canonical.com hardy/partner Packages                        
Hit http://archive.ubuntu.com hardy/main Packages                              
Hit http://archive.ubuntu.com hardy/universe Packages                          
Hit http://archive.ubuntu.com hardy/restricted Packages                        
Hit http://archive.ubuntu.com hardy/multiverse Packages                        
Hit http://security.ubuntu.com hardy-security/universe Packages                
Hit http://security.ubuntu.com hardy-security/main Packages                    
Hit http://security.ubuntu.com hardy-security/multiverse Packages              
Hit http://security.ubuntu.com hardy-security/restricted Packages              
Hit http://archive.ubuntu.com hardy-updates/universe Packages                  
Hit http://archive.ubuntu.com hardy-updates/main Packages            
Hit http://archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://archive.ubuntu.com hardy-updates/restricted Packages      
Hit http://moblock-deb.sourceforge.net hardy Release.gpg             
Ign http://moblock-deb.sourceforge.net hardy/main Translation-en_GB
Get: 1 http://packages.medibuntu.org hardy Release.gpg [189B]
Hit http://moblock-deb.sourceforge.net hardy Release                           
Ign http://packages.medibuntu.org hardy/free Translation-en_GB                 
Ign http://packages.medibuntu.org hardy/non-free Translation-en_GB             
Hit http://moblock-deb.sourceforge.net hardy/main Packages                     
Get: 2 http://packages.medibuntu.org hardy Release [9335B]                     
Ign http://packages.medibuntu.org hardy Release
Hit http://packages.medibuntu.org hardy/free Packages
Hit http://packages.medibuntu.org hardy/non-free Packages
Hit http://moblock-deb.sourceforge.net hardy/main Sources
Fetched 190B in 0s (319B/s)
W: GPG error: http://packages.medibuntu.org hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

Solutions either in terminal C&P ready code or with big pictures would be appreciated ;) 

Thanks for helping guys i've been assured by mate that ubuntu has must helpful forum imaginable!

---

### Post by taurus on 2008-12-09
Do you happen to have synaptic, add/remove, or update-manager running while you run that command from a terminal?

```
ps -A
```

---

### Post by K_K on 2008-12-09
no i cant find any of those processes using that command

---

### Post by cariboo on 2008-12-09
You may have a leftover lock file in /var/lib/dpkg like this:

>  ls -l
total 6208
drwxr-xr-x 2 root root    4096 Dec  9 12:23 alternatives
-rw-r--r-- 1 root root 1473057 Dec  9 12:41 available
-rw-r--r-- 1 root root 1473057 Dec  9 12:41 available-old
-rw-r--r-- 1 root root       8 Oct 29 14:04 cmethopt
-rw-r--r-- 1 root root     758 Dec  4 17:28 diversions
-rw-r--r-- 1 root root     659 Dec  4 17:28 diversions-old
drwxr-xr-x 2 root root  270336 Dec  9 12:41 info
-rw-r----- 1 root root       0 Dec  9 12:41 lock
drwxr-xr-x 2 root root    4096 Sep  3 05:03 parts
-rw-r--r-- 1 root root      65 Oct 29 14:20 statoverride
-rw-r--r-- 1 root root      30 Oct 29 14:19 statoverride-old
-rw-r--r-- 1 root root 1538726 Dec  9 12:41 status
-rw-r--r-- 1 root root 1538720 Dec  9 12:41 status-old
drwxr-xr-x 2 root root    4096 Dec  9 12:23 triggers
drwxr-xr-x 2 root root    4096 Dec  9 12:41 updates

Just cd into the directory and remove the lock file.

Jim

---

### Post by K_K on 2008-12-09
yes there is a lock file. :D - this is probs the stupidest question BUT it says permission denied when deleting it in file browser. i'm highest admin...

---

### Post by karlr42 on 2008-12-09
You'll need to be root-
```
gksudu nautilus
```
then navigate back to it and delete normally.

---

### Post by K_K on 2008-12-09
I'm sorry that made no sense to me...

```
gksudu nautilus
``` is invalid command...

---

### Post by karlr42 on 2008-12-09
sorry, mistype, meant to say **gksudo**

---

### Post by djwright745 on 2008-12-11
After reading this thread.  I was inspired to close Synaptic and try again.  I entered :


```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

```

Then, I get this :
> 
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release                                                
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release.gpg [189B]                                  
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Packages                                       
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Translation-en_US                                
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Translation-en_US                            
Get:2 [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release [11.7kB]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release                                   
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Packages                       
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release.gpg                                            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Translation-en_US
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release.gpg [189B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release [51.2kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Sources
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Packages [237kB]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Packages [3861B]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Sources [74.1kB]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Sources [1169B]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Packages [27.4kB]
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Sources [5727B]
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Packages [14B]
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Sources [14B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security/multiverse Sources
Fetched 401kB in 23s (16.8kB/s)
Reading package lists... Done
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?


Any idea what I might do next?

---

### Post by djwright745 on 2008-12-11
I did [FONT="Courier New"]gksudo nautilus[/FONT] and moved to trash.  (No delete option in menu?  I am new.) Then I 
```
sudo apt-get update
```

I get
> Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Translation-en_US    
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release.gpg               
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Translation-en_US
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release.gpg [189B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Translation-en_US         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Translation-en_US         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release.gpg                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Translation-en_US       
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release                              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security/main Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Packages                                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security/restricted Translation-en_US                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security/universe Translation-en_US  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security Release                                       
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Translation-en_US          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Sources   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Sources                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security/multiverse Packages
Get:2 [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release [11.7kB]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security/multiverse Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Packages 
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Packages
Fetched 190B in 1s (114B/s)
Reading package lists... Done
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems


Afterward, I noticed that if I [FONT="Courier New"]gksudo nautilus[/FONT] again, the lock file is present in [FONT="Courier New"]/var/lib/dpgk[/FONT] again.  Interestingly, lock appears to have nothing in it when opened in [FONT="Courier New"]gedit[/FONT].

---

### Post by cariboo on 2008-12-12
Do you have the Medibuntu key listed in Synaptic-->Settings-->Repositories-->Authentication?

See attached screenshot.

Jim

---

### Post by djwright745 on 2008-12-12
Well, yes actually, I do!  I remember long ago downloading all of those packages at once.  I managed to download codecs, but I do not know if I got all of the Medibuntu packages.  Is there a list anywhere?  Nevermind.  I will just do a search ;).  Thank you for the newb support!

---

### Post by teddersion on 2010-02-12
Hi all,

I had the same problem and found that indeed I had a leftover lock file in /var/lib/dpkg. Deleting it fixed the problem, thanks!

---

### Post by monn on 2010-02-15
> **cariboo907 said:**
> Do you have the Medibuntu key listed in Synaptic-->Settings-->Repositories-->Authentication?

See attached screenshot.

Jim


I updated ubuntu but I don't have medibuntu  key....help...?

---

