---
title: "Problem installing XFCE alongside Unity and KDE"
date: 2015-04-16
forum: Desktop Environments
---

### Post by Kpenguin on 2015-04-16
Hi everyone,
I'm currently trying to install the XFCE interface alongside Unity and KDE on my Ubuntu laptop. Whenever I use the ```
sudo apt-get install xubuntu-desktop
``` commend in terminal to install it, I get the following error: ```
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
``` What do I do about this? I run ```
sudo apt-get update
``` before I try installing it, so I'm not sure what to do from here. Any help would be appreciated!

---

### Post by CantankRus on 2015-04-16
Run ```
sudo apt-get update
``` and post the terminal output.

---

### Post by Kpenguin on 2015-04-17
Here's terminal output for sudo apt-get update:
```
Ign http://security.ubuntu.com trusty-security InRelease
Hit http://security.ubuntu.com trusty-security Release.gpg                     
Ign http://us.archive.ubuntu.com trusty InRelease                              
Ign http://extras.ubuntu.com trusty InRelease                                  
Ign http://archive.canonical.com trusty InRelease                              
Hit http://security.ubuntu.com trusty-security Release                         
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://us.archive.ubuntu.com trusty-updates InRelease                      
Hit http://security.ubuntu.com trusty-security/main Sources                    
Ign http://us.archive.ubuntu.com trusty-backports InRelease                    
Hit http://extras.ubuntu.com trusty Release.gpg                                
Hit http://archive.canonical.com trusty Release.gpg                            
Hit http://security.ubuntu.com trusty-security/restricted Sources              
Ign http://us.archive.ubuntu.com trusty-proposed InRelease                     
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://security.ubuntu.com trusty-security/universe Sources                
Hit http://us.archive.ubuntu.com trusty Release.gpg                            
Hit http://security.ubuntu.com trusty-security/multiverse Sources              
Hit http://extras.ubuntu.com trusty Release                                    
Hit http://archive.canonical.com trusty Release                                
Hit http://us.archive.ubuntu.com trusty-updates Release.gpg                    
Hit http://security.ubuntu.com trusty-security/main amd64 Packages             
Hit http://security.ubuntu.com trusty-security/restricted amd64 Packages       
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://us.archive.ubuntu.com trusty-backports Release.gpg                  
Hit http://security.ubuntu.com trusty-security/universe amd64 Packages         
Hit http://extras.ubuntu.com trusty/main Sources                               
Hit http://us.archive.ubuntu.com trusty-proposed Release.gpg                   
Hit http://security.ubuntu.com trusty-security/multiverse amd64 Packages       
Hit http://archive.canonical.com trusty/partner amd64 Packages                 
Hit http://us.archive.ubuntu.com trusty Release                                
Hit http://security.ubuntu.com trusty-security/main i386 Packages              
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://security.ubuntu.com trusty-security/restricted i386 Packages        
Hit http://us.archive.ubuntu.com trusty-updates Release                        
Hit http://extras.ubuntu.com trusty/main amd64 Packages                        
Hit http://security.ubuntu.com trusty-security/universe i386 Packages          
Hit http://archive.canonical.com trusty/partner i386 Packages                  
Hit http://us.archive.ubuntu.com trusty-backports Release                      
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://us.archive.ubuntu.com trusty-proposed Release                       
Hit http://security.ubuntu.com trusty-security/multiverse i386 Packages        
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Hit http://security.ubuntu.com trusty-security/main Translation-en             
Hit http://us.archive.ubuntu.com trusty/main Sources                           
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en       
Hit http://us.archive.ubuntu.com trusty/restricted Sources                     
Hit http://security.ubuntu.com trusty-security/restricted Translation-en       
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://us.archive.ubuntu.com trusty/universe Sources                       
Hit http://us.archive.ubuntu.com trusty/multiverse Sources                     
Hit http://us.archive.ubuntu.com trusty/main amd64 Packages                    
Hit http://security.ubuntu.com trusty-security/universe Translation-en         
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Ign http://archive.canonical.com trusty/partner Translation-en                 
Hit http://us.archive.ubuntu.com trusty/restricted amd64 Packages              
Hit http://us.archive.ubuntu.com trusty/universe amd64 Packages                
Hit http://ppa.launchpad.net trusty/main i386 Packages            
Hit http://us.archive.ubuntu.com trusty/multiverse amd64 Packages 
Hit http://ppa.launchpad.net trusty/main Translation-en           
Hit http://us.archive.ubuntu.com trusty/main i386 Packages        
Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages  
Hit http://us.archive.ubuntu.com trusty/universe i386 Packages                 
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages               
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://us.archive.ubuntu.com trusty/main Translation-en                    
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en              
Ign http://extras.ubuntu.com trusty/main Translation-en_US          
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en   
Ign http://extras.ubuntu.com trusty/main Translation-en                 
Hit http://us.archive.ubuntu.com trusty/universe Translation-en    
Hit http://us.archive.ubuntu.com trusty-updates/main Sources
Hit http://us.archive.ubuntu.com trusty-updates/restricted Sources
Hit http://us.archive.ubuntu.com trusty-updates/universe Sources
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Sources
Hit http://us.archive.ubuntu.com trusty-updates/main amd64 Packages
Hit http://us.archive.ubuntu.com trusty-updates/restricted amd64 Packages
Hit http://us.archive.ubuntu.com trusty-updates/universe amd64 Packages
Hit http://us.archive.ubuntu.com trusty-updates/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com trusty-updates/main i386 Packages
Hit http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages
Hit http://us.archive.ubuntu.com trusty-updates/universe i386 Packages
Hit http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages
Hit http://us.archive.ubuntu.com trusty-updates/main Translation-en
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en
Hit http://us.archive.ubuntu.com trusty-updates/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty-updates/universe Translation-en
Hit http://us.archive.ubuntu.com trusty-backports/main Sources
Hit http://us.archive.ubuntu.com trusty-backports/restricted Sources
Hit http://us.archive.ubuntu.com trusty-backports/universe Sources
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Sources
Hit http://us.archive.ubuntu.com trusty-backports/main amd64 Packages
Hit http://us.archive.ubuntu.com trusty-backports/restricted amd64 Packages
Hit http://us.archive.ubuntu.com trusty-backports/universe amd64 Packages
Hit http://us.archive.ubuntu.com trusty-backports/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com trusty-backports/main i386 Packages
Hit http://us.archive.ubuntu.com trusty-backports/restricted i386 Packages
Hit http://us.archive.ubuntu.com trusty-backports/universe i386 Packages
Hit http://us.archive.ubuntu.com trusty-backports/multiverse i386 Packages
Hit http://us.archive.ubuntu.com trusty-backports/main Translation-en
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Translation-en
Hit http://us.archive.ubuntu.com trusty-backports/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty-backports/universe Translation-en
Hit http://us.archive.ubuntu.com trusty-proposed/restricted amd64 Packages
Hit http://us.archive.ubuntu.com trusty-proposed/universe amd64 Packages
Hit http://us.archive.ubuntu.com trusty-proposed/main amd64 Packages
Hit http://us.archive.ubuntu.com trusty-proposed/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com trusty-proposed/restricted i386 Packages
Hit http://us.archive.ubuntu.com trusty-proposed/universe i386 Packages
Hit http://us.archive.ubuntu.com trusty-proposed/main i386 Packages
Hit http://us.archive.ubuntu.com trusty-proposed/multiverse i386 Packages
Hit http://us.archive.ubuntu.com trusty-proposed/main Translation-en
Hit http://us.archive.ubuntu.com trusty-proposed/multiverse Translation-en
Hit http://us.archive.ubuntu.com trusty-proposed/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty-proposed/universe Translation-en
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US
Reading package lists... Done
```

---

### Post by CantankRus on 2015-04-17
Any reason you have the proposed repo enabled?
> "Pre-released Updates". The testing area for updates. 
This repository is recommended only to those interested in helping to test updates and provide feedback."

---

### Post by Kpenguin on 2015-04-17
> **CantankRus said:**
> Any reason you have the proposed repo enabled?
Ummm....not that I know of. Should I disable this and if so, how?

---

### Post by CantankRus on 2015-04-17
Run 
```
software-properties-gtk --open-tab 2
```
and unmark proposed. This is a default setting that you must have changed.
[ATTACH=CONFIG]261381[/ATTACH]

Run 
```
sudo apt-get update
``` 
then
```
sudo apt-get dist-upgrade
```

Packages from proposed eventually come into main after a week or two testing and any problems
caused by proposed should be fixed when this happens.
If you have major problems look [**_[COLOR="#B22222"]HERE[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=432636&p=2604826#post2604826") to revert packages to main.
It's an old post but seems to still work judging from replies.

---

### Post by Kpenguin on 2015-04-17
It's still not working. I think this might be due to my router blocking the archive page since I get this error before the one above: ```
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libs/libsexy/libsexy2_0.1.11-2ubuntu1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libs/libsexy/libsexy2_0.1.11-2ubuntu1_amd64.deb) Connection failed [IP: 91.189.91.14 80]
```
I'll mess around with my router some and see if that helps.

---

### Post by CantankRus on 2015-04-17
FYI
Clicking on the link created by your post downloads the deb for me.

---

### Post by Kpenguin on 2015-04-17
It's working now. It had to do with my router.

---

