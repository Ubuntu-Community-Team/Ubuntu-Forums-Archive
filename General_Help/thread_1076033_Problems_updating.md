---
title: "Problems updating"
date: 2009-02-20
forum: General Help
---

### Post by ice2921 on 2009-02-20
My initial problem began when having problems installing open office 3.0 One I tried to update I noticed that there were a lot of errors when running:
```
sudo apt-get update
```

I get the following:

```
Get:1 http://ppa.launchpad.net hardy Release.gpg [307B]
Ign http://ppa.launchpad.net hardy/main Translation-en_US                             
Hit http://us.archive.ubuntu.com intrepid Release.gpg                                 
Ign http://us.archive.ubuntu.com intrepid/main Translation-en_US                      
Hit http://archive.canonical.com intrepid Release.gpg                                 
Ign http://archive.canonical.com intrepid/partner Translation-en_US                   
Get:2 http://packages.medibuntu.org intrepid Release.gpg [197B]                       
Ign http://packages.medibuntu.org intrepid/free Translation-en_US                     
Hit http://ppa.launchpad.net intrepid Release.gpg                                     
Ign http://ppa.launchpad.net intrepid/main Translation-en_US                          
Get:3 http://ppa.launchpad.net hardy Release [27.6kB]                                 
Ign http://us.archive.ubuntu.com intrepid/restricted Translation-en_US                
Ign http://us.archive.ubuntu.com intrepid/universe Translation-en_US                  
Ign http://us.archive.ubuntu.com intrepid/multiverse Translation-en_US                
Hit http://us.archive.ubuntu.com intrepid-updates Release.gpg                         
Ign http://us.archive.ubuntu.com intrepid-updates/main Translation-en_US              
Ign http://us.archive.ubuntu.com intrepid-updates/restricted Translation-en_US        
Ign http://us.archive.ubuntu.com intrepid-updates/universe Translation-en_US          
Ign http://us.archive.ubuntu.com intrepid-updates/multiverse Translation-en_US        
Hit http://us.archive.ubuntu.com hardy-backports Release.gpg                          
Hit http://archive.canonical.com intrepid Release                                     
Hit http://apt.wicd.net hardy Release.gpg                                             
Ign http://apt.wicd.net hardy/extras Translation-en_US                                
Hit http://wine.budgetdedicated.com edgy Release.gpg                                  
Ign http://wine.budgetdedicated.com edgy/main Translation-en_US                       
Ign http://packages.medibuntu.org intrepid/non-free Translation-en_US                 
Get:4 http://packages.medibuntu.org intrepid Release [11.7kB]                         
Ign http://us.archive.ubuntu.com hardy-backports/main Translation-en_US               
Ign http://ppa.launchpad.net hardy Release                                            
Hit http://ppa.launchpad.net intrepid Release                                         
Ign http://us.archive.ubuntu.com hardy-backports/restricted Translation-en_US         
Ign http://us.archive.ubuntu.com hardy-backports/universe Translation-en_US           
Ign http://us.archive.ubuntu.com hardy-backports/multiverse Translation-en_US         
Ign http://us.archive.ubuntu.com edgy Release.gpg                                     
Hit http://apt.wicd.net hardy Release                                                 
Hit http://wine.budgetdedicated.com edgy Release                                      
Hit http://archive.canonical.com intrepid/partner Packages                            
Ign http://ppa.launchpad.net hardy/main Packages                                      
Ign http://us.archive.ubuntu.com edgy/universe Translation-en_US                      
Hit http://us.archive.ubuntu.com intrepid Release                                     
Hit http://us.archive.ubuntu.com intrepid-updates Release                             
Hit http://us.archive.ubuntu.com hardy-backports Release                              
Hit http://archive.canonical.com intrepid/partner Sources                             
Ign http://packages.medibuntu.org intrepid Release                                    
Ign http://ppa.launchpad.net intrepid/main Packages                                   
Ign http://wine.budgetdedicated.com edgy/main Packages                                
Ign http://us.archive.ubuntu.com edgy Release                                         
Hit http://us.archive.ubuntu.com intrepid/main Packages                               
Hit http://us.archive.ubuntu.com intrepid/restricted Packages                         
Hit http://us.archive.ubuntu.com intrepid/main Sources                                
Hit http://us.archive.ubuntu.com intrepid/restricted Sources                          
Hit http://us.archive.ubuntu.com intrepid/universe Packages                           
Ign http://apt.wicd.net hardy/extras Packages                                         
Hit http://ppa.launchpad.net hardy/main Packages                                      
Hit http://packages.medibuntu.org intrepid/free Packages                              
Hit http://wine.budgetdedicated.com edgy/main Packages                                
Hit http://us.archive.ubuntu.com intrepid/universe Sources                            
Hit http://us.archive.ubuntu.com intrepid/multiverse Packages                         
Hit http://us.archive.ubuntu.com intrepid/multiverse Sources                          
Hit http://us.archive.ubuntu.com intrepid-updates/main Packages                       
Hit http://us.archive.ubuntu.com intrepid-updates/restricted Packages                 
Hit http://us.archive.ubuntu.com intrepid-updates/main Sources                        
Hit http://us.archive.ubuntu.com intrepid-updates/restricted Sources                  
Hit http://ppa.launchpad.net intrepid/main Packages                                   
Hit http://us.archive.ubuntu.com intrepid-updates/universe Packages                   
Hit http://us.archive.ubuntu.com intrepid-updates/universe Sources                    
Hit http://packages.medibuntu.org intrepid/non-free Packages                          
Hit http://packages.medibuntu.org intrepid/free Sources                               
Hit http://packages.medibuntu.org intrepid/non-free Sources                           
Hit http://apt.wicd.net hardy/extras Packages                                         
Hit http://us.archive.ubuntu.com intrepid-updates/multiverse Packages                 
Hit http://us.archive.ubuntu.com intrepid-updates/multiverse Sources                  
Hit http://us.archive.ubuntu.com hardy-backports/main Packages                        
Hit http://us.archive.ubuntu.com hardy-backports/restricted Packages                  
Hit http://us.archive.ubuntu.com hardy-backports/universe Packages                    
Hit http://us.archive.ubuntu.com hardy-backports/multiverse Packages                  
Hit http://us.archive.ubuntu.com hardy-backports/main Sources                         
Hit http://us.archive.ubuntu.com hardy-backports/restricted Sources                   
Hit http://us.archive.ubuntu.com hardy-backports/universe Sources                     
Hit http://us.archive.ubuntu.com hardy-backports/multiverse Sources                   
Ign http://us.archive.ubuntu.com edgy/universe Packages                               
Err http://us.archive.ubuntu.com edgy/universe Packages                               
  404 Not Found [IP: 91.189.88.45 80]                                                 
Err http://security.ubuntu.com intrepid-security Release.gpg                          
  Could not connect to security.ubuntu.com:80 (91.189.88.37), connection timed out    
Err http://security.ubuntu.com intrepid-security/main Translation-en_US               
  Unable to connect to security.ubuntu.com http:                                      
Err http://security.ubuntu.com intrepid-security/restricted Translation-en_US         
  Unable to connect to security.ubuntu.com http:
Err http://security.ubuntu.com intrepid-security/universe Translation-en_US
  Unable to connect to security.ubuntu.com http:
Err http://security.ubuntu.com intrepid-security/multiverse Translation-en_US
  Unable to connect to security.ubuntu.com http:
Fetched 12.2kB in 2min0s (102B/s)
Reading package lists... Done
W: GPG error: http://ppa.launchpad.net hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF
W: GPG error: http://packages.medibuntu.org intrepid Release: The following signaturescouldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/intrepid-security/Release.gpg  Could not connect to security.ubuntu.com:80 (91.189.88.37), connection timed out

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/i18n/Translation-en_US.bz2  Unable to connect to security.ubuntu.com http:

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/i18n/Translation-en_US.bz2  Unable to connect to security.ubuntu.com http:

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/i18n/Translation-en_US.bz2  Unable to connect to security.ubuntu.com http:

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/i18n/Translation-en_US.bz2  Unable to connect to security.ubuntu.com http:

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.45 80]

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems
```

I am sure that there are some repositories here that I do not need, but I am not sure which ones I can get rid of safely. So I am hoping that maybe if I had my repositories in order I would have a better chance of installing Open Office. Hope this makes sense.Any help is appreciated.

---

### Post by Yellow Pasque on 2009-02-20
Please post your /etc/apt/sources.list file.

---

### Post by taurus on 2009-02-20
The reason you have all kind of problems is because you have edgy and intrepid repos mixing with hardy, assuming you are really running hardy!  That is one way to screw up your system big time.  So, you need to edit your /etc/apt/sources.list and remove all the repos that have **edgy** and **intrepid** in there.

---

### Post by ice2921 on 2009-02-20
Thanks for the responses here is the output from /etc/apt/sources.list

```

cat /etc/issue                                                         
Ubuntu 8.10 \n \l 
```           


```
# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted                                                                                  
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to              
# newer versions of the distribution.                                                  

deb http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.                                                
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in     
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.                                                                   
deb http://us.archive.ubuntu.com/ubuntu/ intrepid universe                 
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid universe             
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe         
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe     

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in      
## multiverse WILL NOT receive any review or updates from the Ubuntu        
## security team.                                                           
deb http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse                
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse            
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse        
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse    

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

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
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu hardy main
deb http://apt.wicd.net hardy extras
deb http://ppa.launchpad.net/kubuntu-experimental/ubuntu intrepid main
deb http://us.archive.ubuntu.com/ubuntu edgy universe
deb http://wine.budgetdedicated.com/apt edgy main

```

---

### Post by taurus on 2009-02-20
> **ice2921 said:**
> Thanks for the responses here is the output from /etc/apt/sources.list

```

cat /etc/issue                                                         
Ubuntu 8.10 \n \l 
```           


```
# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted                                                                                  
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to              
# newer versions of the distribution.                                                  

deb http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.                                                
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in     
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.                                                                   
deb http://us.archive.ubuntu.com/ubuntu/ intrepid universe                 
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid universe             
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe         
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe     

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in      
## multiverse WILL NOT receive any review or updates from the Ubuntu        
## security team.                                                           
deb http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse                
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse            
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse        
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse    

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
[B][COLOR="Red"]deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse[/COLOR][/B]

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
[B][COLOR="Red"]deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu hardy main
deb http://apt.wicd.net hardy extras[/COLOR][/B]
deb http://ppa.launchpad.net/kubuntu-experimental/ubuntu intrepid main
[B][COLOR="Red"]deb http://us.archive.ubuntu.com/ubuntu edgy universe
deb http://wine.budgetdedicated.com/apt edgy main[/COLOR][/B]

```

Edit /etc/apt/sources.list and remove all the lines in red.  Then, save it and run

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by ice2921 on 2009-02-20
Thanks taurus! Here are the results after updating:

```
~$ sudo apt-get update
Hit http://archive.canonical.com intrepid Release.gpg
Ign http://archive.canonical.com intrepid/partner Translation-en_US                   
Hit http://ppa.launchpad.net intrepid Release.gpg                                     
Ign http://ppa.launchpad.net intrepid/main Translation-en_US                          
Hit http://us.archive.ubuntu.com intrepid Release.gpg                                 
Ign http://us.archive.ubuntu.com intrepid/main Translation-en_US                      
Get:1 http://packages.medibuntu.org intrepid Release.gpg [197B]                       
Ign http://packages.medibuntu.org intrepid/free Translation-en_US                     
Hit http://security.ubuntu.com intrepid-security Release.gpg                          
Ign http://security.ubuntu.com intrepid-security/main Translation-en_US               
Ign http://security.ubuntu.com intrepid-security/restricted Translation-en_US         
Hit http://archive.canonical.com intrepid Release                                     
Hit http://ppa.launchpad.net intrepid Release                                         
Ign http://packages.medibuntu.org intrepid/non-free Translation-en_US                 
Get:2 http://packages.medibuntu.org intrepid Release [11.7kB]                         
Ign http://us.archive.ubuntu.com intrepid/restricted Translation-en_US                
Ign http://us.archive.ubuntu.com intrepid/universe Translation-en_US                  
Ign http://us.archive.ubuntu.com intrepid/multiverse Translation-en_US                
Hit http://us.archive.ubuntu.com intrepid-updates Release.gpg                         
Ign http://us.archive.ubuntu.com intrepid-updates/main Translation-en_US              
Ign http://us.archive.ubuntu.com intrepid-updates/restricted Translation-en_US        
Ign http://us.archive.ubuntu.com intrepid-updates/universe Translation-en_US          
Ign http://us.archive.ubuntu.com intrepid-updates/multiverse Translation-en_US        
Ign http://security.ubuntu.com intrepid-security/universe Translation-en_US           
Ign http://security.ubuntu.com intrepid-security/multiverse Translation-en_US         
Hit http://security.ubuntu.com intrepid-security Release                              
Hit http://us.archive.ubuntu.com intrepid Release                                     
Ign http://packages.medibuntu.org intrepid Release                                    
Hit http://archive.canonical.com intrepid/partner Packages                            
Ign http://ppa.launchpad.net intrepid/main Packages                                   
Hit http://us.archive.ubuntu.com intrepid-updates Release                             
Hit http://packages.medibuntu.org intrepid/free Packages                              
Hit http://archive.canonical.com intrepid/partner Sources                             
Hit http://security.ubuntu.com intrepid-security/main Packages                        
Hit http://ppa.launchpad.net intrepid/main Packages
Hit http://us.archive.ubuntu.com intrepid/main Packages
Hit http://us.archive.ubuntu.com intrepid/restricted Packages
Hit http://us.archive.ubuntu.com intrepid/main Sources
Hit http://us.archive.ubuntu.com intrepid/restricted Sources
Hit http://us.archive.ubuntu.com intrepid/universe Packages
Hit http://packages.medibuntu.org intrepid/non-free Packages
Hit http://packages.medibuntu.org intrepid/free Sources
Hit http://packages.medibuntu.org intrepid/non-free Sources
Hit http://security.ubuntu.com intrepid-security/restricted Packages
Hit http://security.ubuntu.com intrepid-security/main Sources
Hit http://security.ubuntu.com intrepid-security/restricted Sources
Hit http://security.ubuntu.com intrepid-security/universe Packages
Hit http://us.archive.ubuntu.com intrepid/universe Sources
Hit http://us.archive.ubuntu.com intrepid/multiverse Packages
Hit http://us.archive.ubuntu.com intrepid/multiverse Sources
Hit http://us.archive.ubuntu.com intrepid-updates/main Packages
Hit http://us.archive.ubuntu.com intrepid-updates/restricted Packages
Hit http://us.archive.ubuntu.com intrepid-updates/main Sources
Hit http://us.archive.ubuntu.com intrepid-updates/restricted Sources
Hit http://security.ubuntu.com intrepid-security/universe Sources
Hit http://security.ubuntu.com intrepid-security/multiverse Packages
Hit http://security.ubuntu.com intrepid-security/multiverse Sources
Hit http://us.archive.ubuntu.com intrepid-updates/universe Packages
Hit http://us.archive.ubuntu.com intrepid-updates/universe Sources
Hit http://us.archive.ubuntu.com intrepid-updates/multiverse Packages
Hit http://us.archive.ubuntu.com intrepid-updates/multiverse Sources
Fetched 198B in 0s (229B/s)
Reading package lists... Done
W: GPG error: http://packages.medibuntu.org intrepid Release: The following signaturescouldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems
```

Im not sure about the last one..

---

### Post by ice2921 on 2009-02-20
Ok look like i solved the last issue with importing the key again with:
```

wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

Now I just need to install Open Office properly. Any suggestions? Thanks again for your help.

---

### Post by Yellow Pasque on 2009-02-21
Since you're using Intrepid, make sure any 3rd-party repo you add doesn't say "hardy" or some other release of Ubuntu. The guide you followed to add the OpenOffice 3.0 PPA repo is either outdated or you copied the wrong line. You would want to use this for your repo line:
```
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu **intrepid** main
```

---

### Post by MossMethod on 2011-07-23
> **taurus said:**
> The reason you have all kind of problems is because you have edgy and intrepid repos mixing with hardy, assuming you are really running hardy!  That is one way to screw up your system big time.  So, you need to edit your /etc/apt/sources.list and remove all the repos that have **edgy** and **intrepid** in there.

hey thanks I did this (I could not find any that had intrepid, at least I think, LoL i am new) and sure enough I did not get an error when downloading some cruical stuff from this place. [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)    .... Cheers:popcorn: If I knew how to give rep I would~

except now I get some other weird thing that says this- 
Virtual packages like 'icedtea-gcjwebplugin' can't be removed
Virtual packages like 'libflashsupport' can't be removed
E: Unable to locate package libflash-mozplugin

after typing in this code

---

