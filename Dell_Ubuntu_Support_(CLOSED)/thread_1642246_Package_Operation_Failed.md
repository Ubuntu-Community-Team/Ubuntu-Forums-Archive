---
title: "Package Operation Failed"
date: 2010-12-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by WilhelmGGW on 2010-12-10
I recently did a complete install of 10.10 netbook edition on my Dell Mini 9. All went well, except now all my system updates give me a failure message.
"Package Operation Failed: The installation or removal of a software package failed."
How can I solve this problem? Thanks.

---

### Post by karthick87 on 2010-12-10
Try,

```
sudo apt-get autoremove -f 
```
```
sudo apt-get update
```
```
sudo apt-get upgrade
```

---

### Post by sikander3786 on 2010-12-10
We also need to see the output of commands mentioned by **karthick87** above.

While posting, click the # icon in post menu and paste your text in between the generated code tags.

---

### Post by WilhelmGGW on 2010-12-10
```
judy@jaw-Inspiron-910:~$ sudo apt-get autoremove -f
[sudo] password for judy: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up firmware-b43-installer (4.150.10.5-4) ...
Not supported low-power chip with PCI id 14e4:4315!
Aborting.
dpkg: error processing firmware-b43-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 firmware-b43-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
judy@jaw-Inspiron-910:~$ sudo apt-get update
Hit http://us.archive.ubuntu.com maverick Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en
Hit http://security.ubuntu.com maverick-security Release.gpg                              
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en              
Hit http://deb.opera.com stable Release.gpg                                                
Ign http://deb.opera.com/opera/ stable/non-free Translation-en                             
Ign http://www.openprinting.org lsb3.2 Release.gpg                                         
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US                   
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US
Hit http://us.archive.ubuntu.com maverick-updates Release.gpg        
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Hit http://security.ubuntu.com maverick-security Release
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
Ign http://deb.opera.com/opera/ stable/non-free Translation-en_US    
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Hit http://deb.opera.com stable Release                              
Hit http://security.ubuntu.com maverick-security/main Sources        
Ign http://www.openprinting.org/download/printdriver/debian/ lsb3.2/main Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Hit http://us.archive.ubuntu.com maverick Release                    
Hit http://us.archive.ubuntu.com maverick-updates Release            
Ign http://deb.opera.com stable/non-free i386 Packages                                     
Hit http://security.ubuntu.com maverick-security/restricted Sources                        
Hit http://security.ubuntu.com maverick-security/universe Sources                          
Hit http://security.ubuntu.com maverick-security/multiverse Sources                        
Hit http://security.ubuntu.com maverick-security/main i386 Packages                        
Hit http://security.ubuntu.com maverick-security/restricted i386 Packages                  
Ign http://www.openprinting.org/download/printdriver/debian/ lsb3.2/main Translation-en_US 
Hit http://www.openprinting.org lsb3.2 Release                                             
Hit http://us.archive.ubuntu.com maverick/main Sources               
Hit http://security.ubuntu.com maverick-security/universe i386 Packages
Hit http://security.ubuntu.com maverick-security/multiverse i386 Packages
Ign http://deb.opera.com stable/non-free i386 Packages               
Ign http://www.openprinting.org lsb3.2/main i386 Packages/DiffIndex  
Hit http://us.archive.ubuntu.com maverick/restricted Sources
Hit http://us.archive.ubuntu.com maverick/universe Sources
Hit http://us.archive.ubuntu.com maverick/multiverse Sources
Hit http://us.archive.ubuntu.com maverick/main i386 Packages
Hit http://us.archive.ubuntu.com maverick/restricted i386 Packages
Hit http://us.archive.ubuntu.com maverick/universe i386 Packages
Hit http://deb.opera.com stable/non-free i386 Packages               
Ign http://www.openprinting.org lsb3.2/main i386 Packages            
Hit http://us.archive.ubuntu.com maverick/multiverse i386 Packages
Hit http://us.archive.ubuntu.com maverick-updates/main Sources
Hit http://us.archive.ubuntu.com maverick-updates/restricted Sources
Hit http://us.archive.ubuntu.com maverick-updates/universe Sources
Ign http://www.openprinting.org lsb3.2/main i386 Packages
Hit http://us.archive.ubuntu.com maverick-updates/multiverse Sources
Hit http://us.archive.ubuntu.com maverick-updates/main i386 Packages
Hit http://us.archive.ubuntu.com maverick-updates/restricted i386 Packages
Hit http://us.archive.ubuntu.com maverick-updates/universe i386 Packages
Hit http://us.archive.ubuntu.com maverick-updates/multiverse i386 Packages
Hit http://www.openprinting.org lsb3.2/main i386 Packages
Reading package lists... Done
judy@jaw-Inspiron-910:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up firmware-b43-installer (4.150.10.5-4) ...
Not supported low-power chip with PCI id 14e4:4315!
Aborting.
dpkg: error processing firmware-b43-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 firmware-b43-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
judy@jaw-Inspiron-910:~$
```

---

### Post by sikander3786 on 2010-12-10
Try,

```
sudo apt-get remove --purge firmware-b43-installer
```

---

### Post by karthick87 on 2010-12-10
Run,

```
sudo apt-get -f install 
```

---

### Post by WilhelmGGW on 2010-12-10
I ran the commands and got the following..
Then to test it I ran Update Manager but nothing was found to install.
Does this look like it worked for me?
```
judy@jaw-Inspiron-910:~$ sudo apt-get remove --purge firmware-b43-installer
[sudo] password for judy: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  firmware-b43-installer*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 49.2kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 145439 files and directories currently installed.)
Removing firmware-b43-installer ...
Purging configuration files for firmware-b43-installer ...
judy@jaw-Inspiron-910:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by sikander3786 on 2010-12-10
Output suggest that it has been Fixed!

You can test by trying to install some packages.

---

### Post by WilhelmGGW on 2010-12-10
Top-of-the-morning thanks to you all.  Package installation did fine.  Thanks so much.

---

### Post by sikander3786 on 2010-12-10
You are Welcome :-)

Please mark the thread Solved using **[COLOR="Red"]Thread Tools[/COLOR]** near the top of this page so that no more members come here wandering and tying to help you ;-)

Happy Ubuntu-ing!

---

### Post by antoniogarciaiii on 2011-09-17
Thank you!  This fixed my problem. :)

---

