---
title: "after upgrade to 10.04 ,can not update"
date: 2011-09-28
forum: Desktop Environments
---

### Post by weishigoname on 2011-09-28
Hi! after I upgrade to ubuntu 10.04, When I update, getting the follow errors:
ws@ws-laptop:~$ sudo apt-get update
[sudo] password for ws: 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg                             
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/shutter/ppa/ubuntu/](http://ppa.launchpad.net/shutter/ppa/ubuntu/) lucid/main Translation-en_US  
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                             
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US       
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US      
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg [198B]            
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security Release.gpg [198B]           
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Get:3 [http://deb.opera.com](http://deb.opera.com) stable Release.gpg [189B]                           
Ign [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable/non-free Translation-en_US              
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Get:4 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198B]                           
Get:5 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages [1,383kB]                   
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-proposed Release.gpg [198B]           
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-proposed/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-proposed/main Translation-en_US 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-proposed/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release                                 
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release [44.7kB]              
Get:8 [http://deb.opera.com](http://deb.opera.com) stable Release [633B]                               
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                        
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                              
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release.gpg                           
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                              
Get:9 [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages [841B]                     
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic/free Translation-en_US               
Ign [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main Translation-en_US     
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security Release [44.7kB]            
Get:11 [http://dl.google.com](http://dl.google.com) stable Release [1,347B]                            
Get:12 [http://dl.google.com](http://dl.google.com) stable/main Packages [1,203B]                      
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security Release [44.7kB]            
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic/non-free Translation-en_US
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release                               
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-proposed Release [44.7kB]            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security Release                        
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Packages                         
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Packages                     
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Sources                          
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-proposed Release [44.7kB]            
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages                       
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-proposed Release                        
  
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages [519kB]        
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages [3,267B] 
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources [1,443B]  
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources [201kB]         
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources [80.4kB]    
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages [225kB]    
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/main Packages [210kB]       
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/restricted Packages [14B]   
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/restricted Sources [14B]    
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/main Sources [63.1kB]       
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages [519kB]        
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/universe Sources [25.8kB]   
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/universe Packages [84.4kB]  
Fetched 2,895kB in 1min 55s (25.1kB/s)                                         
Reading package lists... Done
W:  GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security Release: The  following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu  Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: A error  occurred during the signature verification. The repository is not  updated and the previous index files will be used.GPG error:  [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-proposed Release: The following  signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive  Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://ppa.launchpad.net/shutter/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.bz2](http://ppa.launchpad.net/shutter/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.bz2)  Hash Sum mismatch

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-proposed/Release](http://us.archive.ubuntu.com/ubuntu/dists/lucid-proposed/Release)  

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-amd64/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-amd64/Packages.bz2)  Hash Sum mismatch

W: Some index files failed to download, they have been ignored, or old ones used instead.
ws@ws-laptop:~$ sudo aptitude update
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                              
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg                              
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US           
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US     
Hit [http://deb.opera.com](http://deb.opera.com) stable Release.gpg                                     
Ign [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable/non-free Translation-en_US               
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                  
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release.gpg                            
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg                      
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US   
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security Release.gpg [198B]            
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-proposed Release.gpg [198B]            
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                         
Hit [http://deb.opera.com](http://deb.opera.com) stable Release                                         
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-proposed/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-proposed/main Translation-en_US  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-proposed/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release                          
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security Release [44.7kB]              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security Release                         
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                  
Ign [http://ppa.launchpad.net/shutter/ppa/ubuntu/](http://ppa.launchpad.net/shutter/ppa/ubuntu/) lucid/main Translation-en_US   
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-proposed Release [44.7kB]              
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-proposed Release                         
  
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic/free Translation-en_US                
Get:5 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198B]                            
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic/non-free Translation-en_US            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                      
Get:6 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages [1,383kB]                    
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                               
Ign [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main Translation-en_US        
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages                        
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages [519kB]          
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                               
Get:8 [http://dl.google.com](http://dl.google.com) stable Release [1,347B]                              
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Packages                      
Get:9 [http://dl.google.com](http://dl.google.com) stable/main Packages [1,203B]                        
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Packages                      
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Sources                           
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Sources                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/main Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/restricted Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/restricted Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/main Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/universe Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/universe Packages               
Fetched 522kB in 1min 18s (6,615B/s)                                            
Reading package lists... Done
W:  GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security Release: The  following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu  Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: A error  occurred during the signature verification. The repository is not  updated and the previous index files will be used.GPG error:  [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-proposed Release: The following  signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive  Automatic Signing Key <ftpmaster@ubuntu.com>


I tried 
1:
sudo apt-get clean
cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
cd ~
sudo apt-get clean
sudo apt-get update

2:
sudo aptitude -o Acquire::http::No-Cache=True -o Acquire::BrokenProxy=true update
then test with
sudo apt-get update

3:
change server and then update

and add key again ,
all above can not fix that error

cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027)]/ karmic main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates restricted main universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security restricted main universe #Added by software-properties
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security universe
# deb [http://ppa.launchpad.net/jason-scheunemann/ppa/ubuntu](http://ppa.launchpad.net/jason-scheunemann/ppa/ubuntu) lucid main # disabled on upgrade to lucid

#theme
# deb [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) lucid main # disabled on upgrade to lucid
# deb-src [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) lucid main # disabled on upgrade to lucid

#ppstream
# deb [http://ppa.launchpad.net/portis25/ppa/ubuntu](http://ppa.launchpad.net/portis25/ppa/ubuntu) lucid main # disabled on upgrade to lucid
# deb-src [http://ppa.launchpad.net/portis25/ppa/ubuntu](http://ppa.launchpad.net/portis25/ppa/ubuntu) lucid main # disabled on upgrade to lucid
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-proposed restricted main universe

I need help

---

### Post by Krytarik on 2011-09-28
Apparently, your "sources.list" wasn't ported correctly to the repos of Lucid. Specifically, this:
```
http://XX.archive.ubuntu.com/ubuntu/ lucid-security ...
```is now:
```
http://security.ubuntu.com/ubuntu lucid-security ...
```I would create a new, proper "sources.list", also reflecting your location, with this tool:

[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

Greetings.

---

### Post by weishigoname on 2011-09-30
> **Krytarik said:**
> Apparently, your "sources.list" wasn't ported correctly to the repos of Lucid. Specifically, this:
```
http://XX.archive.ubuntu.com/ubuntu/ lucid-security ...
```is now:
```
http://security.ubuntu.com/ubuntu lucid-security ...
```I would create a new, proper "sources.list", also reflecting your location, with this tool:

[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

Greetings.
  Hi ! I create a new sources.list:
#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################

###### Ubuntu Main Repos
deb-src [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) lucid main restricted universe multiverse 

###### Ubuntu Update Repos
deb-src [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) lucid-security main restricted universe multiverse 
deb-src [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) lucid-updates main restricted universe multiverse 
deb-src [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) lucid-proposed main restricted universe multiverse 
deb-src [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse 

but it still error:
ws@ws-laptop:~$ sudo apt-get clean
ws@ws-laptop:~$ cd /var/lib/apt
ws@ws-laptop:/var/lib/apt$ sudo mv lists lists.old
mv: cannot move `lists' to `lists.old/lists': Directory not empty
ws@ws-laptop:/var/lib/apt$ sudo mkdir -p lists/partial
ws@ws-laptop:/var/lib/apt$ cd ~
ws@ws-laptop:~$ sudo apt-get clean
ws@ws-laptop:~$ cd /var/lib/apt
ws@ws-laptop:/var/lib/apt$ ls
cdroms.list      keyrings  lists.old   lists.old2  periodic
extended_states  lists     lists.old1  mirrors
ws@ws-laptop:/var/lib/apt$ sudo rm -rf lists
ws@ws-laptop:/var/lib/apt$ sudo mkdir -p lists/partial
ws@ws-laptop:/var/lib/apt$ ls
cdroms.list      keyrings  lists.old   lists.old2  periodic
extended_states  lists     lists.old1  mirrors
ws@ws-laptop:/var/lib/apt$ cd ~
ws@ws-laptop:~$ sudo apt-get clean
ws@ws-laptop:~$ sudo apt-get update
Get:1 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) lucid Release.gpg [189B]
Get:2 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) lucid-security Release.gpg [198B]           
Get:3 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) lucid-updates Release.gpg [198B]            
Get:4 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) lucid-proposed Release.gpg [198B]           
Get:5 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) lucid-backports Release.gpg [198B]          
Get:6 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) lucid Release [57.2kB]                      
Get:7 [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg [198B]                    
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US       
Get:8 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg [316B]                        
Ign [http://ppa.launchpad.net/shutter/ppa/ubuntu/](http://ppa.launchpad.net/shutter/ppa/ubuntu/) lucid/main Translation-en_US  
Get:9 [http://deb.opera.com](http://deb.opera.com) stable Release.gpg [189B]                           
Ign [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable/non-free Translation-en_US              
Get:10 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198B]                          
Get:11 [http://archive.canonical.com](http://archive.canonical.com) lucid Release [8,215B]                     
Get:12 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release [13.9kB]                         
Get:13 [http://deb.opera.com](http://deb.opera.com) stable Release [633B]                              
Get:14 [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release.gpg [197B]                 
Get:15 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) lucid-security Release [44.7kB]            
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                              
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic/free Translation-en_US               
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                              
Get:16 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) lucid-updates Release [44.7kB]             
Get:17 [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages [841B]                    
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic/non-free Translation-en_US           
Get:18 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) lucid-proposed Release [44.7kB]            
Ign [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main Translation-en_US       
Get:19 [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release [9,237B]                   
Get:20 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages [1,251B]                   
Get:21 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) lucid-backports Release [38.5kB]           
Get:22 [http://dl.google.com](http://dl.google.com) stable Release [1,347B]                            
Get:23 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) lucid-backports Release [38.5kB]           
Get:24 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) lucid/main Sources [659kB]                 
Ign [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) lucid-backports Release                       
Get:25 [http://dl.google.com](http://dl.google.com) stable/main Packages [1,200B]                      
Get:26 [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Packages [3,269B]             
Get:27 [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Packages [6,757B]         
Get:28 [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Sources [3,259B]              
Get:29 [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Sources [5,543B]          
Get:30 [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages [13.8kB]            
Get:31 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) lucid/restricted Sources [3,775B]          
Get:32 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) lucid/universe Sources [3,165kB]           
Get:33 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) lucid/multiverse Sources [119kB]           
Get:34 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) lucid-security/main Sources [64.7kB]       
Get:35 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) lucid-security/restricted Sources [14B]    
Get:36 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) lucid-security/universe Sources [25.8kB]   
Get:37 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) lucid-security/multiverse Sources [1,751B] 
Get:38 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) lucid-updates/main Sources [202kB]         
Get:39 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) lucid-updates/restricted Sources [1,443B]  
Get:40 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) lucid-updates/universe Sources [80.8kB]    
Get:41 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) lucid-updates/multiverse Sources [5,070B]  
Get:42 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) lucid-proposed/main Sources [53.0kB]       
Get:43 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) lucid-proposed/restricted Sources [14B]    
Get:44 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) lucid-proposed/universe Sources [6,306B]   
Get:45 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) lucid-proposed/multiverse Sources [14B]    
Get:46 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) lucid-backports/main Sources [7,832B]      
Get:47 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) lucid-backports/restricted Sources [14B]   
Get:48 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) lucid-backports/universe Sources [18.2kB]  
Get:49 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) lucid-backports/multiverse Sources [1,633B]
Fetched 4,715kB in 3min 8s (25.0kB/s)                                          
Reading package lists... Done
W: GPG error: [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) lucid-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

---

### Post by Krytarik on 2011-09-30
> **weishigoname said:**
> ```
W: GPG error: http://cn.archive.ubuntu.com lucid-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
```
Try this:
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5
```

---

### Post by weishigoname on 2011-10-02
> **Krytarik said:**
> Try this:
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5
```

it can not be solved for me :
ws@ws-laptop:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5
[sudo] password for ws: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5
gpg: requesting key 437D05B5 from hkp server keyserver.ubuntu.com
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
ws@ws-laptop:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5
gpg: requesting key 437D05B5 from hkp server keyserver.ubuntu.com
gpg: key 437D05B5: public key "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1
ws@ws-laptop:~$ sudo apt-get update
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198B]
Ign [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main Translation-en_US       
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [1,347B]                             
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                             
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US       
Get:3 [http://dl.google.com](http://dl.google.com) stable/main Packages [1,200B]                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg                             
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/sevenmachines/flash/ubuntu/](http://ppa.launchpad.net/sevenmachines/flash/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg                     
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security Release.gpg                    
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-proposed Release.gpg                    
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-proposed/main Translation-en_US 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-proposed/universe Translation-en_US
Ign [http://ppa.launchpad.net/shutter/ppa/ubuntu/](http://ppa.launchpad.net/shutter/ppa/ubuntu/) lucid/main Translation-en_US  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                        
Hit [http://deb.opera.com](http://deb.opera.com) stable Release.gpg                                    
Ign [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable/non-free Translation-en_US              
Hit [http://www.scootersoftware.com](http://www.scootersoftware.com) stable Release.gpg                          
Ign [http://www.scootersoftware.com/](http://www.scootersoftware.com/) stable/non-free Translation-en_US          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security Release                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release.gpg                           
Hit [http://www.scootersoftware.com](http://www.scootersoftware.com) stable Release                              
Get:4 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages [1,383kB]                   
Hit [http://deb.opera.com](http://deb.opera.com) stable Release                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-proposed Release                        
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic/free Translation-en_US               
Get:5 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages [1,383kB]                   
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                              
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic/non-free Translation-en_US           
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                              
Ign [http://www.scootersoftware.com](http://www.scootersoftware.com) stable/non-free Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages                       
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages [522kB]         
Ign [http://www.scootersoftware.com](http://www.scootersoftware.com) stable/non-free Packages                    
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release                               
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                              
Hit [http://www.scootersoftware.com](http://www.scootersoftware.com) stable/non-free Packages                    
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Packages                         
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Packages                     
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Sources  
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Sources                      
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources [202kB]          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages               
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/main Packages [214kB]        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/main Sources                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/universe Sources               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/universe Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-proposed/main Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-proposed/universe Packages              
Fetched 940kB in 12s (72.8kB/s)                                                
W: Failed to fetch [http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/lucid/main/binary-amd64/Packages.bz2](http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/lucid/main/binary-amd64/Packages.bz2)  Hash Sum mismatch

W: Failed to fetch [http://ppa.launchpad.net/shutter/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.bz2](http://ppa.launchpad.net/shutter/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.bz2)  Hash Sum mismatch

E: Some index files failed to download, they have been ignored, or old ones used instead.
ws@ws-laptop:~$ cd /var/lib/apt
ws@ws-laptop:/var/lib/apt$ ls
cdroms.list      keyrings  lists.old   lists.old2  periodic
extended_states  lists     lists.old1  mirrors
ws@ws-laptop:/var/lib/apt$ sudo su
root@ws-laptop:/var/lib/apt# rm -rf lists
root@ws-laptop:/var/lib/apt# mkdir -p lists/partial
root@ws-laptop:/var/lib/apt# ls
cdroms.list      keyrings  lists.old   lists.old2  periodic
extended_states  lists     lists.old1  mirrors
root@ws-laptop:/var/lib/apt# exit
exit
ws@ws-laptop:/var/lib/apt$ cd ~
ws@ws-laptop:~$ sudo apt-get clean
ws@ws-laptop:~$ sudo apt-get update
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198B]
Ign [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main Translation-en_US       
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [1,347B]                             
Get:3 [http://www.scootersoftware.com](http://www.scootersoftware.com) stable Release.gpg [189B]                 
Ign [http://www.scootersoftware.com/](http://www.scootersoftware.com/) stable/non-free Translation-en_US          
Get:4 [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release.gpg [197B]                  
Get:5 [http://dl.google.com](http://dl.google.com) stable/main Packages [1,200B]                       
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg [189B]                    
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US      
Get:7 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg [316B]                        
Ign [http://ppa.launchpad.net/sevenmachines/flash/ubuntu/](http://ppa.launchpad.net/sevenmachines/flash/ubuntu/) lucid/main Translation-en_US
Get:8 [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg [198B]                    
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US       
Get:9 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg [316B]                        
Get:10 [http://deb.opera.com](http://deb.opera.com) stable Release.gpg [189B]                          
Ign [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable/non-free Translation-en_US              
Get:11 [http://www.scootersoftware.com](http://www.scootersoftware.com) stable Release [1,737B]                  
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg [198B]           
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security Release.gpg [198B]          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-proposed Release.gpg [198B]          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-proposed/main Translation-en_US 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-proposed/universe Translation-en_US
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release [57.2kB]                     
Ign [http://ppa.launchpad.net/shutter/ppa/ubuntu/](http://ppa.launchpad.net/shutter/ppa/ubuntu/) lucid/main Translation-en_US  
Get:16 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release [13.9kB]                         
Get:17 [http://archive.canonical.com](http://archive.canonical.com) lucid Release [8,215B]                     
Ign [http://www.scootersoftware.com](http://www.scootersoftware.com) stable/non-free Packages                    
Get:18 [http://deb.opera.com](http://deb.opera.com) stable Release [633B]                              
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic/free Translation-en_US               
Get:19 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release [13.9kB]                         
Ign [http://www.scootersoftware.com](http://www.scootersoftware.com) stable/non-free Packages                    
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                              
Get:20 [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages [13.8kB]            
Get:21 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages [1,383kB]                  
Get:22 [http://www.scootersoftware.com](http://www.scootersoftware.com) stable/non-free Packages [645B]          
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic/non-free Translation-en_US           
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release [44.7kB]             
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                              
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security Release [44.7kB]            
Get:25 [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages [841B]                    
Get:26 [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release [9,237B]                   
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security Release [44.7kB]            
Get:28 [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages [1,383kB]                  
Get:29 [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Packages [3,269B]             
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-proposed Release [44.7kB]            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security Release                        
Get:31 [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Packages [6,757B]         
Get:32 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-proposed Release [44.7kB]            
Get:33 [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Sources [3,259B]              
Get:34 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources [659kB]                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-proposed Release                        
Get:35 [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Sources [5,543B]          
Get:36 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages [5,430kB]          
Get:37 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages [522kB]        
Get:38 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources [202kB]         
Get:39 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources [80.8kB]    
Get:40 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages [231kB]    
Get:41 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/main Packages [214kB]       
Get:42 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/main Sources [64.7kB]       
Get:43 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources [659kB]                 
Get:44 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages [1,383kB]              
Get:45 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources [3,165kB]           
Get:46 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/universe Sources [25.8kB]   
Get:47 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security/universe Packages [89.2kB]  
Get:48 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-proposed/main Packages [124kB]       
Get:49 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-proposed/universe Packages [19.7kB]  
Fetched 15.2MB in 1min 15s (201kB/s)                                           
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-proposed Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch [http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/lucid/main/binary-amd64/Packages.bz2](http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/lucid/main/binary-amd64/Packages.bz2)  Hash Sum mismatch

W: Failed to fetch [http://ppa.launchpad.net/shutter/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.bz2](http://ppa.launchpad.net/shutter/ppa/ubuntu/dists/lucid/main/binary-amd64/Packages.bz2)  Hash Sum mismatch

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by Krytarik on 2011-10-02
1. You have several Karmic repos enabled now, which were disabled before the regeneration of your "sources.list". They shouldn't be there, try replacing those by the respective Lucid repos.

2. The "sevenmachines/flash" PPA is causing errors, try re-adding those.

3. The GPG error of the "lucid-security Release" repo happens one time and the other time not, which indicates an unstable internet connection, as I see it.

And btw., you should really use code boxes, therefore use the #-button in the editor to enclose the text in code tags.

---

### Post by weishigoname on 2011-10-04
it still can not solve my problem ,and I try to upgrade to 10.10,and get error:

W:GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>, W:GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-proposed Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-amd64/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-amd64/Packages.bz2)  Hash Sum mismatch
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/source/Sources.bz2)  Hash Sum mismatch
, E:Some index files failed to download, they have been ignored, or old ones used instead.

I do not know what to do .

---

### Post by Krytarik on 2011-10-05
> **weishigoname said:**
> I do not know what to do .
Well, first, I would stop upgrading the Ubuntu version to the ever next release at some point - or more precisely, trying to do so. And, as you can see, that doesn't change anything. ;-)

Also, did you know that Lucid 10.04 is an [LTS]("https://wiki.ubuntu.com/LTS") version, while Maverick 10.10 is not!? Which means that Maverick's support ends in roughly half a year.

However, now that I see that same behaviour, and you stating "try to upgrade to 10.10", I'm questioning if you were actually upgraded to Lucid earlier, or if you are still running Karmic. So, before we do anything further, please check that with:
```
lsb_release -a
```

---

### Post by weishigoname on 2011-10-06
> **Krytarik said:**
> Well, first, I would stop upgrading the Ubuntu version to the ever next release at some point - or more precisely, trying to do so. And, as you can see, that doesn't change anything. ;-)

Also, did you know that Lucid 10.04 is an [LTS]("https://wiki.ubuntu.com/LTS") version, while Maverick 10.10 is not!? Which means that Maverick's support ends in roughly half a year.

However, now that I see that same behaviour, and you stating "try to upgrade to 10.10", I'm questioning if you were actually upgraded to Lucid earlier, or if you are still running Karmic. So, before we do anything further, please check that with:
```
lsb_release -a
```

ws@ws-laptop:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 10.04.3 LTS
Release:    10.04
Codename:    lucid
ws@ws-laptop:~$ sudo su
[sudo] password for ws: 
root@ws-laptop:/home/ws# lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 10.04.3 LTS
Release:    10.04
Codename:    lucid

If I can not upgrade to higher version this way ,how I can upgrade ?

---

### Post by Krytarik on 2011-10-06
> **weishigoname said:**
> If I can not upgrade to higher version this way ,how I can upgrade ?
Well, as I indicated in my previous post, I wouldn't upgrade to Maverick 10.10. But if you want to go even higher, I recommend doing a fresh install of Oneiric 11.10 when it's released on October 13th. Having no remnants of your Karmic install anymore then, this issue should be solved then, too.

---

