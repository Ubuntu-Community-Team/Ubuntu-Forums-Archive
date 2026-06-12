---
title: "My apt is screwed. Help"
date: 2009-04-28
forum: General Help
---

### Post by ranjith19 on 2009-04-28
Whenever I update apt half the packages are not updating. I am using ubuntu 8.10

This is what I get. Please help

[FONT="Lucida Console"]
root@master:/home/ranjith# apt-get update
Ign [http://repoubuntusoftware.info](http://repoubuntusoftware.info) intrepid Release.gpg                                                                                                     
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release.gpg [197B]                                                                                             
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release.gpg                                                                                                       
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Translation-en_IN                                                                                         
Get:2 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid Release.gpg [191B]                                                                                           
Get:3 [http://dl.google.com](http://dl.google.com) testing Release.gpg [189B]                                                                                                       
Get:4 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg [307B]                                                                                                  
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release                                                                                                           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_IN                                                                                                
Ign [http://dl.google.com](http://dl.google.com) testing/non-free Translation-en_IN                                                                                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg                                                                                                           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_IN                                                                                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                                                                                                              
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Packages                                                                                                  
Ign [http://repoubuntusoftware.info](http://repoubuntusoftware.info) intrepid/all Translation-en_IN                                                                                           
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Sources                                                                                                   
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid/main Translation-en_IN                                                                                         
Ign [http://repoubuntusoftware.info](http://repoubuntusoftware.info) intrepid Release                                                                                                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_IN                                                                                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg                                                                                                           
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Packages                                                                                                  
Get:5 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid Release [1025B]                                                                                              
Err [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid Release                                                                                                        
  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_IN                                                                                                
Get:6 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg [307B]                                                                                                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_IN                                                                                                
Get:7 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg [307B]                                                                                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_IN                                                                                                  
Get:8 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg [307B]                                                                                                  
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Sources                                                                                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_IN                                                                                                
Get:9 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [46.7kB]                                                                                                    
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release                                                                                                               
  
Get:10 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [27.6kB]                                                                                                   
Ign [http://repoubuntusoftware.info](http://repoubuntusoftware.info) intrepid/all Packages                                                                                                    
Get:11 [http://dl.google.com](http://dl.google.com) testing Release [772B]                                                                                                          
Ign [http://dl.google.com](http://dl.google.com) testing Release                                                                                                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release                                                                                                                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release                                                                                                               
Get:12 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [46.7kB]                                                                                                   
Get:13 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release [52.9kB]                                                                                                     
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release                                                                                                               
  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                                                                                                 
Hit [http://repoubuntusoftware.info](http://repoubuntusoftware.info) intrepid/all Packages                                                                                                    
Get:14 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [46.7kB]                                                                                                   
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release                                                                                                               
  
Get:15 [http://dl.google.com](http://dl.google.com) testing/non-free Packages [746B]                                                                                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                                                                                                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                                                                            
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid Release.gpg                                                                          
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid/main Translation-en_IN                                                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg                                                                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_IN                                                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                                                                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources                                                                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                                                                              
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Translation-en_IN                                                              
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Translation-en_IN                                                          
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid/restricted Translation-en_IN                                   
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid/universe Translation-en_IN                                     
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid/multiverse Translation-en_IN                                                         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_IN                                                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_IN                              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_IN      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                                                     
Get:16 [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release [11.7kB]                                           
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release                                                                
  
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                                                        
  404 Not Found
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid-updates Release.gpg
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid-updates/main Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid-updates/restricted Translation-en_IN
Get:17 [http://apt.debianchile.org](http://apt.debianchile.org) unstable Release.gpg [189B]
Ign [http://apt.debianchile.org](http://apt.debianchile.org) unstable/main Translation-en_IN
Get:18 [http://apt.debianchile.org](http://apt.debianchile.org) unstable Release [3594B]                                                                                                  
Ign [http://apt.debianchile.org](http://apt.debianchile.org) unstable Release                                                                                                             
Hit [http://apt.debianchile.org](http://apt.debianchile.org) unstable/main Packages                                                                                                       
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid-updates/universe Translation-en_IN                                                                                
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_IN                                                                              
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid Release                                                                                                           
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid-updates Release                                                                                                   
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid/main Packages                                                                                                     
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid/restricted Packages                                                                                               
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid/main Sources                                                                                                      
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid/restricted Sources                                                                                                
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid/universe Packages                                                                                                 
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid/universe Sources                                                                                                  
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid/multiverse Packages                                                                                               
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid/multiverse Sources                                                                                                
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid-updates/main Packages                                                                                             
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid-updates/restricted Packages                                                                                       
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid-updates/main Sources                                                                                              
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid-updates/restricted Sources                                                                                        
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid-updates/universe Packages                                                                                         
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid-updates/universe Sources                                                                                          
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid-updates/multiverse Packages                                                                                       
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) intrepid-updates/multiverse Sources                                                                                        
Fetched 3520B in 9s (363B/s)                                                                                                                                
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 778978B00F7992B0

W: GPG error: [http://dl.google.com](http://dl.google.com) testing Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 632D16BB0C713DA6
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 43C0AFF0D7FAE680

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

W: GPG error: [http://apt.debianchile.org](http://apt.debianchile.org) unstable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2C392DFEEFD17969
W: Failed to fetch [http://packages.medibuntu.org/dists/intrepid/Release](http://packages.medibuntu.org/dists/intrepid/Release)  

W: Failed to fetch [http://wine.budgetdedicated.com/apt/dists/intrepid/Release](http://wine.budgetdedicated.com/apt/dists/intrepid/Release)  

W: Failed to fetch [http://ppa.launchpad.net/project-neon/ubuntu/dists/intrepid/Release](http://ppa.launchpad.net/project-neon/ubuntu/dists/intrepid/Release)  

W: Failed to fetch [http://ppa.launchpad.net/openoffice-pkgs/ubuntu/dists/intrepid/Release](http://ppa.launchpad.net/openoffice-pkgs/ubuntu/dists/intrepid/Release)  

W: Failed to fetch [http://ppa.launchpad.net/team-xbmc-intrepid/ubuntu/dists/intrepid/Release](http://ppa.launchpad.net/team-xbmc-intrepid/ubuntu/dists/intrepid/Release)  

W: Failed to fetch [http://ppa.launchpad.net/googlegadgets/ubuntu/dists/intrepid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/googlegadgets/ubuntu/dists/intrepid/main/binary-i386/Packages.gz)  404 Not Found

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems
[/FONT]

---

### Post by northern lights on 2009-04-28
You have a highly modified *sources.list* and some of the repositories it includes are either down or you're missing the GPG key to access them. Remove the *wine* repo and all the *ppas* (Launchpad personal package archives) and you should be able to update.

[EDIT]
I'd also highly recommend getting rid of the debian repositories.
You really shouldn't pull debian binaries with Ubuntu.
[/EDIT]

---

### Post by ranjith19 on 2009-04-28
> **northern lights said:**
> You have a highly modified *sources.list* and some of the repositories it includes are either down or you're missing the GPG key to access them. Remove the *wine* repo and all the *ppas* (Launchpad personal package archives) and you should be able to update.

[EDIT]
I'd also highly recommend getting rid of the debian repositories.
You really shouldn't pull debian binaries with Ubuntu.
[/EDIT]

Please post a copy of your /etc/apt/source.list if it is working

---

### Post by ranjith19 on 2009-04-28
> **northern lights said:**
> You have a highly modified *sources.list* and some of the repositories it includes are either down or you're missing the GPG key to access them. Remove the *wine* repo and all the *ppas* (Launchpad personal package archives) and you should be able to update.

[EDIT]
I'd also highly recommend getting rid of the debian repositories.
You really shouldn't pull debian binaries with Ubuntu.
[/EDIT]
Please post a copy of your /etc/apt/source.list if it is working

---

### Post by northern lights on 2009-04-28
Well, I see no reason for not posting mine and will do so since you requested it, but I think it'd be easier if you posted yours and you'd get it back modified and working.

Anyhow, here's mine (note that it's got German mirrors and is for jaunty):

```
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20081030)]/ jaunty main restricted

deb http://de.archive.ubuntu.com/ubuntu/ jaunty main restricted universe multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ jaunty main restricted universe multiverse

deb http://de.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted universe multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted universe multiverse

# deb http://de.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://de.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

deb http://archive.canonical.com/ubuntu jaunty partner
deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://security.ubuntu.com/ubuntu jaunty-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted universe multiverse

deb http://packages.medibuntu.org/ jaunty free non-free
deb-src http://packages.medibuntu.org/ jaunty free non-free

## intrepid for amarok 1.4
#deb http://de.archive.ubuntu.com/ubuntu intrepid main restricted universe multiverse
#deb http://security.ubuntu.com/ubuntu intrepid-security main restricted universe multiverse
```

---

### Post by ranjith19 on 2009-04-28
> **northern lights said:**
> Well, I see no reason for not posting mine and will do so since you requested it, but I think it'd be easier if you posted yours and you'd get it back modified and working.

I think I have problems because I have installed ubuntu ultimate edition 2.1 based on ubuntu 8.10([http://ultimateedition.info/ultimate-edition-21](http://ultimateedition.info/ultimate-edition-21))

Anyhow, here's mine (note that it's got German mirrors and is for jaunty):

```
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20081030)]/ jaunty main restricted

deb http://de.archive.ubuntu.com/ubuntu/ jaunty main restricted universe multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ jaunty main restricted universe multiverse

deb http://de.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted universe multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted universe multiverse

# deb http://de.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://de.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

deb http://archive.canonical.com/ubuntu jaunty partner
deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://security.ubuntu.com/ubuntu jaunty-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted universe multiverse

deb http://packages.medibuntu.org/ jaunty free non-free
deb-src http://packages.medibuntu.org/ jaunty free non-free

## intrepid for amarok 1.4
#deb http://de.archive.ubuntu.com/ubuntu intrepid main restricted universe multiverse
#deb http://security.ubuntu.com/ubuntu intrepid-security main restricted universe multiverse
```
Here is the main one. but there are other  in the folder /etc/apt/sources.list.d (it is a folder)





# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse

---

### Post by northern lights on 2009-04-28
> **ranjith19 said:**
> Here is the main one. but there are other  in the folder /etc/apt/sources.list.d (it is a folder)
All your non-working repos are in there, actually.

Make a backup and clear that entire folder. You really have a lot of deprecated / unnecessary crap in there.

---

### Post by ranjith19 on 2009-04-28
This is mine. I there are other files in an directory called /etc/apt/sources.list.d/ all with one line each

I think I screwed up because I have installed ubuntu ultimate edition 2.1 based on 8.10([http://ultimateedition.info/ultimate-edition-21](http://ultimateedition.info/ultimate-edition-21))
```

# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://in.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://in.archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://in.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://in.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://in.archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://in.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://in.archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://in.archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://in.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://in.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://in.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://in.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://in.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://in.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu intrepid partner
deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb http://security.ubuntu.com/ubuntu intrepid-security universe
deb-src http://security.ubuntu.com/ubuntu intrepid-security universe
deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse

```

---

### Post by northern lights on 2009-04-28
See my post above.

Your *sources.list* is fine. It's actually completely as oob. Simply backup */etc/apt/sources.list.d* and completely clear it's contents. Or post the content, and I'll tell what is relevant to be cleared.

---

### Post by ranjith19 on 2009-04-28
this is what I got
I think it is updated
thanks for your help


```
[FONT="Lucida Sans Unicode"]root@master:/home/ranjith# apt-get update
Hit http://archive.ubuntu.com intrepid Release.gpg
Ign http://archive.ubuntu.com intrepid/main Translation-en_IN
Ign http://archive.ubuntu.com intrepid/restricted Translation-en_IN
Ign http://archive.ubuntu.com intrepid/universe Translation-en_IN
Ign http://archive.ubuntu.com intrepid/multiverse Translation-en_IN
Hit http://archive.ubuntu.com intrepid-updates Release.gpg
Ign http://archive.ubuntu.com intrepid-updates/main Translation-en_IN
Ign http://archive.ubuntu.com intrepid-updates/restricted Translation-en_IN
Ign http://archive.ubuntu.com intrepid-updates/universe Translation-en_IN
Ign http://archive.ubuntu.com intrepid-updates/multiverse Translation-en_IN
Hit http://archive.ubuntu.com intrepid-security Release.gpg
Ign http://archive.ubuntu.com intrepid-security/main Translation-en_IN
Ign http://archive.ubuntu.com intrepid-security/restricted Translation-en_IN
Ign http://archive.ubuntu.com intrepid-security/universe Translation-en_IN
Ign http://archive.ubuntu.com intrepid-security/multiverse Translation-en_IN
Hit http://archive.ubuntu.com intrepid Release
Hit http://archive.ubuntu.com intrepid-updates Release
Hit http://archive.ubuntu.com intrepid-security Release
Hit http://archive.ubuntu.com intrepid/main Packages
Hit http://archive.ubuntu.com intrepid/restricted Packages
Hit http://archive.ubuntu.com intrepid/main Sources
Hit http://archive.ubuntu.com intrepid/restricted Sources
Hit http://archive.ubuntu.com intrepid/universe Packages
Hit http://archive.ubuntu.com intrepid/universe Sources
Hit http://archive.ubuntu.com intrepid/multiverse Packages
Hit http://archive.ubuntu.com intrepid/multiverse Sources
Hit http://archive.ubuntu.com intrepid-updates/main Packages
Hit http://archive.ubuntu.com intrepid-updates/restricted Packages
Hit http://archive.ubuntu.com intrepid-updates/main Sources
Hit http://archive.ubuntu.com intrepid-updates/restricted Sources
Hit http://archive.ubuntu.com intrepid-updates/universe Packages
Hit http://archive.ubuntu.com intrepid-updates/universe Sources
Hit http://archive.ubuntu.com intrepid-updates/multiverse Packages
Hit http://archive.ubuntu.com intrepid-updates/multiverse Sources
Hit http://archive.ubuntu.com intrepid-security/main Packages
Hit http://archive.ubuntu.com intrepid-security/restricted Packages
Hit http://archive.ubuntu.com intrepid-security/main Sources
Hit http://archive.ubuntu.com intrepid-security/restricted Sources
Hit http://archive.ubuntu.com intrepid-security/universe Packages
Hit http://archive.ubuntu.com intrepid-security/universe Sources
Hit http://archive.ubuntu.com intrepid-security/multiverse Packages
Hit http://archive.ubuntu.com intrepid-security/multiverse Sources
Reading package lists... Done[/FONT]

```

---

### Post by kpkeerthi on 2009-04-28
'sudo apt-get update' just syncs the package list. To update your packages, you should do
```
sudo apt-get upgrade
```

* Always run upgrade after update:
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by ranjith19 on 2009-04-28
thanks 
I did it
It is working
I am able to update and upgarde

UBUNTU ROCKS!

---

### Post by northern lights on 2009-04-28
> **ranjith19 said:**
> 
UBUNTU ROCKS!
Cheers to that.

You can mark your thred as 'solved' in the *Thread Tools* menu.

---

