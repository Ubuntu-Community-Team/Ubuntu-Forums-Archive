---
title: "problems with sun-java6-... installation"
date: 2009-05-09
forum: General Help
---

### Post by bakunin77 on 2009-05-09
Hi, 
I'm on kubuntu 9.04
I tried to install java runtime environment with the command
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
out of yakuake.
Then the Sun licence agreement window appeared, and I was stuck. I couldn't accept; as a matter of fact, I couldn't do anything at all. So I killed the window, logged out and in, and tried to update with
sudo apt-get -f install
This doesn't work, I get the following:


sudo apt-get -f install 
Reading package lists... Done            
Building dependency tree                 
Reading state information... Done        
Correcting dependencies... Done          
The following extra packages will be installed:
  sun-java6-bin sun-java6-jre                  
Suggested packages:                            
  binfmt-support                               
The following packages will be upgraded:       
  sun-java6-bin sun-java6-jre                  
2 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.                             
Need to get 0B/34.7MB of archives.                            
After this operation, 99.5MB of additional disk space will be used.
Do you want to continue [Y/n]? Y                                   
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable                                                              
(Reading database ...                                                                      
dpkg: serious warning: files list file for package `sun-java6-jre' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `sun-java6-bin' missing, assuming package has no files currently installed.
102841 files and directories currently installed.)
Preparing to replace sun-java6-jre 6-13-1 (using .../sun-java6-jre_6-13-1_all.deb) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing /var/cache/apt/archives/sun-java6-jre_6-13-1_all.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Preparing to replace sun-java6-bin 6-13-1 (using .../sun-java6-bin_6-13-1_i386.deb) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing /var/cache/apt/archives/sun-java6-bin_6-13-1_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/sun-java6-jre_6-13-1_all.deb
 /var/cache/apt/archives/sun-java6-bin_6-13-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)



What can I do to clean the mess up and install the stuff?

---

### Post by oldos2er on 2009-05-09
Close any package manager you may have running. In a terminal, run
```
sudo dpkg --configure -a
```
 When the Sun Java license comes up, hit Tab to highlight "ok" then hit Enter.

---

### Post by bakunin77 on 2009-05-09
Thanks... that worked, and TAB did the job :)

---

