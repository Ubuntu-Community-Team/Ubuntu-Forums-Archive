---
title: "Opera/FireFox on 9.04 Jaunty Jackalope"
date: 2009-05-26
forum: Desktop Environments
---

### Post by AllAboutCisco on 2009-05-26
Guys, 
 
I am a Newbie to Ubuntu World and i and having a few problems with Internet browsing. When i go to a site that has video like youtube.com it would display the video. I though it was a browsers problem so i installed Opera and found out it does the same thing. Any Ideas on what do?
 
Dell Inspiron 4550
Intel P(4) 2.53 Ghz
256 MB RAM
 
I also tried following this topic in the forum but didn't get me anywhere. 
Please help!!!
 
[https://help.ubuntu.com/community/RestrictedFormats#Ubuntu%209.04,%208.10,%208.04%20and%207.10](https://help.ubuntu.com/community/RestrictedFormats#Ubuntu%209.04,%208.10,%208.04%20and%207.10)

---

### Post by ugm6hr on 2009-05-26
```
sudo apt-get update
sudo apt-get install flashplugin-nonfree flashplugin-installer
```

Restart Firefox.

---

### Post by AllAboutCisco on 2009-05-26
Thanks man but i tried this already and it still does not work.. Any other Ideas?????




cisco@cisco-desktop:~$ cd \
> sudo apt-get update
bash: cd: sudo: No such file or directory
cisco@cisco-desktop:~$ sudo apt-get update
[sudo] password for cisco: 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Translation-en_US                 
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg [307B]                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_US                      
Get:2 [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release.gpg [197B]                  
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Translation-en_US                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Translation-en_US 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release.gpg          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release                        
Get:3 [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release [11.7kB]          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages                    
Get:4 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [65.9kB]                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release                            
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages     
Get:5 [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Packages [3258B]               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Sources               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources   
Get:6 [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Packages [7943B]
Fetched 23.4kB in 0s (28.5kB/s)
Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7D2C7A23BF810CD5
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems
cisco@cisco-desktop:~$ sudo apt-get install flashplugin-nonfree flashplugin-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-nonfree is already the newest version.
flashplugin-installer is already the newest version.
flashplugin-installer set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
cisco@cisco-desktop:~$

---

### Post by ugm6hr on 2009-05-26
You have some Hardy repositories in your /apt/sources.list - you should remove them.

Not sure why Flash doesn't work for you.

Perhaps just try removing and re-installing.

```
sudo apt-get remove --purge flashplugin-nonfree flashplugin-installer
sudo apt-get install flashplugin-nonfree flashplugin-installer
```

---

### Post by MuddBuddha on 2009-05-26
I had this issue on my wifes laptop and I went to the Add/Remove, searched for FLASH and installed all the varieties of .swf I could find.

Solved the problem.  I realize it's a chintsy work around, but maybe it'll work for you.  I did have to reboot if I remember correctly.

Only did it on her Vaio, all the Thinkpads and Dells worked fine.

---

### Post by AllAboutCisco on 2009-05-26
Thanks you guys that seems to work on the youtube.com but other sites it still does not work. Is there something else i need to load besides flash plug in?

---

### Post by ugm6hr on 2009-05-26
> **AllAboutCisco said:**
> Thanks you guys that seems to work on the youtube.com but other sites it still does not work. Is there something else i need to load besides flash plug in?

What other sites?

Some online video uses realplayer, Windows media, Silverlight etc.  Check out the Multimedia link below for details on most media issues.

---

### Post by AllAboutCisco on 2009-05-27
Guys thank you all so much .. UGMHR your the man dude i follow the multimedia link and it all works great i can hear the audio and stream the video.. 

Thanks you guys.. 

Cisco~

---

