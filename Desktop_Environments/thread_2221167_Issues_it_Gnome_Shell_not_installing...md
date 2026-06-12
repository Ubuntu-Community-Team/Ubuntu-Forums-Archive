---
title: "Issues it Gnome Shell not installing.."
date: 2014-05-01
forum: Desktop Environments
---

### Post by Hl5tory on 2014-05-01
I'v been trying to download Gnome shell for the past few day. The first OS I tired it on was Linux Mint 16 Perta Cinnamon 32bit and gnome shell wouldn't install. Now am trying it on Ubuntu 14.04 LTS and I get this (the same error I got with Linux)

```
historically@Hl5tory:~$ sudo apt-get install gnome-shell
[sudo] password for historically: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 gnome-shell : Depends: gir1.2-mutter-3.0 (>= 3.11.91) but it is not going to be installed
               Depends: libmutter0d (>= 3.11) but it is not going to be installed
               Depends: libmutter0d (< 3.12) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.



```

Not sure why am getting that but I looked around the internet and got suggestions on running ```
sudo apt-get install -f
``` but theres no update to download. I tried to get Gnome Shell from the Ubuntu software center but when I press install I get this error : 

Package dependencies cannot be resolved

This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.

Details :
The following packages have unmet dependencies:

gnome-shell: Depends: libgjs0-libmozjs-24-0 but it is a virtual package
             Depends: libpulse-mainloop-glib0 (>= 1:0.99.1) but 1:4.0-0ubuntu11 is to be installed
             Depends: libpulse0 (>= 1:0.99.1) but 1:4.0-0ubuntu11 is to be installed
             Depends: libxi6 (>= 2:1.2.99.4) but 2:1.7.1.901-1ubuntu1 is to be installed
             Depends: gnome-shell-common (= 3.11.91+git20140315.d6197b09-0ubuntu1~14.04~ricotz0) but 3.11.91+git20140315.d6197b09-0ubuntu1~14.04~ricotz0 is to be installed

Am kind of new to this whole thing and it's probably not a big deal if you know what your doing. Please help me. Thanks.
Am starting to think its a hardware problem. I really hope not.

---

### Post by deadflowr on 2014-05-01
Try
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```
in that order, then try installing gnome-shell.
Post the output if any errors occur.

---

### Post by Frogs Hair on 2014-05-01
If all goes well install the following as well. 

```
sudo apt-get install gnome-shell-extensions
```

```
sudo apt-get install gnome-tweak-tool
```

---

### Post by Hl5tory on 2014-05-01
> **deadflowr said:**
> Try
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```
in that order, then try installing gnome-shell.
Post the output if any errors occur.

Thank you so much for responding. I ran the update and got a error: 
```
historically@Hl5tory:~$ sudo apt-get update
Ign http://dl.google.com stable InRelease
Hit http://dl.google.com stable Release.gpg                                    
Hit http://dl.google.com stable Release                                        
Ign http://us.archive.ubuntu.com trusty InRelease                              
Ign http://security.ubuntu.com trusty-security InRelease                       
Hit http://dl.google.com stable/main i386 Packages                             
Ign http://archive.canonical.com trusty InRelease                              
Ign http://extras.ubuntu.com trusty InRelease                                  
Ign http://us.archive.ubuntu.com trusty-updates InRelease                      
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://us.archive.ubuntu.com trusty-backports InRelease                    
Hit http://security.ubuntu.com trusty-security Release.gpg                     
Ign http://us.archive.ubuntu.com trusty-proposed InRelease                     
Hit http://archive.canonical.com trusty Release.gpg                            
Hit http://extras.ubuntu.com trusty Release.gpg                                
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://us.archive.ubuntu.com trusty Release.gpg                            
Hit http://security.ubuntu.com trusty-security Release                         
Hit http://us.archive.ubuntu.com trusty-updates Release.gpg                    
Hit http://archive.canonical.com trusty Release                                
Hit http://extras.ubuntu.com trusty Release                                    
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://dl.google.com stable/main Translation-en_US                         
Hit http://us.archive.ubuntu.com trusty-backports Release.gpg                  
Ign http://dl.google.com stable/main Translation-en                            
Hit http://us.archive.ubuntu.com trusty-proposed Release.gpg                   
Hit http://security.ubuntu.com trusty-security/main Sources                    
Hit http://archive.canonical.com trusty/partner Sources                        
Hit http://extras.ubuntu.com trusty/main Sources                               
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://us.archive.ubuntu.com trusty Release                                
Hit http://security.ubuntu.com trusty-security/restricted Sources              
Hit http://us.archive.ubuntu.com trusty-updates Release                        
Hit http://archive.canonical.com trusty/partner i386 Packages                  
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://us.archive.ubuntu.com trusty-backports Release                      
Hit http://us.archive.ubuntu.com trusty-proposed Release                       
Hit http://security.ubuntu.com trusty-security/universe Sources                
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://us.archive.ubuntu.com trusty/main Sources                           
Hit http://us.archive.ubuntu.com trusty/restricted Sources                     
Hit http://security.ubuntu.com trusty-security/multiverse Sources              
Hit http://us.archive.ubuntu.com trusty/universe Sources                       
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://us.archive.ubuntu.com trusty/multiverse Sources                     
Hit http://security.ubuntu.com trusty-security/main i386 Packages              
Hit http://us.archive.ubuntu.com trusty/main i386 Packages                     
Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages               
Hit http://security.ubuntu.com trusty-security/restricted i386 Packages        
Hit http://us.archive.ubuntu.com trusty/universe i386 Packages                 
Hit http://security.ubuntu.com trusty-security/universe i386 Packages          
Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages               
Hit http://security.ubuntu.com trusty-security/multiverse i386 Packages        
Ign http://ppa.launchpad.net trusty Release.gpg                                
Hit http://us.archive.ubuntu.com trusty/main Translation-en                    
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en              
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://security.ubuntu.com trusty-security/main Translation-en             
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en              
Hit http://ppa.launchpad.net trusty Release.gpg                                
Ign http://archive.canonical.com trusty/partner Translation-en_US              
Hit http://us.archive.ubuntu.com trusty/universe Translation-en                
Ign http://extras.ubuntu.com trusty/main Translation-en_US                     
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://us.archive.ubuntu.com trusty-updates/main Sources                   
Hit http://us.archive.ubuntu.com trusty-updates/restricted Sources             
Ign http://archive.canonical.com trusty/partner Translation-en                 
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://us.archive.ubuntu.com trusty-updates/universe Sources     
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Sources   
Hit http://us.archive.ubuntu.com trusty-updates/main i386 Packages   
Hit http://ppa.launchpad.net trusty Release                          
Hit http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages       
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en
Hit http://us.archive.ubuntu.com trusty-updates/universe i386 Packages
Ign http://ppa.launchpad.net trusty Release    
Hit http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages
Hit http://ppa.launchpad.net trusty Release                          
Hit http://security.ubuntu.com trusty-security/restricted Translation-en       
Hit http://ppa.launchpad.net trusty Release                          
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://us.archive.ubuntu.com trusty-updates/main Translation-en            
Hit http://security.ubuntu.com trusty-security/universe Translation-en
Hit http://ppa.launchpad.net trusty Release                          
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en      
Hit http://ppa.launchpad.net trusty/main i386 Packages               
Hit http://us.archive.ubuntu.com trusty-updates/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty-updates/universe Translation-en
Hit http://us.archive.ubuntu.com trusty-backports/main Sources
Hit http://us.archive.ubuntu.com trusty-backports/restricted Sources
Hit http://us.archive.ubuntu.com trusty-backports/universe Sources
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Sources
Hit http://us.archive.ubuntu.com trusty-backports/main i386 Packages 
Hit http://us.archive.ubuntu.com trusty-backports/restricted i386 Packages
Hit http://us.archive.ubuntu.com trusty-backports/universe i386 Packages
Hit http://us.archive.ubuntu.com trusty-backports/multiverse i386 Packages
Hit http://us.archive.ubuntu.com trusty-backports/main Translation-en
Hit http://ppa.launchpad.net trusty/main i386 Packages               
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Translation-en
Hit http://us.archive.ubuntu.com trusty-backports/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty-backports/universe Translation-en
Hit http://ppa.launchpad.net trusty/main i386 Packages               
Hit http://us.archive.ubuntu.com trusty-proposed/restricted i386 Packages
Ign http://security.ubuntu.com trusty-security/main Translation-en_US
Hit http://us.archive.ubuntu.com trusty-proposed/universe i386 Packages
Ign http://security.ubuntu.com trusty-security/multiverse Translation-en_US
Hit http://ppa.launchpad.net trusty/main i386 Packages               
Hit http://us.archive.ubuntu.com trusty-proposed/multiverse i386 Packages
Hit http://us.archive.ubuntu.com trusty-proposed/main i386 Packages  
Ign http://security.ubuntu.com trusty-security/restricted Translation-en_US
Hit http://us.archive.ubuntu.com trusty-proposed/main Translation-en 
Hit http://us.archive.ubuntu.com trusty-proposed/multiverse Translation-en
Hit http://ppa.launchpad.net trusty/main i386 Packages               
Hit http://us.archive.ubuntu.com trusty-proposed/restricted Translation-en
Ign http://security.ubuntu.com trusty-security/universe Translation-en_US
Hit http://us.archive.ubuntu.com trusty-proposed/universe Translation-en
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US
Ign http://us.archive.ubuntu.com trusty-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com trusty-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com trusty-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com trusty-backports/main Translation-en_US
Ign http://us.archive.ubuntu.com trusty-backports/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com trusty-backports/restricted Translation-en_US
Ign http://us.archive.ubuntu.com trusty-backports/universe Translation-en_US
Ign http://us.archive.ubuntu.com trusty-proposed/main Translation-en_US
Ign http://us.archive.ubuntu.com trusty-proposed/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com trusty-proposed/restricted Translation-en_US
Ign http://us.archive.ubuntu.com trusty-proposed/universe Translation-en_US
Ign http://ppa.launchpad.net trusty/main Translation-en_US
Ign http://ppa.launchpad.net trusty/main Translation-en
[B]Err http://ppa.launchpad.net trusty/main i386 Packages
  404  Not Found[/B]
Ign http://ppa.launchpad.net trusty/main Translation-en_US
Ign http://ppa.launchpad.net trusty/main Translation-en
Ign http://ppa.launchpad.net trusty/main Translation-en_US
Ign http://ppa.launchpad.net trusty/main Translation-en
Ign http://ppa.launchpad.net trusty/main Translation-en_US
Ign http://ppa.launchpad.net trusty/main Translation-en
Ign http://ppa.launchpad.net trusty/main Translation-en_US
Ign http://ppa.launchpad.net trusty/main Translation-en
Ign http://ppa.launchpad.net trusty/main Translation-en_US
Ign http://ppa.launchpad.net trusty/main Translation-en
**W: Failed to fetch http://ppa.launchpad.net/fsvh/pacifica-icon-theme/ubuntu/dists/trusty/main/binary-i386/Packages  404  Not Found**


E: Some index files failed to download. They have been ignored, or old ones used instead.
```
Am not sure what that means. I ran the other two (Upgrade & dist Update) and there was nothing to update. But I ran gnome shell install again and as I thought it didn't work.

---

### Post by Frogs Hair on 2014-05-01
[B]```
: Failed to fetch http://ppa.launchpad.net/fsvh/pacifica-icon-theme/ubuntu/dists/trusty/main/binary-i386/Packages  404  Not Found
```
T[/B]here is no 14.04 package available for the icon theme. To clear the error open software & Updates and remove the source from the other software tab.

---

### Post by deadflowr on 2014-05-01
> **Frogs Hair said:**
> [B]```
: Failed to fetch http://ppa.launchpad.net/fsvh/pacifica-icon-theme/ubuntu/dists/trusty/main/binary-i386/Packages  404  Not Found
```
T[/B]here is no 14.04 package available for the icon theme. To clear the error open software & Updates and remove the source from the other software tab.

If it doesn't ask you to reload after unchecking/removing the ppa, then run the apt-get update command again.

---

### Post by Hl5tory on 2014-05-02
> **Frogs Hair said:**
> [B]```
: Failed to fetch http://ppa.launchpad.net/fsvh/pacifica-icon-theme/ubuntu/dists/trusty/main/binary-i386/Packages  404  Not Found
```
T[/B]here is no 14.04 package available for the icon theme. To clear the error open software & Updates and remove the source from the other software tab.

I went and removed the Pacifia Icon ppa's and no it didn't ask me to re-install it. I ran the update and didn't get any error's untill I ran the upgrade then towards the end I got an error. But to be safe this is what ran when I did "sudo apt-get upgrade"
```
 historically@Hl5tory:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  duplicity libfreetype6 libfreetype6-dev libsmbclient libwbclient0 numix-icon-theme numix-icon-theme-circle
  python-samba samba-common samba-common-bin samba-libs simple-scan smbclient xserver-xorg-video-ati
  xserver-xorg-video-radeon
15 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 10.4 MB of archives.
After this operation, 2,048 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://us.archive.ubuntu.com/ubuntu/ trusty-proposed/main libfreetype6-dev i386 2.5.2-1ubuntu2.1 [608 kB]
Get:2 http://ppa.launchpad.net/numix/ppa/ubuntu/ trusty/main numix-icon-theme all 0.3+141~201405020003~ubuntu14.04.1 [1,847 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ trusty-proposed/main libfreetype6 i386 2.5.2-1ubuntu2.1 [300 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ trusty-proposed/main libwbclient0 i386 2:4.1.6+dfsg-1ubuntu2.14.04.1 [28.1 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ trusty-proposed/main python-samba i386 2:4.1.6+dfsg-1ubuntu2.14.04.1 [828 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu/ trusty-proposed/main samba-common-bin i386 2:4.1.6+dfsg-1ubuntu2.14.04.1 [490 kB]
Get:7 http://us.archive.ubuntu.com/ubuntu/ trusty-proposed/main smbclient i386 2:4.1.6+dfsg-1ubuntu2.14.04.1 [242 kB]
Get:8 http://us.archive.ubuntu.com/ubuntu/ trusty-proposed/main libsmbclient i386 2:4.1.6+dfsg-1ubuntu2.14.04.1 [50.0 kB]
Get:9 http://us.archive.ubuntu.com/ubuntu/ trusty-proposed/main samba-libs i386 2:4.1.6+dfsg-1ubuntu2.14.04.1 [4,089 kB]
Get:10 http://ppa.launchpad.net/numix/ppa/ubuntu/ trusty/main numix-icon-theme-circle all 0.2+201405020047~434~ubuntu14.04.1 [1,277 kB]
Get:11 http://us.archive.ubuntu.com/ubuntu/ trusty-proposed/main samba-common all 2:4.1.6+dfsg-1ubuntu2.14.04.1 [157 kB]
Get:12 http://us.archive.ubuntu.com/ubuntu/ trusty-proposed/main duplicity i386 0.6.23-1ubuntu4.1 [199 kB]     
Get:13 http://us.archive.ubuntu.com/ubuntu/ trusty-proposed/main simple-scan i386 3.12.1-0ubuntu1 [134 kB]     
Get:14 http://us.archive.ubuntu.com/ubuntu/ trusty-proposed/main xserver-xorg-video-radeon i386 1:7.3.0-1ubuntu3.1 [115 kB]
Get:15 http://us.archive.ubuntu.com/ubuntu/ trusty-proposed/main xserver-xorg-video-ati i386 1:7.3.0-1ubuntu3.1 [6,688 B]
Fetched 10.4 MB in 7s (1,408 kB/s)                                                                             
Preconfiguring packages ...
(Reading database ... 202317 files and directories currently installed.)
Preparing to unpack .../libfreetype6-dev_2.5.2-1ubuntu2.1_i386.deb ...
Unpacking libfreetype6-dev (2.5.2-1ubuntu2.1) over (2.5.2-1ubuntu2) ...
Preparing to unpack .../libfreetype6_2.5.2-1ubuntu2.1_i386.deb ...
Unpacking libfreetype6:i386 (2.5.2-1ubuntu2.1) over (2.5.2-1ubuntu2) ...
Preparing to unpack .../libwbclient0_2%3a4.1.6+dfsg-1ubuntu2.14.04.1_i386.deb ...
Unpacking libwbclient0:i386 (2:4.1.6+dfsg-1ubuntu2.14.04.1) over (2:4.1.6+dfsg-1ubuntu2) ...
Preparing to unpack .../python-samba_2%3a4.1.6+dfsg-1ubuntu2.14.04.1_i386.deb ...
Unpacking python-samba (2:4.1.6+dfsg-1ubuntu2.14.04.1) over (2:4.1.6+dfsg-1ubuntu2) ...
Preparing to unpack .../samba-common-bin_2%3a4.1.6+dfsg-1ubuntu2.14.04.1_i386.deb ...
Unpacking samba-common-bin (2:4.1.6+dfsg-1ubuntu2.14.04.1) over (2:4.1.6+dfsg-1ubuntu2) ...
Preparing to unpack .../smbclient_2%3a4.1.6+dfsg-1ubuntu2.14.04.1_i386.deb ...
Unpacking smbclient (2:4.1.6+dfsg-1ubuntu2.14.04.1) over (2:4.1.6+dfsg-1ubuntu2) ...
Preparing to unpack .../libsmbclient_2%3a4.1.6+dfsg-1ubuntu2.14.04.1_i386.deb ...
Unpacking libsmbclient:i386 (2:4.1.6+dfsg-1ubuntu2.14.04.1) over (2:4.1.6+dfsg-1ubuntu2) ...
Preparing to unpack .../samba-libs_2%3a4.1.6+dfsg-1ubuntu2.14.04.1_i386.deb ...
Unpacking samba-libs:i386 (2:4.1.6+dfsg-1ubuntu2.14.04.1) over (2:4.1.6+dfsg-1ubuntu2) ...
Preparing to unpack .../samba-common_2%3a4.1.6+dfsg-1ubuntu2.14.04.1_all.deb ...
Unpacking samba-common (2:4.1.6+dfsg-1ubuntu2.14.04.1) over (2:4.1.6+dfsg-1ubuntu2) ...
Preparing to unpack .../duplicity_0.6.23-1ubuntu4.1_i386.deb ...
Unpacking duplicity (0.6.23-1ubuntu4.1) over (0.6.23-1ubuntu4) ...
Preparing to unpack .../simple-scan_3.12.1-0ubuntu1_i386.deb ...
Unpacking simple-scan (3.12.1-0ubuntu1) over (3.12.0-0ubuntu1) ...
Preparing to unpack .../xserver-xorg-video-radeon_1%3a7.3.0-1ubuntu3.1_i386.deb ...
Unpacking xserver-xorg-video-radeon (1:7.3.0-1ubuntu3.1) over (1:7.3.0-1ubuntu3) ...
Preparing to unpack .../xserver-xorg-video-ati_1%3a7.3.0-1ubuntu3.1_i386.deb ...
Unpacking xserver-xorg-video-ati (1:7.3.0-1ubuntu3.1) over (1:7.3.0-1ubuntu3) ...
Preparing to unpack .../numix-icon-theme_0.3+141~201405020003~ubuntu14.04.1_all.deb ...
Unpacking numix-icon-theme (0.3+141~201405020003~ubuntu14.04.1) over (0.3+139~201404162023~ubuntu14.04.1) ...
Preparing to unpack .../numix-icon-theme-circle_0.2+201405020047~434~ubuntu14.04.1_all.deb ...
Unpacking numix-icon-theme-circle (0.2+201405020047~434~ubuntu14.04.1) over (0.2+201404292036~433~ubuntu14.04.1) ...
[B]gtk-update-icon-cache-3.0: The generated cache was invalid.
WARNING: icon cache generation failed for /usr/share/icons/Numix-Circle[/B]
Processing triggers for doc-base (0.10.5) ...
Processing 1 changed doc-base file...
Processing triggers for man-db (2.6.7.1-1) ...
Processing triggers for libglib2.0-0:i386 (2.41.0~git20140425.254b8dfc-0ubuntu1~14.04~ricotz0) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.54ubuntu1) ...
Setting up libfreetype6:i386 (2.5.2-1ubuntu2.1) ...
Setting up libfreetype6-dev (2.5.2-1ubuntu2.1) ...
Setting up libwbclient0:i386 (2:4.1.6+dfsg-1ubuntu2.14.04.1) ...
Setting up samba-libs:i386 (2:4.1.6+dfsg-1ubuntu2.14.04.1) ...
Setting up python-samba (2:4.1.6+dfsg-1ubuntu2.14.04.1) ...
Setting up samba-common (2:4.1.6+dfsg-1ubuntu2.14.04.1) ...
Setting up samba-common-bin (2:4.1.6+dfsg-1ubuntu2.14.04.1) ...
Setting up libsmbclient:i386 (2:4.1.6+dfsg-1ubuntu2.14.04.1) ...
Setting up smbclient (2:4.1.6+dfsg-1ubuntu2.14.04.1) ...
Setting up duplicity (0.6.23-1ubuntu4.1) ...
Setting up simple-scan (3.12.1-0ubuntu1) ...
Setting up xserver-xorg-video-radeon (1:7.3.0-1ubuntu3.1) ...
Setting up xserver-xorg-video-ati (1:7.3.0-1ubuntu3.1) ...
Setting up numix-icon-theme (0.3+141~201405020003~ubuntu14.04.1) ...
Setting up numix-icon-theme-circle (0.2+201405020047~434~ubuntu14.04.1) ...
gtk-update-icon-cache: **Failed to open file /usr/share/icons/Numix-Circle/.icon-theme.cache : File exists**
Processing triggers for libc-bin (2.19-0ubuntu6) ...



```

Numix-Circle is actually my current Icon pack right now and it works fine so I don't know why am getting that error.
I ran Gnome-shell again after that and got the same error as the first time.

I really appreciate you guys helping me :D

---

### Post by Frogs Hair on 2014-05-02
I wouldn't worry about the Numix PPA, but it should be reported to maintainer. You should be able to continue with the Gnome Shell installation.

```
sudo apt-get update
```
```
sudo apt-get install gnome-shell

```
```
sudo apt-get install gnome-shell-extensions
```
```
sudo apt-get install gnome-tweak-tool
```

---

### Post by Hl5tory on 2014-05-02
> **Frogs Hair said:**
> I wouldn't worry about the Numix PPA, but it should be reported to maintainer. You should be able to continue with the Gnome Shell installation.

```
sudo apt-get update
```
```
sudo apt-get install gnome-shell

```
```
sudo apt-get install gnome-shell-extensions
```
```
sudo apt-get install gnome-tweak-tool
```

I tried those again and I got this error again : 
```
historically@Hl5tory:~$ sudo apt-get install gnome-shell
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 gnome-shell : Depends: gir1.2-mutter-3.0 (>= 3.11.91) but it is not going to be installed
               Depends: libmutter0d (>= 3.11) but it is not going to be installed
               Depends: libmutter0d (< 3.12) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.



```

---

### Post by Frogs Hair on 2014-05-02
Post the output of the following .```
 cat /etc/apt/sources.list
```

---

### Post by Hl5tory on 2014-05-02
> **Frogs Hair said:**
> Post the output of the following .```
 cat /etc/apt/sources.list
```

```
historically@Hl5tory:~$  cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 14.04 LTS _Trusty Tahr_ - Release i386 (20140417)]/ trusty main restricted


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ trusty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty universe
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu trusty-security main restricted
deb-src http://security.ubuntu.com/ubuntu trusty-security main restricted
deb http://security.ubuntu.com/ubuntu trusty-security universe
deb-src http://security.ubuntu.com/ubuntu trusty-security universe
deb http://security.ubuntu.com/ubuntu trusty-security multiverse
deb-src http://security.ubuntu.com/ubuntu trusty-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu trusty partner
deb-src http://archive.canonical.com/ubuntu trusty partner


## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu trusty main
deb-src http://extras.ubuntu.com/ubuntu trusty main
deb http://us.archive.ubuntu.com/ubuntu/ trusty-proposed restricted universe multiverse main



```

---

### Post by Frogs Hair on 2014-05-02
Do you have PPA.s other than Numix ?

---

### Post by Hl5tory on 2014-05-02
> **Frogs Hair said:**
> Do you have PPA.s other than Numix ?


I have nooblab, ricotz, diesch, numix, and linrunner.

---

### Post by Frogs Hair on 2014-05-02
The ricotz testing PPA is the problem and It would need to be purged  before installing a repository version of the Gnome Shell. Use the PPA or Repository version not both. I have had nothing but problems with Gnome Shell PPAS and don't even try anymore .This gets more complicated if you upgraded with the PPA enabled. 

[https://launchpad.net/~ricotz/+archive/testing](https://launchpad.net/~ricotz/+archive/testing)


WHILE USING THIS PPA MAKE SURE YOU ALSO ADDED THE GNOME3 PPAs!
ppa:gnome3-team/gnome3 ([https://launchpad.net/~gnome3-team/+archive/gnome3]("https://launchpad.net/%7Egnome3-team/+archive/gnome3"))
ppa:gnome3-team/gnome3-staging ([https://launchpad.net/~gnome3-team/+archive/gnome3-staging]("https://launchpad.net/%7Egnome3-team/+archive/gnome3-staging"))

---

### Post by Hl5tory on 2014-05-02
Am sorry I don't understand what exactly am suppose to do.

---

### Post by Frogs Hair on 2014-05-02
Did you install the following PPA before Upgrading to 14.04 ?

 [https://launchpad.net/~ricotz/+archive/testing ]("https://launchpad.net/%7Ericotz/+archive/testing")

---

### Post by Hl5tory on 2014-05-02
> **Frogs Hair said:**
> Did you install the following PPA before Upgrading to 14.04 ?

 [https://launchpad.net/~ricotz/+archive/testing ]("https://launchpad.net/%7Ericotz/+archive/testing")

All I did was download Ubuntu 14.04 from the Ubuntu website and made a bootable flash drive.. not sure when ricotz was installed. Is it the problem?

---

### Post by Frogs Hair on 2014-05-03
I thought it was an upgrade because of the 13.10 icon theme PPA being installed . The testing PPA includes experimental packages for Gnome 3.12 and is most likely the problem. Follow the instructions on the linked page and add the other two PPAS or remove the testing PPA . If you are inexperienced I would opt for removing the testing PPA and install the Gnome shell 3.10 from the repository. There was a PPA Purge available for 13.10 , but I have been unable locate a version for 14.04 so you might have to do some searching or wait until a purge is available. 


Another options is to disable the testing PPA and run the following commands to remove un-needed package from the system and fully reinstall the ubuntu-desktpp . This is not without some risk, but completely installing Gnome 3.12 is also risky.  

```
sudo apt-get update 
```
```
sudo apt-get autoremove
```
```
sudo apt-get install --reinstall ubuntu-desktop
```

---

