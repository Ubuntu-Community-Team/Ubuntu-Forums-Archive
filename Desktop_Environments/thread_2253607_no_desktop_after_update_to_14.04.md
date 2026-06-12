---
title: "no desktop after update to 14.04"
date: 2014-11-21
forum: Desktop Environments
---

### Post by ottosykora on 2014-11-21
So finally I tried to update one of my computers running 12.04 LTS to 14.04 LTS

I was using classic desktop with radiance theme.

Update ended in disaster.
Computer can be started, but as there are no menus , no controls at all on the desktop, no symbols or icons, I am not even able to switch the computer down.

All I did was running the system update. I have waited until now with the update so I am not getting the usual bugs at begining.


But now my computer is useless.
As I have 5 other computers running 12.04 LTS with classic desktop, I would like to know what to do as next?

---

### Post by carl4926 on 2014-11-21
In similar situations I have found it necessary to use a Parted Magic CD or USB live session to delete the /home/username hidden config files/folders. In such a way that all you look and feel would revert to 14.04 default. Effectively, you make it so that when you boot the system it's like a clean install.
Except you leave all your personal files and likes of apps (firefox, chrome/chromium etc...)

If you can live with that, try it.

[https://dl.dropboxusercontent.com/u/10573557/pmagic_2013_08_01.iso](https://dl.dropboxusercontent.com/u/10573557/pmagic_2013_08_01.iso)

---

### Post by carl4926 on 2014-11-21
> **carl4926 said:**
> In similar situations I have found it necessary to use a Parted Magic CD or USB live session to delete the /home/username hidden config files/folders. In such a way that all you look and feel would revert to 14.04 default. Effectively, you make it so that when you boot the system it's like a clean install.
Except you leave all your personal files and likes of apps (firefox, chrome/chromium etc...)

If you can live with that, try it.

[https://dl.dropboxusercontent.com/u/10573557/pmagic_2013_08_01.iso](https://dl.dropboxusercontent.com/u/10573557/pmagic_2013_08_01.iso)


Of course you will want to investigate that your upgrade proceeded without issue/error. You didn't mention any problems during the process....

---

### Post by ottosykora on 2014-11-21
So there is no way to return to classic desktop at all? My desktop is completely lost?

The only way now I have to switch off the computer is to press the power button long time...

I have pmagic myself, so I will find the way there.
In fact I thought the desktop will also be updated but it seems that it is kind of deleted only so nothing is left of it.


Problems during update?
Well did not notice anything special, have just left the update do what it wants. It did ask me few time if some config files should be preserved, I let it preserve them just to make sure, but otherwise it did the update and the desktop was present until the reboot.

From there on there is just colorful surface and simply nothing else present. 
I tried to press some keys, but no functionality at all.

---

### Post by carl4926 on 2014-11-21
I guess you have auto login enabled?
FYI: It's wise to disable this
In which case you login as a guest

Maybe hang fire until someone could direct you how to boot to runlevel3
You will need to be hardwired
And once there you can possibly check the upgrade went OK

Another option is to chroot the system
But you will need a bootable DVD / USB of 14.04 to do that
This effectively uses the live media to run your root OS

---

### Post by deadflowr on 2014-11-21
You are able to login, right?
Are there other sessions in the login screen to choose from?

Also can you switch from the gui to a console with ctrl + alt + F1(or 2--6)?

---

### Post by ottosykora on 2014-11-21
Yes , after I restart the computer by brute force (pressing the power button for long time simply) I can log in to something looking like the standard unity. There is no way to make any changes there, not even to change the desktop color, but it has at least an OFF button.

Have tested other choices, GNOME, and two others there, but all result in empty desktop surface which can not be changed at all, has no controls, no menus or panels etc.

When in the unity, I seem to be able to select ambiance, radiance ....

---

### Post by ottosykora on 2014-11-21
To me it looks like a complete reinstall is needed.
However I need to install the classic desktop.

There used to be some kind of 'sticky' threads with instruction how to install the classic desktop here, but I could not find it so far.

Is there at least a way to use something like xface instead?

---

### Post by deadflowr on 2014-11-21
Sure you can install xfce4, or try reinstalling the gnome-fallback/flashback desktop(s)

(Gnome Classic, now refers to a session which is built upon extensions of the current gnome-shell(new gnome). So it is best to use the flashback, or fallback terms to refer to the older desktops(the ones that use compiz and metacity))

Also, I don't remember it being a sticky, but here's kansasnoob's trusty flashback thread
[http://ubuntuforums.org/showthread.php?t=2220264&highlight=trusty+tweaks](http://ubuntuforums.org/showthread.php?t=2220264&highlight=trusty+tweaks)

---

### Post by ottosykora on 2014-11-21
> **deadflowr said:**
> S
(Gnome Classic, now refers to a session which is built upon extensions of the current gnome-shell(new gnome). So it is best to use the flashback, or fallback terms to refer to the older desktops(the ones that use compiz and metacity))



in the login menu have choise of flashback/fallback -compiz and metacity in the login menu 

However both of them end in an empty desktop with no control components at all. No panels, no buttons, no menus.

I can log into unity OK, it seems that unity works somehow half only. On other computers where I have 12.04, There are not many, but still functioning settings.

On the 14.04 the settings exist too, but there is no way to make any changes. Not even the color of the desktop can be changed. What ever is set, it has absolutely no effect at all.

---

### Post by ottosykora on 2014-11-21
Do I have a chance to at least install Xubuntu over the now useless Ubuntu?
If so what package to install?

---

### Post by ottosykora on 2014-11-28
OK, tried to reinstall flashback, tried to reinstall gnome-panel, components of metacity...
Still no luck. Simply no panals or anything else on desktop. Just Desktop surface.

What to try as next? How to install some kind of panel on the flashback just at least to be able to switch the computer off or find some programs or what ever. 

Any advise?

---

### Post by carl4926 on 2014-11-28
> **ottosykora said:**
> OK, tried to reinstall flashback, tried to reinstall gnome-panel, components of metacity...
Still no luck. Simply no panals or anything else on desktop. Just Desktop surface.

What to try as next? How to install some kind of panel on the flashback just at least to be able to switch the computer off or find some programs or what ever. 

Any advise?

Are you saying you were chroot to the installed system?

---

### Post by ottosykora on 2014-11-30
> **carl4926 said:**
> Are you saying you were chroot to the installed system?

well I tried different things. First ctrl+alt+1 and came to terminal. Tried to install gnome-panel from there, but it said it is already there.
Tired some of the next command lines from Kansasnoob instruction, but was told this needs the gui to be running.

Then logged into unitiy, get to synaptic from there and reinstalled flashback and panel and metacity etc. This all went OK, thought it was all marked as already installed.
But when returning to flashback/metacity (or flashback compiz which behaves same in this case) I found just an empty kind of surface which might be the desktop or not. No panels, no icons no controls etc.

Is there any way to install this flashback and the panel to it so it will show up?

---

### Post by kansasnoob on 2014-11-30
If the Unity DE is usable you could try these commands in case there is some packaging issue due to the upgrade:

```
sudo apt-get update
```

```
sudo apt-get -f install
```

```
sudo dpkg --configure -a
```

Sometimes the output of those commands can help us know what to do next.

If that gives us no further clues we can try renaming some of the existing "hidden dots" in /home followed by a reboot- like;

```
mv .config .config_OLD
```

```
mv .gconf .gconf_OLD
```

```
mv .gnome2 .gnome2_OLD
```

```
mv .local .local_OLD
```

```
mv .cache .cache_OLD
```

```
mv .profile .profile_OLD
```

Or possibly (also followed by a reboot):

```
dconf reset -f /org/gnome/desktop/
```

```
dconf reset -f /org/gnome/gnome-panel/
```

Sort of just grabbing at straws on my end so let us know what happens.

---

### Post by ottosykora on 2014-12-01
OK, kansasnoob, I will try all that and will report here.
The unity is still here and works I suppose as designed. There is also gnome in the login menu, this seems to work somehow too, but is pain too and seems not to be configurable.
The entries flashback/metacity and flashback/compiz have both the effect that only kind of empty surface is presented.
So if I want do some installs I have to go to the unity or gnome3. Looking in Synaptic GUI, all needed items seem to be installed. I assume that some config is stopping the panel from showing up.

The reset of panel I tried, it has no effect, nothing seems to happen.

---

### Post by ottosykora on 2014-12-04
```
root@laptopottos4:/home/otto# dconf reset -f /org/gnome/desktop/
root@laptopottos4:/home/otto# dconf reset -f /org/gnome/gnome-panel/
root@laptopottos4:/home/otto# 

```


ok, so tested the reset, from root terminal from unity

it has no effect at all, as seen nothing even happens

---

### Post by ottosykora on 2014-12-04
Ok, kansasnoob, here the output during the apt-get update and install etc.
There are some ppa which need to be updated or changed and some keys replaced, but they are from ppa which is not from ubuntu, this is some 3rd party things.

```
root@laptopottos4:/home/otto# dconf reset -f /org/gnome/desktop/
root@laptopottos4:/home/otto# dconf reset -f /org/gnome/gnome-panel/
root@laptopottos4:/home/otto# 
root@laptopottos4:/home/otto# 
root@laptopottos4:/home/otto# sudo apt-get update
Ign http://update.swisssign.com trusty InRelease
Ign http://ppa.launchpad.net karmic InRelease                                  
Ign http://archive.canonical.com trusty InRelease                              
Ign http://extras.ubuntu.com trusty InRelease                                  
Holen: 1 http://update.swisssign.com trusty Release.gpg [181 B]                
Ign http://ppa.launchpad.net oneiric InRelease                                 
Holen: 2 http://archive.canonical.com trusty Release.gpg [933 B]               
OK   http://extras.ubuntu.com trusty Release.gpg                               
Holen: 3 http://update.swisssign.com trusty Release [20.0 kB]                  
OK   http://repo.wuala.com stable InRelease                                    
Holen: 4 http://archive.canonical.com trusty Release [9'359 B]                 
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://ppa.launchpad.net karmic Release.gpg                                
OK   http://extras.ubuntu.com trusty Release                                   
OK   http://ppa.launchpad.net oneiric Release.gpg                              
OK   http://ppa.launchpad.net trusty Release.gpg                               
Ign http://archive.ubuntu.com trusty InRelease                                 
Ign http://ppa.launchpad.net karmic Release                                    
OK   http://ppa.launchpad.net oneiric Release                                  
OK   http://ppa.launchpad.net trusty Release                                   
Ign http://archive.ubuntu.com trusty-updates InRelease                         
Ign http://archive.ubuntu.com trusty-security InRelease                        
OK   http://archive.ubuntu.com trusty Release.gpg                              
Holen: 5 http://update.swisssign.com trusty/free i386 Packages [3'447 B]       
Holen: 6 http://archive.canonical.com trusty/partner Sources [7'939 B]         
OK   http://extras.ubuntu.com trusty/main i386 Packages                        
OK   http://repo.wuala.com stable/main i386 Packages                           
Holen: 7 http://archive.ubuntu.com trusty-updates Release.gpg [933 B]          
Holen: 8 http://update.swisssign.com trusty/non-free i386 Packages [2'851 B]   
Holen: 9 http://archive.canonical.com trusty/partner i386 Packages [5'559 B]   
Holen: 10 http://archive.ubuntu.com trusty-security Release.gpg [933 B]        
Ign http://archive.canonical.com trusty/partner Translation-en                 
OK   http://ppa.launchpad.net oneiric/main Sources                             
OK   http://ppa.launchpad.net oneiric/main i386 Packages                       
OK   http://archive.ubuntu.com trusty Release                                  
Holen: 11 http://archive.ubuntu.com trusty-updates Release [62.0 kB]           
Holen: 12 http://deb.torproject.org trusty InRelease [3'526 B]                 
Ign http://deb.torproject.org trusty InRelease                                 
OK   http://ppa.launchpad.net trusty/main Sources                              
OK   http://ppa.launchpad.net trusty/main i386 Packages                        
Ign http://extras.ubuntu.com trusty/main Translation-de_CH                     
Ign http://deb.torproject.org trusty/main i386 Packages/DiffIndex              
Ign http://extras.ubuntu.com trusty/main Translation-de                        
Ign http://update.swisssign.com trusty/free Translation-de_CH                  
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Ign http://repo.wuala.com stable/main Translation-de_CH                        
Ign http://update.swisssign.com trusty/free Translation-de                     
Ign http://update.swisssign.com trusty/free Translation-en                     
Ign http://repo.wuala.com stable/main Translation-de                           
Ign http://update.swisssign.com trusty/non-free Translation-de_CH              
Holen: 13 http://archive.ubuntu.com trusty-security Release [62.0 kB]          
Ign http://update.swisssign.com trusty/non-free Translation-de                 
Ign http://repo.wuala.com stable/main Translation-en                           
Ign http://update.swisssign.com trusty/non-free Translation-en                 
Fehl http://ppa.launchpad.net karmic/main i386 Packages                        
  404  Not Found
Ign http://ppa.launchpad.net karmic/main Translation-de_CH                  
OK   http://archive.ubuntu.com trusty/main Sources                          
Ign http://ppa.launchpad.net karmic/main Translation-de                        
Ign http://ppa.launchpad.net karmic/main Translation-en                        
OK   http://archive.ubuntu.com trusty/restricted Sources                       
OK   http://archive.ubuntu.com trusty/universe Sources                         
OK   http://archive.ubuntu.com trusty/multiverse Sources                       
OK   http://archive.ubuntu.com trusty/main i386 Packages                       
OK   http://archive.ubuntu.com trusty/restricted i386 Packages                 
OK   http://archive.ubuntu.com trusty/universe i386 Packages                   
Ign http://ppa.launchpad.net oneiric/main Translation-de_CH                    
Ign http://ppa.launchpad.net oneiric/main Translation-de                       
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
OK   http://archive.ubuntu.com trusty/multiverse i386 Packages                 
Ign http://ppa.launchpad.net trusty/main Translation-de_CH                     
Ign http://ppa.launchpad.net trusty/main Translation-de                        
Ign http://ppa.launchpad.net trusty/main Translation-en                        
OK   http://archive.ubuntu.com trusty/main Translation-de                      
OK   http://archive.ubuntu.com trusty/main Translation-en              
OK   http://archive.ubuntu.com trusty/multiverse Translation-de       
OK   http://archive.ubuntu.com trusty/multiverse Translation-en       
Holen: 14 http://deb.torproject.org trusty/main i386 Packages [2'616 B]
OK   http://archive.ubuntu.com trusty/restricted Translation-de                
Ign http://deb.torproject.org trusty/main Translation-de_CH           
OK   http://archive.ubuntu.com trusty/restricted Translation-en       
Ign http://deb.torproject.org trusty/main Translation-de              
Ign http://deb.torproject.org trusty/main Translation-en              
OK   http://archive.ubuntu.com trusty/universe Translation-de         
OK   http://archive.ubuntu.com trusty/universe Translation-en
Holen: 15 http://archive.ubuntu.com trusty-updates/main Sources [144 kB]
Holen: 16 http://archive.ubuntu.com trusty-updates/restricted Sources [1'408 B]
Holen: 17 http://archive.ubuntu.com trusty-updates/universe Sources [93.0 kB]  
Holen: 18 http://archive.ubuntu.com trusty-updates/multiverse Sources [3'534 B]
Holen: 19 http://archive.ubuntu.com trusty-updates/main i386 Packages [363 kB]
Holen: 20 http://archive.ubuntu.com trusty-updates/restricted i386 Packages [5'820 B]
Holen: 21 http://archive.ubuntu.com trusty-updates/universe i386 Packages [222 kB]
Holen: 22 http://archive.ubuntu.com trusty-updates/multiverse i386 Packages [9'567 B]
Holen: 23 http://archive.ubuntu.com trusty-updates/main Translation-en [170 kB]
OK   http://archive.ubuntu.com trusty-updates/multiverse Translation-en        
OK   http://archive.ubuntu.com trusty-updates/restricted Translation-en
Holen: 24 http://archive.ubuntu.com trusty-updates/universe Translation-en [112 kB]
Holen: 25 http://archive.ubuntu.com trusty-security/main Sources [54.1 kB]     
Holen: 26 http://archive.ubuntu.com trusty-security/restricted Sources [14 B]
Holen: 27 http://archive.ubuntu.com trusty-security/universe Sources [17.4 kB]
Holen: 28 http://archive.ubuntu.com trusty-security/multiverse Sources [700 B]
Holen: 29 http://archive.ubuntu.com trusty-security/main i386 Packages [160 kB]
Holen: 30 http://archive.ubuntu.com trusty-security/restricted i386 Packages [14 B]
Holen: 31 http://archive.ubuntu.com trusty-security/universe i386 Packages [73.2 kB]
Holen: 32 http://archive.ubuntu.com trusty-security/multiverse i386 Packages [1'389 B]
Holen: 33 http://archive.ubuntu.com trusty-security/main Translation-en [82.5 kB]
OK   http://archive.ubuntu.com trusty-security/multiverse Translation-en       
OK   http://archive.ubuntu.com trusty-security/restricted Translation-en    
Holen: 34 http://archive.ubuntu.com trusty-security/universe Translation-en [39.9 kB]
Ign http://archive.ubuntu.com trusty/main Translation-de_CH                    
Ign http://archive.ubuntu.com trusty/multiverse Translation-de_CH              
Ign http://archive.ubuntu.com trusty/restricted Translation-de_CH              
Ign http://archive.ubuntu.com trusty/universe Translation-de_CH                
Es wurden 1'736 kB in 21 s geholt (82.2 kB/s).                                 
W: GPG-Fehler: http://deb.torproject.org trusty InRelease: Die folgenden Signaturen waren ungültig: KEYEXPIRED 1409325681 KEYEXPIRED 1409325681 KEYEXPIRED 1409325681 KEYEXPIRED 1409325681
W: Fehlschlag beim Holen von http://ppa.launchpad.net/songbird-daily/ppa/ubuntu/dists/karmic/main/binary-i386/Packages  404  Not Found

E: Einige Indexdateien konnten nicht heruntergeladen werden. Sie wurden ignoriert oder alte an ihrer Stelle benutzt.
root@laptopottos4:/home/otto# sudo apt-get -f install
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut.       
Statusinformationen werden eingelesen.... Fertig
Die folgenden Pakete wurden automatisch installiert und werden nicht mehr benötigt:
  compiz-plugins-extra compiz-plugins-main fonts-arphic-uming fonts-breip
  fonts-vlgothic gnome-search-tool gwibber-service hyphen-en-us libdb5.1
  libmuparser2 libppl-c2 libppl7 libquvi-scripts libquvi7 librecad
  librecad-data mythes-cs python-argparse suisseid-configuration
  suisseid-pkcs11 u-boot-tools
Verwenden Sie »apt-get autoremove«, um sie zu entfernen.
0 aktualisiert, 0 neu installiert, 0 zu entfernen und 177 nicht aktualisiert.
W: Duplicate sources.list entry http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu/ oneiric/main i386 Packages (/var/lib/apt/lists/ppa.launchpad.net_ubuntu-clamav_ppa_ubuntu_dists_oneiric_main_binary-i386_Packages)
W: Probieren Sie »apt-get update«, um diese Probleme zu korrigieren.
root@laptopottos4:/home/otto# sudo apt-get update
Ign http://update.swisssign.com trusty InRelease
OK   http://update.swisssign.com trusty Release.gpg                            
Ign http://archive.canonical.com trusty InRelease                              
Ign http://extras.ubuntu.com trusty InRelease                                  
Ign http://ppa.launchpad.net karmic InRelease                                  
OK   http://update.swisssign.com trusty Release                                
OK   http://archive.canonical.com trusty Release.gpg                           
OK   http://repo.wuala.com stable InRelease                                    
OK   http://extras.ubuntu.com trusty Release.gpg                               
Ign http://ppa.launchpad.net oneiric InRelease                                 
OK   http://archive.canonical.com trusty Release                               
OK   http://extras.ubuntu.com trusty Release                                   
Ign http://ppa.launchpad.net trusty InRelease                                  
OK   http://update.swisssign.com trusty/free i386 Packages                     
Ign http://ppa.launchpad.net karmic Release.gpg                                
OK   http://ppa.launchpad.net oneiric Release.gpg                              
OK   http://update.swisssign.com trusty/non-free i386 Packages                 
Holen: 1 http://deb.torproject.org trusty InRelease [3'526 B]                  
OK   http://ppa.launchpad.net trusty Release.gpg                               
Ign http://archive.ubuntu.com trusty InRelease                                 
Ign http://ppa.launchpad.net karmic Release                                    
OK   http://archive.canonical.com trusty/partner Sources                       
OK   http://repo.wuala.com stable/main i386 Packages                           
OK   http://ppa.launchpad.net oneiric Release                                  
OK   http://archive.canonical.com trusty/partner i386 Packages                 
Ign http://deb.torproject.org trusty InRelease                                 
OK   http://extras.ubuntu.com trusty/main i386 Packages                        
OK   http://ppa.launchpad.net trusty Release                                   
Ign http://archive.ubuntu.com trusty-updates InRelease                         
Ign http://archive.canonical.com trusty/partner Translation-en                 
Ign http://deb.torproject.org trusty/main i386 Packages/DiffIndex              
Ign http://archive.ubuntu.com trusty-security InRelease                        
OK   http://ppa.launchpad.net oneiric/main Sources                             
OK   http://ppa.launchpad.net oneiric/main i386 Packages                       
OK   http://archive.ubuntu.com trusty Release.gpg                              
OK   http://archive.ubuntu.com trusty-updates Release.gpg                      
OK   http://ppa.launchpad.net trusty/main Sources                              
Ign http://update.swisssign.com trusty/free Translation-de_CH                  
Ign http://update.swisssign.com trusty/free Translation-de                     
Ign http://update.swisssign.com trusty/free Translation-en                     
Ign http://extras.ubuntu.com trusty/main Translation-de_CH                     
OK   http://archive.ubuntu.com trusty-security Release.gpg                     
Ign http://update.swisssign.com trusty/non-free Translation-de_CH              
Ign http://update.swisssign.com trusty/non-free Translation-de                 
Ign http://extras.ubuntu.com trusty/main Translation-de                        
OK   http://ppa.launchpad.net trusty/main i386 Packages                        
Ign http://update.swisssign.com trusty/non-free Translation-en                 
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Ign http://repo.wuala.com stable/main Translation-de_CH                        
OK   http://archive.ubuntu.com trusty Release                                  
Ign http://repo.wuala.com stable/main Translation-de                           
Ign http://repo.wuala.com stable/main Translation-en                           
OK   http://archive.ubuntu.com trusty-updates Release                          
OK   http://archive.ubuntu.com trusty-security Release                         
OK   http://archive.ubuntu.com trusty/main Sources                             
OK   http://archive.ubuntu.com trusty/restricted Sources                       
OK   http://archive.ubuntu.com trusty/universe Sources                         
OK   http://archive.ubuntu.com trusty/multiverse Sources                       
OK   http://archive.ubuntu.com trusty/main i386 Packages                       
OK   http://archive.ubuntu.com trusty/restricted i386 Packages                 
OK   http://archive.ubuntu.com trusty/universe i386 Packages                   
Fehl http://ppa.launchpad.net karmic/main i386 Packages                        
  404  Not Found
OK   http://archive.ubuntu.com trusty/multiverse i386 Packages                 
Ign http://ppa.launchpad.net karmic/main Translation-de_CH                     
Ign http://ppa.launchpad.net karmic/main Translation-de                        
Ign http://ppa.launchpad.net karmic/main Translation-en                        
Ign http://ppa.launchpad.net oneiric/main Translation-de_CH                    
OK   http://archive.ubuntu.com trusty/main Translation-de                      
Ign http://ppa.launchpad.net oneiric/main Translation-de                       
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Ign http://ppa.launchpad.net trusty/main Translation-de_CH                     
Ign http://ppa.launchpad.net trusty/main Translation-de                        
Ign http://ppa.launchpad.net trusty/main Translation-en                        
OK   http://deb.torproject.org trusty/main i386 Packages                       
OK   http://archive.ubuntu.com trusty/main Translation-en              
Ign http://deb.torproject.org trusty/main Translation-de_CH           
Ign http://deb.torproject.org trusty/main Translation-de              
OK   http://archive.ubuntu.com trusty/multiverse Translation-de       
Ign http://deb.torproject.org trusty/main Translation-en              
OK   http://archive.ubuntu.com trusty/multiverse Translation-en       
OK   http://archive.ubuntu.com trusty/restricted Translation-de
OK   http://archive.ubuntu.com trusty/restricted Translation-en
OK   http://archive.ubuntu.com trusty/universe Translation-de
OK   http://archive.ubuntu.com trusty/universe Translation-en
OK   http://archive.ubuntu.com trusty-updates/main Sources
OK   http://archive.ubuntu.com trusty-updates/restricted Sources
OK   http://archive.ubuntu.com trusty-updates/universe Sources
OK   http://archive.ubuntu.com trusty-updates/multiverse Sources
OK   http://archive.ubuntu.com trusty-updates/main i386 Packages
OK   http://archive.ubuntu.com trusty-updates/restricted i386 Packages
OK   http://archive.ubuntu.com trusty-updates/universe i386 Packages
OK   http://archive.ubuntu.com trusty-updates/multiverse i386 Packages
OK   http://archive.ubuntu.com trusty-updates/main Translation-en
OK   http://archive.ubuntu.com trusty-updates/multiverse Translation-en
OK   http://archive.ubuntu.com trusty-updates/restricted Translation-en
OK   http://archive.ubuntu.com trusty-updates/universe Translation-en
OK   http://archive.ubuntu.com trusty-security/main Sources
OK   http://archive.ubuntu.com trusty-security/restricted Sources
OK   http://archive.ubuntu.com trusty-security/universe Sources
OK   http://archive.ubuntu.com trusty-security/multiverse Sources
OK   http://archive.ubuntu.com trusty-security/main i386 Packages
OK   http://archive.ubuntu.com trusty-security/restricted i386 Packages
OK   http://archive.ubuntu.com trusty-security/universe i386 Packages
OK   http://archive.ubuntu.com trusty-security/multiverse i386 Packages
OK   http://archive.ubuntu.com trusty-security/main Translation-en
OK   http://archive.ubuntu.com trusty-security/multiverse Translation-en
OK   http://archive.ubuntu.com trusty-security/restricted Translation-en       
OK   http://archive.ubuntu.com trusty-security/universe Translation-en         
Ign http://archive.ubuntu.com trusty/main Translation-de_CH                    
Ign http://archive.ubuntu.com trusty/multiverse Translation-de_CH              
Ign http://archive.ubuntu.com trusty/restricted Translation-de_CH              
Ign http://archive.ubuntu.com trusty/universe Translation-de_CH                
Es wurden 3'526 B in 15 s geholt (223 B/s).                                    
W: GPG-Fehler: http://deb.torproject.org trusty InRelease: Die folgenden Signaturen waren ungültig: KEYEXPIRED 1409325681 KEYEXPIRED 1409325681 KEYEXPIRED 1409325681 KEYEXPIRED 1409325681
W: Fehlschlag beim Holen von http://ppa.launchpad.net/songbird-daily/ppa/ubuntu/dists/karmic/main/binary-i386/Packages  404  Not Found

E: Einige Indexdateien konnten nicht heruntergeladen werden. Sie wurden ignoriert oder alte an ihrer Stelle benutzt.
root@laptopottos4:/home/otto# sudo dpkg --configure -a
root@laptopottos4:/home/otto# 

```

---

### Post by ottosykora on 2014-12-04
the mv of the 'dots' has only one result: also all setting on unity are lost, but on gnome/metacity still simply nothing.

---

### Post by kansasnoob on 2014-12-05
> 0 aktualisiert, 0 neu installiert, 0 zu entfernen und **[COLOR="#FF0000"]177 nicht aktualisiert[/COLOR]**.

I only speak english but I think that means you have 177 packages that failed to properly upgrade???

I also see some additional errors but I can't really read them :oops:

---

### Post by kansasnoob on 2014-12-05
There appear to still be some Oneiric sources:

> OK   [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                             
OK   [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                       

And even Karmic:

> Fehl [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main i386 Packages                        
  404  Not Found

So things appear to be quite broken.

---

