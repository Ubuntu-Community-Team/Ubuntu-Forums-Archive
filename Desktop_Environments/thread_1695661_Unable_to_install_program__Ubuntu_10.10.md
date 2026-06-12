---
title: "Unable to install program / Ubuntu 10.10"
date: 2011-02-26
forum: Desktop Environments
---

### Post by gerxrdo on 2011-02-26
I am trying to install last.fm and I am getting this message:


 Package dependencies can not be resolved
This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.

I get same error for any other program I try to install. I opened terminal and typed sudo apt-get install last.fm and get:

lalo@lalo-laptop:~$ sudo apt-get  install last.fm
[sudo] password for lalo: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package last.fm
E: Couldn't find any package by regex


How do I repair package manager catalog?

---

### Post by thefasterblueone on 2011-02-26
Try this and post any errors.

```
sudo dpkg --configure -a && sudo apt-get update
```

---

### Post by Krytarik on 2011-02-26
And check what "Software Sources" are selected.

---

### Post by Cheesehead on 2011-02-26
Seems like you misspelled the package name.

```

sudo apt-get install last.fm   #incorrect
sudo apt-get install lastfm    #correct
```

---

### Post by gerxrdo on 2011-02-27
lalo@lalo-laptop:~$ sudo dpkg --configure -a && sudo apt-get update
[sudo] password for lalo: 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg
Ign [http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/](http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/](http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/) maverick/main Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg                    
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security/main Translation-en    
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security/main Translation-en_US 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg                              
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper/main Translation-en              
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper/main Translation-en_US           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                 
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security/multiverse Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security/restricted Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security/universe Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release                        
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper/multiverse Translation-en        
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper/multiverse Translation-en_US     
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper/restricted Translation-en        
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper/restricted Translation-en_US     
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper/universe Translation-en          
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper/universe Translation-en_US       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg                      
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates/main Translation-en      
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates/main Translation-en_US   
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates/multiverse Translation-en
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources                   
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates/multiverse Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates/restricted Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates/universe Translation-en  
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates/universe Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg                    
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports/main Translation-en    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main i386 Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe i386 Packages         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse i386 Packages       
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports/main Translation-en_US 
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports/multiverse Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports/multiverse Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports/restricted Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports/restricted Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports/universe Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports/universe Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release.gpg                            
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/universe Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_US     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release                                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release                                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main i386 Packages                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted i386 Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe i386 Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse i386 Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Sources                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Sources               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted i386 Packages         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe i386 Packages           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Sources             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Sources               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe i386 Packages         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse i386 Packages       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/universe i386 Packages
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release.gpg    
  Could not connect to packages.freecontrib.org:80 (34.52.53.34). - connect (110: Connection timed out)
Err [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper/free Translation-en
  Unable to connect to packages.freecontrib.org:http:
Err [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper/free Translation-en_US
  Unable to connect to packages.freecontrib.org:http:
Err [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper/non-free Translation-en
  Unable to connect to packages.freecontrib.org:http:
Err [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper/non-free Translation-en_US
  Unable to connect to packages.freecontrib.org:http:
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Sources
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Sources
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free i386 Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free i386 Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Sources
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Sources
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free i386 Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free i386 Packages
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Sources
  Unable to connect to packages.freecontrib.org:http:
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Sources
  Unable to connect to packages.freecontrib.org:http:
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free i386 Packages
  Unable to connect to packages.freecontrib.org:http:
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free i386 Packages
  Unable to connect to packages.freecontrib.org:http:
W: Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/Release.gpg](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/Release.gpg)  Could not connect to packages.freecontrib.org:80 (34.52.53.34). - connect (110: Connection timed out)

W: Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/i18n/Translation-en.bz2](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/i18n/Translation-en.bz2)  Unable to connect to packages.freecontrib.org:http:

W: Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/i18n/Translation-en_US.bz2](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/i18n/Translation-en_US.bz2)  Unable to connect to packages.freecontrib.org:http:

W: Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/i18n/Translation-en.bz2](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/i18n/Translation-en.bz2)  Unable to connect to packages.freecontrib.org:http:

W: Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/i18n/Translation-en_US.bz2](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/i18n/Translation-en_US.bz2)  Unable to connect to packages.freecontrib.org:http:

W: Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/source/Sources.gz](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/source/Sources.gz)  Unable to connect to packages.freecontrib.org:http:

W: Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/source/Sources.gz](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/source/Sources.gz)  Unable to connect to packages.freecontrib.org:http:

W: Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/binary-i386/Packages.gz](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/binary-i386/Packages.gz)  Unable to connect to packages.freecontrib.org:http:

W: Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/binary-i386/Packages.gz](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/binary-i386/Packages.gz)  Unable to connect to packages.freecontrib.org:http:

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by gerxrdo on 2011-02-27
lalo@lalo-laptop:~$ sudo apt-get install lastfm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 lastfm : Depends: libqt4-network (>= 4:4.5.3) but it is not installable
          Depends: libqt4-sql (>= 4:4.5.3) but it is not going to be installed
          Depends: libqt4-xml (>= 4:4.5.3) but it is not installable
          Depends: libqtcore4 (>= 4:4.7.0~beta1) but it is not installable
          Depends: libqtgui4 (>= 4:4.5.3) but it is not installable
E: Broken packages

---

### Post by Willyinpr4u on 2011-02-27
I'm a newbie in Ubuntu, but, can't you install this package from Synaptics?
I click applications, Ubuntu Software Center, Sound and Video, and search for Lastfm, it allowed me to install it.

---

### Post by Krytarik on 2011-02-27
Yeah, I didn't mention the misspelled package name, because it's obviously more a general issue.

You have numerous repos of Dapper in your sources list, I believe that is the root cause.

So, please do the following:
- backup your current "/etc/apt/sources.list"
- generate the correct/default entries here: [http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)
- replace the entries
- check also the selected sources in "Software Sources -> Other Software", some of those seem to not work (anymore)

---

### Post by gerxrdo on 2011-03-01
Thanks!

I added the repos below and unchecked the other ones. Issue fixed.




###### Ubuntu Main Repos
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick main 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick main 

###### Ubuntu Update Repos
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-security main 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates main 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-security main 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates main

---

### Post by Krytarik on 2011-03-01
Cool, then please mark this thread as "solved", via "Thread Tools".

---

