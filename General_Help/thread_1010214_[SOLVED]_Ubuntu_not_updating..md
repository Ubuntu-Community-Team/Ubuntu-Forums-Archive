---
title: "[SOLVED] Ubuntu not updating."
date: 2008-12-13
forum: General Help
---

### Post by maddog46113 on 2008-12-13
Ive noticed my room mates computer has updated numerous times since mine has. When i run apt-get update I get this. 

```

Hit http://archive.canonical.com intrepid Release.gpg
Ign http://archive.canonical.com intrepid/partner Translation-en_US
Ign http://ppa.launchpad.net intrepid Release.gpg                              
Hit http://security.ubuntu.com intrepid-security Release.gpg                   
Ign http://security.ubuntu.com intrepid-security/main Translation-en_US        
Ign http://security.ubuntu.com intrepid-security/restricted Translation-en_US  
Ign http://ppa.launchpad.net intrepid/main Translation-en_US                   
Hit http://us.archive.ubuntu.com intrepid Release.gpg                          
Ign http://us.archive.ubuntu.com intrepid/main Translation-en_US               
Ign http://us.archive.ubuntu.com intrepid/restricted Translation-en_US         
Hit http://repository.akirad.net akirad-intrepid Release.gpg                   
Ign http://repository.akirad.net akirad-intrepid/main Translation-en_US        
Hit http://archive.canonical.com intrepid Release                              
Ign http://security.ubuntu.com intrepid-security/universe Translation-en_US    
Ign http://security.ubuntu.com intrepid-security/multiverse Translation-en_US  
Hit http://security.ubuntu.com intrepid-security Release                       
Ign http://us.archive.ubuntu.com intrepid/universe Translation-en_US           
Ign http://us.archive.ubuntu.com intrepid/multiverse Translation-en_US         
Hit http://us.archive.ubuntu.com intrepid-updates Release.gpg                  
Ign http://us.archive.ubuntu.com intrepid-updates/main Translation-en_US       
Ign http://us.archive.ubuntu.com intrepid-updates/restricted Translation-en_US 
Ign http://us.archive.ubuntu.com intrepid-updates/universe Translation-en_US   
Ign http://us.archive.ubuntu.com intrepid-updates/multiverse Translation-en_US 
Get:1 http://ppa.launchpad.net intrepid Release [27.6kB]                       
Hit http://us.archive.ubuntu.com intrepid-backports Release.gpg                
Ign http://us.archive.ubuntu.com intrepid-backports/main Translation-en_US
Hit http://repository.akirad.net akirad-intrepid Release                       
Ign http://us.archive.ubuntu.com intrepid-backports/restricted Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-backports/universe Translation-en_US 
Hit http://archive.canonical.com intrepid/partner Packages                     
Ign http://ppa.launchpad.net intrepid/main Packages                            
Hit http://security.ubuntu.com intrepid-security/main Packages                 
Hit http://repository.akirad.net akirad-intrepid/main Packages                 
Ign http://us.archive.ubuntu.com intrepid-backports/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com intrepid Release                              
Hit http://archive.canonical.com intrepid/partner Sources            
Hit http://us.archive.ubuntu.com intrepid-updates Release            
Hit http://ppa.launchpad.net intrepid/main Packages                            
Hit http://us.archive.ubuntu.com intrepid-backports Release          
Hit http://security.ubuntu.com intrepid-security/restricted Packages
Hit http://security.ubuntu.com intrepid-security/main Sources       
Hit http://security.ubuntu.com intrepid-security/restricted Sources 
Hit http://us.archive.ubuntu.com intrepid/main Packages             
Hit http://us.archive.ubuntu.com intrepid/restricted Packages
Hit http://us.archive.ubuntu.com intrepid/main Sources
Hit http://us.archive.ubuntu.com intrepid/restricted Sources
Hit http://us.archive.ubuntu.com intrepid/universe Packages
Hit http://security.ubuntu.com intrepid-security/universe Packages
Hit http://security.ubuntu.com intrepid-security/universe Sources
Hit http://security.ubuntu.com intrepid-security/multiverse Packages
Hit http://security.ubuntu.com intrepid-security/multiverse Sources
Hit http://us.archive.ubuntu.com intrepid/universe Sources
Hit http://us.archive.ubuntu.com intrepid/multiverse Packages
Hit http://us.archive.ubuntu.com intrepid/multiverse Sources
Hit http://us.archive.ubuntu.com intrepid-updates/main Packages
Hit http://us.archive.ubuntu.com intrepid-updates/restricted Packages
Hit http://us.archive.ubuntu.com intrepid-updates/main Sources
Hit http://us.archive.ubuntu.com intrepid-updates/restricted Sources
Hit http://us.archive.ubuntu.com intrepid-updates/universe Packages
Hit http://us.archive.ubuntu.com intrepid-updates/universe Sources
Hit http://us.archive.ubuntu.com intrepid-updates/multiverse Packages
Hit http://us.archive.ubuntu.com intrepid-updates/multiverse Sources
Hit http://us.archive.ubuntu.com intrepid-backports/main Packages
Hit http://us.archive.ubuntu.com intrepid-backports/restricted Packages
Hit http://us.archive.ubuntu.com intrepid-backports/universe Packages
Hit http://us.archive.ubuntu.com intrepid-backports/multiverse Packages
Hit http://us.archive.ubuntu.com intrepid-backports/main Sources
Hit http://us.archive.ubuntu.com intrepid-backports/restricted Sources
Hit http://us.archive.ubuntu.com intrepid-backports/universe Sources
Hit http://us.archive.ubuntu.com intrepid-backports/multiverse Sources
Fetched 1B in 1s (1B/s)
Reading package lists... Done

```

I noticed some of the URLS not hitting.

Heres my sources list.

```

# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu intrepid partner
deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb http://security.ubuntu.com/ubuntu intrepid-security universe
deb-src http://security.ubuntu.com/ubuntu intrepid-security universe
deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb http://ppa.launchpad.net/spring/ubuntu intrepid main

```

Please help :( I appreciate everyones comment ahead of time. Thanks

---

### Post by taurus on 2008-12-13
What happens if you run

```
sudo apt-get upgrade
```

---

### Post by maddog46113 on 2008-12-13
```
aaron@Demonic:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Thats what happens.

---

### Post by gjoellee on 2008-12-13
your system is up-to-date my friend

---

### Post by taurus on 2008-12-13
Maybe you have your system updating automatically in the background so you don't have to run it by hand.

Look in System -> Administrations -> Synaptic Package Manager -> Settings -> Preferences.

---

### Post by maddog46113 on 2008-12-13
odd when I run the update manager in interface alot of the urls fail. Doesnt appear to be updating in the background. Im clueless.

---

### Post by maddog46113 on 2008-12-13
*Bump* Anyone have any ideas. I know my system is not up to date. It hasnt updated in about a week. My room mates has updated a few times, his PC also is not failing on any of the sources whereas mine does.

---

### Post by taurus on 2008-12-13
> **maddog46113 said:**
> odd when I run the update manager in interface alot of the urls fail. Doesnt appear to be updating in the background. Im clueless.

Can you post a screenshot of that (Applications -> Accessories -> Take Screenshot)?

---

### Post by drs305 on 2008-12-13
Open Synaptic (or Software Sources). Settings, Repositories, Ubuntu Software: Make sure the main repositories you want are ticked. 

Updates tab: Again, make sure you have the ones you want ticked. Also note your auto-update settings.

Third-Party tab: Make sure you have these ticked if desired.

Back to the main Ubuntu Software tab: Download from > Other and change to another server and see if that helps.

Hit Reload.

In terminal, try 
```

sudo apt-get update    # same as Reload
sudo apt-get upgrade

```

---

### Post by maddog46113 on 2008-12-14
here is a screenshot of whats going on...

[img]http://img525.imageshack.us/img525/3114/screenshot1zq8.png[/img]

---

### Post by maddog46113 on 2008-12-15
*bump* :(

---

### Post by maddog46113 on 2008-12-15
*bump* again anyone?

i found out something else thanks to mr. drs. 

If i type 

Sudo aptitude install 2vcard i get this:
```

aaron@Demonic:~$ sudo aptitude install 2vcard
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Segmentation fault

```

However it i type sudo apt-get 2vcard i get this.
```

aaron@Demonic:~$ sudo apt-get install 2vcard
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  2vcard
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 14.3kB of archives.
After this operation, 111kB of additional disk space will be used.
Get:1 http://mirrors.acm.jhu.edu intrepid/universe 2vcard 0.5-3 [14.3kB]
Fetched 14.3kB in 0s (50.6kB/s)
^CE: Sub-process /usr/bin/dpkg exited unexpectedly
aaron@Demonic:~$ sudo apt-get install 2vcard
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  2vcard
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/14.3kB of archives.
After this operation, 111kB of additional disk space will be used.
Selecting previously deselected package 2vcard.
(Reading database ... 157907 files and directories currently installed.)
Unpacking 2vcard (from .../archives/2vcard_0.5-3_all.deb) ...
Processing triggers for man-db ...
Setting up 2vcard (0.5-3) ...

```

Im utterly confused at this point...

---

### Post by trentscott4 on 2008-12-15
Are you by chance running behind a proxy of some sort or different ethernet line?

---

### Post by philinux on 2008-12-15
System>admin>software sources. Change the server and see if that sorts it.

---

### Post by darkknight045 on 2008-12-15
Looking at all this I would have to guess that your roommates probably got more repositories enabled than you do.

This is no cause for concern, if he has Proposed enabled in his repositories that means he's getting updates that haven't been considered ready for a distro-wide release.  I wouldn't recommend these for some looking to keep their system stable, I've had a few Proposed update break something on me that I had to tinker with to get back running.

You system doesn't appear to be failing on an update, so I wouldn't worry about it.

As for the URLs failing, it looks like its simply ignoring some links and looking elsewhere.  This does not appear unusual.
_____

For independent confirmation of my theories please post what repositories you have enabled, and also post the repositories your roommate has enabled.  Also can you confirm that you are running the same version as he is (8.10 as opposed to 8.04 or 7.10 etc.)?

---

### Post by maddog46113 on 2008-12-15
I finally got it to update. Here is what i done.

I removed the bin cache files

```

sudo apt-get clean

```

and.....

[img]http://img243.imageshack.us/img243/379/screenshotwr1.png[/img]

---

