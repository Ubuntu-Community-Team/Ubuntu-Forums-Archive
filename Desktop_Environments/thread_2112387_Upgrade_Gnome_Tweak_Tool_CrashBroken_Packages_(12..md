---
title: "Upgrade: Gnome Tweak Tool Crash/Broken Packages (12.04)"
date: 2013-02-04
forum: Desktop Environments
---

### Post by LemonLime on 2013-02-04
Hello,

I've browsed through the forum for possible fixes to an issue I have regarding Gnome-Tweak-Tool, and, to a greater degree, the **entire ***gnome user theme* and desktop environment. Thus far, none of the suggested solutions have worked. To start, here is an error I kept getting when I try to install tweak tool:

> [B]The following packages have unmet dependencies:
 gnome-tweak-tool : Depends: gnome-shell (>= 3.3.2) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.[/B]

Before doing a partial upgrade of Ubuntu, I had GTK3+ themes working. However, I couldn't install the gnome user theme package because of broken packages. When Ubuntu began updating my system, I figured this would correct the issue. However, after upgrading, "Advanced Settings" became "Tweak Tool" -- I attempted to launch it out of my dash and it crashed three times in a row, after being unresponsive. It wouldn't show in my dock or even attempt to launch after that. Similarly, the entire system felt bugged and horribly sluggish. 

My themes have reset themselves though the data of my custom themes still exist in the appropriate system folders. Tweak Tool has been uninstalled and the matching sources in synaptic have been purged. Yet I simply can't upgrade it or reinstall it via Terminal, now that it's been purged. 

There's various logs I attached below from terminal, in case you want to reference something. Is this a common issue, and how do I find and fix these "broken packages"?

```

_ATTEMPT 1:_ (advice from papisz @ [http://ubuntuforums.org/showthread.php?t=2004928&highlight=Gnome+Tweak+Tool]("http://ubuntuforums.org/showthread.php?t=2004928&highlight=Gnome+Tweak+Tool"))
[CODE]
daedalus@ubuntu:~$ sudo apt-get remove gnome-tweak-tool
[sudo] password for daedalus: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libcogl9 libcogl-pango0 gir1.2-json-1.0 libmozjs185-1.0 mutter-common libmutter0 gir1.2-coglpango-1.0 libclutter-1.0-common gjs libclutter-1.0-0 gnome-shell-common
  gir1.2-gdesktopenums-3.0 gir1.2-mutter-3.0 libcogl-common libgjs0c gir1.2-cogl-1.0 gir1.2-clutter-1.0
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  gnome-tweak-tool
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 756 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 315917 files and directories currently installed.)
Removing gnome-tweak-tool ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for hicolor-icon-theme ...
daedalus@ubuntu:~$ sudo apt-get install gnome-tweak-tool
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
[B]The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gnome-tweak-tool : Depends: gnome-shell (>= 3.3.2) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
daedalus@ubuntu:~$ gnome-tweak-tool
The program 'gnome-tweak-tool' is currently not installed.  You can install it by typing:
sudo apt-get install gnome-tweak-tool[/B]

daedalus@ubuntu:~$ sudo apt-get install gnome-tweak-tool
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gnome-tweak-tool : Depends: gnome-shell (>= 3.3.2) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

_ATTEMPT 2:_
I proceeded to purge, following the advice of sikander3786 from [this thread]("http://ubuntuforums.org/showthread.php?t=2005240&highlight=Gnome-tweak-tool"). Here is the record from Terminal:

```
daedalus@ubuntu:~$ sudo apt-get purge gnome-tweak-tool
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gnome-tweak-tool is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libcogl9 libcogl-pango0 gir1.2-json-1.0 libmozjs185-1.0 mutter-common libmutter0 gir1.2-coglpango-1.0 libclutter-1.0-common gjs libclutter-1.0-0 gnome-shell-common
  gir1.2-gdesktopenums-3.0 gir1.2-mutter-3.0 libcogl-common libgjs0c gir1.2-cogl-1.0 gir1.2-clutter-1.0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
daedalus@ubuntu:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libcogl9 libcogl-pango0 gir1.2-json-1.0 libmozjs185-1.0 mutter-common libmutter0 gir1.2-coglpango-1.0 libclutter-1.0-common gjs libclutter-1.0-0 gnome-shell-common
  gir1.2-gdesktopenums-3.0 gir1.2-mutter-3.0 libcogl-common libgjs0c gir1.2-cogl-1.0 gir1.2-clutter-1.0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
daedalus@ubuntu:~$ sudo dpkg --configure -a
daedalus@ubuntu:~$ sudo apt-get update && sudo apt-get upgrade
Ign http://security.ubuntu.com precise-security InRelease
Ign http://dl.google.com stable InRelease                                                                                                                              
Get:1 http://security.ubuntu.com precise-security Release.gpg [198 B]                                                                                                  
Hit http://dl.google.com stable Release.gpg                                                                                                                            
Get:2 http://security.ubuntu.com precise-security Release [49.6 kB]                                                                    
Hit http://dl.google.com stable Release                                                                                                                              
Ign http://archive.ubuntu.com precise InRelease                                                                                                                      
Ign http://archive.ubuntu.com precise-updates InRelease                                                                                          
Ign http://archive.canonical.com precise InRelease                                                                                               
Hit http://repo.steampowered.com precise InRelease                                                                                               
Ign http://extras.ubuntu.com precise InRelease                                                                                                   
Ign http://ppa.launchpad.net precise InRelease                                                                                                   
Ign http://ppa.launchpad.net precise InRelease                                                                              
Ign http://ppa.launchpad.net precise InRelease                                                                              
Hit http://dl.google.com stable/main amd64 Packages                                                                                                              
Hit http://archive.ubuntu.com precise Release.gpg                                                                                       
Hit http://ppa.launchpad.net precise Release.gpg                                                                  
Hit http://archive.canonical.com precise Release.gpg                                                              
Get:3 http://extras.ubuntu.com precise Release.gpg [72 B]                                                         
Hit http://repo.steampowered.com precise/steam amd64 Packages                                                     
Get:4 http://security.ubuntu.com precise-security/main amd64 Packages [225 kB]                                                          
Hit http://dl.google.com stable/main i386 Packages                                                                                                                     
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                                       
Ign http://dl.google.com stable/main TranslationIndex                                                                                                                  
Get:5 http://archive.ubuntu.com precise-updates Release.gpg [198 B]                                                                                                    
Hit http://extras.ubuntu.com precise Release                                                                                                                           
Hit http://archive.canonical.com precise Release                                                                                                                       
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                                       
Hit http://archive.ubuntu.com precise Release                                                                                                                          
Hit http://extras.ubuntu.com precise/main Sources                                                                                                                      
Hit http://archive.canonical.com precise/partner amd64 Packages                                                                                                       
Hit http://ppa.launchpad.net precise Release                                                                                                    
Get:6 http://archive.ubuntu.com precise-updates Release [49.6 kB]                                                                                                      
Hit http://extras.ubuntu.com precise/main amd64 Packages                                                                                                               
Hit http://extras.ubuntu.com precise/main i386 Packages                                                                                                                
Hit http://archive.canonical.com precise/partner i386 Packages                                                                                                         
Ign http://archive.canonical.com precise/partner TranslationIndex                                                                                                      
Hit http://ppa.launchpad.net precise Release                                                                                                                           
Ign http://extras.ubuntu.com precise/main TranslationIndex                                                                                                             
Hit http://ppa.launchpad.net precise Release                                                                                                                           
Hit http://repo.steampowered.com precise/steam i386 Packages                                                                                     
Get:7 http://security.ubuntu.com precise-security/restricted amd64 Packages [3,969 B]                                                                                  
Hit http://ppa.launchpad.net precise/main Sources                                                                                                                      
Hit http://ppa.launchpad.net precise/main amd64 Packages                                                                                                               
Get:8 http://security.ubuntu.com precise-security/universe amd64 Packages [62.7 kB]                                                                                    
Ign http://dl.google.com stable/main Translation-en_US                                                                                                                 
Ign http://dl.google.com stable/main Translation-en                                                                                                                    
Hit http://archive.ubuntu.com precise/main amd64 Packages                                                                                                              
Ign http://repo.steampowered.com precise/steam TranslationIndex                                                                                   
Hit http://ppa.launchpad.net precise/main i386 Packages                                                                                           
Ign http://ppa.launchpad.net precise/main TranslationIndex                                                                  
Hit http://ppa.launchpad.net precise/main Sources                                                                           
Hit http://ppa.launchpad.net precise/main amd64 Packages                                                                    
Hit http://ppa.launchpad.net precise/main i386 Packages                                                                     
Ign http://ppa.launchpad.net precise/main TranslationIndex                                                                                        
Hit http://ppa.launchpad.net precise/main Sources                                                                                                 
Hit http://archive.ubuntu.com precise/restricted amd64 Packages                                                                                   
Hit http://archive.ubuntu.com precise/universe amd64 Packages                                                                                     
Hit http://archive.ubuntu.com precise/multiverse amd64 Packages                                                                                   
Hit http://archive.ubuntu.com precise/main i386 Packages                                                                                          
Hit http://archive.ubuntu.com precise/restricted i386 Packages                                                                                    
Hit http://archive.ubuntu.com precise/universe i386 Packages                                                                                      
Hit http://archive.ubuntu.com precise/multiverse i386 Packages                                                                                    
Hit http://archive.ubuntu.com precise/main TranslationIndex                                                                                       
Hit http://archive.ubuntu.com precise/multiverse TranslationIndex                                                                                 
Hit http://archive.ubuntu.com precise/restricted TranslationIndex                                                                                 
Hit http://ppa.launchpad.net precise/main amd64 Packages                                                                                          
Hit http://ppa.launchpad.net precise/main i386 Packages                                                                                           
Ign http://ppa.launchpad.net precise/main TranslationIndex                                                                                        
Hit http://archive.ubuntu.com precise/universe TranslationIndex                                                                                   
Get:9 http://archive.ubuntu.com precise-updates/main amd64 Packages [483 kB]                                                                      
Get:10 http://security.ubuntu.com precise-security/multiverse amd64 Packages [2,184 B]                                                                     
Get:11 http://security.ubuntu.com precise-security/main i386 Packages [233 kB]                                                                                         
Ign http://archive.canonical.com precise/partner Translation-en_US                                                                                                     
Ign http://extras.ubuntu.com precise/main Translation-en_US                                                                                               
Ign http://archive.canonical.com precise/partner Translation-en                                                                      
Ign http://extras.ubuntu.com precise/main Translation-en                                                                             
Ign http://ppa.launchpad.net precise/main Translation-en_US                                                    
Ign http://ppa.launchpad.net precise/main Translation-en                                                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                              
Ign http://ppa.launchpad.net precise/main Translation-en                                 
Ign http://ppa.launchpad.net precise/main Translation-en_US                              
Get:12 http://security.ubuntu.com precise-security/restricted i386 Packages [3,968 B]    
Get:13 http://security.ubuntu.com precise-security/universe i386 Packages [64.2 kB]                            
Ign http://ppa.launchpad.net precise/main Translation-en                                                      
Ign http://repo.steampowered.com precise/steam Translation-en_US                                                   
Get:14 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,366 B]      
Hit http://security.ubuntu.com precise-security/main TranslationIndex                                            
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex                            
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex                            
Hit http://security.ubuntu.com precise-security/universe TranslationIndex                                
Ign http://repo.steampowered.com precise/steam Translation-en                                            
Hit http://security.ubuntu.com precise-security/main Translation-en                                      
Hit http://security.ubuntu.com precise-security/multiverse Translation-en
Hit http://security.ubuntu.com precise-security/restricted Translation-en
Hit http://security.ubuntu.com precise-security/universe Translation-en
Get:15 http://archive.ubuntu.com precise-updates/restricted amd64 Packages [9,609 B]                                                                                   
Get:16 http://archive.ubuntu.com precise-updates/universe amd64 Packages [175 kB]                                                                                      
Get:17 http://archive.ubuntu.com precise-updates/multiverse amd64 Packages [9,425 B]                                                                                   
Get:18 http://archive.ubuntu.com precise-updates/main i386 Packages [493 kB]                                                                                           
Get:19 http://archive.ubuntu.com precise-updates/restricted i386 Packages [9,501 B]                                                                                    
Get:20 http://archive.ubuntu.com precise-updates/universe i386 Packages [176 kB]                                                                                       
Get:21 http://archive.ubuntu.com precise-updates/multiverse i386 Packages [10.4 kB]                                                                                    
Get:22 http://archive.ubuntu.com precise-updates/main TranslationIndex [3,564 B]                                                                                       
Get:23 http://archive.ubuntu.com precise-updates/multiverse TranslationIndex [2,605 B]                                                                                 
Get:24 http://archive.ubuntu.com precise-updates/restricted TranslationIndex [2,461 B]                                                                                 
Get:25 http://archive.ubuntu.com precise-updates/universe TranslationIndex [2,850 B]                                                                                   
Hit http://archive.ubuntu.com precise/main Translation-en                                                                                                              
Hit http://archive.ubuntu.com precise/multiverse Translation-en                                                                                                        
Hit http://archive.ubuntu.com precise/restricted Translation-en                                                                                                        
Hit http://archive.ubuntu.com precise/universe Translation-en                                                                                                          
Get:26 http://archive.ubuntu.com precise-updates/main Translation-en [234 kB]                                                                                          
Hit http://archive.ubuntu.com precise-updates/multiverse Translation-en                                                                                                
Hit http://archive.ubuntu.com precise-updates/restricted Translation-en                                                                                                
Get:27 http://archive.ubuntu.com precise-updates/universe Translation-en [104 kB]                                                                                      
Fetched 2,413 kB in 12s (198 kB/s)                                                                                                                                     
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  liblightdm-gobject-1-0 lightdm
2 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 129 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com/ubuntu/ precise-updates/main lightdm amd64 1.2.3-0ubuntu1 [98.6 kB]
Get:2 http://archive.ubuntu.com/ubuntu/ precise-updates/main liblightdm-gobject-1-0 amd64 1.2.3-0ubuntu1 [30.9 kB]
Fetched 129 kB in 0s (194 kB/s)                
Preconfiguring packages ...
(Reading database ... 315818 files and directories currently installed.)
Preparing to replace lightdm 1.2.1-0ubuntu1.1 (using .../lightdm_1.2.3-0ubuntu1_amd64.deb) ...
Unpacking replacement lightdm ...
Preparing to replace liblightdm-gobject-1-0 1.2.1-0ubuntu1.1 (using .../liblightdm-gobject-1-0_1.2.3-0ubuntu1_amd64.deb) ...
Unpacking replacement liblightdm-gobject-1-0 ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for man-db ...
Setting up lightdm (1.2.3-0ubuntu1) ...
Setting up liblightdm-gobject-1-0 (1.2.3-0ubuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
daedalus@ubuntu:~$ sudo apt-get install gnome-tweak-tool
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

[B]The following packages have unmet dependencies:
 gnome-tweak-tool : Depends: gnome-shell (>= 3.3.2) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.[/B]

```[/code]

-LemonLime

---

