---
title: "[SOLVED] HELP! If you have the Dell Inspiron Mini 9..."
date: 2008-12-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by vegetarianshrimp on 2008-12-26
Hi, If you have the Dell Inspiron Mini 9, please do this for me. It won't change anything on your computer, Its just that I need the default /etc/apt/sources.list. on the Mini.


Go to Applications > Accessories > Terminal type in: 
```
sudo gedit /etc/apt/sources.list.

```
press enter

Wait a little bit, and a screen will pop up. DONT CHANGE ANYTHING. press ctrl+a to select all, then ctrl+c to copy. You can now close that window. In a reply to this thread, press ctrl+v to paste.

Thank You!

---

### Post by crazyness003 on 2008-12-26
I dont have a Dell Mini 9, but heres my sources list anyway (there may be some obscure entries, they're for OOo and WINE)
```
# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
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
deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb http://security.ubuntu.com/ubuntu intrepid-security universe
deb-src http://security.ubuntu.com/ubuntu intrepid-security universe
deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main #OpenOffice.org Launchpad Packages
deb http://wine.budgetdedicated.com/apt intrepid main #WineHQ - Ubuntu 8.10 "Intrepid Ibex"
# deb http://ppa.launchpad.net/tcarrez/ubuntu intrepid main
deb http://download.virtualbox.org/virtualbox/debian intrepid non-free
```

Also, if you dont want anyone to modify their sources.list, have them access it without root priveleges (no sudo is safe sudo...im so original:P). Just a tip.

---

### Post by vegetarianshrimp on 2008-12-26
Thanks, and thanks for the advice! I looked online, where did you get this?

---

### Post by crazyness003 on 2008-12-26
Its mine. Its the one that came pre-loaded with Ubuntu (self-install) + some additives I put in there over the past few weeks.
Im sure most of those entries will be of help to you, but if you seek Dell-specific entries (if they even exist) then I dont have them. Im not sure if dell even hosts Debian/Ubuntu repositories. Specific to Dell software/firmware/hardware. I could be wrong.

By the way, I didnt ask: What happened? Did you tank your sources.list? Or did you just wanna compare with someone else?
I just saw your sig in one of the games and wanted to check it out.

---

### Post by vegetarianshrimp on 2008-12-26
I made some changes to it, and then there were some errors that came popping up, so i wanted to go back to the default. Yours seems to be good. I actually recently downoalded Wine, so that saved me some time. Thanks again

[EDIT]

Actually, it isn't fine... I get this error in the Update manager
> GPG error: [http://download.virtualbox.org](http://download.virtualbox.org) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY DCF9F87B6DFBCBAEFailed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/Release.gpg)  
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/main/i18n/Translation-en_US.bz2)  
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/i18n/Translation-en_US.bz2)  
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/universe/i18n/Translation-en_US.bz2)  
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/i18n/Translation-en_US.bz2)  
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release.gpg)  
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/i18n/Translation-en_US.bz2)  
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/i18n/Translation-en_US.bz2)  
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/i18n/Translation-en_US.bz2)  
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/i18n/Translation-en_US.bz2)  
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-backports/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/hardy-backports/Release.gpg)  
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-backports/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy-backports/main/i18n/Translation-en_US.bz2)  
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-backports/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy-backports/restricted/i18n/Translation-en_US.bz2)  
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-backports/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy-backports/universe/i18n/Translation-en_US.bz2)  
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-backports/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy-backports/multiverse/i18n/Translation-en_US.bz2)  
Failed to fetch [http://download.virtualbox.org/virtualbox/debian/dists/intrepid/non-free/binary-lpia/Packages.gz](http://download.virtualbox.org/virtualbox/debian/dists/intrepid/non-free/binary-lpia/Packages.gz)  404 Not found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/binary-lpia/Packages.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/binary-lpia/Packages.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/binary-lpia/Packages.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/binary-lpia/Packages.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/binary-lpia/Packages.gz)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

[EDIT]

I also get this error:

> W: GPG error: [http://download.virtualbox.org](http://download.virtualbox.org) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY DCF9F87B6DFBCBAE
W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/hardy/Release.gpg](http://archive.canonical.com/ubuntu/dists/hardy/Release.gpg)  Could not resolve 'archive.canonical.com'

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/hardy/partner/i18n/Translation-en_US.bz2](http://archive.canonical.com/ubuntu/dists/hardy/partner/i18n/Translation-en_US.bz2)  Could not resolve 'archive.canonical.com'

W: Failed to fetch [http://download.virtualbox.org/virtualbox/debian/dists/intrepid/non-free/binary-lpia/Packages.gz](http://download.virtualbox.org/virtualbox/debian/dists/intrepid/non-free/binary-lpia/Packages.gz)  404 Not found

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/binary-lpia/Packages.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/binary-lpia/Packages.gz)  404 Not Found

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/binary-lpia/Packages.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/binary-lpia/Packages.gz)  404 Not Found

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/binary-lpia/Packages.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/binary-lpia/Packages.gz)  404 Not Found

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-lpia/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/binary-lpia/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/universe/binary-lpia/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/universe/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/binary-lpia/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/binary-lpia/Packages.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/binary-lpia/Packages.gz)  404 Not Found

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/binary-lpia/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/binary-lpia/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/binary-lpia/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/binary-lpia/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-backports/main/binary-lpia/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/hardy-backports/main/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-backports/restricted/binary-lpia/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/hardy-backports/restricted/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-backports/universe/binary-lpia/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/hardy-backports/universe/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-backports/multiverse/binary-lpia/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/hardy-backports/multiverse/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]

W: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by crazyness003 on 2008-12-26
ok. lemme take a whack here: You're running hardy, right?
If so, anywhere it says "interpid" must be replaced by "hardy"

Heres another poster that had the same problems [http://ubuntuforums.org/showthread.php?t=1004126](http://ubuntuforums.org/showthread.php?t=1004126)

I suggested to him/her to try (in termin[FONT=Verdana]al) [/FONT]```
sudo apt-get update
```[FONT=Verdana] as [/FONT]the Update Manager is not flawless.

Also, the gpg key dosnt work for you since you haven't validated it yet (i shoulda thought of that earlier). Instructions for VirtualBox (if you need the VirtualBox Personal Use and Evaluation License): [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads). There are instructions tward the end and bottom of the page.

Sorry that this happened to you. Just a reminder, when mod important files (hell, any kind of files) make sure you make a backup. Its easy really. This is what I do (in this case for my sources list):```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.xBackup
```This makes an exact copy of my sources list with the xBackup extension. I use .xBackup because its easy for me to remember. You can name your however you wish.
And so whan i need to recover, i just do this
```
sudo cp /etc/apt/sources.list.xBackup /etc/apt/sources.list
```Then i overwrite. This lets me copy back my original while still keeping my backup intact.

Of course if my / partition died, id lose it all, but i dont plan on that happening :P

---

### Post by vegetarianshrimp on 2008-12-26
Ok so I did all that and then this in the terminal:

```
daniel@daniel:~$ sudo apt-get update
Ign file: ./ Release.gpg
Ign file: ./ Translation-en_US                                                                                              
Ign file: ./ Release                                                                                                        
Ign file: ./ Packages                                                                                                       
Get:1 http://download.virtualbox.org hardy Release.gpg [189B]                                                               
Ign http://download.virtualbox.org hardy/non-free Translation-en_US                                                         
Get:2 http://download.virtualbox.org hardy Release [2094B]                                                                  
Ign http://download.virtualbox.org hardy Release                                                                            
Ign http://download.virtualbox.org hardy/non-free Packages                                                                  
Err http://download.virtualbox.org hardy/non-free Packages                                                                  
  404 Not found
Hit http://security.ubuntu.com hardy-security Release.gpg                                                        
Ign http://security.ubuntu.com hardy-security/main Translation-en_US                                             
Hit http://archive.canonical.com hardy Release.gpg                                         
Ign http://archive.canonical.com hardy/partner Translation-en_US                           
Ign http://ppa.launchpad.net hardy Release.gpg                                             
Ign http://ppa.launchpad.net hardy/main Translation-en_US                                  
Hit http://us.archive.ubuntu.com intrepid Release.gpg                                      
Ign http://us.archive.ubuntu.com intrepid/main Translation-en_US                                                 
Hit http://wine.budgetdedicated.com hardy Release.gpg                                                            
Ign http://wine.budgetdedicated.com hardy/main Translation-en_US                                                 
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US                 
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US                   
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US                                       
Hit http://security.ubuntu.com hardy-security Release                                                            
Hit http://archive.canonical.com hardy Release                                                                  
Get:3 http://ppa.launchpad.net hardy Release [27.6kB]                                                           
Ign http://us.archive.ubuntu.com intrepid/restricted Translation-en_US                                          
Ign http://us.archive.ubuntu.com intrepid/universe Translation-en_US
Ign http://us.archive.ubuntu.com intrepid/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com intrepid-updates Release.gpg
Ign http://us.archive.ubuntu.com intrepid-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com hardy-backports Release.gpg
Hit http://wine.budgetdedicated.com hardy Release                                                              
Ign http://us.archive.ubuntu.com hardy-backports/main Translation-en_US                                        
Ign http://us.archive.ubuntu.com hardy-backports/restricted Translation-en_US                                  
Ign http://security.ubuntu.com hardy-security/main Packages                                
Ign http://ppa.launchpad.net hardy/main Packages                                           
Ign http://us.archive.ubuntu.com hardy-backports/universe Translation-en_US                
Ign http://us.archive.ubuntu.com hardy-backports/multiverse Translation-en_US                                    
Hit http://us.archive.ubuntu.com intrepid Release                                                                
Hit http://archive.canonical.com hardy/partner Packages                                                          
Ign http://wine.budgetdedicated.com hardy/main Packages                                                          
Hit http://us.archive.ubuntu.com intrepid-updates Release                                                        
Ign http://security.ubuntu.com hardy-security/restricted Packages                                                           
Hit http://security.ubuntu.com hardy-security/main Sources                                                       
Hit http://security.ubuntu.com hardy-security/restricted Sources                                                 
Ign http://security.ubuntu.com hardy-security/universe Packages                                                  
Hit http://ppa.launchpad.net hardy/main Packages                                                                 
Hit http://us.archive.ubuntu.com hardy-backports Release                                   
Hit http://archive.canonical.com hardy/partner Sources                                                          
Ign http://us.archive.ubuntu.com intrepid/main Packages                                                         
Ign http://us.archive.ubuntu.com intrepid/restricted Packages        
Hit http://us.archive.ubuntu.com intrepid/main Sources               
Hit http://us.archive.ubuntu.com intrepid/restricted Sources         
Ign http://us.archive.ubuntu.com intrepid/universe Packages          
Hit http://wine.budgetdedicated.com hardy/main Packages              
Hit http://security.ubuntu.com hardy-security/universe Sources       
Ign http://security.ubuntu.com hardy-security/multiverse Packages
Hit http://security.ubuntu.com hardy-security/multiverse Sources
Err http://security.ubuntu.com hardy-security/main Packages
  404 Not Found
Err http://security.ubuntu.com hardy-security/restricted Packages
  404 Not Found
Hit http://us.archive.ubuntu.com intrepid/universe Sources
Ign http://us.archive.ubuntu.com intrepid/multiverse Packages
Hit http://us.archive.ubuntu.com intrepid/multiverse Sources
Ign http://us.archive.ubuntu.com intrepid-updates/main Packages
Ign http://us.archive.ubuntu.com intrepid-updates/restricted Packages
Hit http://us.archive.ubuntu.com intrepid-updates/main Sources
Hit http://us.archive.ubuntu.com intrepid-updates/restricted Sources
Ign http://us.archive.ubuntu.com intrepid-updates/universe Packages
Hit http://us.archive.ubuntu.com intrepid-updates/universe Sources
Err http://security.ubuntu.com hardy-security/universe Packages
  404 Not Found
Err http://security.ubuntu.com hardy-security/multiverse Packages
  404 Not Found
Ign http://us.archive.ubuntu.com intrepid-updates/multiverse Packages
Hit http://us.archive.ubuntu.com intrepid-updates/multiverse Sources
Ign http://us.archive.ubuntu.com hardy-backports/main Packages
Ign http://us.archive.ubuntu.com hardy-backports/restricted Packages
Ign http://us.archive.ubuntu.com hardy-backports/universe Packages
Ign http://us.archive.ubuntu.com hardy-backports/multiverse Packages
Hit http://us.archive.ubuntu.com hardy-backports/main Sources
Hit http://us.archive.ubuntu.com hardy-backports/restricted Sources
Hit http://us.archive.ubuntu.com hardy-backports/universe Sources
Hit http://us.archive.ubuntu.com hardy-backports/multiverse Sources
Err http://us.archive.ubuntu.com intrepid/main Packages
  404 Not Found [IP: 91.189.88.40 80]
Err http://us.archive.ubuntu.com intrepid/restricted Packages
  404 Not Found [IP: 91.189.88.40 80]
Err http://us.archive.ubuntu.com intrepid/universe Packages
  404 Not Found [IP: 91.189.88.40 80]
Err http://us.archive.ubuntu.com intrepid/multiverse Packages
  404 Not Found [IP: 91.189.88.40 80]
Err http://us.archive.ubuntu.com intrepid-updates/main Packages
  404 Not Found [IP: 91.189.88.40 80]
Err http://us.archive.ubuntu.com intrepid-updates/restricted Packages
  404 Not Found [IP: 91.189.88.40 80]
Err http://us.archive.ubuntu.com intrepid-updates/universe Packages
  404 Not Found [IP: 91.189.88.40 80]
Err http://us.archive.ubuntu.com intrepid-updates/multiverse Packages
  404 Not Found [IP: 91.189.88.40 80]
Err http://us.archive.ubuntu.com hardy-backports/main Packages
  404 Not Found [IP: 91.189.88.40 80]
Err http://us.archive.ubuntu.com hardy-backports/restricted Packages
  404 Not Found [IP: 91.189.88.40 80]
Err http://us.archive.ubuntu.com hardy-backports/universe Packages
  404 Not Found [IP: 91.189.88.40 80]
Err http://us.archive.ubuntu.com hardy-backports/multiverse Packages
  404 Not Found [IP: 91.189.88.40 80]
Fetched 191B in 1s (97B/s)
W: GPG error: http://download.virtualbox.org hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY DCF9F87B6DFBCBAE
W: Failed to fetch http://download.virtualbox.org/virtualbox/debian/dists/hardy/non-free/binary-lpia/Packages.gz  404 Not found

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-lpia/Packages.gz  404 Not Found

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-lpia/Packages.gz  404 Not Found

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-lpia/Packages.gz  404 Not Found

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-lpia/Packages.gz  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/binary-lpia/Packages.gz  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid/universe/binary-lpia/Packages.gz  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/binary-lpia/Packages.gz  404 Not Found

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/binary-lpia/Packages.gz  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/binary-lpia/Packages.gz  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/binary-lpia/Packages.gz  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/binary-lpia/Packages.gz  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/binary-lpia/Packages.gz  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-backports/main/binary-lpia/Packages.gz  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-backports/restricted/binary-lpia/Packages.gz  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-backports/universe/binary-lpia/Packages.gz  404 Not Found [IP: 91.189.88.40 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-backports/multiverse/binary-lpia/Packages.gz  404 Not Found [IP: 91.189.88.40 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by crazyness003 on 2008-12-26
Ok, i think i may have found an answer. I gave google a nice look-over and hound this Thread.
[http://ubuntuforums.org/showthread.php?t=773137](http://ubuntuforums.org/showthread.php?t=773137)
Within this thread, I found a link to psychocats with some VERY informational...information:
[http://www.psychocats.net/ubuntu/sources#editfile](http://www.psychocats.net/ubuntu/sources#editfile)
Basically, make a copy of your existing /etc/apt/sources.list (either my way, or as described in the 2nd link).
And copy the entries listed in the black text boxes.
For [SIZE=4]**Intrepid**[/SIZE], overwrite everythign in your sources.list with this:
```
deb http://archive.canonical.com/ubuntu intrepid partner  
deb http://archive.ubuntu.com/ubuntu/ intrepid main universe restricted multiverse
deb http://security.ubuntu.com/ubuntu/ intrepid-security universe main multiverse restricted
deb http://archive.ubuntu.com/ubuntu/ intrepid-updates universe main multiverse restricted
deb http://packages.medibuntu.org/ intrepid free non-free
```For [SIZE=4]**Hardy**[/SIZE], do the same with this:
```
deb http://archive.canonical.com/ubuntu hardy partner 
deb http://archive.ubuntu.com/ubuntu/ hardy main universe restricted multiverse
deb http://security.ubuntu.com/ubuntu/ hardy-security universe main multiverse restricted
deb http://archive.ubuntu.com/ubuntu/ hardy-updates universe main multiverse restricted
deb http://packages.medibuntu.org/ hardy free non-free
```Then issue this command
```
sudo apt-get update
```If you get errors, please issue it again (up to 3 times) as stated on an Ubuntu wiki page (cant remember where).[INDENT]**[the following was written by vegetarianshrimp]**
*Do you know how to fix this? *
                                                                Since you helped me with the /etc/apt/sources.list.
for my mini 9, do you think you can help me with this?
The update manager shows this when I click "check"
     ```
Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.
Failed to fetch [http://security.ubuntu.com/ubuntu/di...ia/Packages.gz]("http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-lpia/Packages.gz")  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/di...ia/Packages.gz]("http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-lpia/Packages.gz")  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/di...ia/Packages.gz]("http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-lpia/Packages.gz")  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...ia/Packages.gz]("http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-lpia/Packages.gz")  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...ia/Packages.gz]("http://archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-lpia/Packages.gz")  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...ia/Packages.gz]("http://archive.ubuntu.com/ubuntu/dists/hardy/main/binary-lpia/Packages.gz")  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...ia/Packages.gz]("http://archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-lpia/Packages.gz")  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...ia/Packages.gz]("http://archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-lpia/Packages.gz")  404 Not Found [IP: 91.189.88.31 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...ia/Packages.gz]("http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-lpia/Packages.gz")  404 Not Found [IP: 91.189.88.31 80]
Some index files failed to download, they have been ignored, or old ones used instead.
```**[/end of vegetariansprimp's quote]**
[/INDENT]As for those above mentioned URL's, they dont exist.[noparse]http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/[/noparse]***binary-lpia/**Packages.gz*
The /binary-lpia/ subdirectory is non-existant.
Here is a list of what's supposed to be in place of it:

[LIST]
[*]binary-amd64/
[*]binary-i386/
[*]debian-installer/
[*]source/
[/LIST]

[LIST]
[*]etc
[/LIST]
Im not sure how you got that URL, but thats the culprit for that problem.

---

### Post by BaderEX on 2008-12-26
Thats what I have in my mini 9 

> 

# deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy main universe multiverse restricted
# deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy main universe multiverse restricted

# deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-updates main universe multiverse restricted
# deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-updates main universe multiverse restricted

# deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-security main universe multiverse restricted
# deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-security main universe multiverse restricted

# deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-netbook-base main universe multiverse restricted
# deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-netbook-base main universe multiverse restricted

# deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-dell-mini main universe multiverse restricted
# deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-dell-mini main universe multiverse restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main universe multiverse




---

### Post by vegetarianshrimp on 2008-12-26
It worked, thank you.

[EDIT]

Except when I changed some things in the Software Sources, I got this:
> Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-lpia/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-lpia/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/main/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/main/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.45 80]

---

### Post by crazyness003 on 2008-12-26
what exactly did you change? those url's cannot be found, and i have no idea how you're running into them

---

### Post by vegetarianshrimp on 2008-12-27
I added Wine third party thingy...

---

### Post by vegetarianshrimp on 2009-01-02
[http://ubuntuforums.org/showthread.php?t=1027616](http://ubuntuforums.org/showthread.php?t=1027616)

---

### Post by crazyness003 on 2009-01-02
its a shame that you had to reinstall everything.
make sure to backup your sources.list file next time you mod it.

---

### Post by p388l3s on 2009-01-02
Sry to point this out so late, but the Dell Mini 9 doesn't use a vanilla Hardy install it uses a custom install created by Dell/Ubuntu for MID devices i.e. Mobile Internet Devices.

I'll post my Sources list in a moment if you still need it.

---

### Post by vegetarianshrimp on 2009-01-02
> **p388l3s said:**
> Sry to point this out so late, but the Dell Mini 9 doesn't use a vanilla Hardy install it uses a custom install created by Dell/Ubuntu for MID devices i.e. Mobile Internet Devices.

I'll post my Sources list in a moment if you still need it.

Yes of course, I knew that when I got the computer. 
You don't need to post your sources list, it's ok. Thanks anyway though.:P

---

### Post by p388l3s on 2009-01-02
```
deb http://dell-mini.archive.canonical.com/ubuntu/ hardy main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-updates main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-updates main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-security main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-security main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-netbook-base main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-netbook-base main universe multiverse restricted

deb http://dell-mini.archive.canonical.com/ubuntu/ hardy-dell-mini main universe multiverse restricted
deb-src http://dell-mini.archive.canonical.com/ubuntu/ hardy-dell-mini main universe multiverse restricted
deb http://wine.budgetdedicated.com/apt hardy main #WineHQ - Ubuntu 8.04 "Hardy Heron"
```

This is from my Dell Mini 9.

Hope it's of some use.

---

