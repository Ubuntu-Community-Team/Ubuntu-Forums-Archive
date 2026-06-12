---
title: "software center trouble"
date: 2011-06-29
forum: Desktop Environments
---

### Post by powerage on 2011-06-29
hi.  I just installed ubuntu 11.04 and am experiencing problems loading applications in the software center.  I select a department to see what's available and nothing comes up, it just keeps loading.  Any suggestions would be greatly appreciated.

---

### Post by budugu on 2011-06-29
Hi,

I am new to ubuntu and using 11.04. I am facing problems with software download center. I am giving as much details as possible.

**sudo apt-get update**

Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease                                                                                                              
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg                                                                                                            
  Unable to connect to extras.ubuntu.com:http:
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release                                                               
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main TranslationIndex                                                  
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Sources                                                           
  Unable to connect to extras.ubuntu.com:http:
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main i386 Packages                                                     
  Unable to connect to extras.ubuntu.com:http:
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en_US                                                 
  Unable to connect to extras.ubuntu.com:http:
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en                                                    
  Unable to connect to extras.ubuntu.com:http:
Err [http://archive.canonical.com](http://archive.canonical.com) natty InRelease                                                          
  
Err [http://archive.canonical.com](http://archive.canonical.com) natty Release.gpg                                                        
  Unable to connect to archive.canonical.com:http:
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) natty InRelease         
  
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates InRelease
  
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security InRelease
  
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) natty Release.gpg
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.30 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates Release.gpg
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.30 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security Release.gpg
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.30 80]
Reading package lists... Done
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/natty/InRelease](http://archive.ubuntu.com/ubuntu/dists/natty/InRelease)  

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/natty-updates/InRelease](http://archive.ubuntu.com/ubuntu/dists/natty-updates/InRelease)  

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/natty-security/InRelease](http://archive.ubuntu.com/ubuntu/dists/natty-security/InRelease)  

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/natty/InRelease](http://archive.canonical.com/ubuntu/dists/natty/InRelease)  

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/natty/Release.gpg](http://extras.ubuntu.com/ubuntu/dists/natty/Release.gpg)  Unable to connect to extras.ubuntu.com:http:

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/natty/main/source/Sources](http://extras.ubuntu.com/ubuntu/dists/natty/main/source/Sources)  Unable to connect to extras.ubuntu.com:http:

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/natty/main/binary-i386/Packages](http://extras.ubuntu.com/ubuntu/dists/natty/main/binary-i386/Packages)  Unable to connect to extras.ubuntu.com:http:

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/natty/main/i18n/Translation-en_US](http://extras.ubuntu.com/ubuntu/dists/natty/main/i18n/Translation-en_US)  Unable to connect to extras.ubuntu.com:http:

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/natty/main/i18n/Translation-en](http://extras.ubuntu.com/ubuntu/dists/natty/main/i18n/Translation-en)  Unable to connect to extras.ubuntu.com:http:

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/natty/Release.gpg](http://archive.canonical.com/ubuntu/dists/natty/Release.gpg)  Unable to connect to archive.canonical.com:http:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/natty/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/natty/Release.gpg)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.30 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/natty-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/natty-updates/Release.gpg)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.30 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/natty-security/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/natty-security/Release.gpg)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.30 80]

W: Some index files failed to download. They have been ignored, or old ones used instead.

sources.list
# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)]/ natty main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-updates universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-security universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
# deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main

I have tried modifying the server to main server. But no use. i am able to connect to internet. 

please provide what can be done??

---

### Post by powerage on 2011-06-29
Budugu,

Go to "Launchpad" and pose questions there.  You should get immediate feedback.  I did and my problems with the software center were rectified promptly. :p

I hope this helps,

powerage

---

