---
title: "avant-window-navigator just screwed up my software index"
date: 2008-01-04
forum: Desktop Effects &amp; Customization
---

### Post by pfwd.tech on 2008-01-04
Hi, I have been trying to install Awn/Avant-windows-navigator and Im now stuck
My update manager says the software index is broken and i should run sudo apt-get install -f
this is what happens:
```

$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies...Done
The following packages were automatically installed and are no longer required:
  python-alsaaudio libawn0 python-libgmail cairo-clock
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libawn-bzr
The following NEW packages will be installed
  libawn-bzr
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0B/63.6kB of archives.
After unpacking 180kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 93996 files and directories currently installed.)
Unpacking libawn-bzr (from .../libawn-bzr_0.2.0-bzr151-1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libawn-bzr_0.2.0-bzr151-1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libawn.so.0.0.1', which is also in package libawn0
Errors were encountered while processing:
 /var/cache/apt/archives/libawn-bzr_0.2.0-bzr151-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

This is the output from trying to install the packages.
$```
 sudo aptitude update && sudo aptitude install avant-window-navigator awn-core-applets awn-manager
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_GB
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_GB
Get:1 http://gb.archive.ubuntu.com gutsy Release.gpg [191B]                     
Hit http://gb.archive.ubuntu.com gutsy/main Translation-en_GB                   
Hit http://gb.archive.ubuntu.com gutsy/restricted Translation-en_GB             
Get:2 http://archive.canonical.com gutsy Release.gpg [191B]                     
Ign http://archive.canonical.com gutsy/partner Translation-en_GB                
Hit http://gb.archive.ubuntu.com gutsy/universe Translation-en_GB               
Hit http://gb.archive.ubuntu.com gutsy/multiverse Translation-en_GB             
Get:3 http://gb.archive.ubuntu.com gutsy-updates Release.gpg [191B]             
Ign http://gb.archive.ubuntu.com gutsy-updates/main Translation-en_GB           
Ign http://gb.archive.ubuntu.com gutsy-updates/restricted Translation-en_GB     
Ign http://gb.archive.ubuntu.com gutsy-updates/universe Translation-en_GB       
Ign http://gb.archive.ubuntu.com gutsy-updates/multiverse Translation-en_GB     
Hit http://archive.canonical.com gutsy Release                                  
Get:4 http://security.ubuntu.com gutsy-security Release.gpg [191B]              
Ign http://security.ubuntu.com gutsy-security/main Translation-en_GB            
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_GB      
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_GB        
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_GB      
Get:5 http://download.tuxfamily.org gutsy Release.gpg [189B]                    
Ign http://download.tuxfamily.org gutsy/avant-window-navigator Translation-en_GB
Get:6 http://wine.budgetdedicated.com gutsy Release.gpg [191B]                  
Ign http://wine.budgetdedicated.com gutsy/main Translation-en_GB                
Hit http://gb.archive.ubuntu.com gutsy Release                                  
Hit http://gb.archive.ubuntu.com gutsy-updates Release                          
Hit http://security.ubuntu.com gutsy-security Release                           
Hit http://archive.canonical.com gutsy/partner Packages                         
Hit http://download.tuxfamily.org gutsy Release                                 
Hit http://wine.budgetdedicated.com gutsy Release                               
Hit http://gb.archive.ubuntu.com gutsy/main Packages                            
Hit http://archive.canonical.com gutsy/partner Sources
Hit http://gb.archive.ubuntu.com gutsy/restricted Packages
Hit http://gb.archive.ubuntu.com gutsy/main Sources
Hit http://gb.archive.ubuntu.com gutsy/restricted Sources
Hit http://gb.archive.ubuntu.com gutsy/universe Packages            
Hit http://gb.archive.ubuntu.com gutsy/universe Sources             
Hit http://gb.archive.ubuntu.com gutsy/multiverse Packages          
Hit http://gb.archive.ubuntu.com gutsy/multiverse Sources           
Hit http://gb.archive.ubuntu.com gutsy-updates/main Packages        
Hit http://gb.archive.ubuntu.com gutsy-updates/restricted Packages  
Hit http://gb.archive.ubuntu.com gutsy-updates/main Sources         
Hit http://gb.archive.ubuntu.com gutsy-updates/restricted Sources   
Hit http://gb.archive.ubuntu.com gutsy-updates/universe Packages    
Hit http://gb.archive.ubuntu.com gutsy-updates/universe Sources     
Hit http://security.ubuntu.com gutsy-security/main Packages         
Hit http://gb.archive.ubuntu.com gutsy-updates/multiverse Packages  
Hit http://gb.archive.ubuntu.com gutsy-updates/multiverse Sources    
Hit http://security.ubuntu.com gutsy-security/restricted Packages    
Hit http://security.ubuntu.com gutsy-security/main Sources
Hit http://security.ubuntu.com gutsy-security/restricted Sources
Hit http://download.tuxfamily.org gutsy/avant-window-navigator Packages
Ign http://wine.budgetdedicated.com gutsy/main Packages
Hit http://security.ubuntu.com gutsy-security/universe Packages
Hit http://security.ubuntu.com gutsy-security/universe Sources
Hit http://security.ubuntu.com gutsy-security/multiverse Packages
Hit http://security.ubuntu.com gutsy-security/multiverse Sources
Hit http://download.tuxfamily.org gutsy/avant-window-navigator Sources
Hit http://wine.budgetdedicated.com gutsy/main Sources
Hit http://wine.budgetdedicated.com gutsy/main Packages
Fetched 6B in 0s (9B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Building tag database... Done      
No candidate version found for avant-window-navigator
No candidate version found for awn-core-applets
No candidate version found for awn-manager
The following packages are BROKEN:
  avant-window-navigator-bzr awn-core-applets-bzr python-libawn-bzr 
The following packages are unused and will be REMOVED:
  cairo-clock libawn0 python-alsaaudio python-libgmail 
0 packages upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 3342kB will be freed.
The following packages have unmet dependencies:
  awn-core-applets-bzr: Depends: libawn-bzr but it is not installable
                        Depends: libawn-bzr but it is not installable
  avant-window-navigator-bzr: Depends: libawn-bzr but it is not installable
                              Depends: libawn-bzr (= 0.2.0-bzr151-1) but it is not installable
  python-libawn-bzr: Depends: libawn-bzr (= 0.2.0-bzr151-1) but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Install the following packages:
libawn-bzr [0.2.0-bzr151-1 (gutsy)]

Score is 41

Accept this solution? [Y/n/q/?] y
The following packages are unused and will be REMOVED:
  cairo-clock libawn0 python-alsaaudio python-libgmail 
The following NEW packages will be automatically installed:
  libawn-bzr 
The following NEW packages will be installed:
  libawn-bzr 
The following partially installed packages will be configured:
  avant-window-navigator-bzr awn-core-applets-bzr python-libawn-bzr 
0 packages upgraded, 1 newly installed, 4 to remove and 0 not upgraded.
Need to get 0B/63.6kB of archives. After unpacking 3162kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 93996 files and directories currently installed.)
Unpacking libawn-bzr (from .../libawn-bzr_0.2.0-bzr151-1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libawn-bzr_0.2.0-bzr151-1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libawn.so.0.0.1', which is also in package libawn0
Errors were encountered while processing:
 /var/cache/apt/archives/libawn-bzr_0.2.0-bzr151-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of awn-core-applets-bzr:
 awn-core-applets-bzr depends on libawn-bzr; however:
  Package libawn-bzr is not installed.
 awn-core-applets-bzr depends on libawn-bzr; however:
  Package libawn-bzr is not installed.
dpkg: error processing awn-core-applets-bzr (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-libawn-bzr:
 python-libawn-bzr depends on libawn-bzr (= 0.2.0-bzr151-1); however:
  Package libawn-bzr is not installed.
dpkg: error processing python-libawn-bzr (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of avant-window-navigator-bzr:
 avant-window-navigator-bzr depends on libawn-bzr; however:
  Package libawn-bzr is not installed.
 avant-window-navigator-bzr depends on libawn-bzr (= 0.2.0-bzr151-1); however:
  Package libawn-bzr is not installed.
dpkg: error processing avant-window-navigator-bzr (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 awn-core-applets-bzr
 python-libawn-bzr
 avant-window-navigator-bzr
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Building tag database... Done      
```

is there any way of removing all of awn/avant and starting again?

---

### Post by pfwd.tech on 2008-01-04
I Have fixed the broken packages by using the synaptic package manager. I do however still have the Avant Window Navigator showing in the Accessories menu.
How would i get rid of this?

---

