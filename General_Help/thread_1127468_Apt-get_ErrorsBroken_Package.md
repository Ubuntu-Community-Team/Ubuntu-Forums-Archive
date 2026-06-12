---
title: "Apt-get Errors/Broken Package"
date: 2009-04-16
forum: General Help
---

### Post by Nexusx6 on 2009-04-16
Hola, 

The other day I had seen some updates available, so naturally I had told Adept to update and then went about my usual business. About a minute or two after I chose to update, my computer had suddenly, and without warning, crashed. In the 3 some odd years I've been running Ubuntu, I think I've had 1 system crash ever, so I was seriously perplexed and was forced to cold boot my system.

After I log in, I notice Adept is complaining about problems with my packages. I run ```
sudo apt-get install -f
``` which sorts out almost all of the problems, but I still have one to this day. The package *acroread* is marked as broken, and I'm not sure what to do to fix it. Adept as returned this error message on occasion:
```
Commit failed.
To continue, hit ok and we will try to recover. If you close the application now, we will not do anything and you may try to resolve the problem manually.
(If you suspect this is a bug in Adept, please also provide the following exception description in the report).

The error was: 
APT Error. Context:
    Running dpkg, 
    [ /usr/bin/dpkg, --status-fd, 3, --unpack, /var/cache/apt/archives/acroread_9.1.0-7intrepid1_i386.deb, /var/cache/apt/archives/libvolume-id0_124-9ubuntu0.2_i386.deb, /var/cache/apt/archives/tasksel-data_2.73ubuntu11.1_all.deb, /var/cache/apt/archives/tasksel_2.73ubuntu11.1_all.deb, /var/cache/apt/archives/udev_124-9ubuntu0.2_i386.deb, /var/cache/apt/archives/foo2zjs_20080810-0ubuntu4.1_i386.deb, /var/cache/apt/archives/ghostscript_8.63.dfsg.1-0ubuntu6.4_i386.deb, /var/cache/apt/archives/libgs8_8.63.dfsg.1-0ubuntu6.4_i386.deb, /var/cache/apt/archives/ghostscript-x_8.63.dfsg.1-0ubuntu6.4_i386.deb ], 
    Sup-process returned error code 1, 
    Error processing /var/cache/apt/archives/acroread_9.1.0-7intrepid1_i386.deb : unable to stat `./usr/share/doc/acroread/copyright' (which I was about to install): Stale NFS file handle.
```

I appreciate any help :)

---

### Post by govi333 on 2009-04-16
Try this

```
sudo apt-get remove acroread
```

Then

```
sudo apt-get install acroread
```

---

### Post by blazemore on 2009-04-16
Failing that, try 
```
sudo apt-get **purge** acroread && sudo apt-get install acroread
```

---

### Post by Nexusx6 on 2009-04-17
for both purge and remove, this error is returned:
```
Removing acroread ...                                                          
dpkg: error processing acroread (--remove):
 cannot remove `/usr/share/doc/acroread/copyright': Stale NFS file handle
Errors were encountered while processing:
 acroread
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Kevbert on 2009-04-17
What do you get with
```
sudo apt-get update
sudo apt-get upgrade
```
If you get the same error it may be that the package status file is broken.

---

### Post by Nexusx6 on 2009-04-17
```
fox@Aurora-Project:~$ sudo apt-get update                                                                                                                                                                                                   
Hit http://us.archive.ubuntu.com intrepid Release.gpg                                                                                                                                                                                       
Hit http://archive.ubuntu.com intrepid Release.gpg                                                                                                                                                                                          
Ign http://us.archive.ubuntu.com intrepid/main Translation-en_US                                                                                                                                                                            
Ign http://archive.ubuntu.com intrepid/main Translation-en_US                                                                                                                                                                               
Ign http://archive.ubuntu.com intrepid/restricted Translation-en_US                                                                                                                                                                         
Hit http://security.ubuntu.com intrepid-security Release.gpg                                                                                                                                                                                
Ign http://security.ubuntu.com intrepid-security/main Translation-en_US                                                                                                                                                                     
Ign http://security.ubuntu.com intrepid-security/restricted Translation-en_US                                                                                                                                                               
Ign http://us.archive.ubuntu.com intrepid/restricted Translation-en_US                                                                                                                                                                      
Ign http://us.archive.ubuntu.com intrepid/universe Translation-en_US                                                                                                                                                                        
Ign http://us.archive.ubuntu.com intrepid/multiverse Translation-en_US                                                                                                                                                                      
Hit http://us.archive.ubuntu.com intrepid-updates Release.gpg                                                                                                                                                                               
Ign http://us.archive.ubuntu.com intrepid-updates/main Translation-en_US                                                                                                                                                                    
Ign http://us.archive.ubuntu.com intrepid-updates/restricted Translation-en_US                                                                                                                                                              
Hit http://archive.ubuntu.com intrepid Release                                                                                                                                                                                              
Ign http://us.archive.ubuntu.com intrepid-updates/universe Translation-en_US                                                                                                                                                                
Ign http://us.archive.ubuntu.com intrepid-updates/multiverse Translation-en_US                                                                                                                                                              
Hit http://us.archive.ubuntu.com intrepid-backports Release.gpg                                                                                                                                                                             
Ign http://security.ubuntu.com intrepid-security/universe Translation-en_US                                                                                                                                                                 
Ign http://security.ubuntu.com intrepid-security/multiverse Translation-en_US                                                                                                                                                               
Hit http://security.ubuntu.com intrepid-security Release                                                                                                                                                                                    
Ign http://us.archive.ubuntu.com intrepid-backports/main Translation-en_US                                                                                                                                                                  
Ign http://us.archive.ubuntu.com intrepid-backports/restricted Translation-en_US                                                                                                                                                            
Hit http://archive.ubuntu.com intrepid/main Packages                                                                                                                                                                                        
Hit http://security.ubuntu.com intrepid-security/main Packages                                                                                                                                                                              
Ign http://us.archive.ubuntu.com intrepid-backports/universe Translation-en_US                                                                                                                                                              
Ign http://us.archive.ubuntu.com intrepid-backports/multiverse Translation-en_US                                                                                                                                                            
Hit http://us.archive.ubuntu.com intrepid Release                                                                                                                                                                                           
Hit http://us.archive.ubuntu.com intrepid-updates Release                                                                                                                                                                                   
Hit http://archive.ubuntu.com intrepid/restricted Packages                                                                                                                                                                                  
Hit http://security.ubuntu.com intrepid-security/restricted Packages                                                                                                                                                                        
Hit http://security.ubuntu.com intrepid-security/main Sources                                                                                                                                                                               
Hit http://security.ubuntu.com intrepid-security/restricted Sources                                                                                                                                                                         
Hit http://security.ubuntu.com intrepid-security/universe Packages                                                                                                                                                                          
Hit http://us.archive.ubuntu.com intrepid-backports Release                                                                                                                                                                                 
Hit http://us.archive.ubuntu.com intrepid/main Packages                                                                                                                                                                                     
Hit http://us.archive.ubuntu.com intrepid/restricted Packages                                                                                                                                                                               
Hit http://us.archive.ubuntu.com intrepid/main Sources                                                                                                                                                                                      
Hit http://us.archive.ubuntu.com intrepid/restricted Sources                                                                                                                                                                                
Hit http://us.archive.ubuntu.com intrepid/universe Packages                                                                                                                                                                                 
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
Hit http://archive.canonical.com intrepid Release.gpg                                                                                                                                                                                       
Ign http://archive.canonical.com intrepid/partner Translation-en_US                                                                                                                                                                         
Hit http://ppa.launchpad.net intrepid Release.gpg                                                                                                                                                                                           
Ign http://ppa.launchpad.net intrepid/main Translation-en_US                                                                                                                                                                                
Get:1 http://ppa.launchpad.net intrepid Release.gpg [307B]                                                                                                                                                                                  
Hit http://archive.canonical.com intrepid Release                                                                                                                                                                                           
Ign http://ppa.launchpad.net intrepid/main Translation-en_US                                                                                                                                                                                
Hit http://ppa.launchpad.net intrepid Release                                                                                                                                                                                               
Ign http://archive.canonical.com intrepid/partner Packages                                                                                                                                                                                  
Get:2 http://ppa.launchpad.net intrepid Release [46.7kB]                                                                                                                                                                                    
Ign http://ppa.launchpad.net intrepid Release                                                                                                                                                                                               
Ign http://archive.canonical.com intrepid/partner Sources                                                                                                                                                                                   
Ign http://ppa.launchpad.net intrepid/main Packages                                                                                                                                                                                         
Hit http://archive.canonical.com intrepid/partner Packages                                                                                                                                                                                  
Ign http://ppa.launchpad.net intrepid/main Packages                                                                                                                                                                                         
Ign http://ppa.launchpad.net intrepid/main Sources                                                                                                                                                                                          
Hit http://archive.canonical.com intrepid/partner Sources                                                                                                                                                                                   
Hit http://ppa.launchpad.net intrepid/main Packages                                                                                                                                                                                         
Hit http://ppa.launchpad.net intrepid/main Packages                                                                                                                                                                                         
Hit http://ppa.launchpad.net intrepid/main Sources                                                                                                                                                                                          
Hit http://packages.medibuntu.org intrepid Release.gpg                                                                                                                                                                                      
Ign http://packages.medibuntu.org intrepid/free Translation-en_US                                                                                                                                                                           
Hit http://wine.budgetdedicated.com intrepid Release.gpg                                                                                                                                                                                    
Ign http://wine.budgetdedicated.com intrepid/main Translation-en_US                                                                                                                                                                         
Ign http://packages.medibuntu.org intrepid/non-free Translation-en_US                                                                                                                                                                       
Hit http://packages.medibuntu.org intrepid Release                                                                                                                                                                                          
Hit http://wine.budgetdedicated.com intrepid Release                                                                                                                                                                                        
Hit http://packages.medibuntu.org intrepid/free Packages                                                                                                                                                                                    
Hit http://packages.medibuntu.org intrepid/non-free Packages                                                                                                                                                                                
Hit http://packages.medibuntu.org intrepid/free Sources                                                                                                                                                                                     
Hit http://packages.medibuntu.org intrepid/non-free Sources                                                                                                                                                                                 
Ign http://wine.budgetdedicated.com intrepid/main Packages                                                                                                                                                                                  
Hit http://wine.budgetdedicated.com intrepid/main Packages                                                                                                                                                                                  
Get:3 http://dl.google.com stable Release.gpg [189B]                                                                                                                                                                                        
Ign http://dl.google.com stable/non-free Translation-en_US
Get:4 http://dl.google.com stable Release [1300B]
Get:5 http://dl.google.com stable/non-free Packages [954B]
Fetched 2751B in 15s (179B/s)
Reading package lists... Done
W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY DE62F7B1165B2836
W: You may want to run apt-get update to correct these problems

```

Dispite the last line, running update again doesn't correct the GPG error.

```
fox@Aurora-Project:~$ sudo apt-get upgrade
Reading package lists... Done             
Building dependency tree                  
Reading state information... Done         
The following packages will be REMOVED:   
  acroread                                
The following packages have been kept back:
  gwenview                                 
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
3 not fully installed or removed.                             
After this operation, 71.2MB disk space will be freed.        
Do you want to continue [Y/n]? Y
(Reading database ... 147064 files and directories currently installed.)
Removing acroread ...
dpkg: error processing acroread (--remove):
 cannot remove `/usr/share/doc/acroread/copyright': Stale NFS file handle
Errors were encountered while processing:
 acroread
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Kevbert on 2009-04-18
To correct the gpg key error see [[COLOR="Red"]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1053126"), especially post #2.
The acroread problem looks like a possible bug that should be reported on [COLOR="Red"][Launchpad]("https://launchpad.net/")[/COLOR].  There have been similar problems in the past to this (but no immediate solution).

---

### Post by stalkingwolf on 2009-04-18
you can try booting into the recovery mode then when recovery finishes select fix broken packages

---

### Post by Nexusx6 on 2009-04-18
> **Kevbert said:**
> To correct the gpg key error see [[COLOR="Red"]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1053126"), especially post #2.
The acroread problem looks like a possible bug that should be reported on [COLOR="Red"][Launchpad]("https://launchpad.net/")[/COLOR].  There have been similar problems in the past to this (but no immediate solution).

Awesome, thanks a bunch for the GPG fix. I'll report the acroread issue today then.

> you can try booting into the recovery mode then when recovery finishes select fix broken packages 

I'll try this too on my next boot.

---

### Post by hikaricore on 2009-04-18
>  cannot remove `/usr/share/doc/acroread/copyright': Stale NFS file handle

This is kinda bizarre.  Are you even using NFS?

---

### Post by Nexusx6 on 2009-04-18
> **hikaricore said:**
> This is kinda bizarre.  Are you even using NFS?

I didn't understand that either. No I'm not, I use SMB. I don't even have the NFS packages installed.

---

