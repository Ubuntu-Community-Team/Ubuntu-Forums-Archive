---
title: "KDE 4.2 upgrade"
date: 2009-02-23
forum: General Help
---

### Post by ashwinhgtx on 2009-02-23
I tried to upgrade to KDE 4.2 according to the instructions posted here.
[http://www.kubuntu.org/news/kde-4.2](http://www.kubuntu.org/news/kde-4.2)

I'm on Kubuntu 8.10 using KDE 4.1.4

I have edited and updated the sources and when I do sudo apt-get upgrade, all the kde updates are listed out. But then it says that no update can be performed as the listed kde updates have been 'kept back'.

I have all the checkboxes ticked for recommended updates, backport updates, unsupported updates etc. but still i"m getting this error.
I don't want to force an upgrade and break my system.
Can anyone help me out?
Thanks in advance.

---

### Post by xeth_delta on 2009-02-23
I upgraded last week. Hope I can help. Did you also remember to run
```
sudo apt-get update
```
before the upgrade?

---

### Post by ashwinhgtx on 2009-02-23
Yes i did run sudo apt-get update. That's why the kde updates are being listed out to me right?

---

### Post by xeth_delta on 2009-02-23
> **ashwinhgtx said:**
> Yes i did run sudo apt-get update. That's why the kde updates are being listed out to me right?

The fact that some packages are being kept back does not necessarily mean that the upgrades would not be done. When you issue "apt-get update", does it tell you how many packages will be updated? Can you please post that output?

---

### Post by ashwinhgtx on 2009-02-23
Here's the output you had asked for. 
```
sudo apt-get update
[sudo] password for ashwin:              
Get:1 http://archive.canonical.com intrepid Release.gpg [189B]                  
Get:2 http://in.archive.ubuntu.com intrepid Release.gpg [189B]                  
Ign http://ppa.launchpad.net intrepid Release.gpg                               
Ign http://archive.canonical.com intrepid/partner Translation-en_IN             
Get:3 http://security.ubuntu.com intrepid-security Release.gpg [189B]           
Ign http://in.archive.ubuntu.com intrepid/main Translation-en_IN                
Ign http://ppa.launchpad.net intrepid/main Translation-en_IN                    
Ign http://security.ubuntu.com intrepid-security/restricted Translation-en_IN   
Hit http://archive.canonical.com intrepid Release                               
Get:4 http://ppa.launchpad.net intrepid Release.gpg [307B]                      
Ign http://security.ubuntu.com intrepid-security/main Translation-en_IN         
Ign http://ppa.launchpad.net intrepid/main Translation-en_IN                    
Ign http://in.archive.ubuntu.com intrepid/restricted Translation-en_IN          
Hit http://archive.canonical.com intrepid/partner Packages                      
Ign http://security.ubuntu.com intrepid-security/multiverse Translation-en_IN   
Get:5 http://ppa.launchpad.net intrepid Release [27.6kB]                        
Ign http://in.archive.ubuntu.com intrepid/universe Translation-en_IN            
Get:6 http://packages.medibuntu.org intrepid Release.gpg [197B]                 
Ign http://security.ubuntu.com intrepid-security/universe Translation-en_IN     
Ign http://in.archive.ubuntu.com intrepid/multiverse Translation-en_IN          
Ign http://packages.medibuntu.org intrepid/free Translation-en_IN               
Get:7 http://ppa.launchpad.net intrepid Release [27.6kB]                        
Ign http://packages.medibuntu.org intrepid/non-free Translation-en_IN           
Hit http://security.ubuntu.com intrepid-security Release                        
Get:8 http://repository.akirad.net akirad-intrepid Release.gpg [197B]           
Ign http://repository.akirad.net akirad-intrepid/main Translation-en_IN         
Get:9 http://packages.medibuntu.org intrepid Release [11.7kB]                   
Get:10 http://in.archive.ubuntu.com intrepid-backports Release.gpg [189B]       
Ign http://packages.medibuntu.org intrepid Release                              
Hit http://repository.akirad.net akirad-intrepid Release                        
Hit http://packages.medibuntu.org intrepid/free Packages                        
Ign http://in.archive.ubuntu.com intrepid-backports/restricted Translation-en_IN
Hit http://repository.akirad.net akirad-intrepid/main Packages                  
Get:11 http://packages.medibuntu.org intrepid/non-free Packages [12.6kB]        
Ign http://in.archive.ubuntu.com intrepid-backports/main Translation-en_IN      
Ign http://in.archive.ubuntu.com intrepid-backports/multiverse Translation-en_IN
Ign http://ppa.launchpad.net intrepid/main Packages                             
Ign http://in.archive.ubuntu.com intrepid-backports/universe Translation-en_IN  
Ign http://ppa.launchpad.net intrepid/main Packages                             
Get:12 http://in.archive.ubuntu.com intrepid-proposed Release.gpg [189B]        
Hit http://ppa.launchpad.net intrepid/main Packages                             
Ign http://in.archive.ubuntu.com intrepid-proposed/restricted Translation-en_IN 
Ign http://in.archive.ubuntu.com intrepid-proposed/main Translation-en_IN       
Get:13 http://ppa.launchpad.net intrepid/main Packages [71.9kB]                 
Ign http://in.archive.ubuntu.com intrepid-proposed/multiverse Translation-en_IN 
Ign http://in.archive.ubuntu.com intrepid-proposed/universe Translation-en_IN   
Get:14 http://in.archive.ubuntu.com intrepid-updates Release.gpg [189B]         
Ign http://in.archive.ubuntu.com intrepid-updates/restricted Translation-en_IN  
Ign http://in.archive.ubuntu.com intrepid-updates/main Translation-en_IN        
Ign http://in.archive.ubuntu.com intrepid-updates/multiverse Translation-en_IN  
Ign http://in.archive.ubuntu.com intrepid-updates/universe Translation-en_IN    
Hit http://in.archive.ubuntu.com intrepid Release                               
Hit http://security.ubuntu.com intrepid-security/restricted Packages            
Hit http://security.ubuntu.com intrepid-security/main Packages                  
Hit http://security.ubuntu.com intrepid-security/multiverse Packages            
Hit http://security.ubuntu.com intrepid-security/universe Packages              
Get:15 http://in.archive.ubuntu.com intrepid-backports Release [44.0kB]         
Hit http://in.archive.ubuntu.com intrepid-proposed Release                      
Hit http://in.archive.ubuntu.com intrepid-updates Release                       
Hit http://in.archive.ubuntu.com intrepid/main Packages                         
Hit http://in.archive.ubuntu.com intrepid/restricted Packages                   
Hit http://in.archive.ubuntu.com intrepid/main Sources                          
Hit http://in.archive.ubuntu.com intrepid/restricted Sources                    
Hit http://in.archive.ubuntu.com intrepid/universe Packages                     
Hit http://in.archive.ubuntu.com intrepid/universe Sources                      
Hit http://in.archive.ubuntu.com intrepid/multiverse Packages                   
Hit http://in.archive.ubuntu.com intrepid/multiverse Sources                    
Get:16 http://in.archive.ubuntu.com intrepid-backports/restricted Packages [14B]
Get:17 http://in.archive.ubuntu.com intrepid-backports/main Packages [80.0kB]   
Get:18 http://in.archive.ubuntu.com intrepid-backports/multiverse Packages [14B]
Get:19 http://in.archive.ubuntu.com intrepid-backports/universe Packages [32.2kB]
Hit http://in.archive.ubuntu.com intrepid-proposed/restricted Packages           
Hit http://in.archive.ubuntu.com intrepid-proposed/main Packages                 
Hit http://in.archive.ubuntu.com intrepid-proposed/multiverse Packages           
Hit http://in.archive.ubuntu.com intrepid-proposed/universe Packages             
Hit http://in.archive.ubuntu.com intrepid-updates/restricted Packages            
Hit http://in.archive.ubuntu.com intrepid-updates/main Packages                  
Hit http://in.archive.ubuntu.com intrepid-updates/multiverse Packages            
Hit http://in.archive.ubuntu.com intrepid-updates/universe Packages              
Fetched 270kB in 9min51s (457B/s)                                                
Reading package lists... Done                                                    
W: GPG error: http://packages.medibuntu.org intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783                                                                    
W: You may want to run apt-get update to correct these problems  
```


```
sudo apt-get upgrade                                       
Reading package lists... Done                                                    
Building dependency tree                                                         
Reading state information... Done                                                
The following packages have been kept back:                                      
  akregator amor ark blinken bovo dolphin dragonplayer gwenview kaddressbook
  kalzium kamera kanagram kate katomic kbattleship kblackbox kblocks kbounce
  kbreakout kde-window-manager kde-zeroconf kdebase-bin kdebase-data
  kdebase-plasma kdebase-runtime kdebase-runtime-bin-kde4 kdebase-workspace-bin
  kdebase-workspace-data kdebase-workspace-libs4+5 kdebluetooth kdegames
  kdegraphics-strigi-plugins kdelibs-bin kdelibs5 kdemultimedia-kio-plugins
  kdepasswd kdepim-kresources kdepim-strigi-plugins kdepim-wizards kdepimlibs5
  kdeplasma-addons kdeplasma-addons-data kdiamond kdm kfind kfourinline
  kgoldrunner khangman khelpcenter4 kinfocenter kiriki kjumpingcube klines
  klipper kmag kmahjongg kmail kmines kmix kmousetool knetwalk knotes kolf
  kollision konqueror konqueror-nsplugins konquest konsole kontact kopete
  korganizer kpat krdc kreversi krfb ksame kshisen ksirk ksnapshot kspaceduel
  ksquares kstars ksudoku ksysguard ksystemlog kteatime ktimetracker ktouch
  ktuberling kturtle kubrick kuser kwalletmanager libakonadiprivate1 libkcddb4
  libkdecorations4 libkdeedu4 libkdegames4 libkdepim4 libkholidays4 libkleo4
  libkonq5 libkpgp4 libksieve4 libkwineffects1 libmarble4 libmimelib4
  libokularcore1 linux-generic linux-headers-generic linux-image-generic
  linux-restricted-modules-generic lskat marble okular okular-extra-backends
  parley plasmoid-quickaccess python-kde4 systemsettings
0 upgraded, 0 newly installed, 0 to remove and 120 not upgraded.
```

---

### Post by ashwinhgtx on 2009-02-23
The gpg key error in the end of the output after sudo apt-get update has been there for a really long time but has never caused any problems. All the medibuntu packages like codecs and stuff have been installed and configured properly. I would be grateful if anyone can help me sort out this error also. Not that it is causing any problems but just like that. ;)

---

### Post by abn91c on 2009-02-23
> **ashwinhgtx said:**
> The gpg key error in the end of the output after sudo apt-get update has been there for a really long time but has never caused any problems. All the medibuntu packages like codecs and stuff have been installed and configured properly. I would be grateful if anyone can help me sort out this error also. Not that it is causing any problems but just like that. ;)
remove the medibuntu repo and try again

---

### Post by xeth_delta on 2009-02-23
Strange. It is indeed not upgrading, and I believe, as a consequence of this, keeping the old packages.

Try the following commands:
```
sudo apt-get -f install
```
```
sudo dpkg --configure -a
```

Then again "apt-get upgrade".
Not direclty related to what you are trying to solve, but I had some problems when upgrading with two packages needing to replace a couple of old config files. A --force flag for dpkg solved this and the rest installed properly. You might encounter this error too, a tad later.

---

### Post by ashwinhgtx on 2009-02-23
> **xeth_delta said:**
> Strange. It is indeed not upgrading, and I believe, as a consequence of this, keeping the old packages.

Try the following commands:
```
sudo apt-get -f install
```
```
sudo dpkg --configure -a
```

Then again "apt-get upgrade".
Not direclty related to what you are trying to solve, but I had some problems when upgrading with two packages needing to replace a couple of old config files. A --force flag for dpkg solved this and the rest installed properly. You might encounter this error too, a tad later.

What's the argument I have to give for sudo apt-get -f install?

---

### Post by xeth_delta on 2009-02-23
> **ashwinhgtx said:**
> What's the argument I have to give for sudo apt-get -f install?

That's all. No extra argument needed. If I am not mistaken, the -f flag in this case will finish any pending installations.

---

### Post by ashwinhgtx on 2009-02-23
> **xeth_delta said:**
> That's all. No extra argument needed. If I am not mistaken, the -f flag in this case will finish any pending installations.

Will it break anything?

---

### Post by ashwinhgtx on 2009-02-23
This is what i get after doing -f install
```
 sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libcommons-collections3-java libstlport4.6ldbl scorched3d-data lp-solve
  libxpp3-java libbackport-util-concurrent-java libxom-java
  liblog4j1.2-java-gcj libjaxme-java libregexp-java libsmokeqt1
  liblog4j1.2-java libjdom1-java liblucene2-java libsuitesparse-3.1.0
  libcommons-logging-java uno-libs3 libcommons-codec-java libxpp2-java
  libsaxonb-java libswfdec-0.8-0 libcommons-beanutils-java libdb-je-java ure
  libqt0-ruby1.8 libcommons-digester-java libdb4.5-java-gcj libdb4.5-java
  libjtidy-java libservlet2.3-java libdom4j-java libjaxen-java
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 120 not upgraded.

```

---

### Post by ashwinhgtx on 2009-02-23
And for dpkg --configure -a
```
ashwin@TWINTURBOV8:~$ sudo dpkg --configure -a
ashwin@TWINTURBOV8:~$

```

Well?

---

### Post by ikisham on 2009-02-23
For the gpg key issue you must run this:

gpg --keyserver keyserver.ubuntu.com --recv-keys 493B3065 && gpg --export -a 493B3065 | sudo apt-key add -

as stated in that first link you posted.

---

### Post by ashwinhgtx on 2009-02-23
> **abn91c said:**
> remove the medibuntu repo and try again

Ya I did that. I don't get the gpg key error anymore. Thanks a lot.:D

---

### Post by ashwinhgtx on 2009-02-23
> **ikisham said:**
> For the gpg key issue you must run this:

gpg --keyserver keyserver.ubuntu.com --recv-keys 493B3065 && gpg --export -a 493B3065 | sudo apt-key add -

as stated in that first link you posted.

That gpg error was due to the medibuntu repository. It's fixed now. I did add the gpg key given here
[http://www.kubuntu.org/news/kde-4.2il](http://www.kubuntu.org/news/kde-4.2il)

That's why the updates are getting listed. But I am not able to upgrade. What is keeping me back from these upgrades? Is apt trying stopping me cos the upgrade might break my system?

---

### Post by ikisham on 2009-02-23
This is what I can tell you since I'm a noob too: when I had ubuntu 8.10 installed I also installed the kde package to have a try. By then it was 4.1.3 and much tweaking didn't work so to upgrade to 4.2 version all I did was enable 'Intrepid proposed' updates under Software Sources. Then it was automatically updated. I don't even remember if it was made under Gnome or under Kde. But it was just that.

---

### Post by ashwinhgtx on 2009-02-24
Even though I did check all the checkboxes under the software updates(like recommended updates, backports, unsupported updates etc.) tab through adept I think the changes are not taking place. That's because a similar problem had occurred on my machine 2 months back. I edited out a repository graphically through the software sources tab but something went wrong and adept failed to start. I tried reverting the changes through the GUI but the changes were not taking place. Finally some kind people on the forums taught me how to do it through the command line. And it worked like a charm. Here's the link if you are interested.
[http://ubuntuforums.org/showthread.php?t=1007305](http://ubuntuforums.org/showthread.php?t=1007305)

Is it possible that even though I am ticking the checkboxes graphically but the changes are not actually taking place? Can anyone tell me how to effectively implement those checkbox ticks through the terminal??

---

### Post by xeth_delta on 2009-02-24
> **ashwinhgtx said:**
> Even though I did check all the checkboxes under the software updates(like recommended updates, backports, unsupported updates etc.) tab through adept I think the changes are not taking place. That's because a similar problem had occurred on my machine 2 months back. I edited out a repository graphically through the software sources tab but something went wrong and adept failed to start. I tried reverting the changes through the GUI but the changes were not taking place. Finally some kind people on the forums taught me how to do it through the command line. And it worked like a charm. Here's the link if you are interested.
[http://ubuntuforums.org/showthread.php?t=1007305](http://ubuntuforums.org/showthread.php?t=1007305)

Is it possible that even though I am ticking the checkboxes graphically but the changes are not actually taking place? Can anyone tell me how to effectively implement those checkbox ticks through the terminal??

First make sure you backup the repository file:
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list-bkp
```
Then edit the file directly:
```
kdesudo kate /etc/apt/sources.list
```
I am sorry I cannot help you more right now. I fell sick with what seems to be a quite strong flu.

---

### Post by ashwinhgtx on 2009-02-24
I'm running KDE 4.2!!
The updates worked through Synaptic even though Adept and apt-get didn't let me do the updates.

Lots of widgets are broken and Wine applications cause screen blackouts plus I get some Akonadi server error during login but I just don't care! I'm on KDE 4.2!!!

I have no idea what went wrong with the package management and I'm pretty sure that the next time I update, lots of things are going to get screwed but I'm happy now. I've been trying for so many days to get 4.2.

Life is like a box of chocolates, you never know what you are gonna get. 

Thanks everyone for your time. You guys rock!!! :guitar:

---

### Post by xeth_delta on 2009-02-25
> **ashwinhgtx said:**
> I'm running KDE 4.2!!
The updates worked through Synaptic even though Adept and apt-get didn't let me do the updates.

Lots of widgets are broken and Wine applications cause screen blackouts plus I get some Akonadi server error during login but I just don't care! I'm on KDE 4.2!!!

I have no idea what went wrong with the package management and I'm pretty sure that the next time I update, lots of things are going to get screwed but I'm happy now. I've been trying for so many days to get 4.2.

Life is like a box of chocolates, you never know what you are gonna get. 

Thanks everyone for your time. You guys rock!!! :guitar:

About the plasma widgets/plasmoids, did you remove tho old ones before installing KDE 4.2? I read on the install page that the old versions are incompatible (and hence broken after the upgrade). I wonder if this was what was stopping apt-get from upgrading. Anyway, I think that if you reinstall the plasmoids, they will work again. They work on my machine.
Enjoy KDE 4.2!

---

### Post by Frankaz on 2009-02-26
Had this same problem myself, so I installed Synaptic, went to Settings > Repositories > Updates > Ticked all (important, recommended, proposed & unsupported).

Then pressed the reload button, then pressed mark all upgrades. It picked up all packages for 4.2 and then I applied the changes.

---

