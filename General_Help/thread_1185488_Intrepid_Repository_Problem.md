---
title: "Intrepid Repository Problem"
date: 2009-06-12
forum: General Help
---

### Post by FoxIII on 2009-06-12
I have been hunting around for a solution and haven't found anything yet. I have found threads and google results similar, but nothing specific - and they all seem to be problems with jaunty rather than inrepid.

When I run

```
sudo apt-get update
```

I get the output:

```
Hit http://security.ubuntu.com intrepid-security Release.gpg            
Ign http://security.ubuntu.com intrepid-security/main Translation-en_GB 
Hit http://gb.archive.ubuntu.com intrepid Release.gpg                   
Hit http://gb.archive.ubuntu.com intrepid/main Translation-en_GB        
Ign http://security.ubuntu.com intrepid-security/restricted Translation-en_GB
Ign http://security.ubuntu.com intrepid-security/universe Translation-en_GB  
Ign http://security.ubuntu.com intrepid-security/multiverse Translation-en_GB
Hit http://security.ubuntu.com intrepid-security Release                     
Hit http://gb.archive.ubuntu.com intrepid/restricted Translation-en_GB       
Hit http://gb.archive.ubuntu.com intrepid/universe Translation-en_GB         
Hit http://gb.archive.ubuntu.com intrepid/multiverse Translation-en_GB       
Hit http://gb.archive.ubuntu.com intrepid-updates Release.gpg                
Hit http://gb.archive.ubuntu.com intrepid-updates/main Translation-en_GB     
Hit http://gb.archive.ubuntu.com intrepid-updates/restricted Translation-en_GB
Hit http://gb.archive.ubuntu.com intrepid-updates/universe Translation-en_GB  
Hit http://gb.archive.ubuntu.com intrepid-updates/multiverse Translation-en_GB
Hit http://gb.archive.ubuntu.com intrepid-backports Release.gpg               
Ign http://gb.archive.ubuntu.com intrepid-backports/main Translation-en_GB    
Ign http://gb.archive.ubuntu.com intrepid-backports/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com intrepid-backports/universe Translation-en_GB  
Ign http://gb.archive.ubuntu.com intrepid-backports/multiverse Translation-en_GB
Hit http://gb.archive.ubuntu.com intrepid Release                               
Hit http://gb.archive.ubuntu.com intrepid-updates Release                       
Hit http://security.ubuntu.com intrepid-security/main Packages                  
Hit http://gb.archive.ubuntu.com intrepid-backports Release                     
Hit http://security.ubuntu.com intrepid-security/restricted Packages            
Hit http://security.ubuntu.com intrepid-security/main Sources                   
Hit http://security.ubuntu.com intrepid-security/restricted Sources             
Hit http://security.ubuntu.com intrepid-security/universe Packages              
Hit http://gb.archive.ubuntu.com intrepid/main Packages                         
Hit http://gb.archive.ubuntu.com intrepid/restricted Packages                   
Hit http://gb.archive.ubuntu.com intrepid/main Sources                          
Hit http://gb.archive.ubuntu.com intrepid/restricted Sources                    
Hit http://gb.archive.ubuntu.com intrepid/universe Packages                     
Hit http://gb.archive.ubuntu.com intrepid/universe Sources                      
Hit http://security.ubuntu.com intrepid-security/universe Sources               
Hit http://security.ubuntu.com intrepid-security/multiverse Packages
Hit http://security.ubuntu.com intrepid-security/multiverse Sources
Hit http://gb.archive.ubuntu.com intrepid/multiverse Packages
Hit http://gb.archive.ubuntu.com intrepid/multiverse Sources
Hit http://gb.archive.ubuntu.com intrepid-updates/main Packages
Hit http://gb.archive.ubuntu.com intrepid-updates/restricted Packages
Hit http://gb.archive.ubuntu.com intrepid-updates/main Sources
Hit http://gb.archive.ubuntu.com intrepid-updates/restricted Sources
Hit http://gb.archive.ubuntu.com intrepid-updates/universe Packages
Hit http://gb.archive.ubuntu.com intrepid-updates/universe Sources
Hit http://gb.archive.ubuntu.com intrepid-updates/multiverse Packages
Hit http://gb.archive.ubuntu.com intrepid-updates/multiverse Sources
Hit http://gb.archive.ubuntu.com intrepid-backports/main Packages
Hit http://gb.archive.ubuntu.com intrepid-backports/restricted Packages
Hit http://gb.archive.ubuntu.com intrepid-backports/universe Packages
Hit http://gb.archive.ubuntu.com intrepid-backports/multiverse Packages
Hit http://gb.archive.ubuntu.com intrepid-backports/main Sources
Hit http://gb.archive.ubuntu.com intrepid-backports/restricted Sources
Hit http://gb.archive.ubuntu.com intrepid-backports/universe Sources
Hit http://gb.archive.ubuntu.com intrepid-backports/multiverse Sources
Reading package lists... Done

```

as can be seen, it is ignoring a few of the repositories and I can't figure out why.

My sources.list is:

```
# deb cdrom:[Kubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.1)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://gb.archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu intrepid partner
# deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb http://security.ubuntu.com/ubuntu intrepid-security universe
deb-src http://security.ubuntu.com/ubuntu intrepid-security universe
deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse

```

Any help greatly appreciated.

---

