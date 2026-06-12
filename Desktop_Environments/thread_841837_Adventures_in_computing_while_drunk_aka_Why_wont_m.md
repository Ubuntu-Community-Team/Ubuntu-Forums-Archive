---
title: "Adventures in computing while drunk aka Why wont my panels or k-menu start up?"
date: 2008-06-26
forum: Desktop Environments
---

### Post by Wiseblood on 2008-06-26
Ok I got my kubuntu machine finally on the internet after about a month or two without any. I updated it iand it was all down loaded whe n it came up to updayting dsome NSA keygen  that was faulty. When it was installing the NSA stuff, it came u p on the detail /terminal (I was using adept) with a screen that was informing me of instructions that i need to do to reset the key ( I believe) then there was a prompt with in the screen asking for confirmation via "OK". Now here is where I screwed up. I attempted to confirm the ok by hitting enter then i went and right cliicked and made it do (cont) but it still wouildnt go {brace for idiocy} so for whatever resaon I hit User1 or what ever in the context rightclick menu on the detail screen. This promptly caused the adept manager to crash and when I tried to open it again it crashed yet again ( idont recall the error name). I then proceeded to use Synap which crashed as well. Thinking (stupidly it might all go away with a restart I restarted and then the icons loaded up but none of the panels launched and I cant open the kmenu from mouse either. Nor does it show the box on the center of the screen when I switch desktops indicating which desktop I am in. 

yossarian@Yossarian:~$ uname -a
Linux Yossarian 2.6.22-15-generic #1 SMP Tue Jun 10 09:21:34 UTC 2008 i686 GNU/Linux
yossarian@Yossarian:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 7.10
Release:        7.10
Codename:       gutsy


HEre are some of the info you might need to help sorry that it is sloppy and if I am misssing something .... I am drunk. Please help me. I really need and want my KDE!

---

### Post by Wiseblood on 2008-06-26
Help Anyone/

---

### Post by Xiong Chiamiov on 2008-06-27
When you boot into the GUI, what happens when you press alt+f2 and run kicker?

Is this KDE 3 or 4?

If you press ctrl+alt+f1 to get to a prompt, do you get any errors from the command
```

sudo apt-get update && sudo apt-get upgrade

```

---

### Post by Wiseblood on 2008-06-27
yossarian@Yossarian:~$ sudo apt-get update && sudo apt-get upgrade
[sudo] password for yossarian:
Ign [http://apt.wicd.net](http://apt.wicd.net) gutsy Release.gpg
Ign [http://apt.wicd.net](http://apt.wicd.net) gutsy/extras Translation-en_US                         
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [189B]             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US           
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg [191B]                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Translation-en_US                  
Get:3 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]                    
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_US               
Ign [http://www.getautomatix.com](http://www.getautomatix.com) gutsy Release.gpg                              
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed Release.gpg [189B]              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/main Translation-en_US            
Ign [http://www.getautomatix.com](http://www.getautomatix.com) gutsy/main Translation-en_US                   
Hit [http://apt.wicd.net](http://apt.wicd.net) gutsy Release                                          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Translation-en_US              
Ign [http://www.getautomatix.com](http://www.getautomatix.com) gutsy Release                                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Translation-en_US            
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release [58.5kB]               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/multiverse Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/universe Translation-en_US        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/restricted Translation-en_US      
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release.gpg [189B]               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Translation-en_US         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US       
Ign [http://www.getautomatix.com](http://www.getautomatix.com) gutsy/main Packages                            
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release                                 
Hit [http://apt.wicd.net](http://apt.wicd.net) gutsy/extras Packages                                  
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release.gpg [189B]            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Translation-en_US       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US 
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports Release.gpg [189B]      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/main Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/multiverse Translation-en_US
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports Release.gpg [189B]       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed Release                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release                         
Err [http://www.getautomatix.com](http://www.getautomatix.com) gutsy/main Packages                         
  404 Not Found
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/main Translation-en_US        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/multiverse Translation-en_US  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/universe Translation-en_US    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release                         
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/main Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports Release             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports Release              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/multiverse Packages      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Packages       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Packages     
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages [101kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Sources    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/universe Sources
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages [5280B]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources [19.0kB]      
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages [74.6kB] 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-backports/multiverse Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/multiverse Packages
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources [11.3kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/universe Packages
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages [5774B]
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources [812B]
Fetched 276kB in 5s (51.0kB/s)                         
Failed to fetch [http://www.getautomatix.com/apt/dists/gutsy/main/binary-i386/Packages.gz](http://www.getautomatix.com/apt/dists/gutsy/main/binary-i386/Packages.gz)  404 Not Found
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

There we go

I am now using gnome which I dislike.

---

### Post by Wiseblood on 2008-06-27
Help me please, guys it is annoying (gnome).

---

### Post by Wiseblood on 2008-06-27
Just noticed the previous questions. I run KDE 3.5 and I will try that kicker thing. what is the commenad?

And thanks for responding though. :)

---

### Post by Wiseblood on 2008-06-29
Please help me anyone?

---

