---
title: "apt broken: files list contains empty filename"
date: 2009-04-21
forum: General Help
---

### Post by sphilli8 on 2009-04-21
Folks,
I recently upgraded from Hardy to Jaunty, because my apt was constantly breaking and I thought that might fix it. Buh-bow. It's broken again.

Here is the error message:
```
Fetched 80.3MB in 7min 44s (173kB/s)
Extracting templates from packages: 100%
Preconfiguring packages ...
nvidia-common failed to preconfigure, with exit status 139
(Reading database ... dpkg: unrecoverable fatal error, aborting:
 files list file for package `libgl1-mesa-dri' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

I have tried both:
```
echo -en '\n' | sudo tee -a /var/lib/dpkg/info
```
and
```
sudo dpkg --configure -a
```

after reading other people's problems on the 'net, but neither has worked.

Can someone help?

---

### Post by sphilli8 on 2009-04-21
Righto, I have now spent several hours trying to fix my apt problems. Each time I overcome one issue ( I got past the problem in the post above by purging the package in question. It then simply replaced that package name with another, and so on and so on), I am confronted with another. I have now reached a dead end. Maybe someone can help.

The second last error message  I got was:
[CODE]bzip2: Data integrity error when decompressing.                                                                                                
        Input file = (stdin), output file = (stdout)                                                                                           

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.     

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.            

Err http://au.archive.ubuntu.com jaunty/universe Sources                                                                                       
  Sub-process bzip2 returned an error code (2)                                                                                                 
Fetched 7132kB in 47s (150kB/s)                                                                                                                
Reading package lists... Done    [/CODE}

So I did a "sudo aptitude purge bzip2" on it, and got given this:
[CODE]$ sudo aptitude purge bzip2
Reading package lists... Done                          
Building dependency tree                               
Reading state information... Done                      
Reading extended state information                     
Initializing package states... Done                    
The following packages are BROKEN:                     
  akregator amarok apt apt-transport-https apt-utils aptitude ark aspell cdrdao cups cupsddk cupsddk-drivers dolphin dragonplayer 
  dvd+rw-tools exiv2 gcc-4.3 gettext-base gparted groff-base gwenview hal hpijs k3b kaddressbook kamera kate kde-style-qtcurve    
  kde-window-manager kde-zeroconf kdebase-bin kdebase-plasma kdebase-runtime kdebase-runtime-bin-kde4 kdebase-workspace-bin       
  kdebase-workspace-libs4+5 kdebluetooth kdegraphics-strigi-plugins kdelibs-bin kdelibs4c2a kdelibs5 kdemultimedia-kio-plugins kdepasswd 
  kdepim-kresources kdepim-strigi-plugins kdepim-wizards kdepimlibs5 kdeplasma-addons kdesudo kdm kfind khelpcenter4 klipper kmag kmail  
  kmix kmousetool knotes konqueror konqueror-nsplugins konqueror-plugin-searchbar konsole kontact kopete korganizer kpackagekit krdc krfb 
  krusader ksnapshot ksysguard ksystemlog ktimetracker ktorrent kubuntu-desktop kvkbd kwalletmanager lftp libakonadiprivate1 libaspell15  
  libavahi-qt3-1 libboost-program-options1.35.0 libc6 libcaca0 libcairomm-1.0-1 libclucene0ldbl libcwidget3 libdbus-qt-1-1c2              
  libdirectfb-1.0-0 libdjvulibre21 libenchant1c2a libept0 libexiv2-5 libflac++6 libgc1c2 libgksu2-0 libglibmm-2.4-1c2a libglu1-mesa       
  libgtkmm-2.4-1c2a libhunspell-1.2-0 libicu38 libilmbase6 libk3b3 libk3b3-extracodecs libkcddb4 libkdecorations4 libkdepim4 libkexiv2-7  
  libkholidays4 libkipi6 libkleo4 libkonq5 libkpgp4 libksieve4 libkwineffects1 libmimelib4 libmodplug0c2 libmsn0.1 libmusicbrainz4c2a     
  libokularcore1 libopenexr6 libpackagekit-qt11 libpangomm-1.4-1 libphonon4 libplasma3 libpoppler-qt4-3 libpoppler4 libqca2               
  libqca2-plugin-ossl libqedje0 libqt3-mt libqt4-assistant libqt4-dbus libqt4-designer libqt4-help libqt4-network libqt4-opengl           
  libqt4-qt3support libqt4-script libqt4-sql libqt4-sql-mysql libqt4-sql-sqlite libqt4-svg libqt4-test libqt4-webkit libqt4-xml           
  libqt4-xmlpatterns libqtcore4 libqtgui4 libqzion0 libsearchclient0 libsigc++-2.0-0c2a libsmbios2 libsoprano4 libstdc++6                 
  libstlport4.6ldbl libstreamanalyzer0 libstreams0 libstrigihtmlgui0 libtag1c2a libwpd8c2a libwpg-0.1-1 libwps-0.1-1 libxapian15 lshw lzma 
  okular okular-extra-backends openoffice.org-base-core openoffice.org-calc openoffice.org-core openoffice.org-draw openoffice.org-impress 
  openoffice.org-kde openoffice.org-math openoffice.org-writer phonon-backend-xine pinentry-qt4 plasma-widget-network-manager              
  plasma-widget-quickaccess policykit-kde poppler-utils python-apt python-kde4 python-qt4 python-qt4-dbus python-sip4 python-uno           
  python-xapian qt4-qtconfig quassel skype soprano-daemon speedcrunch splix strigi-client strigi-daemon systemsettings telnet toshset      
  ubuntu-minimal uno-libs3 ure xserver-xorg-core xserver-xorg-video-ati                                                                    
The following packages will be REMOVED:                                                                                                    
  apport{u} bzip2{ap} python-apport{u} python-problem-report{u}                                                                            
The following partially installed packages will be configured:                                                                             
  linux-headers-2.6.28-11-generic linux-headers-generic                                                                                    
0 packages upgraded, 0 newly installed, 4 to remove and 18 not upgraded.                                                                   
Need to get 0B of archives. After unpacking 1483kB will be freed.                                                                          
The following packages have unmet dependencies:                                                                                            
  libclucene0ldbl: Depends: libgcc1 (>= 1:4.1.1-21) but it is not installable                                                              
  libstlport4.6ldbl: Depends: libgcc1 (>= 1:4.1.1-21) but it is not installable                                                            
  ksystemlog: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                      
  krdc: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                            
  libwpd8c2a: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                      
  krfb: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                            
  kdebase-plasma: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                  
  libstdc++6: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                      
  kdelibs4c2a: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                     
  libqca2: Depends: libgcc1 (>= 1:4.1.1-21) but it is not installable                                                                      
  libqt4-opengl: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                   
  libenchant1c2a: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                  
  openoffice.org-core: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                             
  openoffice.org-writer: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                           
  libqt4-assistant: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                
  krusader: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                        
  openoffice.org-impress: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                          
  aspell: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                          
  telnet: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                          
  lshw: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                            
  libcaca0: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                        
  libk3b3: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                         
  xserver-xorg-video-ati: Depends: xserver-xorg-video-radeon but it is not installable                                                     
  libdjvulibre21: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                  
  plasma-widget-quickaccess: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                       
  kpackagekit: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                     
  openoffice.org-draw: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                             
  libicu38: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                        
  libilmbase6: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                     
  libkwineffects1: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                 
  ksnapshot: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                       
  kde-style-qtcurve: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                               
  kdebluetooth: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                    
  libkipi6: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                        
  policykit-kde: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                   
  cupsddk: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                         
  openoffice.org-kde: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                              
  lzma: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                            
  libboost-program-options1.35.0: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                  
  libqt4-test: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                     
  gparted: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                         
  kdebase-runtime: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                 
  libkleo4: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                        
  libqt4-sql-mysql: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                
  libqt4-dbus: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                     
  libwpg-0.1-1: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                    
  konqueror-nsplugins: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                             
  gwenview: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                        
            Depends: libsopralo4 (>= 2.2.2) which is a virtual package.                                                                    
  kdelibs5: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                        
  okular-extra-backends: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                           
  hpijs: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                           
  dvd+rw-tools: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                    
  libglu1-mesa: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                    
  apt-transport-https: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                             
  quassel: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                         
  libqt4-qt3support: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                               
  libsearchclient0: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                
  klipper: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                         
  libmimelib4: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                     
  kdemultimedia-kio-plugins: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                       
  kdeplasma-addons: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                
  aptitude: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                        
  libflac++6: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                      
  python-apt: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                      
  kontact: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                         
  groff-base: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                      
  kdebase-workspace-libs4+5: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                       
  libkexiv2-7: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                     
  ksysguard: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                       
  libsmbios2: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                      
  libexiv2-5: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                      
  libkcddb4: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                       
  libcwidget3: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                     
  xserver-xorg-core: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                               
  kubuntu-desktop: Depends: kuser but it is not installable                                                                                
  dolphin: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                         
  gcc-4.3: Depends: libgcc1 (>= 1:4.3.3-5ubuntu4) but it is not installable                                                                
  toshset: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                         
  kdesudo: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                         
  apt-utils: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                       
  kde-zeroconf: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                    
  libdirectfb-1.0-0: Depends: libts-0.0-0 (>= 1.0) but it is not installable                                                               
  skype: Depends: libgcc1 (>= 1:4.1.1-12) but it is not installable                                                                        
  konsole: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                         
  libcairomm-1.0-1: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                
  libakonadiprivate1: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                              
  libqt4-xmlpatterns: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                              
  korganizer: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                      
  k3b: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                             
  libsoprano4: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                     
  akregator: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                       
  libglibmm-2.4-1c2a: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                              
  libqt4-help: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                     
  libmusicbrainz4c2a: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                              
  python-qt4: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                      
  kamera: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                          
  apt: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                             
  ark: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                             
  libkpgp4: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                        
  libk3b3-extracodecs: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                             
  libpackagekit-qt11: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                              
  uno-libs3: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                       
  kdebase-runtime-bin-kde4: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                        
  libqt4-webkit: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                   
  kdebase-workspace-bin: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                           
                         Depends: libstrigiqtdbusclient0 (>= 0.6.4) but it is not installable                                              
  libhunspell-1.2-0: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                               
  kvkbd: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                           
  openoffice.org-math: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                             
  libkonq5: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                        
  libkdepim4: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                      
  libkdecorations4: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                
  libsigc++-2.0-0c2a: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                              
  hal: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                             
  libpangomm-1.4-1: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                
  libqtcore4: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                      
  libavahi-qt3-1: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                  
  libept0: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                         
  python-qt4-dbus: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                 
  python-uno: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                      
  python-sip4: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                     
  konqueror-plugin-searchbar: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                      
  libksieve4: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                      
  kfind: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                           
  kdebase-bin: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                     
  systemsettings: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                  
  splix: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                           
  kdm: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                             
  speedcrunch: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                     
  python-xapian: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                   
  libopenexr6: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                     
  amarok: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                          
  libpoppler4: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                     
  libqt4-sql-sqlite: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                               
  libqzion0: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                       
  libgtkmm-2.4-1c2a: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                               
  libxapian15: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                     
  ubuntu-minimal: Depends: bzip2 but it is not installable                                                                                 
  cups: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                            
  knotes: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                          
  openoffice.org-base-core: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                        
  libqt4-sql: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                      
  libdbus-qt-1-1c2: Depends: libgcc1 (>= 1:4.1.2) but it is not installable                                                                
  libqt4-svg: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                      
  libwps-0.1-1: Depends: libgcc1 (>= 1:4.1.1-21) but it is not installable                                                                 
  konqueror: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                       
  libpoppler-qt4-3: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                
  libstreamanalyzer0: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                              
  libphonon4: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                      
  kaddressbook: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                    
  libqt4-xml: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                      
  gettext-base: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                    
  cdrdao: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                          
  ure: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                             
  libplasma3: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                      
  cupsddk-drivers: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                 
  libqt4-network: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                  
  phonon-backend-xine: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                             
  libqt4-designer: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                 
  kdepimlibs5: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                     
  libstrigihtmlgui0: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                               
  kdelibs-bin: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                     
  libqtgui4: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                       
  khelpcenter4: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                    
  libtag1c2a: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                      
  libkholidays4: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                   
  libgksu2-0: Depends: libgcond2-4 (>= 2.13.5) which is a virtual package.                                                                 
  poppler-utils: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                   
  kdegraphics-strigi-plugins: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                      
  ktorrent: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                        
  libstreams0: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                     
  kwalletmanager: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                  
  libqca2-plugin-ossl: Depends: libgcc1 (>= 1:4.2.1) but it is not installable                                                             
  libmodplug0c2: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                   
  exiv2: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                           
  plasma-widget-network-manager: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                   
  ktimetracker: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                    
  kdepim-strigi-plugins: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                           
  kopete: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                          
  libgc1c2: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                        
  libokularcore1: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                  
                  Depends: libqt4-network (>= 4.5.0|+rc1) but 4.5.0-0ubuntu4 is installed.                                                 
  libqt3-mt: Depends: libgcc1 (>= 1:4.1.1-21) but it is not installable                                                                    
  kate: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                            
  kmail: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                           
  libqt4-script: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                   
  openoffice.org-calc: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                             
  libc6: Depends: libgcc1 but it is not installable                                                                                        
  soprano-daemon: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                  
  strigi-client: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                   
                 Depends: libstrigiqtdbusclient0 (= 0.6.4-0ubuntu2) but it is not installable                                              
  kde-window-manager: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                              
  dragonplayer: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                    
  okular: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                          
  kmousetool: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                      
  libaspell15: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                     
  pinentry-qt4: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                    
  libmsn0.1: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                       
  kmag: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                            
  kdepim-kresources: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                               
  kdepim-wizards: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                  
  libqedje0: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                       
  python-kde4: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                     
  strigi-daemon: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                   
  qt4-qtconfig: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                    
  lftp: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                            
  kdepasswd: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                       
  kmix: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                            
open: 1; closed: 54; defer: 60; conflict: 2                                                                                                   oUnable to resolve dependencies!  Giving up...                                                                                                  
The following packages are BROKEN:                                                                                                             
  akregator amarok apt apt-transport-https apt-utils aptitude ark aspell cdrdao cups cupsddk cupsddk-drivers dolphin dragonplayer              
  dvd+rw-tools exiv2 gcc-4.3 gettext-base gparted groff-base gwenview hal hpijs k3b kaddressbook kamera kate kde-style-qtcurve                 
  kde-window-manager kde-zeroconf kdebase-bin kdebase-plasma kdebase-runtime kdebase-runtime-bin-kde4 kdebase-workspace-bin                    
  kdebase-workspace-libs4+5 kdebluetooth kdegraphics-strigi-plugins kdelibs-bin kdelibs4c2a kdelibs5 kdemultimedia-kio-plugins kdepasswd       
  kdepim-kresources kdepim-strigi-plugins kdepim-wizards kdepimlibs5 kdeplasma-addons kdesudo kdm kfind khelpcenter4 klipper kmag kmail        
  kmix kmousetool knotes konqueror konqueror-nsplugins konqueror-plugin-searchbar konsole kontact kopete korganizer kpackagekit krdc krfb      
  krusader ksnapshot ksysguard ksystemlog ktimetracker ktorrent kubuntu-desktop kvkbd kwalletmanager lftp libakonadiprivate1 libaspell15       
  libavahi-qt3-1 libboost-program-options1.35.0 libc6 libcaca0 libcairomm-1.0-1 libclucene0ldbl libcwidget3 libdbus-qt-1-1c2                   
  libdirectfb-1.0-0 libdjvulibre21 libenchant1c2a libept0 libexiv2-5 libflac++6 libgc1c2 libgksu2-0 libglibmm-2.4-1c2a libglu1-mesa            
  libgtkmm-2.4-1c2a libhunspell-1.2-0 libicu38 libilmbase6 libk3b3 libk3b3-extracodecs libkcddb4 libkdecorations4 libkdepim4 libkexiv2-7       
  libkholidays4 libkipi6 libkleo4 libkonq5 libkpgp4 libksieve4 libkwineffects1 libmimelib4 libmodplug0c2 libmsn0.1 libmusicbrainz4c2a          
  libokularcore1 libopenexr6 libpackagekit-qt11 libpangomm-1.4-1 libphonon4 libplasma3 libpoppler-qt4-3 libpoppler4 libqca2                    
  libqca2-plugin-ossl libqedje0 libqt3-mt libqt4-assistant libqt4-dbus libqt4-designer libqt4-help libqt4-network libqt4-opengl                
  libqt4-qt3support libqt4-script libqt4-sql libqt4-sql-mysql libqt4-sql-sqlite libqt4-svg libqt4-test libqt4-webkit libqt4-xml                
  libqt4-xmlpatterns libqtcore4 libqtgui4 libqzion0 libsearchclient0 libsigc++-2.0-0c2a libsmbios2 libsoprano4 libstdc++6                      
  libstlport4.6ldbl libstreamanalyzer0 libstreams0 libstrigihtmlgui0 libtag1c2a libwpd8c2a libwpg-0.1-1 libwps-0.1-1 libxapian15 lshw lzma     
  okular okular-extra-backends openoffice.org-base-core openoffice.org-calc openoffice.org-core openoffice.org-draw openoffice.org-impress     
  openoffice.org-kde openoffice.org-math openoffice.org-writer phonon-backend-xine pinentry-qt4 plasma-widget-network-manager                  
  plasma-widget-quickaccess policykit-kde poppler-utils python-apt python-kde4 python-qt4 python-qt4-dbus python-sip4 python-uno               
  python-xapian qt4-qtconfig quassel skype soprano-daemon speedcrunch splix strigi-client strigi-daemon systemsettings telnet toshset          
  ubuntu-minimal uno-libs3 ure xserver-xorg-core xserver-xorg-video-ati                                                                        
The following packages will be REMOVED:                                                                                                        
  apport{u} bzip2{ap} python-apport{u} python-problem-report{u}                                                                                
The following partially installed packages will be configured:                                                                                 
  linux-headers-2.6.28-11-generic linux-headers-generic                                                                                        
0 packages upgraded, 0 newly installed, 4 to remove and 18 not upgraded.                                                                       
Need to get 0B of archives. After unpacking 1483kB will be freed.                                                                              
aptitude failed to find a solution to these dependencies.  You can solve them yourself by hand or type 'n' to quit.                            
The following packages have unmet dependencies:                                                                                                
  libclucene0ldbl: Depends: libgcc1 (>= 1:4.1.1-21) but it is not installable                                                                  
  libstlport4.6ldbl: Depends: libgcc1 (>= 1:4.1.1-21) but it is not installable                                                                
  ksystemlog: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                          
  krdc: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                                
  libwpd8c2a: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                          
  krfb: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                                
  kdebase-plasma: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                      
  libstdc++6: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                          
  kdelibs4c2a: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                         
  libqca2: Depends: libgcc1 (>= 1:4.1.1-21) but it is not installable                                                                          
  libqt4-opengl: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                       
  libenchant1c2a: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                      
  openoffice.org-core: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                 
  openoffice.org-writer: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                               
  libqt4-assistant: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                    
  krusader: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                            
  openoffice.org-impress: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                              
  aspell: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                              
  telnet: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                              
  lshw: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                                
  libcaca0: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                            
  libk3b3: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                             
  xserver-xorg-video-ati: Depends: xserver-xorg-video-radeon but it is not installable                                                         
  libdjvulibre21: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                      
  plasma-widget-quickaccess: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                           
  kpackagekit: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                         
  openoffice.org-draw: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                 
  libicu38: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                            
  libilmbase6: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                         
  libkwineffects1: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                     
  ksnapshot: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                           
  kde-style-qtcurve: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                   
  kdebluetooth: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                        
  libkipi6: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                            
  policykit-kde: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                       
  cupsddk: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                             
  openoffice.org-kde: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                  
  lzma: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                                
  libboost-program-options1.35.0: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                      
  libqt4-test: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                         
  gparted: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                             
  kdebase-runtime: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                     
  libkleo4: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                            
  libqt4-sql-mysql: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                    
  libqt4-dbus: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                         
  libwpg-0.1-1: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                        
  konqueror-nsplugins: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                 
  gwenview: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                            
            Depends: libsopralo4 (>= 2.2.2) which is a virtual package.                                                                        
  kdelibs5: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                            
  okular-extra-backends: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                               
  hpijs: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                               
  dvd+rw-tools: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                        
  libglu1-mesa: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                        
  apt-transport-https: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                 
  quassel: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                             
  libqt4-qt3support: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                   
  libsearchclient0: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                    
  klipper: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                             
  libmimelib4: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                         
  kdemultimedia-kio-plugins: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                           
  kdeplasma-addons: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                    
  aptitude: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                            
  libflac++6: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                          
  python-apt: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                          
  kontact: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                             
  groff-base: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                          
  kdebase-workspace-libs4+5: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                           
  libkexiv2-7: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                         
  ksysguard: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                           
  libsmbios2: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                          
  libexiv2-5: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                          
  libkcddb4: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                           
  libcwidget3: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                         
  xserver-xorg-core: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                   
  kubuntu-desktop: Depends: kuser but it is not installable                                                                                    
  dolphin: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                             
  gcc-4.3: Depends: libgcc1 (>= 1:4.3.3-5ubuntu4) but it is not installable                                                                    
  toshset: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                             
  kdesudo: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                             
  apt-utils: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                           
  kde-zeroconf: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                        
  libdirectfb-1.0-0: Depends: libts-0.0-0 (>= 1.0) but it is not installable                                                                   
  skype: Depends: libgcc1 (>= 1:4.1.1-12) but it is not installable                                                                            
  konsole: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                             
  libcairomm-1.0-1: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                    
  libakonadiprivate1: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                  
  libqt4-xmlpatterns: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                  
  korganizer: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                          
  k3b: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                                 
  libsoprano4: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                         
  akregator: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                           
  libglibmm-2.4-1c2a: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                  
  libqt4-help: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                         
  libmusicbrainz4c2a: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                  
  python-qt4: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                          
  kamera: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                              
  apt: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                                 
  ark: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                                 
  libkpgp4: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                            
  libk3b3-extracodecs: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                 
  libpackagekit-qt11: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                  
  uno-libs3: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                           
  kdebase-runtime-bin-kde4: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                            
  libqt4-webkit: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                       
  kdebase-workspace-bin: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                               
                         Depends: libstrigiqtdbusclient0 (>= 0.6.4) but it is not installable                                                  
  libhunspell-1.2-0: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                   
  kvkbd: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                               
  openoffice.org-math: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                 
  libkonq5: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                            
  libkdepim4: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                          
  libkdecorations4: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                    
  libsigc++-2.0-0c2a: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                  
  hal: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                                 
  libpangomm-1.4-1: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                    
  libqtcore4: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                          
  libavahi-qt3-1: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                      
  libept0: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                             
  python-qt4-dbus: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                     
  python-uno: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                          
  python-sip4: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                         
  konqueror-plugin-searchbar: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                          
  libksieve4: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                          
  kfind: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                               
  kdebase-bin: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                         
  systemsettings: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                      
  splix: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                               
  kdm: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                                 
  speedcrunch: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                         
  python-xapian: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                       
  libopenexr6: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                         
  amarok: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                              
  libpoppler4: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                         
  libqt4-sql-sqlite: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                   
  libqzion0: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                           
  libgtkmm-2.4-1c2a: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                   
  libxapian15: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                         
  ubuntu-minimal: Depends: bzip2 but it is not installable                                                                                     
  cups: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                                
  knotes: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                              
  openoffice.org-base-core: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                            
  libqt4-sql: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                          
  libdbus-qt-1-1c2: Depends: libgcc1 (>= 1:4.1.2) but it is not installable                                                                    
  libqt4-svg: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                          
  libwps-0.1-1: Depends: libgcc1 (>= 1:4.1.1-21) but it is not installable                                                                     
  konqueror: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                           
  libpoppler-qt4-3: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                    
  libstreamanalyzer0: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                  
  libphonon4: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                          
  kaddressbook: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                        
  libqt4-xml: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                          
  gettext-base: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                        
  cdrdao: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                              
  ure: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                                 
  libplasma3: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                          
  cupsddk-drivers: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                     
  libqt4-network: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                      
  phonon-backend-xine: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                 
  libqt4-designer: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                     
  kdepimlibs5: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                         
  libstrigihtmlgui0: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                   
  kdelibs-bin: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                         
  libqtgui4: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                           
  khelpcenter4: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                        
  libtag1c2a: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                          
  libkholidays4: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                       
  libgksu2-0: Depends: libgcond2-4 (>= 2.13.5) which is a virtual package.                                                                     
  poppler-utils: Depends: libgcc1 (>= 1:4.1.1) but it is not installable                                                                       
  kdegraphics-strigi-plugins: Depends: libgcc1 (>= 1:4.1.1) but it is not installable
  ktorrent: Depends: libgcc1 (>= 1:4.1.1) but it is not installable
  libstreams0: Depends: libgcc1 (>= 1:4.1.1) but it is not installable
  kwalletmanager: Depends: libgcc1 (>= 1:4.1.1) but it is not installable
  libqca2-plugin-ossl: Depends: libgcc1 (>= 1:4.2.1) but it is not installable
  libmodplug0c2: Depends: libgcc1 (>= 1:4.1.1) but it is not installable
  exiv2: Depends: libgcc1 (>= 1:4.1.1) but it is not installable
  plasma-widget-network-manager: Depends: libgcc1 (>= 1:4.1.1) but it is not installable
  ktimetracker: Depends: libgcc1 (>= 1:4.1.1) but it is not installable
  kdepim-strigi-plugins: Depends: libgcc1 (>= 1:4.1.1) but it is not installable
  kopete: Depends: libgcc1 (>= 1:4.1.1) but it is not installable
  libgc1c2: Depends: libgcc1 (>= 1:4.1.1) but it is not installable
  libokularcore1: Depends: libgcc1 (>= 1:4.1.1) but it is not installable
                  Depends: libqt4-network (>= 4.5.0|+rc1) but 4.5.0-0ubuntu4 is installed.
  libqt3-mt: Depends: libgcc1 (>= 1:4.1.1-21) but it is not installable
  kate: Depends: libgcc1 (>= 1:4.1.1) but it is not installable
  kmail: Depends: libgcc1 (>= 1:4.1.1) but it is not installable
  libqt4-script: Depends: libgcc1 (>= 1:4.1.1) but it is not installable
  openoffice.org-calc: Depends: libgcc1 (>= 1:4.1.1) but it is not installable
  libc6: Depends: libgcc1 but it is not installable
  soprano-daemon: Depends: libgcc1 (>= 1:4.1.1) but it is not installable
  strigi-client: Depends: libgcc1 (>= 1:4.1.1) but it is not installable
                 Depends: libstrigiqtdbusclient0 (= 0.6.4-0ubuntu2) but it is not installable
  kde-window-manager: Depends: libgcc1 (>= 1:4.1.1) but it is not installable
  dragonplayer: Depends: libgcc1 (>= 1:4.1.1) but it is not installable
  okular: Depends: libgcc1 (>= 1:4.1.1) but it is not installable
  kmousetool: Depends: libgcc1 (>= 1:4.1.1) but it is not installable
  libaspell15: Depends: libgcc1 (>= 1:4.1.1) but it is not installable
  pinentry-qt4: Depends: libgcc1 (>= 1:4.1.1) but it is not installable
  libmsn0.1: Depends: libgcc1 (>= 1:4.1.1) but it is not installable
  kmag: Depends: libgcc1 (>= 1:4.1.1) but it is not installable
  kdepim-kresources: Depends: libgcc1 (>= 1:4.1.1) but it is not installable
  kdepim-wizards: Depends: libgcc1 (>= 1:4.1.1) but it is not installable
  libqedje0: Depends: libgcc1 (>= 1:4.1.1) but it is not installable
  python-kde4: Depends: libgcc1 (>= 1:4.1.1) but it is not installable
  strigi-daemon: Depends: libgcc1 (>= 1:4.1.1) but it is not installable
  qt4-qtconfig: Depends: libgcc1 (>= 1:4.1.1) but it is not installable
  lftp: Depends: libgcc1 (>= 1:4.1.1) but it is not installable
  kdepasswd: Depends: libgcc1 (>= 1:4.1.1) but it is not installable
  kmix: Depends: libgcc1 (>= 1:4.1.1) but it is not installable
Resolve these dependencies by hand? [N/+/-/_/:/?]
Abort.
[/CODE}

Yikes.

Please help.

---

### Post by sphilli8 on 2009-04-22
So, I reckon I've narrowed my ongoing APT breakages down to damaged hardware of some kind (unfortunately the motherboard I suspect, since a RAM test came up fine and I've tried a second hard drive with no success). That would explain why it was happening both before and after my Hardy-Jaunty upgrade.

Which sucks.

---

### Post by codeseer on 2009-04-22
Did you run a check on the Live CD?

---

### Post by sphilli8 on 2009-05-01
Yea, the CD was fine. I used it to install on a desktop (where I am now because the laptop in question is broken) and haven't had any probs

---

### Post by codeseer on 2009-05-01
> **sphilli8 said:**
> Yea, the CD was fine. I used it to install on a desktop (where I am now because the laptop in question is broken) and haven't had any probs

I wouldn't claim hardware failure until I had wiped the partitions and reinstalled fresh.

---

