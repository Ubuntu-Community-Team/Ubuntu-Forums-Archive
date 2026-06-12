---
title: "having trounle installing software"
date: 2009-05-20
forum: General Help
---

### Post by sn0m on 2009-05-20
Hey guys, can someone help me fix this:
sn0m@sn0m-desktop:~$ sudo apt-get install pysdm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed
  pysdm
0 upgraded, 1 newly installed, 0 to remove and 11 not upgraded.
Need to get 0B/29.1kB of archives.
After this operation, 299kB of additional disk space will be used.
dpkg: parse error, in file `/var/lib/dpkg/available' near line 6328 package `libmtp8':
 newline in field name `Original-Ma'
E: Sub-process /usr/bin/dpkg returned an error code (2)
sn0m@sn0m-desktop:~$ 

I tried sudo dpkg --configure -a but no luck.
Thanks in advance
Sokol

---

### Post by sn0m on 2009-05-21
ping ping, 
if [no reply ]then 
  echo "you're in trouble"
   else ? "file a bug report"
guys serious do I stand a chance fixing it or shall i do a re-install of ubuntu....

---

### Post by Soul-Sing on 2009-05-21
dpkg --clean-avail
apt-get update

or ```
sudo dpkg --clean-avail
apt-get update
```

---

### Post by sn0m on 2009-05-21
thanks leoquet, still no luck:

sn0m@sn0m-desktop:~$ sudo dpkg --clean-avail
[sudo] password for sn0m: 
dpkg: unknown option --clean-avail

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license|--licence for copyright licence and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
sn0m@sn0m-desktop:~$

---

### Post by KhurramM on 2009-05-21
Download the debian and use dpkg -i ...

Hope this helps

---

### Post by Soul-Sing on 2009-05-21
```
sudo dpkg --clear-avail && sudo apt-get update
```
i made a mistake...sorry

or: ```
sudo dpkg --configure -a && sudo apt-get -f install
```

---

### Post by sn0m on 2009-05-21
No luck chaps.

sn0m@sn0m-desktop:~$ sudo dpkg --clear-avail && sudo apt-get update
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_GB          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_GB    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty Release.gpg                            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/main Translation-en_GB                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/restricted Translation-en_GB           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release                                   
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release.gpg                            
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Translation-en_GB              
Hit [http://winff.org](http://winff.org) jaunty Release.gpg                                        
Ign [http://winff.org](http://winff.org) jaunty/universe Translation-en_GB                         
Get: 1 [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release.gpg [197B]                 
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Translation-en_GB                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_GB      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_GB    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release                         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/universe Translation-en_GB             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/multiverse Translation-en_GB           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates Release.gpg                    
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/main Translation-en_GB         
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/restricted Translation-en_GB   
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/universe Translation-en_GB     
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_GB   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Sources                              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty Release                                
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release                                
Hit [http://winff.org](http://winff.org) jaunty Release                                            
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Translation-en_GB            
Get: 2 [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release [11.7kB]                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Sources                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates Release                        
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages                       
Hit [http://winff.org](http://winff.org) jaunty/universe Packages                                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/main Packages                          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/restricted Packages                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/restricted Sources                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/main Sources                           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/multiverse Sources                     
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Sources                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/universe Sources                       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/universe Packages            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/multiverse Packages          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/main Packages        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/restricted Packages  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/restricted Sources   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/main Sources         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/multiverse Sources   
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages             
Get: 3 [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Packages [3260B]    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/universe Sources               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/universe Packages    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/multiverse Packages  
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Sources              
Get: 4 [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Packages [11.4kB]
Get: 5 [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Sources [3200B]
Get: 6 [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Sources [8133B]
Fetched 37.9kB in 5s (6424B/s)                     
Reading package lists... Done
sn0m@sn0m-desktop:~$ sudo apt-get install pysdm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed
  pysdm
0 upgraded, 1 newly installed, 0 to remove and 11 not upgraded.
Need to get 0B/29.1kB of archives.
After this operation, 299kB of additional disk space will be used.
Selecting previously deselected package pysdm.
(Reading database ... 
dpkg: serious warning: files list file for package `libmpfr1ldbl' missing, assuming package has no files currently installed.
dpkg: unrecoverable fatal error, aborting:
 files list file for package `libsoup2.4-1' is missing final newline
E: Sub-process /usr/bin/dpkg returned an error code (2)
sn0m@sn0m-desktop:~$

---

