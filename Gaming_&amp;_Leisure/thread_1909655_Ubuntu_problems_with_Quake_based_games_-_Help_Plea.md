---
title: "Ubuntu problems with Quake based games - Help Please"
date: 2012-01-15
forum: Gaming &amp; Leisure
---

### Post by SavageIntoxicant on 2012-01-15
Hello everyone, thanks for your time if you are reading this.

I am having some trouble with smokin' guns,  and wolfenstein: enemy territory.

I downloaded Smokin' Guns from PlayDeb Repository awhile ago and loved it,  but since upgrading to maverick I have been having some troubles.   

The graphics of the game are mixing up like double rifle icons where the double pistols should be,  random asci characters for bullets,  Moneybags for health bars etc etc, sometimes more are correct and sometimes less.

I attempted a fresh install from the website,  and managed to run the game with gksudo since setting the permissions were giving me difficulty.  Still the same issues.   

The windows .exe file runs in wine with the same issues.  However after deleting all that and downloading from playdeb again,  I have the same graphical issues, but the servers list wont load (stuck on getting info on -1 servers) when click get new list from internet.  

also I managed to get wolfenstein to run since I upgraded to maverick but it was EXTREMELY slow/laggy,  and now after reinstalling smokin guns from playdeb I cannot get the server list on wolfenstein anymore either.  

very confused,  Do not even know where to start,   

I will post terminal output if someone tells me how to locate the smokin' guns default directory.

Been on ubuntu for awhile but im still hopeless,  anyone willing to help me out?

p.s. Tried registering on smokin guns forum first and registration never got accepted,  however im sure the problem lies with my system not their game.

---

### Post by SavageIntoxicant on 2012-01-15
UPDATE  

Is this a chipset issue?  I have [B]Intel Corporation 82945G/GZ Integrated Graphics Controller



[/B]> **ronin@ronin-daemon:~$ lspci**
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 01)
00:1c.4 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5 (rev 01)
00:1c.5 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GH (ICH7DH) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 RAID bus controller: Intel Corporation 82801GR/GH (ICH7 Family) SATA RAID Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
06:01.0 Communication controller: Agere Systems Lucent V.92 Data/Fax Modem
06:05.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
06:08.0 Ethernet controller: Intel Corporation N10/ICH 7 Family LAN Controller (rev 01)
ronin@ronin-daemon:~$ update-pciids
update-pciids: /usr/share/misc/pci.ids.new is read-only
ronin@ronin-daemon:~$ lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 01)
00:1c.4 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5 (rev 01)
00:1c.5 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GH (ICH7DH) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 RAID bus controller: Intel Corporation 82801GR/GH (ICH7 Family) SATA RAID Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
06:01.0 Communication controller: Agere Systems Lucent V.92 Data/Fax Modem
06:05.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
06:08.0 Ethernet controller: Intel Corporation N10/ICH 7 Family LAN Controller (rev 01)
**ronin@ronin-daemon:~$ sudo apt-get update && sudo apt-get install xserver-xorg-video-intel**
[sudo] password for ronin: 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en         
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_US      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                             
Ign [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/) maverick/main Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg                  
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en  
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en   
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en   
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates Release.gpg        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                        
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release                      
Hit [http://archive.getdeb.net](http://archive.getdeb.net) oneiric-getdeb Release.gpg                      
Ign [http://archive.getdeb.net/ubuntu/](http://archive.getdeb.net/ubuntu/) oneiric-getdeb/games Translation-en
Ign [http://archive.getdeb.net/ubuntu/](http://archive.getdeb.net/ubuntu/) oneiric-getdeb/games Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports Release.gpg               
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports/main Translation-en
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources           
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports/multiverse Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports/multiverse Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse i386 Packages
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports/restricted Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports/universe Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports/universe Translation-en_US
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-proposed Release.gpg [198B]
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-proposed/main Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-proposed/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-proposed/multiverse Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-proposed/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-proposed/restricted Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-proposed/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-proposed/universe Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-proposed/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates Release            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports Release          
Hit [http://archive.getdeb.net](http://archive.getdeb.net) oneiric-getdeb Release                 
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-proposed Release [40.8kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted Sources                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe Sources      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main i386 Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/restricted Sources
Hit [http://archive.getdeb.net](http://archive.getdeb.net) oneiric-getdeb/games Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/universe i386 Packages
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-proposed/restricted Sources [14B]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-proposed/main Sources [56.7kB]    
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-proposed/multiverse Sources [1,324B]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-proposed/universe Sources [14.1kB]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-proposed/restricted i386 Packages [14B]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-proposed/main i386 Packages [137kB]
Hit [http://archive.getdeb.net](http://archive.getdeb.net) oneiric-getdeb/games i386 Packages              
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-proposed/multiverse i386 Packages [2,202B]
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-proposed/universe i386 Packages [36.6kB]
Fetched 289kB in 3s (92.8kB/s)                           
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
ronin@ronin-daemon:~$ sudo apt-get update && sudo apt-get install xserver-xorg-video-intel
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en  
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                             
Ign [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/) maverick/main Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release.gpg                         
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en         
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_US      
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release                      
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en   
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en   
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates Release.gpg        
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Hit [http://archive.getdeb.net](http://archive.getdeb.net) oneiric-getdeb Release.gpg                      
Ign [http://archive.getdeb.net/ubuntu/](http://archive.getdeb.net/ubuntu/) oneiric-getdeb/games Translation-en     
Ign [http://archive.getdeb.net/ubuntu/](http://archive.getdeb.net/ubuntu/) oneiric-getdeb/games Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources           
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports Release.gpg               
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports/main Translation-en
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main i386 Packages  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse i386 Packages
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports/multiverse Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports/restricted Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports/universe Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-proposed Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-proposed/main Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-proposed/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-proposed/multiverse Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-proposed/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-proposed/restricted Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-proposed/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-proposed/universe Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-proposed/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates Release            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports Release          
Hit [http://archive.getdeb.net](http://archive.getdeb.net) oneiric-getdeb Release                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-proposed Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted Sources                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main Sources                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/main i386 Packages
Hit [http://archive.getdeb.net](http://archive.getdeb.net) oneiric-getdeb/games Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-proposed/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-proposed/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-proposed/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-proposed/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-proposed/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-proposed/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-proposed/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-proposed/universe i386 Packages
Hit [http://archive.getdeb.net](http://archive.getdeb.net) oneiric-getdeb/games i386 Packages
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-video-intel is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ronin@ronin-daemon:~$ 


---

### Post by mastablasta on 2012-01-17
i think you probably didn't disable ppa's when you upgraded. i would try to purge previous install completelly and then reinstall. maybe that would help.
 
if you are still having problems use a PPA to upgrade your graphics card drivers.

---

### Post by SavageIntoxicant on 2012-01-17
My CD burner always burns with errors since its old.  

I have a Kubuntu install on another partition, is there a way that I can do a purge and reinstall with gparted from that distro?


I believe its setup on SDB1 but what command would I use to make sure?

---

