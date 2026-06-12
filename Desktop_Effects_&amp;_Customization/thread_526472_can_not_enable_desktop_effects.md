---
title: "can not enable desktop effects"
date: 2007-08-15
forum: Desktop Effects &amp; Customization
---

### Post by legend1912 on 2007-08-15
i know that there are 4 other threads about this but none of these threads solved my problem and also i switched from xp just 2 hours ago.

i go to  System>preferences>desktop effects 
And this is what i get 
[http://img518.imageshack.us/img518/7259/screenshotcj3.png](http://img518.imageshack.us/img518/7259/screenshotcj3.png)
After i click on the "enable....." this is what happens 
[http://img411.imageshack.us/img411/4530/screenshot1ra9.png](http://img411.imageshack.us/img411/4530/screenshot1ra9.png)
after a few second i am back to desktop
[http://img518.imageshack.us/img518/7259/screenshotcj3.png](http://img518.imageshack.us/img518/7259/screenshotcj3.png)

this is some info if it helps.

 *-display               
       description: VGA compatible controller
       product: 82865G Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@00:02.0
       version: 02
       size: 128MB
       width: 32 bits
       clock: 33MHz
       capabilities: vga bus_master cap_list
       configuration: latency=0
       resources: iomemory:f0000000-f7ffffff iomemory:feb80000-febfffff ioport:ed98-ed9f irq:11

Computer info:
dell b110
ram 256mb
2.5 Ghz processor speed

---

### Post by dougfractal on 2007-08-15
follow this
[http://ubuntuforums.org/showthread.php?t=481314](http://ubuntuforums.org/showthread.php?t=481314)

---

### Post by legend1912 on 2007-08-15
after i add  the code to /etc/apt/sources.list i can not save it

---

### Post by dougfractal on 2007-08-15
> First add Amaranth's repository:
add to your /etc/apt/sources.list (see [https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto](https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto) (Adding Repositories) for additional help)

sudo gedit /etc/apt/sources.list

---

### Post by legend1912 on 2007-08-15
i have it fully installed and i did everything step by step but nothing happed
look at the last 8 lines ....can that be the problem

sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get install compiz compizconfig-settings-manager
Ign [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty Release.gpg
Ign [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/main Translation-en_US             
Ign [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/restricted Translation-en_US       
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US    
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed Release.gpg [191B]             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/restricted Translation-en_US     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/main Translation-en_US           
Ign [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/universe Translation-en_US         
Ign [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/multiverse Translation-en_US       
Ign [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/deb-src Translation-en_US          
Ign [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/http://ppa.dogfood.launchpad.net/amaranth/ubuntu Translation-en_US
Ign [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/feisty Translation-en_US 
Ign [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/main Translation-en_US   
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg [191B]         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US              
Ign [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US    
Ign [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/universe Translation-en_US         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/multiverse Translation-en_US     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/universe Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed Release                
Ign [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/multiverse Translation-en_US
Ign [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US 
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg [191B] 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Ign [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/restricted Translation-en_US
Ign [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/universe Translation-en_US
Ign [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/multiverse Translation-en_US
Ign [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/deb-src Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages                   
Ign [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/http://ppa.dogfood.launchpad.net/amaranth/ubuntu Translation-en_US
Ign [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/feisty Translation-en_US           
Ign [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/main Translation-en_US             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release                                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/restricted Packages    
Ign [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/restricted Translation-en_US       
Ign [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/universe Translation-en_US         
Ign [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/multiverse Translation-en_US       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/main Packages                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/multiverse Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/universe Packages                
Ign [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/main Translation-en_US             
Ign [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/restricted Translation-en_US       
Ign [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/universe Translation-en_US         
Ign [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/multiverse Translation-en_US       
Hit [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty Release                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/restricted Sources               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/main Sources           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/multiverse Sources     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-proposed/universe Sources       
Ign [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/main Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages
Ign [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/restricted Packages
Ign [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/universe Packages
Ign [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/multiverse Packages
Ign [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/deb-src Packages
Ign [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/http://ppa.dogfood.launchpad.net/amaranth/ubuntu Packages
Ign [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/feisty Packages
Ign [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/main Packages
Ign [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/restricted Packages
Ign [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Sources
Ign [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/multiverse Packages
Ign [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/main Packages
Ign [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/restricted Packages
Ign [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/universe Packages
Ign [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/multiverse Packages
Ign [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/deb-src Packages
Ign [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/http://ppa.dogfood.launchpad.net/amaranth/ubuntu Packages
Ign [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/feisty Packages
Ign [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/main Packages
Ign [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/restricted Packages
Ign [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/universe Packages
Ign [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/multiverse Packages
Ign [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/main Packages
Ign [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/restricted Packages
Ign [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/universe Packages
Ign [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/multiverse Packages
Ign [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/main Sources
Ign [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/restricted Sources
Ign [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/universe Sources
Ign [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/multiverse Sources
Hit [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/main Packages
Hit [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/restricted Packages
Hit [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/universe Packages
Hit [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/multiverse Packages
Err [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/deb-src Packages
  404 Not Found
Err [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/http://ppa.dogfood.launchpad.net/amaranth/ubuntu Packages
  404 Not Found
Err [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/feisty Packages
  404 Not Found
Hit [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/main Packages
Hit [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/restricted Packages
Hit [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/universe Packages
Hit [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/multiverse Packages
Hit [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/main Packages
Hit [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/restricted Packages
Hit [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/universe Packages
Hit [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/multiverse Packages
Err [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/deb-src Packages
  404 Not Found
Err [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/http://ppa.dogfood.launchpad.net/amaranth/ubuntu Packages
  404 Not Found
Err [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/feisty Packages
  404 Not Found
Hit [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/main Packages
Hit [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/restricted Packages
Hit [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/universe Packages
Hit [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/multiverse Packages
Hit [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/main Packages
Hit [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/restricted Packages
Hit [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/universe Packages
Hit [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/multiverse Packages
Get:5 [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/main Sources [2070B]
Get:6 [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/restricted Sources [45B]
Get:7 [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/universe Sources [45B]
Get:8 [http://ppa.dogfood.launchpad.net](http://ppa.dogfood.launchpad.net) feisty/multiverse Sources [45B]
Fetched 2209B in 2s (946B/s)
Failed to fetch [http://ppa.dogfood.launchpad.net/amaranth/ubuntu/dists/feisty/deb-src/binary-i386/Packages.gz](http://ppa.dogfood.launchpad.net/amaranth/ubuntu/dists/feisty/deb-src/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ppa.dogfood.launchpad.net/amaranth/ubuntu/dists/feisty/http://ppa.dogfood.launchpad.net/amaranth/ubuntu/binary-i386/Packages.gz](http://ppa.dogfood.launchpad.net/amaranth/ubuntu/dists/feisty/http://ppa.dogfood.launchpad.net/amaranth/ubuntu/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ppa.dogfood.launchpad.net/amaranth/ubuntu/dists/feisty/feisty/binary-i386/Packages.gz](http://ppa.dogfood.launchpad.net/amaranth/ubuntu/dists/feisty/feisty/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ppa.dogfood.launchpad.net/amaranth/ubuntu/dists/feisty/deb-src/binary-i386/Packages.gz](http://ppa.dogfood.launchpad.net/amaranth/ubuntu/dists/feisty/deb-src/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ppa.dogfood.launchpad.net/amaranth/ubuntu/dists/feisty/http://ppa.dogfood.launchpad.net/amaranth/ubuntu/binary-i386/Packages.gz](http://ppa.dogfood.launchpad.net/amaranth/ubuntu/dists/feisty/http://ppa.dogfood.launchpad.net/amaranth/ubuntu/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ppa.dogfood.launchpad.net/amaranth/ubuntu/dists/feisty/feisty/binary-i386/Packages.gz](http://ppa.dogfood.launchpad.net/amaranth/ubuntu/dists/feisty/feisty/binary-i386/Packages.gz)  404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by dougfractal on 2007-08-15
hi legend1912

you've got one messed up /etc/apt/sources.list
can you post ...  so I can repair it.
> cat /etc/apt/sources.list


what the output > compiz --replace &

---

### Post by legend1912 on 2007-08-15
Sorry i am new and its hard to swich from window to ubuntu
compiz --replace & 

igli@igli-desktop:~$ compiz --replace &
[1] 10960
igli@igli-desktop:~$ Checking for Xgl: not present. 
Blacklisted 'vesa' driver is in use 
aborting and using fallback: /usr/bin/metacity 
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"


the /etc/apt/sources.list list

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-proposed restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-proposed restricted main multiverse universe #Added by software-properties
deb [http://ppa.dogfood.launchpad.net/amaranth/ubuntu](http://ppa.dogfood.launchpad.net/amaranth/ubuntu) feisty main restricted universe multiverse deb-src [http://ppa.dogfood.launchpad.net/amaranth/ubuntu](http://ppa.dogfood.launchpad.net/amaranth/ubuntu) feisty main restricted universe multiverse
deb [http://ppa.dogfood.launchpad.net/amaranth/ubuntu](http://ppa.dogfood.launchpad.net/amaranth/ubuntu) feisty main restricted universe multiverse deb-src [http://ppa.dogfood.launchpad.net/amaranth/ubuntu](http://ppa.dogfood.launchpad.net/amaranth/ubuntu) feisty main restricted universe multiverse
deb [http://ppa.dogfood.launchpad.net/amaranth/ubuntu](http://ppa.dogfood.launchpad.net/amaranth/ubuntu) feisty main restricted universe multiverse
deb-src [http://ppa.dogfood.launchpad.net/amaranth/ubuntu](http://ppa.dogfood.launchpad.net/amaranth/ubuntu) feisty main restricted universe multiverse

---

### Post by dougfractal on 2007-08-15
sudo rm /etc/apt/sources.list
sudo gedit /etc/apt/sources.list
> # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security restricted main multiverse universe 

#Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-proposed restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-proposed restricted main multiverse universe 

#eye candy
deb [http://ppa.dogfood.launchpad.net/amaranth/ubuntu](http://ppa.dogfood.launchpad.net/amaranth/ubuntu) feisty main restricted universe multiverse 
deb-src [http://ppa.dogfood.launchpad.net/amaranth/ubuntu](http://ppa.dogfood.launchpad.net/amaranth/ubuntu) feisty main restricted universe multiverse




sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get install compiz compizconfig-settings-manager

---

### Post by legend1912 on 2007-08-15
do i need to do everything again??

---

### Post by dougfractal on 2007-08-15
Just paste in the new sources.list
and run the update.

I've been googling your card, It may not be easy. :(

can you attach /etc/X11/xorg.conf and /var/log/Xorg.0.log . You need to save them as .txt or rightclick them and archive them .gz to post.

---

### Post by legend1912 on 2007-08-15
this is the only update that i get [http://img175.imageshack.us/img175/8955/screenshotcn4.png](http://img175.imageshack.us/img175/8955/screenshotcn4.png)
when i try to install it it says   [http://img520.imageshack.us/img520/6215/screenshot1jx4.png](http://img520.imageshack.us/img520/6215/screenshot1jx4.png)
when i press apply it starts installing new software  [http://img520.imageshack.us/img520/4461/screenshot2ml8.png](http://img520.imageshack.us/img520/4461/screenshot2ml8.png)
after it starts looking for new updates and it finds the same update..and is the same thing over and over.

xorg.conf  is attached to this post 
the other one is too large it says so here it is 

```
X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux igli-desktop 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Aug 15 16:37:10 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "DELL 1504FP"
(**) |   |-->Device "Generic Video Card"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc,
	/usr/X11R6/lib/X11/fonts/misc,
	/usr/share/fonts/X11/cyrillic,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/X11R6/lib/X11/fonts/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81c92e0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.1
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2570 card 1028,01d5 rev 02 class 06,00,00 hdr 00
(II) PCI: 00:02:0: chip 8086,2572 card 1028,01d5 rev 02 class 03,00,00 hdr 00
(II) PCI: 00:1d:0: chip 8086,24d2 card 1028,01d5 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,24d4 card 1028,01d5 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,24de card 1028,01d5 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,24dd card 1028,01d5 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev c2 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,24d0 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,24db card 1028,01d5 rev 02 class 01,01,8a hdr 00
(II) PCI: 00:1f:3: chip 8086,24d3 card 1028,01d5 rev 02 class 0c,05,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,24d5 card 1028,01d5 rev 02 class 04,01,00 hdr 00
(II) PCI: 01:00:0: chip 8086,1229 card 0e11,b0d7 rev 05 class 02,00,00 hdr 00
(II) PCI: 01:01:0: chip 8086,1080 card 1028,1000 rev 04 class 07,03,00 hdr 00
(II) PCI: 01:02:0: chip 1186,1300 card 1186,1301 rev 10 class 02,00,00 hdr 00
(II) PCI: 01:08:0: chip 8086,1050 card 1028,01d5 rev 02 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:30:0), (0,1,1), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfe800000 - 0xfeafffff (0x300000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xfc000000 - 0xfc0fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(0:2:0) Intel Corporation 82865G Integrated Graphics Controller rev 2, Mem @ 0xf0000000/27, 0xfeb80000/19, I/O @ 0xed98/3
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xf8000000 from 0xfbffffff to 0xf7ffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xfe8ff000 - 0xfe8fffff (0x1000) MX[B]
	[1] -1	0	0xfe8fdf00 - 0xfe8fdfff (0x100) MX[B]
	[2] -1	0	0xfe8fe000 - 0xfe8fefff (0x1000) MX[B]
	[3] -1	0	0xfe900000 - 0xfe9fffff (0x100000) MX[B]
	[4] -1	0	0xfc000000 - 0xfc000fff (0x1000) MX[B]
	[5] -1	0	0xfeb7f900 - 0xfeb7f9ff (0x100) MX[B]
	[6] -1	0	0xfeb7fa00 - 0xfeb7fbff (0x200) MX[B]
	[7] -1	0	0xfeb7fc00 - 0xfeb7ffff (0x400) MX[B]
	[8] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[9] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[10] -1	0	0xfeb80000 - 0xfebfffff (0x80000) MX[B](B)
	[11] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[12] -1	0	0x0000dcc0 - 0x0000dcff (0x40) IX[B]
	[13] -1	0	0x0000de00 - 0x0000deff (0x100) IX[B]
	[14] -1	0	0x0000dd00 - 0x0000ddff (0x100) IX[B]
	[15] -1	0	0x0000dca0 - 0x0000dcbf (0x20) IX[B]
	[16] -1	0	0x0000edc0 - 0x0000edff (0x40) IX[B]
	[17] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B]
	[18] -1	0	0x0000eda0 - 0x0000edbf (0x20) IX[B]
	[19] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[20] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[21] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[22] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[24] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[25] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[26] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[27] -1	0	0x0000ed98 - 0x0000ed9f (0x8) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfe8ff000 - 0xfe8fffff (0x1000) MX[B]
	[1] -1	0	0xfe8fdf00 - 0xfe8fdfff (0x100) MX[B]
	[2] -1	0	0xfe8fe000 - 0xfe8fefff (0x1000) MX[B]
	[3] -1	0	0xfe900000 - 0xfe9fffff (0x100000) MX[B]
	[4] -1	0	0xfc000000 - 0xfc000fff (0x1000) MX[B]
	[5] -1	0	0xfeb7f900 - 0xfeb7f9ff (0x100) MX[B]
	[6] -1	0	0xfeb7fa00 - 0xfeb7fbff (0x200) MX[B]
	[7] -1	0	0xfeb7fc00 - 0xfeb7ffff (0x400) MX[B]
	[8] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[9] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[10] -1	0	0xfeb80000 - 0xfebfffff (0x80000) MX[B](B)
	[11] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[12] -1	0	0x0000dcc0 - 0x0000dcff (0x40) IX[B]
	[13] -1	0	0x0000de00 - 0x0000deff (0x100) IX[B]
	[14] -1	0	0x0000dd00 - 0x0000ddff (0x100) IX[B]
	[15] -1	0	0x0000dca0 - 0x0000dcbf (0x20) IX[B]
	[16] -1	0	0x0000edc0 - 0x0000edff (0x40) IX[B]
	[17] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B]
	[18] -1	0	0x0000eda0 - 0x0000edbf (0x20) IX[B]
	[19] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[20] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[21] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[22] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[24] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[25] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[26] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[27] -1	0	0x0000ed98 - 0x0000ed9f (0x8) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfe8ff000 - 0xfe8fffff (0x1000) MX[B]
	[5] -1	0	0xfe8fdf00 - 0xfe8fdfff (0x100) MX[B]
	[6] -1	0	0xfe8fe000 - 0xfe8fefff (0x1000) MX[B]
	[7] -1	0	0xfe900000 - 0xfe9fffff (0x100000) MX[B]
	[8] -1	0	0xfc000000 - 0xfc000fff (0x1000) MX[B]
	[9] -1	0	0xfeb7f900 - 0xfeb7f9ff (0x100) MX[B]
	[10] -1	0	0xfeb7fa00 - 0xfeb7fbff (0x200) MX[B]
	[11] -1	0	0xfeb7fc00 - 0xfeb7ffff (0x400) MX[B]
	[12] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[13] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[14] -1	0	0xfeb80000 - 0xfebfffff (0x80000) MX[B](B)
	[15] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000dcc0 - 0x0000dcff (0x40) IX[B]
	[19] -1	0	0x0000de00 - 0x0000deff (0x100) IX[B]
	[20] -1	0	0x0000dd00 - 0x0000ddff (0x100) IX[B]
	[21] -1	0	0x0000dca0 - 0x0000dcbf (0x20) IX[B]
	[22] -1	0	0x0000edc0 - 0x0000edff (0x40) IX[B]
	[23] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B]
	[24] -1	0	0x0000eda0 - 0x0000edbf (0x20) IX[B]
	[25] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[26] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[27] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[28] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[30] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[31] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[32] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[33] -1	0	0x0000ed98 - 0x0000ed9f (0x8) IX[B](B)
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules//libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules//libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.2.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) Wacom driver level: 47-0.7.7-7 $
(II) VESA: driver for VESA chipsets: vesa
(II) Primary Device is: PCI 00:02:0
(--) Chipset vesa found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfe8ff000 - 0xfe8fffff (0x1000) MX[B]
	[5] -1	0	0xfe8fdf00 - 0xfe8fdfff (0x100) MX[B]
	[6] -1	0	0xfe8fe000 - 0xfe8fefff (0x1000) MX[B]
	[7] -1	0	0xfe900000 - 0xfe9fffff (0x100000) MX[B]
	[8] -1	0	0xfc000000 - 0xfc000fff (0x1000) MX[B]
	[9] -1	0	0xfeb7f900 - 0xfeb7f9ff (0x100) MX[B]
	[10] -1	0	0xfeb7fa00 - 0xfeb7fbff (0x200) MX[B]
	[11] -1	0	0xfeb7fc00 - 0xfeb7ffff (0x400) MX[B]
	[12] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[13] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[14] -1	0	0xfeb80000 - 0xfebfffff (0x80000) MX[B](B)
	[15] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000dcc0 - 0x0000dcff (0x40) IX[B]
	[19] -1	0	0x0000de00 - 0x0000deff (0x100) IX[B]
	[20] -1	0	0x0000dd00 - 0x0000ddff (0x100) IX[B]
	[21] -1	0	0x0000dca0 - 0x0000dcbf (0x20) IX[B]
	[22] -1	0	0x0000edc0 - 0x0000edff (0x40) IX[B]
	[23] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B]
	[24] -1	0	0x0000eda0 - 0x0000edbf (0x20) IX[B]
	[25] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[26] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[27] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[28] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[30] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[31] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[32] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[33] -1	0	0x0000ed98 - 0x0000ed9f (0x8) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfe8ff000 - 0xfe8fffff (0x1000) MX[B]
	[5] -1	0	0xfe8fdf00 - 0xfe8fdfff (0x100) MX[B]
	[6] -1	0	0xfe8fe000 - 0xfe8fefff (0x1000) MX[B]
	[7] -1	0	0xfe900000 - 0xfe9fffff (0x100000) MX[B]
	[8] -1	0	0xfc000000 - 0xfc000fff (0x1000) MX[B]
	[9] -1	0	0xfeb7f900 - 0xfeb7f9ff (0x100) MX[B]
	[10] -1	0	0xfeb7fa00 - 0xfeb7fbff (0x200) MX[B]
	[11] -1	0	0xfeb7fc00 - 0xfeb7ffff (0x400) MX[B]
	[12] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[13] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[14] -1	0	0xfeb80000 - 0xfebfffff (0x80000) MX[B](B)
	[15] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000dcc0 - 0x0000dcff (0x40) IX[B]
	[22] -1	0	0x0000de00 - 0x0000deff (0x100) IX[B]
	[23] -1	0	0x0000dd00 - 0x0000ddff (0x100) IX[B]
	[24] -1	0	0x0000dca0 - 0x0000dcbf (0x20) IX[B]
	[25] -1	0	0x0000edc0 - 0x0000edff (0x40) IX[B]
	[26] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B]
	[27] -1	0	0x0000eda0 - 0x0000edbf (0x20) IX[B]
	[28] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[29] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[30] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[31] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[33] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[34] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[35] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[36] -1	0	0x0000ed98 - 0x0000ed9f (0x8) IX[B](B)
	[37] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[38] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules//libvbe.so
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) VESA(0): initializing int10
(II) Loading sub module "vm86"
(II) LoadModule: "vm86"
(II) Loading /usr/lib/xorg/modules//libvm86.so
(II) Module vm86: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 8000 kB
(II) VESA(0): VESA VBE OEM: Intel(r)865G Graphics Chip Accelerated VGA BIOS
(II) VESA(0): VESA VBE OEM Software Rev: 1.0
(II) VESA(0): VESA VBE OEM Vendor: Intel Corporation
(II) VESA(0): VESA VBE OEM Product: Intel(r)865G Graphics Controller
(II) VESA(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(**) VESA(0): Depth 24, (--) framebuffer bpp 32
(==) VESA(0): RGB weight 888
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules//libddc.so
(II) VESA(0): VESA VBE DDC supported
(II) VESA(0): VESA VBE DDC Level 2
(II) VESA(0): VESA VBE DDC transfer in appr. 1 sec.
(II) VESA(0): VESA VBE DDC read successfully
(II) VESA(0): Manufacturer: DEL  Model: 300c  Serial#: 1093752922
(II) VESA(0): Year: 2003  Week: 48
(II) VESA(0): EDID Version: 1.3
(II) VESA(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) VESA(0): Sync:  Separate
(II) VESA(0): Max H-Image Size [cm]: horiz.: 30  vert.: 22
(II) VESA(0): Gamma: 2.20
(II) VESA(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) VESA(0): Default color space is primary color space
(II) VESA(0): First detailed timing is preferred mode
(II) VESA(0): redX: 0.631 redY: 0.358   greenX: 0.300 greenY: 0.580
(II) VESA(0): blueX: 0.143 blueY: 0.095   whiteX: 0.310 whiteY: 0.330
(II) VESA(0): Supported VESA Video Modes:
(II) VESA(0): 720x400@70Hz
(II) VESA(0): 640x480@60Hz
(II) VESA(0): 640x480@75Hz
(II) VESA(0): 800x600@60Hz
(II) VESA(0): 800x600@75Hz
(II) VESA(0): 1024x768@60Hz
(II) VESA(0): 1024x768@75Hz
(II) VESA(0): Manufacturer's mask: 0
(II) VESA(0): Supported additional Video Mode:
(II) VESA(0): clock: 65.0 MHz   Image Size:  304 x 228 mm
(II) VESA(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) VESA(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) VESA(0): Serial No: U30013BOA1XZ
(II) VESA(0): Monitor name: DELL 1504FP
(II) VESA(0): Ranges: V min: 56  V max: 75 Hz, H min: 30  H max: 60 kHz, PixClock max 80 MHz
(II) VESA(0): EDID (in hex):
(II) VESA(0): 	00ffffffffffff0010ac0c305a583141
(II) VESA(0): 	300d0103681e1678eebe96a15b4c9424
(II) VESA(0): 	184f54a54a0001010101010101010101
(II) VESA(0): 	01010101010164190040410026301888
(II) VESA(0): 	360030e410000018000000ff00553330
(II) VESA(0): 	303133424f4131585a0a000000fc0044
(II) VESA(0): 	454c4c203135303446500a20000000fd
(II) VESA(0): 	00384b1e3c08000a20202020202000b6
(II) VESA(0): Using EDID range info for horizontal sync
(II) VESA(0): Using EDID range info for vertical refresh
(II) VESA(0): Printing DDC gathered Modelines:
(II) VESA(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(II) VESA(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(II) VESA(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(II) VESA(0): Modeline "720x400"   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
(II) VESA(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(II) VESA(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) VESA(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(II) VESA(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) VESA(0): Searching for matching VESA mode(s):
Mode: 13c (1920x1440)
	ModeAttributes: 0x9a
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005ace
	BytesPerScanline: 1920
	XResolution: 1920
	YResolution: 1440
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 1920
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 14d (1920x1440)
	ModeAttributes: 0x9a
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005ace
	BytesPerScanline: 3840
	XResolution: 1920
	YResolution: 1440
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 3840
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 15c (1920x1440)
	ModeAttributes: 0x9a
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005ace
	BytesPerScanline: 7680
	XResolution: 1920
	YResolution: 1440
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 7680
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000
Mode: 13a (1600x1200)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005ace
	BytesPerScanline: 1600
	XResolution: 1600
	YResolution: 1200
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 3
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 1600
	BnkNumberOfImagePages: 3
	LinNumberOfImagePages: 3
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 14b (1600x1200)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005ace
	BytesPerScanline: 3200
	XResolution: 1600
	YResolution: 1200
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 3200
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
*(II) VESA(0): Not using built-in mode "1600x1200" (hsync out of range)
Mode: 15a (1600x1200)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005ace
	BytesPerScanline: 6400
	XResolution: 1600
	YResolution: 1200
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 6400
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000
Mode: 107 (1280x1024)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005ace
	BytesPerScanline: 1280
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 5
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 5
	LinNumberOfImagePages: 5
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 11a (1280x1024)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005ace
	BytesPerScanline: 2560
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 2
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 2
	LinNumberOfImagePages: 2
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
*(II) VESA(0): Not using built-in mode "1280x1024" (hsync out of range)
Mode: 11b (1280x1024)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005ace
	BytesPerScanline: 5120
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 5120
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000
Mode: 105 (1024x768)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005ace
	BytesPerScanline: 1024
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 9
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 1024
	BnkNumberOfImagePages: 9
	LinNumberOfImagePages: 9
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 117 (1024x768)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005ace
	BytesPerScanline: 2048
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 4
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 2048
	BnkNumberOfImagePages: 4
	LinNumberOfImagePages: 4
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
*Mode: 118 (1024x768)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005ace
	BytesPerScanline: 4096
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 4096
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000
*Mode: 112 (640x480)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005ace
	BytesPerScanline: 2560
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 5
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 5
	LinNumberOfImagePages: 5
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000
Mode: 114 (800x600)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005ace
	BytesPerScanline: 1600
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 7
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 1600
	BnkNumberOfImagePages: 7
	LinNumberOfImagePages: 7
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
*Mode: 115 (800x600)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005ace
	BytesPerScanline: 3200
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 3
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 3200
	BnkNumberOfImagePages: 3
	LinNumberOfImagePages: 3
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000
Mode: 101 (640x480)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005ace
	BytesPerScanline: 640
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 24
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 24
	LinNumberOfImagePages: 24
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 103 (800x600)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005ace
	BytesPerScanline: 800
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 16
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 800
	BnkNumberOfImagePages: 16
	LinNumberOfImagePages: 16
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 111 (640x480)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005ace
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 12
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 12
	LinNumberOfImagePages: 12
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000

(II) VESA(0): Total Memory: 125 64KB banks (8000kB)
(II) VESA(0): DELL 1504FP: Using hsync range of 30.00-60.00 kHz
(II) VESA(0): DELL 1504FP: Using vrefresh range of 56.00-75.00 Hz
(II) VESA(0): Not using mode "720x400" (no mode of this name)
(--) VESA(0): Virtual size is 1024x768 (pitch 1024)
(**) VESA(0): *Built-in mode "1024x768"
(**) VESA(0): *Built-in mode "800x600"
(**) VESA(0): *Built-in mode "640x480"
(**) VESA(0): Display dimensions: (300, 220) mm
(**) VESA(0): DPI set to (86, 88)
(II) VESA(0): Attempting to use 75Hz refresh for mode "1024x768" (118)
(II) VESA(0): Attempting to use 72Hz refresh for mode "800x600" (115)
(II) VESA(0): Attempting to use 73Hz refresh for mode "640x480" (112)
(**) VESA(0): Using "Shadow Framebuffer"
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/lib/xorg/modules//libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfe8ff000 - 0xfe8fffff (0x1000) MX[B]
	[5] -1	0	0xfe8fdf00 - 0xfe8fdfff (0x100) MX[B]
	[6] -1	0	0xfe8fe000 - 0xfe8fefff (0x1000) MX[B]
	[7] -1	0	0xfe900000 - 0xfe9fffff (0x100000) MX[B]
	[8] -1	0	0xfc000000 - 0xfc000fff (0x1000) MX[B]
	[9] -1	0	0xfeb7f900 - 0xfeb7f9ff (0x100) MX[B]
	[10] -1	0	0xfeb7fa00 - 0xfeb7fbff (0x200) MX[B]
	[11] -1	0	0xfeb7fc00 - 0xfeb7ffff (0x400) MX[B]
	[12] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[13] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[14] -1	0	0xfeb80000 - 0xfebfffff (0x80000) MX[B](B)
	[15] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000dcc0 - 0x0000dcff (0x40) IX[B]
	[22] -1	0	0x0000de00 - 0x0000deff (0x100) IX[B]
	[23] -1	0	0x0000dd00 - 0x0000ddff (0x100) IX[B]
	[24] -1	0	0x0000dca0 - 0x0000dcbf (0x20) IX[B]
	[25] -1	0	0x0000edc0 - 0x0000edff (0x40) IX[B]
	[26] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B]
	[27] -1	0	0x0000eda0 - 0x0000edbf (0x20) IX[B]
	[28] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[29] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[30] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[31] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[33] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[34] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[35] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[36] -1	0	0x0000ed98 - 0x0000ed9f (0x8) IX[B](B)
	[37] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[38] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 8000 kB
(II) VESA(0): VESA VBE OEM: Intel(r)865G Graphics Chip Accelerated VGA BIOS
(II) VESA(0): VESA VBE OEM Software Rev: 1.0
(II) VESA(0): VESA VBE OEM Vendor: Intel Corporation
(II) VESA(0): VESA VBE OEM Product: Intel(r)865G Graphics Controller
(II) VESA(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) VESA(0): Splitting WC range: base: 0xf0000000, size: 0x7d0000
(II) VESA(0): Splitting WC range: base: 0xf0400000, size: 0x3d0000
(II) VESA(0): Splitting WC range: base: 0xf0600000, size: 0x1d0000
(II) VESA(0): Splitting WC range: base: 0xf0700000, size: 0xd0000
(II) VESA(0): Splitting WC range: base: 0xf0780000, size: 0x50000
(==) VESA(0): Write-combining range (0xf07c0000,0x10000)
(==) VESA(0): Write-combining range (0xf0780000,0x50000)
(==) VESA(0): Write-combining range (0xf0700000,0xd0000)
(==) VESA(0): Write-combining range (0xf0600000,0x1d0000)
(==) VESA(0): Write-combining range (0xf0400000,0x3d0000)
(==) VESA(0): Write-combining range (0xf0000000,0x7d0000)
(II) VESA(0): virtual address = 0xb7352000,
	physical address = 0xf0000000, size = 8192000
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Backing store disabled
(**) Option "dpms"
(**) VESA(0): DPMS enabled
(==) RandR enabled
(II) Setting vga for screen 0.
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(EE) AIGLX: Screen 0 is not DRI capable
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/input/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/input/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/input/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!
SetClientVersion: 0 9
SetClientVersion: 0 9
SetClientVersion: 0 9
```

---

### Post by dougfractal on 2007-08-16
This is going to create a test xorg.conf then attempt to display it.
1st time round it has to setup X permissions, so you need to restart X.
Tell me how it goes.
Any problems just reboot and you will be back to square 1.


> sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.i810                                      # create a test xorg.conf
sudo sed -i 's\Driver		"vesa"\Driver		"i810"\'  /etc/X11/xorg.conf.i810      #  vesa -> i810
wget -O testx [http://redballoonlearner.co.uk/doug/ubuntu/testx.sh](http://redballoonlearner.co.uk/doug/ubuntu/testx.sh)
chmod a+x testx
sudo ./testx xorg.conf.i810

---

### Post by legend1912 on 2007-08-16
i did and the only thing i got was a black screen with /var/log/Xorg.0.log document in the middle .

Do i need to install beryl??

---

### Post by dougfractal on 2007-08-16
It worked !!! :) using the i810 driver instead of the vesa

when you press q (for quit) and went back to normal did you replace the xorg.conf.

If not run
> sudo ./testx xorg.conf.i810
as it installs the new driver and reinstates the prems.

then reset X and try compiz

---

### Post by legend1912 on 2007-08-16
there was a error window saying: 
There were errors in xorg.conf.i810 
(EE) AIGLX: Screen 0 is not DRI capable
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom

---

### Post by dougfractal on 2007-08-16
The errors aren't serious,  but you need to get i810 driver in there

In vesa 
glxgears  #(leave for 10 sec)  post

in the new i810
glxgears  #(leave for 10 sec)  post


then  install 915resolution giving this command in the terminal:
> sudo apt-get install 915resolution

restart X
glxgears  #(leave for 10 sec)  post

---

### Post by legend1912 on 2007-08-16
i did  
in the new i810
glxgears #(leave for 10 sec) post 

and this has been working for like 20 min  [http://img501.imageshack.us/img501/3339/screenshot5mp2.png](http://img501.imageshack.us/img501/3339/screenshot5mp2.png)

do i need to wait or just  type this comand on terminal      sudo apt-get install 915resolution

---

### Post by dougfractal on 2007-08-16
> In vesa
glxgears #(leave for 10 sec) post

in the new i810
glxgears #(leave for 10 sec) post


then install 915resolution giving this command in the terminal:
Quote:
sudo apt-get install 915resolution
restart X
glxgears #(leave for 10 sec) post


I just want you to benchmark the 3 different states so I can see if you are getting closer.
{ctrl+c) == kill or click close after about 10 secs then post the fps

once 915resolution is installed and X is restarted.
> 
glxinfo | grep direct

---

### Post by legend1912 on 2007-08-16
In vesa
glxgears #(leave for 10 sec) post
```
1564 frames in 5.3 seconds = 294.224 FPS
1582 frames in 5.2 seconds = 302.167 FPS
1582 frames in 5.2 seconds = 303.313 FPS
1582 frames in 5.2 seconds = 303.017 FPS
1582 frames in 5.2 seconds = 303.116 FPS

```
in the new i810
glxgears #(leave for 10 sec) post
```
1362 frames in 5.2 seconds = 264.051 FPS
1582 frames in 5.3 seconds = 299.704 FPS
1582 frames in 5.3 seconds = 297.856 FPS
1469 frames in 5.0 seconds = 291.316 FPS

```
sudo apt-get install 915resolution
```
igli@igli-desktop:~$ sudo apt-get install 915resolution
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  915resolution
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 14.6kB of archives.
After unpacking 127kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com feisty-proposed/universe 915resolution 0.5.2-10ubuntu2 [14.6kB]
Fetched 14.6kB in 0s (20.6kB/s)      
Selecting previously deselected package 915resolution.
(Reading database ... 123538 files and directories currently installed.)
Unpacking 915resolution (from .../915resolution_0.5.2-10ubuntu2_i386.deb) ...
Setting up 915resolution (0.5.2-10ubuntu2) ...
Starting 915resolution: Panel id function not supported
*** Your 915resolution was not automatically configured! ***
Please read /usr/share/doc/915resolution/README.Debian then define
MODE, XRESO, and YRESO manually in /etc/default/915resolution .
For now a default will be set, which might be inappropiate.
915resolution.
```
glxgears #(leave for 10 sec) post
```
igli@igli-desktop:~$ glxgears #(leave for 10 sec) post
1387 frames in 5.2 seconds = 264.854 FPS
1695 frames in 5.3 seconds = 320.995 FPS
1695 frames in 5.2 seconds = 323.939 FPS
1695 frames in 5.3 seconds = 319.726 FPS
```

---

### Post by dougfractal on 2007-08-16
no real improvement :(

could you post
> glxinfo

edit your xorg.conf  change defaultdepth     16
> sudo sed -i 's\DefaultDepth    24\DefaultDepth    16\' /etc/X11/xorg.conf # defaultdepth     16
restart X
> glxgears #(leave for 10 sec) post

---

### Post by legend1912 on 2007-08-16
glxinfo
```
igli@igli-desktop:~$ glxinfo
name of display: :0.0
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  16
  Current serial number in output stream:  17
igli@igli-desktop:~$
```

dit your xorg.conf change defaultdepth 16
```
igli@igli-desktop:~$ sudo sed -i 's\DefaultDepth 24\DefaultDepth 16\' /etc/X11/xorg.conf # defaultdepth 16
Password:
igli@igli-desktop:~$
```
 
glxgears #(leave for 10 sec) post
```
igli@igli-desktop:~$ glxgears #(leave for 10 sec) post
1133 frames in 5.0 seconds = 225.977 FPS
1130 frames in 5.3 seconds = 213.146 FPS
1356 frames in 5.3 seconds = 257.437 FPS
1356 frames in 5.3 seconds = 255.589 FPS
```

---

### Post by dougfractal on 2007-08-16
can  you post the /var/log/Xorg.0.log  please attach.

---

### Post by legend1912 on 2007-08-16
[http://img231.imageshack.us/img231/4928/screenshotgw4.png](http://img231.imageshack.us/img231/4928/screenshotgw4.png)
and their size is bigger than the  allowed size for attachment 

```

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux igli-desktop 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Aug 16 12:18:28 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "DELL 1504FP"
(**) |   |-->Device "Generic Video Card"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc,
	/usr/X11R6/lib/X11/fonts/misc,
	/usr/share/fonts/X11/cyrillic,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/X11R6/lib/X11/fonts/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81c92e0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.1
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2570 card 1028,01d5 rev 02 class 06,00,00 hdr 00
(II) PCI: 00:02:0: chip 8086,2572 card 1028,01d5 rev 02 class 03,00,00 hdr 00
(II) PCI: 00:1d:0: chip 8086,24d2 card 1028,01d5 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,24d4 card 1028,01d5 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,24de card 1028,01d5 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,24dd card 1028,01d5 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev c2 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,24d0 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,24db card 1028,01d5 rev 02 class 01,01,8a hdr 00
(II) PCI: 00:1f:3: chip 8086,24d3 card 1028,01d5 rev 02 class 0c,05,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,24d5 card 1028,01d5 rev 02 class 04,01,00 hdr 00
(II) PCI: 01:00:0: chip 8086,1229 card 0e11,b0d7 rev 05 class 02,00,00 hdr 00
(II) PCI: 01:01:0: chip 8086,1080 card 1028,1000 rev 04 class 07,03,00 hdr 00
(II) PCI: 01:02:0: chip 1186,1300 card 1186,1301 rev 10 class 02,00,00 hdr 00
(II) PCI: 01:08:0: chip 8086,1050 card 1028,01d5 rev 02 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:30:0), (0,1,1), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfe800000 - 0xfeafffff (0x300000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xfc000000 - 0xfc0fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(0:2:0) Intel Corporation 82865G Integrated Graphics Controller rev 2, Mem @ 0xf0000000/27, 0xfeb80000/19, I/O @ 0xed98/3
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xf8000000 from 0xfbffffff to 0xf7ffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xfe8ff000 - 0xfe8fffff (0x1000) MX[B]
	[1] -1	0	0xfe8fdf00 - 0xfe8fdfff (0x100) MX[B]
	[2] -1	0	0xfe8fe000 - 0xfe8fefff (0x1000) MX[B]
	[3] -1	0	0xfe900000 - 0xfe9fffff (0x100000) MX[B]
	[4] -1	0	0xfc000000 - 0xfc000fff (0x1000) MX[B]
	[5] -1	0	0xfeb7f900 - 0xfeb7f9ff (0x100) MX[B]
	[6] -1	0	0xfeb7fa00 - 0xfeb7fbff (0x200) MX[B]
	[7] -1	0	0xfeb7fc00 - 0xfeb7ffff (0x400) MX[B]
	[8] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[9] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[10] -1	0	0xfeb80000 - 0xfebfffff (0x80000) MX[B](B)
	[11] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[12] -1	0	0x0000dcc0 - 0x0000dcff (0x40) IX[B]
	[13] -1	0	0x0000de00 - 0x0000deff (0x100) IX[B]
	[14] -1	0	0x0000dd00 - 0x0000ddff (0x100) IX[B]
	[15] -1	0	0x0000dca0 - 0x0000dcbf (0x20) IX[B]
	[16] -1	0	0x0000edc0 - 0x0000edff (0x40) IX[B]
	[17] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B]
	[18] -1	0	0x0000eda0 - 0x0000edbf (0x20) IX[B]
	[19] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[20] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[21] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[22] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[24] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[25] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[26] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[27] -1	0	0x0000ed98 - 0x0000ed9f (0x8) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfe8ff000 - 0xfe8fffff (0x1000) MX[B]
	[1] -1	0	0xfe8fdf00 - 0xfe8fdfff (0x100) MX[B]
	[2] -1	0	0xfe8fe000 - 0xfe8fefff (0x1000) MX[B]
	[3] -1	0	0xfe900000 - 0xfe9fffff (0x100000) MX[B]
	[4] -1	0	0xfc000000 - 0xfc000fff (0x1000) MX[B]
	[5] -1	0	0xfeb7f900 - 0xfeb7f9ff (0x100) MX[B]
	[6] -1	0	0xfeb7fa00 - 0xfeb7fbff (0x200) MX[B]
	[7] -1	0	0xfeb7fc00 - 0xfeb7ffff (0x400) MX[B]
	[8] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[9] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[10] -1	0	0xfeb80000 - 0xfebfffff (0x80000) MX[B](B)
	[11] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[12] -1	0	0x0000dcc0 - 0x0000dcff (0x40) IX[B]
	[13] -1	0	0x0000de00 - 0x0000deff (0x100) IX[B]
	[14] -1	0	0x0000dd00 - 0x0000ddff (0x100) IX[B]
	[15] -1	0	0x0000dca0 - 0x0000dcbf (0x20) IX[B]
	[16] -1	0	0x0000edc0 - 0x0000edff (0x40) IX[B]
	[17] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B]
	[18] -1	0	0x0000eda0 - 0x0000edbf (0x20) IX[B]
	[19] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[20] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[21] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[22] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[24] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[25] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[26] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[27] -1	0	0x0000ed98 - 0x0000ed9f (0x8) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfe8ff000 - 0xfe8fffff (0x1000) MX[B]
	[5] -1	0	0xfe8fdf00 - 0xfe8fdfff (0x100) MX[B]
	[6] -1	0	0xfe8fe000 - 0xfe8fefff (0x1000) MX[B]
	[7] -1	0	0xfe900000 - 0xfe9fffff (0x100000) MX[B]
	[8] -1	0	0xfc000000 - 0xfc000fff (0x1000) MX[B]
	[9] -1	0	0xfeb7f900 - 0xfeb7f9ff (0x100) MX[B]
	[10] -1	0	0xfeb7fa00 - 0xfeb7fbff (0x200) MX[B]
	[11] -1	0	0xfeb7fc00 - 0xfeb7ffff (0x400) MX[B]
	[12] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[13] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[14] -1	0	0xfeb80000 - 0xfebfffff (0x80000) MX[B](B)
	[15] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000dcc0 - 0x0000dcff (0x40) IX[B]
	[19] -1	0	0x0000de00 - 0x0000deff (0x100) IX[B]
	[20] -1	0	0x0000dd00 - 0x0000ddff (0x100) IX[B]
	[21] -1	0	0x0000dca0 - 0x0000dcbf (0x20) IX[B]
	[22] -1	0	0x0000edc0 - 0x0000edff (0x40) IX[B]
	[23] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B]
	[24] -1	0	0x0000eda0 - 0x0000edbf (0x20) IX[B]
	[25] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[26] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[27] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[28] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[30] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[31] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[32] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[33] -1	0	0x0000ed98 - 0x0000ed9f (0x8) IX[B](B)
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules//libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules//libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.2.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) Wacom driver level: 47-0.7.7-7 $
(II) VESA: driver for VESA chipsets: vesa
(II) Primary Device is: PCI 00:02:0
(--) Chipset vesa found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfe8ff000 - 0xfe8fffff (0x1000) MX[B]
	[5] -1	0	0xfe8fdf00 - 0xfe8fdfff (0x100) MX[B]
	[6] -1	0	0xfe8fe000 - 0xfe8fefff (0x1000) MX[B]
	[7] -1	0	0xfe900000 - 0xfe9fffff (0x100000) MX[B]
	[8] -1	0	0xfc000000 - 0xfc000fff (0x1000) MX[B]
	[9] -1	0	0xfeb7f900 - 0xfeb7f9ff (0x100) MX[B]
	[10] -1	0	0xfeb7fa00 - 0xfeb7fbff (0x200) MX[B]
	[11] -1	0	0xfeb7fc00 - 0xfeb7ffff (0x400) MX[B]
	[12] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[13] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[14] -1	0	0xfeb80000 - 0xfebfffff (0x80000) MX[B](B)
	[15] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000dcc0 - 0x0000dcff (0x40) IX[B]
	[19] -1	0	0x0000de00 - 0x0000deff (0x100) IX[B]
	[20] -1	0	0x0000dd00 - 0x0000ddff (0x100) IX[B]
	[21] -1	0	0x0000dca0 - 0x0000dcbf (0x20) IX[B]
	[22] -1	0	0x0000edc0 - 0x0000edff (0x40) IX[B]
	[23] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B]
	[24] -1	0	0x0000eda0 - 0x0000edbf (0x20) IX[B]
	[25] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[26] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[27] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[28] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[30] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[31] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[32] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[33] -1	0	0x0000ed98 - 0x0000ed9f (0x8) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfe8ff000 - 0xfe8fffff (0x1000) MX[B]
	[5] -1	0	0xfe8fdf00 - 0xfe8fdfff (0x100) MX[B]
	[6] -1	0	0xfe8fe000 - 0xfe8fefff (0x1000) MX[B]
	[7] -1	0	0xfe900000 - 0xfe9fffff (0x100000) MX[B]
	[8] -1	0	0xfc000000 - 0xfc000fff (0x1000) MX[B]
	[9] -1	0	0xfeb7f900 - 0xfeb7f9ff (0x100) MX[B]
	[10] -1	0	0xfeb7fa00 - 0xfeb7fbff (0x200) MX[B]
	[11] -1	0	0xfeb7fc00 - 0xfeb7ffff (0x400) MX[B]
	[12] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[13] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[14] -1	0	0xfeb80000 - 0xfebfffff (0x80000) MX[B](B)
	[15] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000dcc0 - 0x0000dcff (0x40) IX[B]
	[22] -1	0	0x0000de00 - 0x0000deff (0x100) IX[B]
	[23] -1	0	0x0000dd00 - 0x0000ddff (0x100) IX[B]
	[24] -1	0	0x0000dca0 - 0x0000dcbf (0x20) IX[B]
	[25] -1	0	0x0000edc0 - 0x0000edff (0x40) IX[B]
	[26] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B]
	[27] -1	0	0x0000eda0 - 0x0000edbf (0x20) IX[B]
	[28] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[29] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[30] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[31] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[33] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[34] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[35] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[36] -1	0	0x0000ed98 - 0x0000ed9f (0x8) IX[B](B)
	[37] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[38] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules//libvbe.so
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) VESA(0): initializing int10
(II) Loading sub module "vm86"
(II) LoadModule: "vm86"
(II) Loading /usr/lib/xorg/modules//libvm86.so
(II) Module vm86: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 8000 kB
(II) VESA(0): VESA VBE OEM: Intel(r)865G Graphics Chip Accelerated VGA BIOS
(II) VESA(0): VESA VBE OEM Software Rev: 1.0
(II) VESA(0): VESA VBE OEM Vendor: Intel Corporation
(II) VESA(0): VESA VBE OEM Product: Intel(r)865G Graphics Controller
(II) VESA(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(**) VESA(0): Depth 24, (--) framebuffer bpp 32
(==) VESA(0): RGB weight 888
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules//libddc.so
(II) VESA(0): VESA VBE DDC supported
(II) VESA(0): VESA VBE DDC Level 2
(II) VESA(0): VESA VBE DDC transfer in appr. 1 sec.
(II) VESA(0): VESA VBE DDC read successfully
(II) VESA(0): Manufacturer: DEL  Model: 300c  Serial#: 1093752922
(II) VESA(0): Year: 2003  Week: 48
(II) VESA(0): EDID Version: 1.3
(II) VESA(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) VESA(0): Sync:  Separate
(II) VESA(0): Max H-Image Size [cm]: horiz.: 30  vert.: 22
(II) VESA(0): Gamma: 2.20
(II) VESA(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) VESA(0): Default color space is primary color space
(II) VESA(0): First detailed timing is preferred mode
(II) VESA(0): redX: 0.631 redY: 0.358   greenX: 0.300 greenY: 0.580
(II) VESA(0): blueX: 0.143 blueY: 0.095   whiteX: 0.310 whiteY: 0.330
(II) VESA(0): Supported VESA Video Modes:
(II) VESA(0): 720x400@70Hz
(II) VESA(0): 640x480@60Hz
(II) VESA(0): 640x480@75Hz
(II) VESA(0): 800x600@60Hz
(II) VESA(0): 800x600@75Hz
(II) VESA(0): 1024x768@60Hz
(II) VESA(0): 1024x768@75Hz
(II) VESA(0): Manufacturer's mask: 0
(II) VESA(0): Supported additional Video Mode:
(II) VESA(0): clock: 65.0 MHz   Image Size:  304 x 228 mm
(II) VESA(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
(II) VESA(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
(II) VESA(0): Serial No: U30013BOA1XZ
(II) VESA(0): Monitor name: DELL 1504FP
(II) VESA(0): Ranges: V min: 56  V max: 75 Hz, H min: 30  H max: 60 kHz, PixClock max 80 MHz
(II) VESA(0): EDID (in hex):
(II) VESA(0): 	00ffffffffffff0010ac0c305a583141
(II) VESA(0): 	300d0103681e1678eebe96a15b4c9424
(II) VESA(0): 	184f54a54a0001010101010101010101
(II) VESA(0): 	01010101010164190040410026301888
(II) VESA(0): 	360030e410000018000000ff00553330
(II) VESA(0): 	303133424f4131585a0a000000fc0044
(II) VESA(0): 	454c4c203135303446500a20000000fd
(II) VESA(0): 	00384b1e3c08000a20202020202000b6
(II) VESA(0): Using EDID range info for horizontal sync
(II) VESA(0): Using EDID range info for vertical refresh
(II) VESA(0): Printing DDC gathered Modelines:
(II) VESA(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(II) VESA(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(II) VESA(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(II) VESA(0): Modeline "720x400"   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
(II) VESA(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(II) VESA(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) VESA(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(II) VESA(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) VESA(0): Searching for matching VESA mode(s):
Mode: 13c (1920x1440)
	ModeAttributes: 0x9a
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005ace
	BytesPerScanline: 1920
	XResolution: 1920
	YResolution: 1440
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 1920
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 14d (1920x1440)
	ModeAttributes: 0x9a
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005ace
	BytesPerScanline: 3840
	XResolution: 1920
	YResolution: 1440
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 3840
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 15c (1920x1440)
	ModeAttributes: 0x9a
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005ace
	BytesPerScanline: 7680
	XResolution: 1920
	YResolution: 1440
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 7680
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000
Mode: 13a (1600x1200)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005ace
	BytesPerScanline: 1600
	XResolution: 1600
	YResolution: 1200
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 3
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 1600
	BnkNumberOfImagePages: 3
	LinNumberOfImagePages: 3
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 14b (1600x1200)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005ace
	BytesPerScanline: 3200
	XResolution: 1600
	YResolution: 1200
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 3200
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
*(II) VESA(0): Not using built-in mode "1600x1200" (hsync out of range)
Mode: 15a (1600x1200)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005ace
	BytesPerScanline: 6400
	XResolution: 1600
	YResolution: 1200
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 6400
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000
Mode: 107 (1280x1024)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005ace
	BytesPerScanline: 1280
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 5
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 5
	LinNumberOfImagePages: 5
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 11a (1280x1024)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005ace
	BytesPerScanline: 2560
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 2
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 2
	LinNumberOfImagePages: 2
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
*(II) VESA(0): Not using built-in mode "1280x1024" (hsync out of range)
Mode: 11b (1280x1024)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005ace
	BytesPerScanline: 5120
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 5120
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000
Mode: 105 (1024x768)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005ace
	BytesPerScanline: 1024
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 9
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 1024
	BnkNumberOfImagePages: 9
	LinNumberOfImagePages: 9
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 117 (1024x768)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005ace
	BytesPerScanline: 2048
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 4
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 2048
	BnkNumberOfImagePages: 4
	LinNumberOfImagePages: 4
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
*Mode: 118 (1024x768)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005ace
	BytesPerScanline: 4096
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 4096
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000
*Mode: 112 (640x480)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005ace
	BytesPerScanline: 2560
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 5
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 5
	LinNumberOfImagePages: 5
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000
Mode: 114 (800x600)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005ace
	BytesPerScanline: 1600
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 7
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 1600
	BnkNumberOfImagePages: 7
	LinNumberOfImagePages: 7
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
*Mode: 115 (800x600)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005ace
	BytesPerScanline: 3200
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 3
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 3200
	BnkNumberOfImagePages: 3
	LinNumberOfImagePages: 3
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000
Mode: 101 (640x480)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005ace
	BytesPerScanline: 640
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 24
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 24
	LinNumberOfImagePages: 24
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 103 (800x600)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005ace
	BytesPerScanline: 800
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 16
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 800
	BnkNumberOfImagePages: 16
	LinNumberOfImagePages: 16
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 111 (640x480)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005ace
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 12
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 12
	LinNumberOfImagePages: 12
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000

(II) VESA(0): Total Memory: 125 64KB banks (8000kB)
(II) VESA(0): DELL 1504FP: Using hsync range of 30.00-60.00 kHz
(II) VESA(0): DELL 1504FP: Using vrefresh range of 56.00-75.00 Hz
(II) VESA(0): Not using mode "720x400" (no mode of this name)
(--) VESA(0): Virtual size is 1024x768 (pitch 1024)
(**) VESA(0): *Built-in mode "1024x768"
(**) VESA(0): *Built-in mode "800x600"
(**) VESA(0): *Built-in mode "640x480"
(**) VESA(0): Display dimensions: (300, 220) mm
(**) VESA(0): DPI set to (86, 88)
(II) VESA(0): Attempting to use 75Hz refresh for mode "1024x768" (118)
(II) VESA(0): Attempting to use 72Hz refresh for mode "800x600" (115)
(II) VESA(0): Attempting to use 73Hz refresh for mode "640x480" (112)
(**) VESA(0): Using "Shadow Framebuffer"
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/lib/xorg/modules//libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfe8ff000 - 0xfe8fffff (0x1000) MX[B]
	[5] -1	0	0xfe8fdf00 - 0xfe8fdfff (0x100) MX[B]
	[6] -1	0	0xfe8fe000 - 0xfe8fefff (0x1000) MX[B]
	[7] -1	0	0xfe900000 - 0xfe9fffff (0x100000) MX[B]
	[8] -1	0	0xfc000000 - 0xfc000fff (0x1000) MX[B]
	[9] -1	0	0xfeb7f900 - 0xfeb7f9ff (0x100) MX[B]
	[10] -1	0	0xfeb7fa00 - 0xfeb7fbff (0x200) MX[B]
	[11] -1	0	0xfeb7fc00 - 0xfeb7ffff (0x400) MX[B]
	[12] -1	0	0xffa80800 - 0xffa80bff (0x400) MX[B]
	[13] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[14] -1	0	0xfeb80000 - 0xfebfffff (0x80000) MX[B](B)
	[15] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000dcc0 - 0x0000dcff (0x40) IX[B]
	[22] -1	0	0x0000de00 - 0x0000deff (0x100) IX[B]
	[23] -1	0	0x0000dd00 - 0x0000ddff (0x100) IX[B]
	[24] -1	0	0x0000dca0 - 0x0000dcbf (0x20) IX[B]
	[25] -1	0	0x0000edc0 - 0x0000edff (0x40) IX[B]
	[26] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B]
	[27] -1	0	0x0000eda0 - 0x0000edbf (0x20) IX[B]
	[28] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[29] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[30] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[31] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[33] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[34] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[35] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[36] -1	0	0x0000ed98 - 0x0000ed9f (0x8) IX[B](B)
	[37] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[38] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 8000 kB
(II) VESA(0): VESA VBE OEM: Intel(r)865G Graphics Chip Accelerated VGA BIOS
(II) VESA(0): VESA VBE OEM Software Rev: 1.0
(II) VESA(0): VESA VBE OEM Vendor: Intel Corporation
(II) VESA(0): VESA VBE OEM Product: Intel(r)865G Graphics Controller
(II) VESA(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) VESA(0): Splitting WC range: base: 0xf0000000, size: 0x7d0000
(II) VESA(0): Splitting WC range: base: 0xf0400000, size: 0x3d0000
(II) VESA(0): Splitting WC range: base: 0xf0600000, size: 0x1d0000
(II) VESA(0): Splitting WC range: base: 0xf0700000, size: 0xd0000
(II) VESA(0): Splitting WC range: base: 0xf0780000, size: 0x50000
(==) VESA(0): Write-combining range (0xf07c0000,0x10000)
(==) VESA(0): Write-combining range (0xf0780000,0x50000)
(==) VESA(0): Write-combining range (0xf0700000,0xd0000)
(==) VESA(0): Write-combining range (0xf0600000,0x1d0000)
(==) VESA(0): Write-combining range (0xf0400000,0x3d0000)
(==) VESA(0): Write-combining range (0xf0000000,0x7d0000)
(II) VESA(0): virtual address = 0xb731d000,
	physical address = 0xf0000000, size = 8192000
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Backing store disabled
(**) Option "dpms"
(**) VESA(0): DPMS enabled
(==) RandR enabled
(II) Setting vga for screen 0.
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(EE) AIGLX: Screen 0 is not DRI capable
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/input/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/input/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/input/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!
find_mesa_visual returned NULL for visualID = 0x0025
```

---

### Post by dougfractal on 2007-08-16
It looks like you are still using vesa.

> grep "i810" /etc/X11/xorg.conf 
**if no output then **
> sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.vesa
sudo cp /etc/X11/xorg.conf.i810 /etc/X11/xorg.conf
reboot 
> sudo reboot
then post this

> glxinfo
glxgears # fps
grep -i "dri" /var/log/Xorg.0.log

---

### Post by legend1912 on 2007-08-16
```
igli@igli-desktop:~$ glxinfo
name of display: :0.0
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  16
  Current serial number in output stream:  17
igli@igli-desktop:~$
```

```
igli@igli-desktop:~$ glxgears # fps
1613 frames in 5.5 seconds = 293.812 FPS
1356 frames in 5.1 seconds = 264.427 FPS
1356 frames in 5.2 seconds = 261.122 FPS
1356 frames in 5.2 seconds = 258.638 FPS
```

```
igli@igli-desktop:~$ grep "dri" /var/log/Xorg.0.log
        X.Org XInput driver : 0.7
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
(II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
        ABI class: X.Org XInput driver, version 0.7
        ABI class: X.Org XInput driver, version 0.7
        ABI class: X.Org XInput driver, version 0.7
(II) Wacom driver level: 47-0.7.7-7 $
(II) VESA: driver for VESA chipsets: vesa

```

---

### Post by dougfractal on 2007-08-16
I've just found this post. Although not quite running but closer than you.
[http://forum.compiz-fusion.org/showthread.php?t=3269&highlight=intel](http://forum.compiz-fusion.org/showthread.php?t=3269&highlight=intel)

```
sudo apt-get install xserver-xorg-video-intel
```

sudo /etc/X11/xorg.conf.intel
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
# sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
FontPath "/usr/share/fonts/X11/misc"
FontPath "/usr/share/fonts/X11/cyrillic"
FontPath "/usr/share/fonts/X11/100dpi/:unscaled"
FontPath "/usr/share/fonts/X11/75dpi/:unscaled"
FontPath "/usr/share/fonts/X11/Type1"
FontPath "/usr/share/fonts/X11/100dpi"
FontPath "/usr/share/fonts/X11/75dpi"
# path to defoma fonts
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
Load "i2c"
Load "bitmap"
Load "ddc"
Load "dri"
Load "extmod"
Load "freetype"
Load "glx"
Load "int10"
Load "vbe"
EndSection

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "us"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ImPS/2"
Option "ZAxisMapping" "4 5"
Option "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "stylus"
Option "Device" "/dev/input/wacom"
Option "Type" "stylus"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "eraser"
Option "Device" "/dev/input/wacom"
Option "Type" "eraser"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "cursor"
Option "Device" "/dev/input/wacom"
Option "Type" "cursor"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "Device"
Identifier "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
Driver "intel"
BusID "PCI:0:2:0"
Option "AddARGBGLXVisuals" "True"
EndSection

Section "Monitor"
Identifier "E151FP"
Option "DPMS"
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
Monitor "E151FP"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x819" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x819" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x819" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x819" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1024x768" "832x624" "800x600" "720x400" "640x819" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x819" "640x480"
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
InputDevice "stylus" "SendCoreEvents"
InputDevice "cursor" "SendCoreEvents"
InputDevice "eraser" "SendCoreEvents"
EndSection

Section "DRI"
Mode 0666
EndSection
```
```

sudo ./testx xorg.conf.intel
```You will have to reset the prems again

if successful post
```
glxinfo
glxgrears
```

---

### Post by dougfractal on 2007-08-18
have hope ;-)

I've been working on intel's the last few days and come up with a diagnostic tool

```
mkdir ~/Xinfo
cd ~/Xinfo
wget -O xinfo.sh  http://fractaldimension.org.uk/ubuntu/xinfo.txt
chmod a+x ./xinfo.sh
./xinfo.sh
```


please attach the ***xinfo.tar.gz**

view script
 [http://fractaldimension.org.uk/ubuntu/xinfo.txt](http://fractaldimension.org.uk/ubuntu/xinfo.txt)

---

