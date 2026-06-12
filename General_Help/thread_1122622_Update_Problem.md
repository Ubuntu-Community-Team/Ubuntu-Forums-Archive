---
title: "Update Problem"
date: 2009-04-11
forum: General Help
---

### Post by Naz_Farooq on 2009-04-11
Hi guys,
I have been facing a big problem for last few days but now after a hard struggle I have fixed it. The Problem was that, through a LAN Cable, I could access to main server and internet when using Ubuntu 8.10 but when I started WindowsXP, it started working well. But now I have fixed it. There is an other problem for me now. My system was last updated 38 days ago. Now when I start update manager and press "check" button for updates, it gives me errors. Some errors are of signature & some are others. I have attached a picture of the errors.
Please help me in this regard. What should I do to fix this problem.
Thanks in advance.

---

### Post by taurus on 2009-04-11
You've added some third-party repos to your /etc/apt/sources.list so you need to import the keys for them as well.  And by the way, are you running hardy or intrepid because it looks like you have both hardy and intrepid repos in /etc/apt/sources.list?

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

### Post by Naz_Farooq on 2009-04-11
> **taurus said:**
> You've added some third-party repos to your /etc/apt/sources.list so you need to import the keys for them as well.  And by the way, are you running hardy or intrepid because it looks like you have both hardy and intrepid repos in /etc/apt/sources.list?

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

I am running intrepid 8.10
this is the result from the command you suggested for me.
```
nazfarooq@nazfarooq-laptop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ae.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://ae.archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ae.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://ae.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ae.archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://ae.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://ae.archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://ae.archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ae.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://ae.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://ae.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://ae.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ae.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://ae.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu intrepid partner
# deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb http://security.ubuntu.com/ubuntu intrepid-security universe
deb-src http://security.ubuntu.com/ubuntu intrepid-security universe
deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb http://ppa.launchpad.net/compiz/ubuntu intrepid main #Compiz Fusion
deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb http://ppa.launchpad.net/awn-testing/ubuntu hardy main
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main #OpenOffice.org
deb http://archive.ubuntu.org.cn/ubuntu-cn/ intrepid main restricted universe multiverse #Ubuntu Chinese Repository
deb http://ppa.launchpad.net/fta/ubuntu intrepid main #Firefox
deb http://ppa.launchpad.net/stemp/ubuntu intrepid main #Midori
deb http://download.skype.com/linux/repos/debian stable non-free #Skype
deb http://deb.opera.com/opera/ lenny non-free #Opera
deb http://ppa.launchpad.net/project-neon/ubuntu/ intrepid main #Amarok
deb http://ppa.launchpad.net/reacocard-awn/ubuntu/ intrepid main #Avant Window Navigator
# deb http://repository.cairo-dock.org/ubuntu intrepid cairo-dock #Cairo Dock
# deb http://ppa.launchpad.net/do-core/ubuntu intrepid main #GNOME Do
# deb http://ppa.launchpad.net/banshee-team/ubuntu intrepid main #Banshee (Stable Version)
# deb http://ppa.launchpad.net/banshee-unstable-team/ubuntu intrepid main #Banshee (Unstable Version)
# deb http://dl.google.com/linux/deb/ stable non-free #Google
# deb http://ppa.launchpad.net/lidaobing/ubuntu intrepid main #Chmsee
# deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu intrepid main #KDE 4
deb http://www.getdropbox.com/static/ubuntu intrepid main #Nautilus DropBox
# deb http://ppa.launchpad.net/tualatrix/ubuntu intrepid main #Ubuntu Tweak
# deb http://ppa.launchpad.net/gilir/ubuntu intrepid main #Screenlets
deb http://wine.budgetdedicated.com/apt intrepid main #Wine
# deb http://download.virtualbox.org/virtualbox/debian intrepid non-free #VirtualBox
# deb http://ppa.launchpad.net/gnome-terminator/ubuntu intrepid main #Terminator
# deb http://ppa.launchpad.net/gscrot/ubuntu intrepid main #GScrot
# deb http://packages.medibuntu.org/ intrepid free non-free #Medibuntu
# deb http://ppa.launchpad.net/team-xbmc/ubuntu intrepid main #XBMC
deb-src http://ppa.launchpad.net/awn-testing/ubuntu hardy main
deb http://apt.wicd.net hardy extras
```

what should I do now

---

### Post by taurus on 2009-04-11
> [COLOR="Red"]deb-src [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main[/COLOR]
deb [http://apt.wicd.net](http://apt.wicd.net) hardy extras

You have three entries for hardy (two duplicate in red) so you need to edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and either put a # in front of those three entries to comment them out or replace the word **hardy** with **intrepid**.  Save it and run

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Naz_Farooq on 2009-04-11
> **taurus said:**
> You have three entries for hardy (two duplicate in red) so you need to edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and either put a # in front of those three entries to comment them out or replace the word **hardy** with **intrepid**.  Save it and run

```
sudo apt-get update
sudo apt-get upgrade
```

Thanx but it did not fix my problem. I got this
```
nazfarooq@nazfarooq-laptop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ae.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://ae.archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ae.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://ae.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ae.archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://ae.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://ae.archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://ae.archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ae.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://ae.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://ae.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://ae.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ae.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://ae.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu intrepid partner
# deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb http://security.ubuntu.com/ubuntu intrepid-security universe
deb-src http://security.ubuntu.com/ubuntu intrepid-security universe
deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb http://ppa.launchpad.net/compiz/ubuntu intrepid main #Compiz Fusion
deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb http://ppa.launchpad.net/awn-testing/ubuntu hardy main
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main #OpenOffice.org
deb http://archive.ubuntu.org.cn/ubuntu-cn/ intrepid main restricted universe multiverse #Ubuntu Chinese Repository
deb http://ppa.launchpad.net/fta/ubuntu intrepid main #Firefox
deb http://ppa.launchpad.net/stemp/ubuntu intrepid main #Midori
deb http://download.skype.com/linux/repos/debian stable non-free #Skype
deb http://deb.opera.com/opera/ lenny non-free #Opera
deb http://ppa.launchpad.net/project-neon/ubuntu/ intrepid main #Amarok
deb http://ppa.launchpad.net/reacocard-awn/ubuntu/ intrepid main #Avant Window Navigator
# deb http://repository.cairo-dock.org/ubuntu intrepid cairo-dock #Cairo Dock
# deb http://ppa.launchpad.net/do-core/ubuntu intrepid main #GNOME Do
# deb http://ppa.launchpad.net/banshee-team/ubuntu intrepid main #Banshee (Stable Version)
# deb http://ppa.launchpad.net/banshee-unstable-team/ubuntu intrepid main #Banshee (Unstable Version)
# deb http://dl.google.com/linux/deb/ stable non-free #Google
# deb http://ppa.launchpad.net/lidaobing/ubuntu intrepid main #Chmsee
# deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu intrepid main #KDE 4
deb http://www.getdropbox.com/static/ubuntu intrepid main #Nautilus DropBox
# deb http://ppa.launchpad.net/tualatrix/ubuntu intrepid main #Ubuntu Tweak
# deb http://ppa.launchpad.net/gilir/ubuntu intrepid main #Screenlets
deb http://wine.budgetdedicated.com/apt intrepid main #Wine
# deb http://download.virtualbox.org/virtualbox/debian intrepid non-free #VirtualBox
# deb http://ppa.launchpad.net/gnome-terminator/ubuntu intrepid main #Terminator
# deb http://ppa.launchpad.net/gscrot/ubuntu intrepid main #GScrot
# deb http://packages.medibuntu.org/ intrepid free non-free #Medibuntu
# deb http://ppa.launchpad.net/team-xbmc/ubuntu intrepid main #XBMC
deb-src http://ppa.launchpad.net/awn-testing/ubuntu hardy main
deb http://apt.wicd.net hardy extras
nazfarooq@nazfarooq-laptop:~$ gksudo gedit /etc/apt/source.list
nazfarooq@nazfarooq-laptop:~$ sudo apt-get update
Ign http://download.skype.com stable Release.gpg
Ign http://download.skype.com stable/non-free Translation-en_US                
Ign http://download.skype.com stable Release                                   
Ign http://download.skype.com stable/non-free Packages                         
Err http://download.skype.com stable/non-free Packages                         
  403 Forbidden [IP: 204.9.165.82 80]
Hit http://apt.wicd.net hardy Release.gpg                                      
Ign http://apt.wicd.net hardy/extras Translation-en_US                         
Hit http://apt.wicd.net hardy Release                                          
Ign http://apt.wicd.net hardy/extras Packages                                  
Hit http://apt.wicd.net hardy/extras Packages                                  
Get:1 http://security.ubuntu.com intrepid-security Release.gpg [189B]          
Hit http://deb.opera.com lenny Release.gpg                                     
Ign http://security.ubuntu.com intrepid-security/main Translation-en_US        
Hit http://ae.archive.ubuntu.com intrepid Release.gpg                          
Ign http://security.ubuntu.com intrepid-security/restricted Translation-en_US  
Ign http://security.ubuntu.com intrepid-security/universe Translation-en_US    
Ign http://security.ubuntu.com intrepid-security/multiverse Translation-en_US  
Get:2 http://security.ubuntu.com intrepid-security Release [51.2kB]            
Err http://security.ubuntu.com intrepid-security Release                       
  
Ign http://ae.archive.ubuntu.com intrepid/main Translation-en_US               
Ign http://ppa.launchpad.net intrepid Release.gpg                              
Ign http://ppa.launchpad.net intrepid/main Translation-en_US                   
Ign http://deb.opera.com lenny/non-free Translation-en_US                      
Get:3 http://ppa.launchpad.net hardy Release.gpg [307B]                        
Ign http://ae.archive.ubuntu.com intrepid/restricted Translation-en_US         
Ign http://ppa.launchpad.net hardy/main Translation-en_US                      
Ign http://ae.archive.ubuntu.com intrepid/universe Translation-en_US           
Hit http://deb.opera.com lenny Release                                         
Hit http://ppa.launchpad.net intrepid Release.gpg                              
Ign http://ae.archive.ubuntu.com intrepid/multiverse Translation-en_US         
Get:4 http://ae.archive.ubuntu.com intrepid-updates Release.gpg [189B]         
Ign http://ae.archive.ubuntu.com intrepid-updates/main Translation-en_US       
Ign http://deb.opera.com lenny/non-free Packages                               
Ign http://ppa.launchpad.net intrepid/main Translation-en_US                   
Ign http://ae.archive.ubuntu.com intrepid-updates/restricted Translation-en_US 
Hit http://ppa.launchpad.net intrepid Release.gpg                              
Ign http://ae.archive.ubuntu.com intrepid-updates/universe Translation-en_US   
Hit http://deb.opera.com lenny/non-free Packages                               
Ign http://ae.archive.ubuntu.com intrepid-updates/multiverse Translation-en_US 
Ign http://ppa.launchpad.net intrepid/main Translation-en_US                   
Hit http://ppa.launchpad.net intrepid Release.gpg                              
Hit http://wine.budgetdedicated.com intrepid Release.gpg                       
Hit http://ae.archive.ubuntu.com intrepid Release                              
Get:5 http://ae.archive.ubuntu.com intrepid-updates Release [51.2kB]           
Err http://ae.archive.ubuntu.com intrepid-updates Release                      
  
Hit http://ae.archive.ubuntu.com intrepid/main Packages                        
Hit http://ae.archive.ubuntu.com intrepid/restricted Packages                  
Ign http://ppa.launchpad.net intrepid/main Translation-en_US                   
Hit http://ppa.launchpad.net intrepid Release.gpg                              
Ign http://wine.budgetdedicated.com intrepid/main Translation-en_US            
Hit http://ae.archive.ubuntu.com intrepid/main Sources                         
Ign http://archive.ubuntu.org.cn intrepid Release.gpg                          
Hit http://ae.archive.ubuntu.com intrepid/restricted Sources                   
Hit http://ae.archive.ubuntu.com intrepid/universe Packages                    
Hit http://wine.budgetdedicated.com intrepid Release                           
Hit http://ae.archive.ubuntu.com intrepid/universe Sources                     
Ign http://ppa.launchpad.net intrepid/main Translation-en_US                   
Hit http://ae.archive.ubuntu.com intrepid/multiverse Packages                  
Hit http://ae.archive.ubuntu.com intrepid/multiverse Sources                   
Ign http://ppa.launchpad.net intrepid Release.gpg                              
Ign http://wine.budgetdedicated.com intrepid/main Packages                     
Ign http://ppa.launchpad.net intrepid/main Translation-en_US                   
Hit http://wine.budgetdedicated.com intrepid/main Packages                     
Get:6 http://ppa.launchpad.net intrepid Release [27.6kB]                       
Get:7 http://ppa.launchpad.net hardy Release [46.7kB]                          
Ign http://ppa.launchpad.net hardy Release                                     
Hit http://ppa.launchpad.net intrepid Release                                  
Ign http://www.getdropbox.com intrepid Release.gpg                             
Hit http://ppa.launchpad.net intrepid Release                                  
Ign http://www.getdropbox.com intrepid/main Translation-en_US                  
Hit http://ppa.launchpad.net intrepid Release                                  
Hit http://ppa.launchpad.net intrepid Release                                  
Ign http://www.getdropbox.com intrepid Release                                 
Get:8 http://ppa.launchpad.net intrepid Release [27.6kB]                       
Ign http://www.getdropbox.com intrepid/main Packages                           
Ign http://ppa.launchpad.net intrepid/main Packages                            
Ign http://ppa.launchpad.net hardy/main Packages                               
Hit http://www.getdropbox.com intrepid/main Packages                           
Ign http://ppa.launchpad.net hardy/main Sources                                
Ign http://ppa.launchpad.net intrepid/main Packages                            
Ign http://ppa.launchpad.net intrepid/main Packages                            
Ign http://ppa.launchpad.net intrepid/main Packages                            
Ign http://ppa.launchpad.net intrepid/main Packages                            
Ign http://ppa.launchpad.net intrepid/main Packages                            
Hit http://ppa.launchpad.net intrepid/main Packages                            
Hit http://ppa.launchpad.net hardy/main Packages                               
Ign http://archive.ubuntu.org.cn intrepid/main Translation-en_US               
Hit http://ppa.launchpad.net hardy/main Sources                                
Hit http://ppa.launchpad.net intrepid/main Packages                            
Hit http://ppa.launchpad.net intrepid/main Packages                            
Hit http://ppa.launchpad.net intrepid/main Packages                            
Hit http://ppa.launchpad.net intrepid/main Packages                            
Hit http://ppa.launchpad.net intrepid/main Packages                            
Ign http://archive.ubuntu.org.cn intrepid/restricted Translation-en_US         
Ign http://archive.ubuntu.org.cn intrepid/universe Translation-en_US           
Ign http://archive.ubuntu.org.cn intrepid/multiverse Translation-en_US         
Ign http://archive.ubuntu.org.cn intrepid Release                              
Ign http://archive.ubuntu.org.cn intrepid/main Packages
Ign http://archive.ubuntu.org.cn intrepid/restricted Packages
Ign http://archive.ubuntu.org.cn intrepid/universe Packages
Ign http://archive.ubuntu.org.cn intrepid/multiverse Packages
Get:9 http://archive.ubuntu.org.cn intrepid/main Packages [85.0kB]
Hit http://archive.ubuntu.org.cn intrepid/restricted Packages                  
Hit http://archive.ubuntu.org.cn intrepid/universe Packages                    
Hit http://archive.ubuntu.org.cn intrepid/multiverse Packages               
Fetched 85.6kB in 32s (2668B/s)                                                
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://security.ubuntu.com intrepid-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://ae.archive.ubuntu.com intrepid-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: http://ppa.launchpad.net hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7D2C7A23BF810CD5
W: Failed to fetch http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-i386/Packages.gz  403 Forbidden [IP: 204.9.165.82 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/intrepid-security/Release  

W: Failed to fetch http://ae.archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
nazfarooq@nazfarooq-laptop:~$ sudo upgrade
sudo: upgrade: command not found
nazfarooq@nazfarooq-laptop:~$ sudo apt-get upgrade
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
nazfarooq@nazfarooq-laptop:~$ 
```

is there any way to solve it? please help me. I want to update my system.

---

### Post by taurus on 2009-04-11
Post your new /etc/apt/sources.list again.  And by the way, you have another process, adept, running in the background so that's why you got an error message when you ran sudo apt-get update.

p.s.  Personally, I would comment out all those repos that you added them in by hand.  They cause more trouble than anything else.

---

### Post by Naz_Farooq on 2009-04-12
> **taurus said:**
> Post your new /etc/apt/sources.list again.  And by the way, you have another process, adept, running in the background so that's why you got an error message when you ran sudo apt-get update.

p.s.  Personally, I would comment out all those repos that you added them in by hand.  They cause more trouble than anything else.

Hi,
now I am getting this problem. check the attachment and please give me a solution.
how to get source list?
what should I type in terminal for source list.

---

### Post by Naz_Farooq on 2009-04-12
here is my latest source list.
```
 # deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ae.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://ae.archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ae.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://ae.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ae.archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://ae.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://ae.archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://ae.archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ae.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://ae.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://ae.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://ae.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ae.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://ae.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu intrepid partner
# deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb http://security.ubuntu.com/ubuntu intrepid-security universe
deb-src http://security.ubuntu.com/ubuntu intrepid-security universe
deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb http://ppa.launchpad.net/compiz/ubuntu intrepid main #Compiz Fusion
deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb http://ppa.launchpad.net/awn-testing/ubuntu hardy main
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main #OpenOffice.org
deb http://archive.ubuntu.org.cn/ubuntu-cn/ intrepid main restricted universe multiverse #Ubuntu Chinese Repository
deb http://ppa.launchpad.net/fta/ubuntu intrepid main #Firefox
deb http://ppa.launchpad.net/stemp/ubuntu intrepid main #Midori
deb http://download.skype.com/linux/repos/debian stable non-free #Skype
deb http://deb.opera.com/opera/ lenny non-free #Opera
deb http://ppa.launchpad.net/project-neon/ubuntu/ intrepid main #Amarok
deb http://ppa.launchpad.net/reacocard-awn/ubuntu/ intrepid main #Avant Window Navigator
# deb http://repository.cairo-dock.org/ubuntu intrepid cairo-dock #Cairo Dock
# deb http://ppa.launchpad.net/do-core/ubuntu intrepid main #GNOME Do
# deb http://ppa.launchpad.net/banshee-team/ubuntu intrepid main #Banshee (Stable Version)
# deb http://ppa.launchpad.net/banshee-unstable-team/ubuntu intrepid main #Banshee (Unstable Version)
# deb http://dl.google.com/linux/deb/ stable non-free #Google
# deb http://ppa.launchpad.net/lidaobing/ubuntu intrepid main #Chmsee
# deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu intrepid main #KDE 4
deb http://www.getdropbox.com/static/ubuntu intrepid main #Nautilus DropBox
# deb http://ppa.launchpad.net/tualatrix/ubuntu intrepid main #Ubuntu Tweak
# deb http://ppa.launchpad.net/gilir/ubuntu intrepid main #Screenlets
deb http://wine.budgetdedicated.com/apt intrepid main #Wine
# deb http://download.virtualbox.org/virtualbox/debian intrepid non-free #VirtualBox
# deb http://ppa.launchpad.net/gnome-terminator/ubuntu intrepid main #Terminator
# deb http://ppa.launchpad.net/gscrot/ubuntu intrepid main #GScrot
# deb http://packages.medibuntu.org/ intrepid free non-free #Medibuntu
# deb http://ppa.launchpad.net/team-xbmc/ubuntu intrepid main #XBMC
deb-src http://ppa.launchpad.net/awn-testing/ubuntu hardy main
deb http://apt.wicd.net hardy extras 
```

what to do now please.

---

### Post by Naz_Farooq on 2009-04-12
My update log is like this in terminal
```
 nazfarooq@nazfarooq-laptop:~$ gksudo gedit /etc/apt/sources.list
nazfarooq@nazfarooq-laptop:~$ sudo apt-get update
Ign http://ppa.launchpad.net intrepid Release.gpg                              
Ign http://ppa.launchpad.net intrepid/main Translation-en_US                   
Get:1 http://ppa.launchpad.net hardy Release.gpg [307B]                        
Ign http://ppa.launchpad.net hardy/main Translation-en_US                      
Hit http://ppa.launchpad.net intrepid Release.gpg                              
Ign http://ppa.launchpad.net intrepid/main Translation-en_US                   
Hit http://ppa.launchpad.net intrepid Release.gpg                              
Ign http://archive.ubuntu.org.cn intrepid Release.gpg                          
Ign http://ppa.launchpad.net intrepid/main Translation-en_US                   
Hit http://ppa.launchpad.net intrepid Release.gpg                              
Ign http://ppa.launchpad.net intrepid/main Translation-en_US                   
Hit http://ppa.launchpad.net intrepid Release.gpg                              
Ign http://ppa.launchpad.net intrepid/main Translation-en_US                   
Ign http://ppa.launchpad.net intrepid Release.gpg                              
Ign http://archive.ubuntu.org.cn intrepid/main Translation-en_US               
Ign http://ppa.launchpad.net intrepid/main Translation-en_US                   
Get:2 http://ppa.launchpad.net intrepid Release [27.6kB]                       
Get:3 http://ppa.launchpad.net hardy Release [46.7kB]                          
Ign http://ppa.launchpad.net hardy Release                                     
Hit http://ppa.launchpad.net intrepid Release                                  
Hit http://ppa.launchpad.net intrepid Release                                  
Hit http://ppa.launchpad.net intrepid Release                                  
Get:4 http://ppa.launchpad.net intrepid Release [46.7kB]                       
Ign http://archive.ubuntu.org.cn intrepid/restricted Translation-en_US         
Ign http://ppa.launchpad.net intrepid Release                                  
Get:5 http://ppa.launchpad.net intrepid Release [27.6kB]                       
Ign http://ppa.launchpad.net intrepid/main Packages                            
Ign http://ppa.launchpad.net hardy/main Packages                               
Ign http://download.skype.com stable Release.gpg                               
Ign http://download.skype.com stable/non-free Translation-en_US                
Ign http://ppa.launchpad.net hardy/main Sources                                
Ign http://download.skype.com stable Release                                   
Ign http://download.skype.com stable/non-free Packages                         
Err http://download.skype.com stable/non-free Packages                         
  403 Forbidden [IP: 212.72.53.130 80]
Get:6 http://security.ubuntu.com intrepid-security Release.gpg [189B]          
Ign http://ppa.launchpad.net intrepid/main Packages                            
Hit http://deb.opera.com lenny Release.gpg                                     
Hit http://ae.archive.ubuntu.com intrepid Release.gpg                          
Ign http://ae.archive.ubuntu.com intrepid/main Translation-en_US               
Hit http://wine.budgetdedicated.com intrepid Release.gpg                       
Ign http://deb.opera.com lenny/non-free Translation-en_US                      
Hit http://deb.opera.com lenny Release                                         
Ign http://security.ubuntu.com intrepid-security/main Translation-en_US        
Ign http://ae.archive.ubuntu.com intrepid/restricted Translation-en_US         
Ign http://security.ubuntu.com intrepid-security/restricted Translation-en_US  
Ign http://ae.archive.ubuntu.com intrepid/universe Translation-en_US           
Ign http://deb.opera.com lenny/non-free Packages                               
Ign http://security.ubuntu.com intrepid-security/universe Translation-en_US    
Hit http://deb.opera.com lenny/non-free Packages                               
Ign http://ae.archive.ubuntu.com intrepid/multiverse Translation-en_US         
Get:7 http://ae.archive.ubuntu.com intrepid-updates Release.gpg [189B]         
Ign http://security.ubuntu.com intrepid-security/multiverse Translation-en_US                                                                                              
Ign http://ae.archive.ubuntu.com intrepid-updates/main Translation-en_US                                                                                                   
Get:8 http://security.ubuntu.com intrepid-security Release [51.2kB]                                                                                                        
Err http://security.ubuntu.com intrepid-security Release                                                                                                                   
  
Ign http://ae.archive.ubuntu.com intrepid-updates/restricted Translation-en_US                                                                                             
Ign http://wine.budgetdedicated.com intrepid/main Translation-en_US                                                                                                        
Ign http://ae.archive.ubuntu.com intrepid-updates/universe Translation-en_US                                                                                               
Hit http://wine.budgetdedicated.com intrepid Release                                                                                                                       
Ign http://ae.archive.ubuntu.com intrepid-updates/multiverse Translation-en_US                                                                                             
Hit http://ae.archive.ubuntu.com intrepid Release                                                                                                                          
Hit http://apt.wicd.net hardy Release.gpg                                                                                                                                  
Get:9 http://ae.archive.ubuntu.com intrepid-updates Release [51.2kB]                                                                                                       
Err http://ae.archive.ubuntu.com intrepid-updates Release                                                                                                                  
  
Hit http://ae.archive.ubuntu.com intrepid/main Packages                                                                                                                    
Ign http://apt.wicd.net hardy/extras Translation-en_US                                                                                                                     
Ign http://ppa.launchpad.net intrepid/main Packages                                                                                                                        
Hit http://apt.wicd.net hardy Release                                                                                                                                      
Hit http://ae.archive.ubuntu.com intrepid/restricted Packages                                                                                                              
Ign http://wine.budgetdedicated.com intrepid/main Packages                                                                                                                 
Hit http://ae.archive.ubuntu.com intrepid/main Sources                                                                                                                     
Ign http://ppa.launchpad.net intrepid/main Packages                                                                                                                        
Hit http://ae.archive.ubuntu.com intrepid/restricted Sources                                                                                                               
Hit http://ae.archive.ubuntu.com intrepid/universe Packages                                                                                                                
Hit http://ae.archive.ubuntu.com intrepid/universe Sources                                                                                                            
Ign http://ppa.launchpad.net intrepid/main Packages                                                                                                                        
Ign http://ppa.launchpad.net intrepid/main Packages                                                                                                                        
Hit http://wine.budgetdedicated.com intrepid/main Packages                                                                                                            
Hit http://ppa.launchpad.net intrepid/main Packages                                                                                                                        
Ign http://apt.wicd.net hardy/extras Packages                                                                                                                              
Hit http://apt.wicd.net hardy/extras Packages                                                                                                                              
Hit http://ppa.launchpad.net hardy/main Packages                                                                                                                           
Hit http://ppa.launchpad.net hardy/main Sources                                                                                                                            
Hit http://ppa.launchpad.net intrepid/main Packages                                                                                                                        
Hit http://ppa.launchpad.net intrepid/main Packages                                                                                                                        
Hit http://ppa.launchpad.net intrepid/main Packages                                                                                                                        
Get:10 http://ppa.launchpad.net intrepid/main Packages [8896B]                                                                                                             
Hit http://ppa.launchpad.net intrepid/main Packages                                                                                                                        
Ign http://www.getdropbox.com intrepid Release.gpg                                                                                                                         
Ign http://www.getdropbox.com intrepid/main Translation-en_US                                                                                                              
Ign http://www.getdropbox.com intrepid Release                                                                                                                             
Ign http://www.getdropbox.com intrepid/main Packages                                                                                                                       
Hit http://www.getdropbox.com intrepid/main Packages                                                                                                                       
Ign http://archive.ubuntu.org.cn intrepid/universe Translation-en_US                                                                                                       
Ign http://archive.ubuntu.org.cn intrepid/multiverse Translation-en_US        
Ign http://archive.ubuntu.org.cn intrepid Release                             
Ign http://archive.ubuntu.org.cn intrepid/main Packages                       
Ign http://archive.ubuntu.org.cn intrepid/restricted Packages                 
Ign http://archive.ubuntu.org.cn intrepid/universe Packages                   
Ign http://archive.ubuntu.org.cn intrepid/multiverse Packages                 
Get:11 http://archive.ubuntu.org.cn intrepid/main Packages [85.0kB]           
Hit http://archive.ubuntu.org.cn intrepid/restricted Packages                     
Hit http://archive.ubuntu.org.cn intrepid/universe Packages                                                  
Hit http://archive.ubuntu.org.cn intrepid/multiverse Packages                                                
Hit http://ae.archive.ubuntu.com intrepid/multiverse Packages                                                                                                              
Hit http://ae.archive.ubuntu.com intrepid/multiverse Sources
Fetched 141kB in 2min13s (1062B/s)
Reading package lists... Done
W: GPG error: http://ppa.launchpad.net hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7D2C7A23BF810CD5
W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures were invalid: BADSIG 778978B00F7992B0 Launchpad PPA for Project Neon
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://security.ubuntu.com intrepid-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://ae.archive.ubuntu.com intrepid-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-i386/Packages.gz  403 Forbidden [IP: 212.72.53.130 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/intrepid-security/Release  

W: Failed to fetch http://ae.archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems
nazfarooq@nazfarooq-laptop:~$ 
```

I want to update my system as soon as possible.
Please help me.

---

