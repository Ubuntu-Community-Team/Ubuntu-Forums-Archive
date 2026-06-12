---
title: "Help!  I've broken Install/Remove."
date: 2011-01-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by bluplanet on 2011-01-25
I've got 10.10 on a Dell Inspiron 1520
I installed a Brother printer driver that didn't do exactly what I wanted.  I tried to remove it.  Now I can't install or remove anything.  No updates either.

The package is mfc685cwlpr.
Now it shows up in synaptic with a red X but I can't do anything with it.
It tries to complete the removal every time I start the computer but crashes.
I've tried:
sudo apt-get remove mfc685cwlpr
sudo apt-get install -f
sudo apt-get install --remove mfc685cwlpr

Nothing works.
I get this:

Errors were encountered while processing: 
mfc685cwlpr 
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by trinitydan on 2011-01-25
Did you add a repository to get the Brother driver?   Maybe remove the repository from your sources list and try 
```
sudo apt-get update
```

---

### Post by bluplanet on 2011-01-25
A repository?? hmmmm.  what's that?  

I downloaded the driver from Brother, clicked on it and xubuntu took over from there for the installation.
The driver now shows up in Synaptic in a red field with a red x in the status indicator box.  Can't do nothing with it.
I tried     sudo apt-get update       and then tried      sudo apt-get remove mfc685cwlpr     again.
Didn't work.
I went into Synaptic to try to remove it again and got this message in the details when it failed:

(Reading database ... 204842 fiiles and directories currently installed.)
Removing mfc685cwlpr ...
start: Unknown job: lpd
dpkg: error processing mfc685cwlpr (--purge):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already 

Errors were entered while processing:
mfc685cwlpr
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install. Trying to recover:

---

### Post by ugm6hr on 2011-01-26
Post the exact output from:
```
sudo apt-get install -f
```

I suspect that it hasn't installed properly - hence you can't remove it. dpkg might be able to undo whatever it did.

Point us to where you got the driver from - are you sure it's an Ubuntu driver?

---

### Post by bluplanet on 2011-01-26
[FONT=Courier New]ComputerName-inspiron-1520:~sudo apt-get install -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required: wesnoth-1.8-data libbost-regex1.42.0 ttf-wqy-zenhei wesnoth-1.8-core libsdl-net1.2 csh libsd-ttf2.0-0 libmikmod2 libboost-iostreams1.42.0 livsdl-mixer1.2 libsmpeg0
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
mfc685cwlpr
0 upgraded, 0 newly installed, 1 to remove and 75 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? 
<Y> 
(Reading database ... 204842 files and directories currently installed.)
Removing mfc685cwlpr ...
start: Unknown job: lpd
dpkg: error processing mfc685cwlpr (--remove):
subprocess installed post-removal script returned error exit status 1
ComputerName-Inspiron-1520:~$[/FONT]

---

### Post by bluplanet on 2011-01-26
[FONT=Courier New]Note:
Post above is complete output from
sudo apt-get install -f

Post immediately below is complete output from 
sudo apt-get autoremove
[/FONT]

---

### Post by bluplanet on 2011-01-26
[FONT=Courier New]ComputerName-Inspiron-1520:~$ **sudo** apt-get autoremove 
 [sudo] password for Name:  
 Reading package lists... Done 
 Building dependency tree        
 Reading state information... Done 
 The following packages will be REMOVED: 
   csh libboost-iostreams1.42.0 libboost-regex1.42.0 libmikmod2 libsdl-mixer1.2 
   libsdl-net1.2 libsdl-ttf2.0-0 libsmpeg0 mfc685cwlpr ttf-wqy-zenhei 
   wesnoth-1.8-core wesnoth-1.8-data 
 0 upgraded, 0 newly installed, 12 to remove and 75 not upgraded. 
 1 not fully installed or removed. 
 After this operation, 154MB disk space will be freed. 
 Do you want to continue [Y/n]? y 
 (Reading database ... 204842 files and directories currently installed.) 
 Removing mfc685cwlpr ... 
 start: Unknown job: lpd 
 dpkg: error processing mfc685cwlpr (--remove): 
  subprocess installed post-removal script returned error exit status 1 
 No apport report written because MaxReports is reached already 
                                                               Removing csh ... 
 update-alternatives: using /bin/tcsh to provide /bin/csh (csh) in auto mode. 
 Removing wesnoth-1.8-core ... 
 Removing 'diversion of /usr/games/wesnoth to /usr/games/wesnoth-old by wesnoth-1.8-core' 
 Removing 'diversion of /usr/games/wesnoth-nolog to /usr/games/wesnoth-nolog-old by wesnoth-1.8-core' 
 Removing 'diversion of /usr/games/wesnoth-smallgui to /usr/games/wesnoth-smallgui-old by wesnoth-1.8-core' 
 Removing 'diversion of /usr/games/wesnoth-editor to /usr/games/wesnoth-editor-old by wesnoth-1.8-core' 
 Removing 'diversion of /usr/share/man/ca_ES@valencia/man6/wesnoth.6.gz to /usr/share/man/ca_ES@valencia/man6/wesnoth-old.6.gz by wesnoth-1.8-core' 
 Removing 'diversion of /usr/share/man/cs/man6/wesnoth.6.gz to /usr/share/man/cs/man6/wesnoth-old.6.gz by wesnoth-1.8-core' 
 Removing 'diversion of /usr/share/man/da/man6/wesnoth.6.gz to /usr/share/man/da/man6/wesnoth-old.6.gz by wesnoth-1.8-core' 
 Removing 'diversion of /usr/share/man/de/man6/wesnoth.6.gz to /usr/share/man/de/man6/wesnoth-old.6.gz by wesnoth-1.8-core' 
 Removing 'diversion of /usr/share/man/en_GB/man6/wesnoth.6.gz to /usr/share/man/en_GB/man6/wesnoth-old.6.gz by wesnoth-1.8-core' 
 Removing 'diversion of /usr/share/man/es/man6/wesnoth.6.gz to /usr/share/man/es/man6/wesnoth-old.6.gz by wesnoth-1.8-core' 
 Removing 'diversion of /usr/share/man/et/man6/wesnoth.6.gz to /usr/share/man/et/man6/wesnoth-old.6.gz by wesnoth-1.8-core' 
 Removing 'diversion of /usr/share/man/fi/man6/wesnoth.6.gz to /usr/share/man/fi/man6/wesnoth-old.6.gz by wesnoth-1.8-core' 
 Removing 'diversion of /usr/share/man/fr/man6/wesnoth.6.gz to /usr/share/man/fr/man6/wesnoth-old.6.gz by wesnoth-1.8-core' 
 Removing 'diversion of /usr/share/man/gl/man6/wesnoth.6.gz to /usr/share/man/gl/man6/wesnoth-old.6.gz by wesnoth-1.8-core' 
 Removing 'diversion of /usr/share/man/hu/man6/wesnoth.6.gz to /usr/share/man/hu/man6/wesnoth-old.6.gz by wesnoth-1.8-core' 
 Removing 'diversion of /usr/share/man/it/man6/wesnoth.6.gz to /usr/share/man/it/man6/wesnoth-old.6.gz by wesnoth-1.8-core' 
 Removing 'diversion of /usr/share/man/ja/man6/wesnoth.6.gz to /usr/share/man/ja/man6/wesnoth-old.6.gz by wesnoth-1.8-core' 
 Removing 'diversion of /usr/share/man/lt/man6/wesnoth.6.gz to /usr/share/man/lt/man6/wesnoth-old.6.gz by wesnoth-1.8-core' 
 Removing 'diversion of /usr/share/man/nl/man6/wesnoth.6.gz to /usr/share/man/nl/man6/wesnoth-old.6.gz by wesnoth-1.8-core' 
 Removing 'diversion of /usr/share/man/pl/man6/wesnoth.6.gz to /usr/share/man/pl/man6/wesnoth-old.6.gz by wesnoth-1.8-core' 
 Removing 'diversion of /usr/share/man/sk/man6/wesnoth.6.gz to /usr/share/man/sk/man6/wesnoth-old.6.gz by wesnoth-1.8-core' 
 Removing 'diversion of /usr/share/man/sr/man6/wesnoth.6.gz to /usr/share/man/sr/man6/wesnoth-old.6.gz by wesnoth-1.8-core' 
 Removing 'diversion of /usr/share/man/sr@latin/man6/wesnoth.6.gz to /usr/share/man/sr@latin/man6/wesnoth-old.6.gz by wesnoth-1.8-core' 
 Removing 'diversion of /usr/share/man/sv/man6/wesnoth.6.gz to /usr/share/man/sv/man6/wesnoth-old.6.gz by wesnoth-1.8-core' 
 Removing 'diversion of /usr/share/man/tr/man6/wesnoth.6.gz to /usr/share/man/tr/man6/wesnoth-old.6.gz by wesnoth-1.8-core' 
 Removing 'diversion of /usr/share/man/zh_CN/man6/wesnoth.6.gz to /usr/share/man/zh_CN/man6/wesnoth-old.6.gz by wesnoth-1.8-core' 
 Removing 'diversion of /usr/share/man/zh_TW/man6/wesnoth.6.gz to /usr/share/man/zh_TW/man6/wesnoth-old.6.gz by wesnoth-1.8-core' 
 Removing libboost-iostreams1.42.0 ... 
 Removing libboost-regex1.42.0 ... 
 Removing libsdl-mixer1.2 ... 
 Removing libmikmod2 ... 
 Removing libsdl-net1.2 ... 
 Removing libsdl-ttf2.0-0 ... 
 Removing libsmpeg0 ... 
 Removing ttf-wqy-zenhei ... 
 Removing wesnoth-1.8-data ... 
 Processing triggers for doc-base ... 
 Processing 2 removed doc-base file(s)... 
 Registering documents with scrollkeeper... 
 Processing triggers for man-db ... 
 Processing triggers for desktop-file-utils ... 
 Processing triggers for python-gmenu ... 
 Rebuilding /usr/share/applications/desktop.en_US.utf8.cache... 
 Processing triggers for libc-bin ... 
 ldconfig deferred processing now taking place 
 Processing triggers for fontconfig ... 
 Processing triggers for python-support ... 
 Errors were encountered while processing: 
  mfc685cwlpr 
 E: Sub-process /usr/bin/dpkg returned an error code (1) 
 ComputerName-Inspiron-1520:~$ ^C 
 ComputerName-Inspiron-1520:~$[/FONT]

---

### Post by bluplanet on 2011-01-26
I DL'd the driver from Brother.

---

### Post by bluplanet on 2011-01-26
> **ugm6hr said:**
> Post the exact output from:
```
sudo apt-get install -f
```**I suspect that it hasn't installed properly - hence you can't remove it**. dpkg might be able to undo whatever it did.

Point us to where you got the driver from - are you sure it's an Ubuntu driver?


Maybe so, but be aware that I can't install or remove ANYTHING.  

I got the Debian driver here: 
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html)
Links I used from this site: 
"Before the Installation"
"Download" / "Printer Driver"
"Instruction" / "Printer (CUPS)" /<all>
"Instruction" / "Printer (LPR)" / "Driver Install"

---

### Post by bluplanet on 2011-01-26
I've discovered that **mfc685cwlpr** isn't the only package that's stuck in limbo.
Another Brother printer driver that I attempted to remove, **brhl2140lpr**, has the same problem.
Both show up in synaptic with red highlight and a red X in the status box.
I found the second one using Computer Janitor.

---

### Post by bluplanet on 2011-01-26
The following is the output from:
sudo apt-get update...

ComputerName-Inspiron-1520:~$ sudo apt-get update
[sudo] password for MyName: 
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [197B]                           
Ign [http://dl.google.com/linux/earth/deb/](http://dl.google.com/linux/earth/deb/) stable/main Translation-en           
Ign [http://dl.google.com/linux/earth/deb/](http://dl.google.com/linux/earth/deb/) stable/main Translation-en_US        
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [1,338B]                             
Get:3 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [471B]                    
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg [198B]          
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release.gpg                          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_US       
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_US
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release [31.4kB]            
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en    
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_US 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en    
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en      
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_US   
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates Release.gpg [198B]         
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release                              
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates Release [31.4kB]           
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources [23.1kB]       
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources [14B]    
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources [9,802B]  
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg                          
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en       
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en_US    
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release                             
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources [649B]  
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main i386 Packages [75.0kB]
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main Sources                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted Sources                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse Sources                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main i386 Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted i386 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe i386 Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse i386 Packages             
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main Sources [77.3kB]     
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages [14B]
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe i386 Packages [38.5kB]
Get:16 [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg [72B]                     
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en              
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_US           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release                                  
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources                             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages                       
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse i386 Packages [1,655B]
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted Sources [778B] 
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe Sources [26.8kB] 
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse Sources [1,068B]
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main i386 Packages [211kB]
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted i386 Packages [1,797B]
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe i386 Packages [84.8kB]
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse i386 Packages [2,544B]
Fetched 620kB in 27s (22.9kB/s)                                                
Reading package lists... Done

---

