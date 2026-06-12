---
title: "problem upgrading openoffice.org 3.0 to 3.1"
date: 2009-06-11
forum: General Help
---

### Post by charonred on 2009-06-11
I have OpenOffice.org 3.0.1 installed on Ubuntu 8.04.2 and it's been running fine for months.

Yesterday OO.org notified me of an update, so I clicked the notifier in OO.org and downloaded the 3.1.0 update (OOo_3.1.0_LinuxIntel_install_en-US_deb.tar.gz) and extracted it to a folder on my desktop, but I cannot figure out how to get it to update the existing installation - If I click the 'Install' button in OO.org downloader after the download, it just greys out and goes nowhere; if I try to run the setup file in the extracted folder, same story, it goes nowhere.

I can't recall how I did the original installation of OO.org after removing the OO that came with Ubuntu.

---

### Post by kyle2595 on 2009-06-11
How do you you update Open Office in the first place?  I am running Ubuntu 9.04.

---

### Post by lindsay7 on 2009-06-11
Here is some info that may help.

[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

---

### Post by densou on 2009-06-11
> **kyle2595 said:**
> How do you you update Open Office in the first place?  I am running Ubuntu 9.04.

Just add [this PPA]("https://launchpad.net/~openoffice-pkgs/+archive/ppa") into your repositories list - that page explains how to do it eventually ;) -

---

### Post by charonred on 2009-06-11
thanks densou and lindsay7,

I've added the key and the 2 PPA repositories
> deb [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) hardy main

deb-src [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) hardy main

software sources reloaded, but that's all that happened; I'm not being informed of any updates available for OO.org 3.0 - I ran update manager and it said my system was up to date - shouldn't need to do this but I'll try a system reboot and see what happens.

---

### Post by charonred on 2009-06-11
rebooted - no update notifications; still running OO.org 3.0.1

just fired up OO.org 3 and it informed me there's an update available, yet Synaptic doesn't ?

So it looks like the only way is to use OO.org updater, but it requires me to have sufficient access rights to install - it doesn't prompt for password after downloading, so how do I set access rights ?

---

### Post by lindsay7 on 2009-06-11
Did you do, sudo apt-get update and sudo apt-get upgrade?

You could just install the new version at  [http://news.softpedia.com/news/How-to-Install-OpenOffice-org-3-1-on-Ubuntu-9-04-111105.shtml](http://news.softpedia.com/news/How-to-Install-OpenOffice-org-3-1-on-Ubuntu-9-04-111105.shtml)



How to Install OpenOffice.org 3.1 on Ubuntu 9.04


Or

How to Install OpenOffice.org 3.0 on Ubuntu 8.10 

at    [http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

---

### Post by charonred on 2009-06-11
I've just done that, but no result
> johnno@amd28u8041:~$ sudo apt-get update
[sudo] password for johnno: 
Ign cdrom://Edubuntu 8.04.1 _Hardy Heron_ - Release i386 Binary-1 (20080701.1) hardy/main Translation-en_AU
Ign cdrom://Edubuntu 8.04.1 _Hardy Heron_ - Release i386 Binary-1 (20080701.1) hardy/restricted Translation-en_AU
Ign cdrom://Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/main Translation-en_AU
Ign cdrom://Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/restricted Translation-en_AU
Ign cdrom://Kubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080701.2) hardy/main Translation-en_AU
Ign cdrom://Kubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080701.2) hardy/restricted Translation-en_AU
Ign cdrom://Mythbuntu 8.04.1 080705 i386 hardy Release.gpg                     
Ign cdrom://Mythbuntu 8.04.1 080705 i386 hardy/main Translation-en_AU          
Ign cdrom://Mythbuntu 8.04.1 080705 i386 hardy/restricted Translation-en_AU    
Ign cdrom://Mythbuntu 8.04.1 080705 i386 hardy/universe Translation-en_AU      
Ign cdrom://Mythbuntu 8.04.1 080705 i386 hardy Release                         
Hit [http://download.virtualbox.org](http://download.virtualbox.org) hardy Release.gpg                           
Ign [http://download.virtualbox.org](http://download.virtualbox.org) hardy/non-free Translation-en_AU            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg                                
Hit [http://download.virtualbox.org](http://download.virtualbox.org) hardy Release                               
Ign [http://ftp.osuosl.org](http://ftp.osuosl.org) hardy/ Release.gpg                                   
Ign [http://ftp.osuosl.org](http://ftp.osuosl.org) hardy/ Translation-en_AU                             
Hit [http://download.virtualbox.org](http://download.virtualbox.org) hardy/non-free Packages                     
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg                             
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_AU               
Ign [http://ftp.osuosl.org](http://ftp.osuosl.org) hardy/ Release                                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_AU                      
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release                                 
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg                            
Ign [http://ftp.osuosl.org](http://ftp.osuosl.org) hardy/ Packages                                      
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_AU                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release                                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en_AU                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Translation-en_AU               
Hit [http://ftp.osuosl.org](http://ftp.osuosl.org) hardy/ Packages                                      
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages                        
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_AU             
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release                                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Translation-en_AU                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Translation-en_AU     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release.gpg              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Translation-en_AU             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Translation-en_AU       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Translation-en_AU         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Translation-en_AU
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/main Translation-en_AU
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/restricted Translation-en_AU
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources                         
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/universe Translation-en_AU
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/multiverse Translation-en_AU
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security Release.gpg             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Translation-en_AU  
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages              
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Translation-en_AU
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Translation-en_AU
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Translation-en_AU
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports Release
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Sources
Reading package lists... Done
johnno@amd28u8041:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
johnno@amd28u8041:~$ 


The install guides referred to are for 9.04 and 8.10, though I imagine they are the same for 8.04.2 which is what I'm using.

If I run Update Manager, I'm told the system is up to date, even after asking it to 'Check', so something isn't working right.

If I can just set system to 'SU' mode, then I can simply use OO.org updater to download and install the update itself.

---

### Post by colau on 2009-06-11
[openoffice 3.1]("http://news.softpedia.com/news/How-to-Install-OpenOffice-org-3-1-on-Ubuntu-9-04-111105.shtml")

---

### Post by charonred on 2009-06-11
thanks colau, but I've already visited that site as per previous replies and done as suggested (added PPA sources and key), but as stated before, no update eventuates.

I've used OO.org updater 4 times now, downloaded the 3.1 update 4 times and tried to install it 4 times ... nothing 

Everytime I open OO.org Writer I'm informed of the update being available,  but can I update/install it ... NO, does Synaptic help ... NO

I am using OpenOffice.org 3.0, not OpenOffice 3.0 as supplied with Ubuntu - is there a difference in the way Synaptic handles these, are the PPA sources for the version I'm using?

this is getting frustrating .... :frown:

could the problem be that OO.org 3.0 wasn't originally installed via Synaptic, and as such Synaptic 'can't update' it ? (I installed OO.org 3.0 manually months ago, though I can't remember how).

---

### Post by lindsay7 on 2009-06-11
Here is the site to get the program file. I am not sure how to install it however.

[http://download.openoffice.org/index.html](http://download.openoffice.org/index.html)

---

### Post by lindsay7 on 2009-06-11
Here is the file info,

[ATTACH]117298[/ATTACH]

---

### Post by charonred on 2009-06-11
thanks, that's the same file I've downloaded 4 times, but I just don't know how to manually install it either.

---

### Post by lindsay7 on 2009-06-11
I download this and extracted it, but I can figure out how to install it. If you do will you post it?

Thanks,

---

### Post by charonred on 2009-06-12
got some advice on how to install 'tarballs' (.tar.gz) from [another post]("http://ubuntuforums.org/showthread.php?p=7442986&posted=1#post7442986") I made


so this is what I did in Terminal;

> ```
mkdir /home/username/tarsrc/
``` 
('[COLOR="Blue"]tarsrc[/COLOR]'  was what I named my folder for tarballs)


I moved the tarball into it, then in terminal I changed to that directory.
```
cd /home/username/tarsrc/
```



After changing directory in terminal, I checked that the tarball was there.
```
 ls
```
(listed the tarball as    [COLOR="Blue"]OOo_3.1.0_LinuxIntel_install_en-US_deb.tar.gz[/COLOR])



Then I ran this command to extract it.
```
tar -zxvf <filename>
```
( where <filename> =    [COLOR="Blue"]OOo_3.1.0_LinuxIntel_install_en-US_deb.tar.gz[/COLOR])



This created a new directory with source files, and to get the name I ran this
 ```
ls
```
(which listed the tarball and the extracted source files.
[COLOR="Blue"]OOo_3.1.0_LinuxIntel_install_en-US_deb.tar.gz[/COLOR]
[COLOR="Blue"]OOO310_m11_native_packed-4_en-US.9399[/COLOR])



next I changed to the directory with the extracted source files.
 ```
cd <directory>
``` 
(where my <directory> =   [COLOR="Blue"]OOO310_m11_native_packed-4_en-US.9399[/COLOR])


I then changed directory to the [COLOR="Blue"]DEBS[/COLOR] folder inside 
```
cd <directory>
``` 
(where the <directory> =   [COLOR="Blue"]DEBS[/COLOR])



finally I ran the following which completed the install

```
 sudo dpkg -i *.deb
```


after that I fired up OpenOffice.org 3.0 and checked the version number in the 'About' menu which was 3.10  
:D

.

---

### Post by Arup on 2009-06-12
The scribbler ppa has been updated and now it seamlessly updates to OO3.1 without the partial upgrade hassles of past. All you do is add the ppa and key and hit upgrade and viola.........you have OO3.1 on your Jaunty, Intrepid or Hardy.

---

### Post by charonred on 2009-06-12
Unless they have updated it in the last couple of hours, it won't work on my system  ... I ended up doing it the above method because I tried several times this morning to get the PPA to install the update/install files, but it just doesn't work in my system, despite adding the key and the repositories .. don't know why, and that's why I had to resorted to using the .tar.gz method.

---

### Post by lindsay7 on 2009-06-12
Your directions work great. Thanks for the tip.

---

### Post by charonred on 2009-06-12
glad it worked for you too; I got them originally from here [http://ubuntuforums.org/showpost.php?p=7442781&postcount=2]("http://ubuntuforums.org/showpost.php?p=7442781&postcount=2") - after a bit of trial and error, I figured out what worked for my system, so thought I'd post back to the forum.

---

### Post by ralphaw on 2009-06-12
TO charonred

Thanks for the info,(screen shots great for newbies like me) worked like a charm.

---

