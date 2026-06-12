---
title: "I do not foun gpg for repository"
date: 2009-02-28
forum: General Help
---

### Post by El Rengo on 2009-02-28
It is my source.lst:

```
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://archive.ubuntu.com/ubuntu/ intrepid universe
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ar.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://ar.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu intrepid partner
# deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://archive.ubuntu.com/ubuntu/ intrepid-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-security main restricted
deb http://archive.ubuntu.com/ubuntu/ intrepid-security universe
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-security universe
deb http://archive.ubuntu.com/ubuntu/ intrepid-security multiverse
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-security multiverse
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
deb http://ppa.launchpad.net/reacocard-awn/ubuntu intrepid main
```

I have the following error when I execute aptitude update:

```
Writing extended state information... Done
Hit http://packages.medibuntu.org intrepid Release.gpg
Ign http://packages.medibuntu.org intrepid/free Translation-en_US                                                                                            
Hit http://archive.canonical.com intrepid Release.gpg                                                                                                        
Ign http://archive.canonical.com intrepid/partner Translation-en_US                                                                                          
Get:1 http://ppa.launchpad.net intrepid Release.gpg [307B]                                                                    
Ign http://ppa.launchpad.net intrepid/main Translation-en_US                                            
Ign http://packages.medibuntu.org intrepid/non-free Translation-en_US                                                         
Hit http://packages.medibuntu.org intrepid Release                                                                            
Get:2 http://wine.budgetdedicated.com intrepid Release.gpg [191B]                                                             
Ign http://wine.budgetdedicated.com intrepid/main Translation-en_US                                                          
Hit http://archive.canonical.com intrepid Release                                                                            
Ign http://ppa.launchpad.net intrepid Release.gpg                                                                           
Ign http://ppa.launchpad.net intrepid/main Translation-en_US                                            
Get:3 http://ppa.launchpad.net intrepid Release [27.6kB]                                                
Ign http://ppa.launchpad.net intrepid Release                                                                                        
Hit http://packages.medibuntu.org intrepid/free Packages                                                                       
Get:4 http://wine.budgetdedicated.com intrepid Release [1025B]                                                                
Ign http://wine.budgetdedicated.com intrepid Release                                                                               
Hit http://archive.canonical.com intrepid/partner Packages                                                                    
Get:5 http://ppa.launchpad.net intrepid Release [27.6kB]                                                
Hit http://packages.medibuntu.org intrepid/non-free Packages                                                   
Ign http://wine.budgetdedicated.com intrepid/main Packages                        
Ign http://ppa.launchpad.net intrepid/main Packages                               
Hit http://wine.budgetdedicated.com intrepid/main Packages  
Ign http://ppa.launchpad.net intrepid/main Packages         
Hit http://ppa.launchpad.net intrepid/main Packages         
Hit http://ppa.launchpad.net intrepid/main Packages
Hit http://archive.ubuntu.com intrepid Release.gpg   
Ign http://archive.ubuntu.com intrepid/main Translation-en_US
Ign http://archive.ubuntu.com intrepid/restricted Translation-en_US
Ign http://archive.ubuntu.com intrepid/universe Translation-en_US
Ign http://archive.ubuntu.com intrepid/multiverse Translation-en_US
Hit http://archive.ubuntu.com intrepid-updates Release.gpg
Ign http://archive.ubuntu.com intrepid-updates/main Translation-en_US
Ign http://archive.ubuntu.com intrepid-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com intrepid-updates/universe Translation-en_US
Ign http://archive.ubuntu.com intrepid-updates/multiverse Translation-en_US
Hit http://archive.ubuntu.com intrepid-security Release.gpg
Ign http://archive.ubuntu.com intrepid-security/main Translation-en_US
Ign http://archive.ubuntu.com intrepid-security/restricted Translation-en_US
Ign http://archive.ubuntu.com intrepid-security/universe Translation-en_US                                                                                   
Ign http://archive.ubuntu.com intrepid-security/multiverse Translation-en_US                                                                                 
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
Fetched 501B in 7s (63B/s)                                                                                                                                   
Reading package lists... Done             
W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF
W: GPG error: http://wine.budgetdedicated.com intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
W: You may want to run apt-get update to correct these problems

```

I try to download from ubuntuservers using the key: 60D11217247D1CFF and 58403026387EE263 but not found them! :S
How I can disable this error?
Thanks!

---

### Post by Therion on 2009-02-28
See this thread:  [http://ubuntuforums.org/showthread.php?t=1056099](http://ubuntuforums.org/showthread.php?t=1056099)

---

### Post by sisco311 on 2009-02-28
[thread]1056099[/thread]

EDIT: d'oh, i'm slow.

---

### Post by El Rengo on 2009-02-28
Thanks all!!! The Lounchpad GPG is solved!! :D
I try searching the wine gpg :S

---

### Post by plucky on 2009-03-01
> I try searching the wine gpg

Try this ```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
``` to add the Wine gpg


Good Luck

---

