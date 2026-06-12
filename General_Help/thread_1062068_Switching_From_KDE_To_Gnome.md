---
title: "Switching From KDE To Gnome"
date: 2009-02-06
forum: General Help
---

### Post by s1mp13m4n on 2009-02-06
Hello everyone.  I am new to Linux.  I installed Kubuntu 8.10 the other day and I do not like KDE it is to complex.  I have used Gnome in the past and I think it is simplier to use and cleaner.  I want to go back to Gnome and have that as my default environment.  How do I uninstall KDE and install Gnome?  I have tried some things online from using Google but they have not worked.

---

### Post by taurus on 2009-02-06
```
sudo apt-get update
sudo apt-get install ubuntu-desktop gdm
```

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by s1mp13m4n on 2009-02-06
It did not work, i used the code you pasted and also your link for KDE4.  I got errors both times.

---

### Post by taurus on 2009-02-06
Want to share the error messages?

---

### Post by optimistique1 on 2009-02-06
Hi Buddy, you can also go into Synaptic Package Manager and type in Ubuntu Desktop.  Highlight this for installation.  Then during installation it will ask you which default login you want, IE: GDM/KDM.  Pick GDM and then you should be good to go.  Make sure you log out after installation and then select Gnome as you default login.

I have done this and had no probs.

This way you have the option of of Gnome and KDE by selecting the session you want.  or you can go back to Synaptic and uninstall Kubuntu Desktop is you want.

See the below link if you need anymore help :-)

[http://psychocats.net/ubuntu/kde](http://psychocats.net/ubuntu/kde)

---

### Post by s1mp13m4n on 2009-02-06
results from the first lind of code:

paul@LinuxLaptop:~$ sudo apt-get update
[sudo] password for paul:              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Translation-en_US 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release.gpg          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Translation-en_US  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_US 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_US   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_US 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Sources                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Sources                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Sources                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Sources          
Reading package lists... Done                                                 
paul@LinuxLaptop:~$ sudo apt-get remove adept akregator amarok amarok-common amarok-engine-xine apport-qt ark dolphin dragonplayer exiv2 foomatic-db-gutenprint gdebi-kde gnupg-agent gtk-qt-engine guidance-power-manager gwenview hpijs-ppds hplip-gui ijsgutenprint imagemagick install-package jockey-kde k3b k3b-data kaddressbook kamera kate kde-icons-oxygen kde-printer-applet kde-window-manager kde-zeroconf kdebase-bin kdebase-data kdebase-plasma kdebase-runtime kdebase-runtime-bin-kde4 kdebase-runtime-data kdebase-runtime-data-common kdebase-workspace-bin kdebase-workspace-data kdebase-workspace-libs4+5 kdebluetooth kdegraphics-strigi-plugins kdelibs-bin kdelibs-data kdelibs4c2a kdelibs5 kdelibs5-data kdemultimedia-kio-plugins kdepasswd kdepim-kresources kdepim-strigi-plugins kdepim-wizards kdepimlibs-data kdepimlibs5 kdeplasma-addons kdeplasma-addons-data kdeplasma-addons-libs4 kdesudo kdm kfind kgrubeditor khelpcenter4 klipper kmag kmail kmix kmousetool knotes konqueror konqueror-nsplugins konqueror-plugin-searchbar konsole kontact konversation kopete korganizer krdc krfb ksnapshot ksysguard ksysguardd ksystemlog ktimetracker ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kuser kvkbd kwalletmanager language-selector-qt libakonadiprivate1 libarts1c2a libartsc0 libaudio2 libavahi-qt3-1 libcapseo0 libcaptury0 libclucene0ldbl libdbus-1-qt3 libdbus-qt-install ubuntu-desktop gdm                    sudo aptitude update exit
E: The update command takes no arguments     
paul@LinuxLaptop:~$ sudo apt-get update      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Translation-en_US       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Translation-en_US         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Translation-en_US       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release.gpg                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Translation-en_US     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Translation-en_US  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_US   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_US 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Sources                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Sources                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Sources
Reading package lists... Done
paul@LinuxLaptop:~$


Results from the second line of code:

paul@LinuxLaptop:~$ sudo apt-get update
[sudo] password for paul:              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Translation-en_US 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release.gpg          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Translation-en_US  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_US 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_US   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_US 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Sources                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Sources                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Sources                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Sources          
Reading package lists... Done                                                 
paul@LinuxLaptop:~$ sudo apt-get remove adept akregator amarok amarok-common amarok-engine-xine apport-qt ark dolphin dragonplayer exiv2 foomatic-db-gutenprint gdebi-kde gnupg-agent gtk-qt-engine guidance-power-manager gwenview hpijs-ppds hplip-gui ijsgutenprint imagemagick install-package jockey-kde k3b k3b-data kaddressbook kamera kate kde-icons-oxygen kde-printer-applet kde-window-manager kde-zeroconf kdebase-bin kdebase-data kdebase-plasma kdebase-runtime kdebase-runtime-bin-kde4 kdebase-runtime-data kdebase-runtime-data-common kdebase-workspace-bin kdebase-workspace-data kdebase-workspace-libs4+5 kdebluetooth kdegraphics-strigi-plugins kdelibs-bin kdelibs-data kdelibs4c2a kdelibs5 kdelibs5-data kdemultimedia-kio-plugins kdepasswd kdepim-kresources kdepim-strigi-plugins kdepim-wizards kdepimlibs-data kdepimlibs5 kdeplasma-addons kdeplasma-addons-data kdeplasma-addons-libs4 kdesudo kdm kfind kgrubeditor khelpcenter4 klipper kmag kmail kmix kmousetool knotes konqueror konqueror-nsplugins konqueror-plugin-searchbar konsole kontact konversation kopete korganizer krdc krfb ksnapshot ksysguard ksysguardd ksystemlog ktimetracker ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kuser kvkbd kwalletmanager language-selector-qt libakonadiprivate1 libarts1c2a libartsc0 libaudio2 libavahi-qt3-1 libcapseo0 libcaptury0 libclucene0ldbl libdbus-1-qt3 libdbus-qt-install ubuntu-desktop gdm                    sudo aptitude update exit
E: The update command takes no arguments     
paul@LinuxLaptop:~$ sudo apt-get update      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Translation-en_US       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Translation-en_US         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Translation-en_US       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release.gpg                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Translation-en_US     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Translation-en_US  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_US   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_US 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Sources                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Sources                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Sources                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Sources          
Reading package lists... Done                                                 
paul@LinuxLaptop:~$ clear                                                     
paul@LinuxLaptop:~$ sudo apt-get install ubuntu-desktop gdm
Reading package lists... Done                              
Building dependency tree                                   
Reading state information... Done                          
The following extra packages will be installed:            
  alacarte app-install-data-commercial apport-gtk at-spi binfmt-support
  bluez-gnome brasero brltty-x11 capplets-data cli-common compiz compiz-core
  compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome       
  compiz-plugins compizconfig-backend-gconf contact-lookup-applet dcraw     
  deskbar-applet desktop-file-utils dmz-cursor-theme doc-base ekiga eog     
  espeak espeak-data evince evolution evolution-common evolution-data-server
  evolution-data-server-common evolution-exchange evolution-plugins         
  evolution-webcal example-content f-spot fast-user-switch-applet           
  file-roller firefox firefox-3.0-gnome-support firefox-gnome-support       
  gcalctool gconf-editor gdebi gdm-guest-session gedit gedit-common         
  ggzcore-bin gimp gimp-data gnome-about gnome-accessibility-themes         
  gnome-applets gnome-applets-data gnome-cards-data gnome-control-center    
  gnome-desktop-data gnome-doc-utils gnome-games gnome-games-data gnome-mag 
  gnome-media gnome-media-common gnome-menus gnome-netstatus-applet         
  gnome-nettool gnome-orca gnome-panel gnome-panel-data gnome-pilot         
  gnome-pilot-conduits gnome-power-manager gnome-screensaver gnome-session  
  gnome-settings-daemon gnome-spell gnome-system-monitor gnome-system-tools 
  gnome-terminal gnome-terminal-data gnome-themes gnome-user-guide          
  gnome-utils gstreamer0.10-alsa gstreamer0.10-gnomevfs                     
  gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps                
  gstreamer0.10-plugins-good gstreamer0.10-pulseaudio                       
  gstreamer0.10-schroedinger gstreamer0.10-tools gstreamer0.10-x            
  gtk2-engines gtk2-engines-murrine gtk2-engines-pixbuf gucharmap           
  guile-1.8-libs gvfs gvfs-backends gvfs-bin gvfs-fuse human-icon-theme     
  human-theme hwtest hwtest-gtk jockey-gtk language-selector libart2.0-cil  
  libatspi1.0-0 libavahi-gobject0 libavahi-ui0 libbabl-0.0-0 libbeagle1     
  libcairomm-1.0-1 libcamel1.2-14 libcanberra-gnome libcanberra-gtk-module  
  libcanberra-gtk0 libcanberra0 libcdio-cdda0 libcdio-paranoia0             
  libcompizconfig0 libcryptui0 libdecoration0 libdeskbar-tracker libdmx1    
  libdv4 libebackend1.2-0 libebook1.2-9 libecal1.2-7 libedata-book1.2-2     
  libedata-cal1.2-6 libedataserver1.2-11 libedataserverui1.2-8 libeel2-2    
  libeel2-data libegroupwise1.2-13 libespeak1 libexchange-storage1.2-3      
  libexempi3 libflickrnet2.1.5-cil libfreezethaw-perl libgadu3              
  libgail-gnome-module libgconf2.0-cil libgdata-google1.2-1 libgdata1.2-1   
  libgdiplus libgegl-0.0-0 libggz2 libggzcore9 libggzmod4 libgimp2.0        
  libglade2.0-cil libglew1.5 libglib2.0-cil libglibmm-2.4-1c2a libglitz-glx1
  libglitz1 libgmime-2.0-2a libgmime2.2-cil libgnome-desktop-2-7            
  libgnome-keyring1.0-cil libgnome-mag2 libgnome-media0 libgnome-menu2      
  libgnome-pilot2 libgnome-speech7 libgnome-vfs2.0-cil                      
  libgnome-window-settings1 libgnome2.0-cil libgnomecups1.0-1               
  libgnomekbd-common libgnomekbd3 libgnomekbdui3 libgnomeprint2.2-0         
  libgnomeprint2.2-data libgnomeprintui2.2-0 libgnomeprintui2.2-common      
  libgnomevfs2-bin libgpod3 libgtk-vnc-1.0-0 libgtk2.0-cil libgtkglext1     
  libgtkhtml-editor-common libgtkhtml-editor0 libgtkhtml3.14-19             
  libgtkmm-2.4-1c2a libgtksourceview-common libgtksourceview1.0-0           
  libgtksourceview2.0-0 libgtksourceview2.0-common libgtkspell0             
  libgucharmap7 libgvfscommon0 libgweather-common libgweather1 libhesiod0   
  libiec61883-0 libjpeg-progs libkpathsea4 liblpint-bonobo0 libmbca0        
  libmeanwhile1 libmetacity0 libmldbm-perl libmono-addins-gui0.2-cil        
  libmono-addins0.2-cil libmono-cairo1.0-cil libmono-cairo2.0-cil           
  libmono-corlib1.0-cil libmono-corlib2.0-cil libmono-data-tds1.0-cil       
  libmono-data-tds2.0-cil libmono-i18n1.0-cil libmono-i18n2.0-cil           
  libmono-security1.0-cil libmono-security2.0-cil libmono-sharpzip0.84-cil  
  libmono-sharpzip2.84-cil libmono-sqlite2.0-cil libmono-system-data1.0-cil 
  libmono-system-data2.0-cil libmono-system-web1.0-cil                      
  libmono-system-web2.0-cil libmono-system1.0-cil libmono-system2.0-cil     
  libmono0 libmono1.0-cil libmono2.0-cil libnautilus-burn4                  
  libnautilus-extension1 libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil     
  libnet-dbus-perl liboobs-1-4 libopal-2.2 libopenobex1 libpanel-applet2-0  
  libpangomm-1.4-1 libpisock9 libpisync1 libpoppler-glib3 libportaudio0     
  libpt-1.10.10 libpt-1.10.10-plugins-alsa libpt-1.10.10-plugins-v4l        
  libpt-1.10.10-plugins-v4l2 libpulse-browse0 libpulsecore5 libpurple-bin   
  libpurple0 librarian0 libscim8c2a libsilc-1.1-2 libsndfile1 libsoup2.4-1  
  libspeexdsp1 libsqlite0 libtie-ixhash-perl libtotem-plparser12            
  libtracker-gtk0 libtrackerclient0 libuuid-perl libv4l-0 libwv-1.2-3       
  libx11-xcb1 libxevie1 libxml-twig-perl libxml-xpath-perl libxml2-utils    
  libzephyr3 metacity metacity-common mobile-broadband-provider-info        
  mono-common mono-gac mono-jit mono-runtime mousetweaks mtools nautilus    
  nautilus-cd-burner nautilus-data nautilus-sendto nautilus-share           
  network-manager-gnome obex-data-server onboard openoffice.org-gnome       
  openoffice.org-gtk pidgin pidgin-data pidgin-otr pkg-config pulseaudio    
  pulseaudio-esound-compat pulseaudio-module-gconf pulseaudio-module-hal    
  pulseaudio-module-x11 pulseaudio-utils python-beagle python-brlapi        
  python-gdata python-gmenu python-gnome2 python-gnome2-desktop             
  python-gnomecanvas python-gtksourceview2 python-notify                    
  python-pkg-resources python-pyatspi python-rdflib python-virtkey          
  rarian-compat rhythmbox rss-glx scim scim-bridge-agent                    
  scim-bridge-client-gtk scim-gtk2-immodule scim-modules-socket             
  screen-resolution-extra screensaver-default-images seahorse               
  seahorse-plugins sqlite sqlite3 ssh-askpass-gnome syslinux                
  system-config-printer-gnome system-tools-backends tangerine-icon-theme    
  tomboy totem totem-common totem-gstreamer totem-mozilla totem-plugins     
  tracker tracker-search-tool tracker-utils transmission-common             
  transmission-gtk tsclient ubuntu-artwork ubuntu-docs ubuntu-gdm-themes    
  ubuntu-sounds ubuntu-system-service ubuntu-wallpapers untex update-manager
  update-notifier usb-creator vinagre vino whois wv xbase-clients xbitmaps  
  xdg-user-dirs-gtk xsane xsane-common xscreensaver xscreensaver-data       
  xscreensaver-gl xsltproc xterm xulrunner-1.9-gnome-support yelp zenity    
Suggested packages:                                                         
  gstreamer0.10-fluendo-mp3 gstreamer0.10-plugins-bad vcdimager gphoto2     
  netpbm python-soappy siproxd gnugk mediaproxy ser openser rtpproxy        
  asterisk yate callweaver unrar bug-buddy evolution-dbg                    
  evolution-plugins-experimental evolution-data-server-dbg                  
  evolution-exchange-dbg xnest lha sharutils lzop rpm ncompress unace p7zip 
  p7zip-full arj uswsusp gdm-themes libgimp-perl gimp-data-extras xrdb      
  python-gtkglext1 python-opengl gnome-hearts gnome-games-extra-data        
  gnome2-user-guide menu-xdg desktop-base ntp gnome-themes-extras           
  monodoc-gtk2.0-manual libdv-bin glew-utils festival libgtkhtml3.14-dbg    
  libgda2-3 libmono-winforms2.0-cil libmono-winforms1.0-cil jpilot          
  pilot-link kpilot claws-mail sylpheed tcl8.4 tk8.4 libunicode-map8-perl   
  libunicode-string-perl xml-twig-tools floppyd thunderbird samba           
  openoffice.org-evolution pavumeter pavucontrol paman paprefs padevchooser 
  python-gnome2-desktop-doc python-gnome2-desktop-dbg python-gnomecanvas-dbg
  libgtksourceview2.0-dev python-setuptools gstreamer0.10-plugins-ugly      
  python-coherence scim-uim scim-pinyin scim-hangul scim-chewing scim-m17n  
  scim-prime scim-anthy scim-skk scim-canna scim-tables-additional          
  scim-tables-ja scim-tables-ko scim-tables-zh scim-thai sqlite-doc         
  sqlite3-doc tasque totem-plugins-extra gstreamer0.10-ffmpeg gromit        
  djvulibre-bin gnumeric vnc-viewer tetex-extra elinks links lynx xsane-doc 
  hylafax-client mgetty-fax gv gocr xli xloadimage xfishtank qcam streamer  
  xfonts-cyrillic                                                           
Recommended packages:                                                       
  python-gst                                                                
The following packages will be REMOVED:                                     
  libgpod3-nogtk scrollkeeper                                               
The following NEW packages will be installed:                               
  alacarte app-install-data-commercial apport-gtk at-spi binfmt-support     
  bluez-gnome brasero brltty-x11 capplets-data cli-common compiz compiz-core
  compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome       
  compiz-plugins compizconfig-backend-gconf contact-lookup-applet dcraw     
  deskbar-applet desktop-file-utils dmz-cursor-theme doc-base ekiga eog     
  espeak espeak-data evince evolution evolution-common evolution-data-server
  evolution-data-server-common evolution-exchange evolution-plugins         
  evolution-webcal example-content f-spot fast-user-switch-applet           
  file-roller firefox firefox-3.0-gnome-support firefox-gnome-support       
  gcalctool gconf-editor gdebi gdm gdm-guest-session gedit gedit-common     
  ggzcore-bin gimp gimp-data gnome-about gnome-accessibility-themes         
  gnome-applets gnome-applets-data gnome-cards-data gnome-control-center    
  gnome-desktop-data gnome-doc-utils gnome-games gnome-games-data gnome-mag 
  gnome-media gnome-media-common gnome-menus gnome-netstatus-applet         
  gnome-nettool gnome-orca gnome-panel gnome-panel-data gnome-pilot         
  gnome-pilot-conduits gnome-power-manager gnome-screensaver gnome-session  
  gnome-settings-daemon gnome-spell gnome-system-monitor gnome-system-tools 
  gnome-terminal gnome-terminal-data gnome-themes gnome-user-guide          
  gnome-utils gstreamer0.10-alsa gstreamer0.10-gnomevfs                     
  gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps                
  gstreamer0.10-plugins-good gstreamer0.10-pulseaudio                       
  gstreamer0.10-schroedinger gstreamer0.10-tools gstreamer0.10-x            
  gtk2-engines gtk2-engines-murrine gtk2-engines-pixbuf gucharmap           
  guile-1.8-libs gvfs gvfs-backends gvfs-bin gvfs-fuse human-icon-theme     
  human-theme hwtest hwtest-gtk jockey-gtk language-selector libart2.0-cil  
  libatspi1.0-0 libavahi-gobject0 libavahi-ui0 libbabl-0.0-0 libbeagle1     
  libcairomm-1.0-1 libcamel1.2-14 libcanberra-gnome libcanberra-gtk-module  
  libcanberra-gtk0 libcanberra0 libcdio-cdda0 libcdio-paranoia0             
  libcompizconfig0 libcryptui0 libdecoration0 libdeskbar-tracker libdmx1    
  libdv4 libebackend1.2-0 libebook1.2-9 libecal1.2-7 libedata-book1.2-2     
  libedata-cal1.2-6 libedataserver1.2-11 libedataserverui1.2-8 libeel2-2    
  libeel2-data libegroupwise1.2-13 libespeak1 libexchange-storage1.2-3      
  libexempi3 libflickrnet2.1.5-cil libfreezethaw-perl libgadu3              
  libgail-gnome-module libgconf2.0-cil libgdata-google1.2-1 libgdata1.2-1   
  libgdiplus libgegl-0.0-0 libggz2 libggzcore9 libggzmod4 libgimp2.0        
  libglade2.0-cil libglew1.5 libglib2.0-cil libglibmm-2.4-1c2a libglitz-glx1
  libglitz1 libgmime-2.0-2a libgmime2.2-cil libgnome-desktop-2-7            
  libgnome-keyring1.0-cil libgnome-mag2 libgnome-media0 libgnome-menu2      
  libgnome-pilot2 libgnome-speech7 libgnome-vfs2.0-cil                      
  libgnome-window-settings1 libgnome2.0-cil libgnomecups1.0-1               
  libgnomekbd-common libgnomekbd3 libgnomekbdui3 libgnomeprint2.2-0         
  libgnomeprint2.2-data libgnomeprintui2.2-0 libgnomeprintui2.2-common      
  libgnomevfs2-bin libgpod3 libgtk-vnc-1.0-0 libgtk2.0-cil libgtkglext1     
  libgtkhtml-editor-common libgtkhtml-editor0 libgtkhtml3.14-19             
  libgtkmm-2.4-1c2a libgtksourceview-common libgtksourceview1.0-0           
  libgtksourceview2.0-0 libgtksourceview2.0-common libgtkspell0             
  libgucharmap7 libgvfscommon0 libgweather-common libgweather1 libhesiod0   
  libiec61883-0 libjpeg-progs libkpathsea4 liblpint-bonobo0 libmbca0        
  libmeanwhile1 libmetacity0 libmldbm-perl libmono-addins-gui0.2-cil        
  libmono-addins0.2-cil libmono-cairo1.0-cil libmono-cairo2.0-cil           
  libmono-corlib1.0-cil libmono-corlib2.0-cil libmono-data-tds1.0-cil       
  libmono-data-tds2.0-cil libmono-i18n1.0-cil libmono-i18n2.0-cil           
  libmono-security1.0-cil libmono-security2.0-cil libmono-sharpzip0.84-cil  
  libmono-sharpzip2.84-cil libmono-sqlite2.0-cil libmono-system-data1.0-cil 
  libmono-system-data2.0-cil libmono-system-web1.0-cil                      
  libmono-system-web2.0-cil libmono-system1.0-cil libmono-system2.0-cil     
  libmono0 libmono1.0-cil libmono2.0-cil libnautilus-burn4                  
  libnautilus-extension1 libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil     
  libnet-dbus-perl liboobs-1-4 libopal-2.2 libopenobex1 libpanel-applet2-0  
  libpangomm-1.4-1 libpisock9 libpisync1 libpoppler-glib3 libportaudio0     
  libpt-1.10.10 libpt-1.10.10-plugins-alsa libpt-1.10.10-plugins-v4l        
  libpt-1.10.10-plugins-v4l2 libpulse-browse0 libpulsecore5 libpurple-bin   
  libpurple0 librarian0 libscim8c2a libsilc-1.1-2 libsndfile1 libsoup2.4-1  
  libspeexdsp1 libsqlite0 libtie-ixhash-perl libtotem-plparser12            
  libtracker-gtk0 libtrackerclient0 libuuid-perl libv4l-0 libwv-1.2-3       
  libx11-xcb1 libxevie1 libxml-twig-perl libxml-xpath-perl libxml2-utils    
  libzephyr3 metacity metacity-common mobile-broadband-provider-info        
  mono-common mono-gac mono-jit mono-runtime mousetweaks mtools nautilus    
  nautilus-cd-burner nautilus-data nautilus-sendto nautilus-share           
  network-manager-gnome obex-data-server onboard openoffice.org-gnome       
  openoffice.org-gtk pidgin pidgin-data pidgin-otr pkg-config pulseaudio    
  pulseaudio-esound-compat pulseaudio-module-gconf pulseaudio-module-hal    
  pulseaudio-module-x11 pulseaudio-utils python-beagle python-brlapi        
  python-gdata python-gmenu python-gnome2 python-gnome2-desktop             
  python-gnomecanvas python-gtksourceview2 python-notify
  python-pkg-resources python-pyatspi python-rdflib python-virtkey
  rarian-compat rhythmbox rss-glx scim scim-bridge-agent
  scim-bridge-client-gtk scim-gtk2-immodule scim-modules-socket
  screen-resolution-extra screensaver-default-images seahorse
  seahorse-plugins sqlite sqlite3 ssh-askpass-gnome syslinux
  system-config-printer-gnome system-tools-backends tangerine-icon-theme
  tomboy totem totem-common totem-gstreamer totem-mozilla totem-plugins
  tracker tracker-search-tool tracker-utils transmission-common
  transmission-gtk tsclient ubuntu-artwork ubuntu-desktop ubuntu-docs
  ubuntu-gdm-themes ubuntu-sounds ubuntu-system-service ubuntu-wallpapers
  untex update-manager update-notifier usb-creator vinagre vino whois wv
  xbase-clients xbitmaps xdg-user-dirs-gtk xsane xsane-common xscreensaver
  xscreensaver-data xscreensaver-gl xsltproc xterm
  xulrunner-1.9-gnome-support yelp zenity
0 upgraded, 375 newly installed, 2 to remove and 0 not upgraded.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory
paul@LinuxLaptop:~$


Reslts from using the link you sent me about removing KDE4:

paul@LinuxLaptop:~$ sudo apt-get remove adept akregator amarok amarok-common amarok-engine-xine apport-qt ark dolphin dragonplayer exiv2 foomatic-db-gutenprint gdebi-kde gnupg-agent gtk-qt-engine guidance-power-manager gwenview hpijs-ppds hplip-gui ijsgutenprint imagemagick install-package jockey-kde k3b k3b-data kaddressbook kamera kate kde-icons-oxygen kde-printer-applet kde-window-manager kde-zeroconf kdebase-bin kdebase-data kdebase-plasma kdebase-runtime kdebase-runtime-bin-kde4 kdebase-runtime-data kdebase-runtime-data-common kdebase-workspace-bin kdebase-workspace-data kdebase-workspace-libs4+5 kdebluetooth kdegraphics-strigi-plugins kdelibs-bin kdelibs-data kdelibs4c2a kdelibs5 kdelibs5-data kdemultimedia-kio-plugins kdepasswd kdepim-kresources kdepim-strigi-plugins kdepim-wizards kdepimlibs-data kdepimlibs5 kdeplasma-addons kdeplasma-addons-data kdeplasma-addons-libs4 kdesudo kdm kfind kgrubeditor khelpcenter4 klipper kmag kmail kmix kmousetool knotes konqueror konqueror-nsplugins konqueror-plugin-searchbar konsole kontact konversation kopete korganizer krdc krfb ksnapshot ksysguard ksysguardd ksystemlog ktimetracker ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kuser kvkbd kwalletmanager language-selector-qt libakonadiprivate1 libarts1c2a libartsc0 libaudio2 libavahi-qt3-1 libcapseo0 libcaptury0 libclucene0ldbl libdbus-1-qt3 libdbus-qt-1-1c2 libexiv2-4 libfftw3-3 libflac++6 libgeoip1 libifp4 libk3b3 libkcddb4 libkdecorations4 libkdepim4 libkholidays4 libkipi-common libkipi5 libkleo4 libkonq5 libkonq5-templates libkpgp4 libksieve4 libkwineffects1 liblua50 liblualib50 libmimelib4 libmodplug0c2 libmpcdec3 libmysqlclient15off libnjb5 libofa0 libokularcore1 libphonon4 libplasma2 libpoppler-qt4-3 libpq5 libqca2 libqca2-plugin-ossl libqimageblitz4 libqt3-mt libqt4-assistant libqt4-core libqt4-dbus libqt4-designer libqt4-help libqt4-network libqt4-opengl libqt4-qt3support libqt4-script libqt4-sql libqt4-sql-mysql libqt4-svg libqt4-test libqt4-webkit libqt4-xml libqt4-xmlpatterns libqtcore4 libqtgui4 libraptor1 librasqal0 librdf0 libruby1.8 libsearchclient0 libsoprano4 libstreamanalyzer0 libstreams0 libstrigihtmlgui0 libstrigiqtdbusclient0 libtunepimp5 libvncserver0 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxine1 libxine1-bin libxine1-console libxine1-misc-plugins libxine1-x libxvmc1 libzip1 mediamanager mysql-common network-manager-kde okular okular-extra-backends openoffice.org-kde openoffice.org-style-crystal oxygen-cursor-theme phonon phonon-backend-gstreamer phonon-backend-xine pinentry-gtk2 pinentry-qt4 plasmoid-quickaccess python-kde4 python-qt3 python-qt4 python-qt4-common python-qt4-dbus python-reportlab python-sip4 qt4-qtconfig raptor-utils redland-utils ruby ruby1.8 software-properties-kde soprano-daemon speedcrunch strigi-client strigi-daemon system-config-printer-kde systemsettings ttf-dustin update-manager-kde update-notifier-kde 
Reading package lists... Done                                                 
Building dependency tree                                                      
Reading state information... Done                                             
Package kubuntu-desktop is not installed, so not removed                      
Package phonon-backend-gstreamer is not installed, so not removed             
Package pinentry-gtk2 is not installed, so not removed                        
The following packages were automatically installed and are no longer required:                                                                             
  libswscale0 libtwolame0 libavutil49 liblircclient0 libdca0 libpostproc51    
  libass1 libavformat52 libdvbpsi4 libcdio7 libx264-59 libschroedinger-1.0-0  
  libvlc2 libenca0 libavc1394-0 libshout3 libgsm1 libdvdnav4 libiso9660-5     
  libdvdread3 libavcodec51 liblua5.1-0 libmad0 libid3tag0 vlc-data liboil0.3  
  libtar libvlccore0 libvcdinfo0 libebml0 libmatroska0 libmpeg2-4             
  libsdl-image1.2 libfaad0 liba52-0.7.4                                       
Use 'apt-get autoremove' to remove them.                                      
The following packages will be REMOVED:                                       
  adept akregator amarok amarok-common amarok-engine-xine apport-qt ark       
  dolphin dragonplayer exiv2 foomatic-db-gutenprint gdebi-kde gnupg-agent     
  gtk-qt-engine guidance-power-manager gwenview hpijs-ppds hplip-gui          
  ijsgutenprint imagemagick install-package jockey-kde k3b k3b-data           
  kaddressbook kamera kate kde-icons-oxygen kde-printer-applet                
  kde-window-manager kde-zeroconf kdebase-bin kdebase-data kdebase-plasma     
  kdebase-runtime kdebase-runtime-bin-kde4 kdebase-runtime-data               
  kdebase-runtime-data-common kdebase-workspace-bin kdebase-workspace-data    
  kdebase-workspace-libs4+5 kdebluetooth kdegraphics-strigi-plugins           
  kdelibs-bin kdelibs-data kdelibs4c2a kdelibs5 kdelibs5-data                 
  kdemultimedia-kio-plugins kdepasswd kdepim-kresources                       
  kdepim-strigi-plugins kdepim-wizards kdepimlibs-data kdepimlibs5            
  kdeplasma-addons kdeplasma-addons-data kdeplasma-addons-libs4 kdesudo kdm   
  kfind kgrubeditor khelpcenter4 klipper kmag kmail kmix kmousetool knotes    
  konqueror konqueror-nsplugins konqueror-plugin-searchbar konsole kontact    
  konversation kopete korganizer krdc krfb ksnapshot ksysguard ksysguardd     
  ksystemlog ktimetracker ktorrent kubuntu-artwork-usplash                    
  kubuntu-default-settings kubuntu-docs kubuntu-konqueror-shortcuts kuser     
  kvkbd kwalletmanager language-selector-qt libakonadiprivate1 libarts1c2a    
  libartsc0 libaudio2 libavahi-qt3-1 libcapseo0 libcaptury0 libclucene0ldbl   
  libdbus-1-qt3 libdbus-qt-1-1c2 libexiv2-4 libfftw3-3 libflac++6 libgeoip1   
  libifp4 libk3b3 libkcddb4 libkdecorations4 libkdepim4 libkholidays4         
  libkipi-common libkipi5 libkleo4 libkonq5 libkonq5-templates libkpgp4       
  libksieve4 libkwineffects1 liblua50 liblualib50 libmimelib4 libmodplug0c2   
  libmpcdec3 libmysqlclient15off libnjb5 libofa0 libokularcore1 libphonon4    
  libplasma2 libpoppler-qt4-3 libpq5 libqca2 libqca2-plugin-ossl              
  libqimageblitz4 libqt3-mt libqt4-assistant libqt4-core libqt4-dbus          
  libqt4-designer libqt4-help libqt4-network libqt4-opengl libqt4-qt3support  
  libqt4-script libqt4-sql libqt4-sql-mysql libqt4-svg libqt4-test
  libqt4-webkit libqt4-xml libqt4-xmlpatterns libqtcore4 libqtgui4
  libraptor1 librasqal0 librdf0 libruby1.8 libsearchclient0 libsoprano4
  libstreamanalyzer0 libstreams0 libstrigihtmlgui0 libstrigiqtdbusclient0
  libtunepimp5 libvncserver0 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxine1
  libxine1-bin libxine1-console libxine1-misc-plugins libxine1-x libxvmc1
  libzip1 mediamanager mozilla-plugin-vlc mysql-common network-manager-kde
  okular okular-extra-backends openoffice.org-kde
  openoffice.org-style-crystal oxygen-cursor-theme phonon
  phonon-backend-xine pinentry-qt4 plasmoid-quickaccess python-kde4
  python-qt3 python-qt4 python-qt4-common python-qt4-dbus python-reportlab
  python-sip4 qt4-qtconfig raptor-utils redland-utils ruby ruby1.8
  software-properties-kde soprano-daemon speedcrunch strigi-client
  strigi-daemon system-config-printer-kde systemsettings ttf-dustin
  update-manager-kde update-notifier-kde vlc vlc-nox xorg
0 upgraded, 0 newly installed, 216 to remove and 0 not upgraded.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory
paul@LinuxLaptop:~$

---

### Post by s1mp13m4n on 2009-02-06
This is what happened when I ran Synaptic Package Manager and tried to instal Gnome:

eeerrr the error message did not copy and paste, it was the same message as the others about E not unlocking and such

---

### Post by taurus on 2009-02-06
You cannot run synaptic at the same time as **sudo apt-get** from a terminal.  If you want to use the terminal to install it, close down synaptic first.

---

### Post by s1mp13m4n on 2009-02-06
I did, I ran the first set of commands in terminal, shut it down and then ran synaptic.  They were both ran seperately. :)

---

### Post by taurus on 2009-02-06
What happens when you try to install the ubuntu-desktop package?

```
sudo apt-get install ubuntu-desktop
```

---

### Post by 123Mike on 2009-02-06
If you're looking for something light and snappy, consider starting from scratch and use Xubuntu. It uses the XFCE window manager. It's lighter, faster, and I think it's better configurable than Gnome.

---

### Post by s1mp13m4n on 2009-02-06
This is what I get when I run the above command in a terminal.  


Only one display manager can manage a given X server, but multiple      &#9618;
 &#9474; display manager packages are installed. Please select which display     &#9618;
 &#9474; manager should run by default.                                          &#9618;
 &#9474;                                                                         &#9618;
 &#9474; Multiple display managers can run simultaneously if they are            &#9618;
 &#9474; configured to manage different servers; to achieve this, configure the  &#9618;
 &#9474; display managers accordingly, edit each of their init scripts in        &#9646;
 &#9474; /etc/init.d, and disable the check for a default display manager.

---

### Post by mb_webguy on 2009-02-06
At the login screen, click Options, and then Select Session.  There should be something there about Gnome.  Select that, and you should log in using Gnome.

---

### Post by s1mp13m4n on 2009-02-06
Only KDE shows up when you look into that.  Here is what I did since it was a new fresh install and I had nothing to lose, I started over and instaled Ubuntu 8.10.  I seem to like Gnome better than KDE.  To me it is cleaner, easier to figure out for a newbie, and less frills.  I will be back asking more questions as I keep learning but for now a new install of Ubuntu was my ticket.  Thanks for the help.

---

