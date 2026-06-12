---
title: "having problems with KDE"
date: 2011-08-06
forum: Desktop Environments
---

### Post by davidcafu412 on 2011-08-06
hi guys, i recently installed kde plasma desktop environment, then i uninstalled it without realising i uninstalled something abt kde runtime, so i tried installing K3b, it says, i need kde runtime, but this is wat i get when i try to install kde runtime :


kdebase-runtime:
 Depends: libkdesu5 but it is not going to be installed
 Depends: libkhtml5 but it is not going to be installed
 Depends: libkmediaplayer4 but it is not going to be installed
 Depends: libknotifyconfig4 but it is not going to be installed
 Depends: kdelibs5-plugins but it is not going to be installed
  Depends: [COLOR="Lime"]plasma-scriptengine-javascript (=4:4.5.5-0ubuntu2) but 4:4.6.2-0ubuntu1~maverick1~ppa1[/COLOR] is to be installed
 Recommends: kubuntu-debug-installer but it is not going to be installed

plz help me, and i dunt understand the words in "lime color", what is that ?

---

### Post by oldos2er on 2011-08-06
It's complaining that the version of the package plasma-scriptengine-javascript differs between what kdebase-runtime is expecting (=4:4.5.5-0ubuntu2), compared with the version that's going to be installed (4:4.6.2-0ubuntu1~maverick1~ppa1).

If you disable any KDE-specific PPAs, run **sudo apt-get update**, try installing k3b again, it should work. If not, please post all the terminal output here.

---

### Post by davidcafu412 on 2011-08-07
hi...here is the output of da terminal :

davidcafu@Davidcafu:~$ sudo apt-get update
[sudo] password for davidcafu: 
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) maverick Release.gpg
Ign [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) maverick/main Translation-en          
Ign [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_US       
Ign [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en    
Ign [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_US 
Ign [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en    
Ign [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_US 
Ign [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en      
Ign [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_US   
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) maverick-updates Release.gpg                  
Ign [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en  
Ign [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_US
Ign [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Ign [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_US
Ign [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_US
Ign [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Ign [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_US
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) maverick Release                              
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) maverick-updates Release                      
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198B]                           
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) maverick/main Sources                         
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) maverick/restricted Sources                   
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) maverick/universe Sources                     
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) maverick/multiverse Sources                   
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) maverick/main i386 Packages                   
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) maverick/restricted i386 Packages             
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) maverick/universe i386 Packages               
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) maverick/multiverse i386 Packages             
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) maverick-updates/main Sources                 
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) maverick-updates/restricted Sources           
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) maverick-updates/universe Sources             
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) maverick-updates/multiverse Sources           
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) maverick-updates/main i386 Packages           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
Ign [http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/](http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/](http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/) maverick/main Translation-en_US
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) maverick-updates/restricted i386 Packages     
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) maverick-updates/universe i386 Packages       
Hit [http://my.archive.ubuntu.com](http://my.archive.ubuntu.com) maverick-updates/multiverse i386 Packages     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg                              
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en              
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_US           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg                   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
Ign [http://ppa.launchpad.net/bisigi/dev/ubuntu/](http://ppa.launchpad.net/bisigi/dev/ubuntu/) maverick/main Translation-en   
Ign [http://ppa.launchpad.net/bisigi/dev/ubuntu/](http://ppa.launchpad.net/bisigi/dev/ubuntu/) maverick/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
Ign [http://ppa.launchpad.net/ilap/lwp/ubuntu/](http://ppa.launchpad.net/ilap/lwp/ubuntu/) maverick/main Translation-en     
Ign [http://ppa.launchpad.net/ilap/lwp/ubuntu/](http://ppa.launchpad.net/ilap/lwp/ubuntu/) maverick/main Translation-en_US  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
Ign [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/) maverick/main Translation-en
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release                                  
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release                       
Ign [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/) maverick/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) maverick/main Translation-en_US
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg [316B]                     
Ign [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/) maverick/main Translation-en_US
Hit [http://archive.getdeb.net](http://archive.getdeb.net) maverick-getdeb Release.gpg                      
Ign [http://archive.getdeb.net/ubuntu/](http://archive.getdeb.net/ubuntu/) maverick-getdeb/apps Translation-en      
Ign [http://archive.getdeb.net/ubuntu/](http://archive.getdeb.net/ubuntu/) maverick-getdeb/apps Translation-en_US   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources                  
Ign [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main Translation-en          
Ign [http://archive.getdeb.net/ubuntu/](http://archive.getdeb.net/ubuntu/) maverick-getdeb/games Translation-en     
Ign [http://archive.getdeb.net/ubuntu/](http://archive.getdeb.net/ubuntu/) maverick-getdeb/games Translation-en_US  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release [9,753B]                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main i386 Packages            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe i386 Packages        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse i386 Packages      
Ign [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main Translation-en_US       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources/DiffIndex                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages/DiffIndex             
Get:4 [http://dl.google.com](http://dl.google.com) stable Release [1,347B]                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages                       
Get:5 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [1,195B]                  
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick Release.gpg                         
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg                          
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en       
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en_US    
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release                              
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick/free Translation-en                
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Sources                      
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick/free Translation-en_US             
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages                
Hit [http://archive.getdeb.net](http://archive.getdeb.net) maverick-getdeb Release                          
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick/non-free Translation-en            
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick/non-free Translation-en_US         
Hit [http://archive.getdeb.net](http://archive.getdeb.net) maverick-getdeb/apps Sources                     
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick Release                             
Hit [http://linux.dropbox.com](http://linux.dropbox.com) maverick Release.gpg                              
Ign [http://linux.dropbox.com/ubuntu/](http://linux.dropbox.com/ubuntu/) maverick/main Translation-en              
Ign [http://linux.dropbox.com/ubuntu/](http://linux.dropbox.com/ubuntu/) maverick/main Translation-en_US           
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/free Sources                        
Hit [http://linux.dropbox.com](http://linux.dropbox.com) maverick Release                                  
Hit [http://linux.dropbox.com](http://linux.dropbox.com) maverick/main i386 Packages                       
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/non-free Sources                    
Hit [http://archive.getdeb.net](http://archive.getdeb.net) maverick-getdeb/apps i386 Packages               
Hit [http://archive.getdeb.net](http://archive.getdeb.net) maverick-getdeb/games i386 Packages              
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/free i386 Packages                  
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/non-free i386 Packages              
Fetched 3,057B in 14s (208B/s)                                                 
Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9A06AEF9CB8DB0
[COLOR="Blue"]davidcafu@Davidcafu:~$ sudo apt-get install k3b
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 k3b : Depends: kdebase-runtime but it is not going to be installed
       Depends: libk3b6 (= 2.0.1-1ubuntu3) but 2.0.1-1ubuntu5~maverick1~ppa1 is to be installed
       Depends: libknotifyconfig4 (>= 4:4.4.4) but it is not going to be installed
       Depends: k3b-data (= 2.0.1-1ubuntu3) but 2.0.1-1ubuntu5~maverick1~ppa1 is to be installed
E: Broken packages
davidcafu@Davidcafu:~$ [/COLOR]

---

