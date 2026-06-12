---
title: "Plasma Workspace Crash after Login"
date: 2010-02-03
forum: Desktop Environments
---

### Post by ApocoLypTus on 2010-02-03
I have just did some recent updates and when i did that, i wanted to have the full effect of the updates. Once i restarted, It came up with a black screen, had a couple of windows open(because i had them open before.) All i can do is enter windows, I am on Kubuntu 9.10. There is some blocked updates and one is Kubuntu-Desktop. But i can't get it. Do you think that that will help my desktop?

---

### Post by ApocoLypTus on 2010-02-03
I dont have any other desktops, so i am screwed.

Here is what the error is

Executable: kdeinit4 PID: 1944 Signal: 11 (Segmentation fault)

PLEASSE HELP!

---

### Post by oshunluvr on 2010-02-04
look at your log file first - /var/log/Xorg.0.log and /var/log/messages

---

### Post by lykwydchykyn on 2010-02-04
"blocked updates" sounds like a kpackagekit issue.  It might help to update from the terminal.  

Hit ctrl-alt-f1 to get to a virtual terminal and do:
```

sudo aptitude update
sudo aptitude dist-upgrade

```

Of course, the blocked updates may have nothing to do with your desktop issue, but it's a good place to start.

If that doesn't work, try defaulting your kde settings like so:
```

mv .kde .kde-old

```

---

### Post by CentralCaFan on 2010-02-11
I had the same problem. Late yesterday my sources list prompted me to install a slew of updates. After re-booting instead of seeing my desktop with panel, icons, background, etc... I got a black screen. But with the black screen still lots of functionality, including mouse pointer but nothing to point to. Could alt / f2 and open programs that way, and the programs I had open when I re-booted opened as they normally would. I'm eager to try the fix recommended here, above. As a novice, I couldn't seem to roll back updates in KPackageKit (option greyed out, maybe I forgot to run as administrator though).

Curious, why would such a bug or error be befall so many users by an apparent standard update (KDE 4.4, was that the culprit?) From searching for answers, it appears that many had the same issue weeks or months ago with earlier release candidates.

---

### Post by lykwydchykyn on 2010-02-11
> **CentralCaFan said:**
> I had the same problem. Late yesterday my sources list prompted me to install a slew of updates. After re-booting instead of seeing my desktop with panel, icons, background, etc... I got a black screen. But with the black screen still lots of functionality, including mouse pointer but nothing to point to. Could alt / f2 and open programs that way, and the programs I had open when I re-booted opened as they normally would. I'm eager to try the fix recommended here, above. As a novice, I couldn't seem to roll back updates in KPackageKit (option greyed out, maybe I forgot to run as administrator though).

Curious, why would such a bug or error be befall so many users by an apparent standard update (KDE 4.4, was that the culprit?) From searching for answers, it appears that many had the same issue weeks or months ago with earlier release candidates.

Sounds like you got KDE 4.4, and plasma is crashing.  Plasma provides the desktop (wallpaper, icons, panels, widgets, etc), so when it crashes you get a black screen, but you can still alt-f2 to run things.

I found after updating to 4.4 that plasma would crash if I had third-party plasmoids that were compiled against KDE 4.3.  In my case it was Daisy dock and smooth tasks.  Fancy tasks also would crash it.  If you've got a ppa for plasmoids like samrog131's ppa, then those plasmoids would crash it.

Basically, the two solutions are to either default your kde settings and don't use third party plasma widgets, or to recompile the widgets from source against KDE 4.4.

---

### Post by CentralCaFan on 2010-02-11
Oh thanks. Interesting about the 3rd-party widgets. I have one that I like. Or had one... to display weather on desktop, much nicer than the ones that come packaged. Can't wait to try out the fix you posted earlier. Thanks very much, John.

---

### Post by lykwydchykyn on 2010-02-11
I would assume any widget compiled against QT 4.5 is going to fail when things are upgraded to QT 4.6 (which is required for KDE 4.4), but that might not be so in every case.

I should mention the third option, if you're feeling savvy enough, is to do surgery on your ~/.kde/share/config/plasma-desktop-appletsrc file and remove the entries for the offending plasmoids.  The file isn't that complicated, but you do have to study it a bit to figure out what needs to be deleted.

---

### Post by CentralCaFan on 2010-02-11
Hey, ok I tried updating sources then upgrading from a console login. No dice. Also, mv .kde .kde-old. 

I don't think I have that file any longer, the ~/.kde/share/config/plasma-desktop-appletsrc exists. I enter ls -al and ls -la and nothing.

I press control-escape and krunner is running. Someone mentioned a possible session problem and to try to look for $KDEHOME but I can't quite get my head around how to deal with that now.

Any ideas? Sorry to be such a dufus.

---

### Post by CentralCaFan on 2010-02-11
Tried a number of other things including creating new user. Logging in to that user acct, and still, black screen. Am now backing up and ready to reinstall.

---

### Post by lykwydchykyn on 2010-02-12
Open a konsole by running it from krunner (alt-f2).

run "plasma-desktop" in that konsole and tell us the output.

---

### Post by grahampa on 2010-02-12
I had the same problem.
When I went to KPackage it said I had 38 or so blocked updates.
I then tried updating via aptitude 
"sudo aptitude update
sudo aptitude dist-upgrade"
in order to install these updates and then after a reboot it no longer segmentation faulted.
I hope this helps.

---

### Post by Ubuntiac on 2010-02-12
Just a safety tip... *any* time you use dist-upgrade in the console, check what packages it is going to remove. Sometimes it may want to remove a whole bunch of stuff you need. Often this can be fixed with:

> apt-get install kubuntu-desktop

This is especially true when only half of a big KDE update has come down the line. Often you can also just fix it by waiting an hour or so and updating again.

Remember, dist-upgrade can fix a lot of problems, but it can also install and *remove* software, making more problems. Do be careful and understand this before just typing it in and saying "yes".

---

### Post by CentralCaFan on 2010-02-12
Hey, ok this is a reply to each of the previous three posts (and thanks for posting!). I have tried again just now to type "plasma-desktop" (without quotes) in the alt-f2 "run" window. I did also try that before, and right now that's the only way I can start programs (and once they're minimized I bring up system activity via control-escape and the show "show application window" with right click. Anyway, what happened just now and earlier when I tried it is that the compact alt-f2 window just did nothing, my text remained and no response when I pressed enter.

That file I'm supposed to have, the one ending in appletsrc doesn't exist which I guess is worrisome. I was supposed to try editing that as my third option. But, I am 95% certain it existed *after* this all happened and that I deleted it, whether boneheaded move or not, as part of trying to fix this.

Thanks to you others for posting. Sounds like at least two posters here have solved their issue by running update and upgrade from console. Didn't work for me.

And the last post sounds interesting... it must have been something like that. I had suddenly loads of updates, so many I was a bit startled. And many were blocked (not sure if just bugs or updates). 

Thanks again, hope to hear more, but prepared to re-install. John.

---

### Post by lykwydchykyn on 2010-02-12
It would be more helpful if you'd run plasma-desktop from an actual Konsole, since that would provide some kind of feedback as to why it's not running.

It could be that plasma-desktop got removed due to some dependency conflict.  You might want to try installing that package.

```

sudo aptitude install plasma-desktop

```

That command also might reveal other things, such as whether or not your upgrade actually completed or if you need to run dpkg-configure or something.

---

### Post by CentralCaFan on 2010-02-12
Oh thanks. I misunderstood didn't I. Obviously, must do that from a console login. I will try in the afternoon and report back. I'm thinking this might work but what the heck would I know.

---

### Post by CentralCaFan on 2010-02-12
Thanks for your help! It's ok now. The "plasma-desktop" had been removed or uninstalled. Not sure if part of the updates, or partial updates, but it seemed so simple... just go to console login, issue install command, and back to normal with the new KDE4.4 features.

By the way, that plasmoid I thought was the culprit, or someone else suggested it was, was in the list of available plasmoids, or is, so that I could add it to the desktop. Not sure if that's a surprise or not.

---

### Post by Ubuntiac on 2010-02-13
"apt-get install kubuntu-desktop" as posted above would have installed this (and any other missing KDE packages) before.

Just so you know for next time. ;)

---

### Post by CentralCaFan on 2010-02-13
Oh thanks. I hadn't missed that just was a bit dense and didn't know if I should try that. Seeing "kubuntu" and not knowing otherwise, I thought that might overwrite data and settings, etc. But now I know.

p.s. ever since this latest when I try to run Dolphin as root it crashes, but I posted a separate thread for that in the general forum... couldn't find it addressed by existing threads

---

### Post by paulbarratt on 2010-02-16
I got the same result this morning and fortunately managed to get it running again.

Here is my tale, in case it helps anyone (apologies if the post is too long):

I upgraded to KDE 4.4 with Kubuntu 9.10.  I did this by adding the following repository in KPackagekit:

```
deb http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu karmic main

```

I hit the 'Refresh' button and KPackageKit reported 99 new packages and some held back, so I selected all of them and hit 'apply'.   After the upgrade there were still about 38 packages held back, so I thought "weird, but it probably knows what it is doing" and carried on.

So I logged out to try the new KDE and when I logged in all my applications had loaded from the previous session but plasma had crashed - no taskbar and a black screen background.
The KDE crash catcher appeared but it said the crash information was not useful enough to submit to launchpad.

I opened konsole (alt-F2) and ran 'plasma-desktop' and this was the output:

```

paul@mantaray Documents$: plasma-desktop
QDBusObjectPath: invalid path ""        
plasma-desktop(3757)/plasma PlasmaApp::PlasmaApp: Setting the pixmap cache size to 30953 kilobytes
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
plasma-desktop(3757)/kdecore (KSycoca) KSycocaPrivate::openDatabase: Trying to open ksycoca from  "/var/tmp/kdecache-paulriearg/ksycoca4"
plasma-desktop(3757)/libplasma Plasma::ContainmentPrivate::positionPanel: positioning non- horizontal panel; forced? false               
plasma-desktop(3757)/libplasma Plasma::ContainmentPrivate::positionPanel: moved to QPointF(11606, -44)                                   
plasma-desktop(3757)/libplasma Plasma::ContainmentPrivate::positionPanel: positioning non- horizontal panel; forced? false               
plasma-desktop(3757)/libplasma Plasma::ContainmentPrivate::positionPanel: moved to QPointF(11606, -44)                                   
plasma-desktop(3757)/libplasma Plasma::ContainmentPrivate::positionPanel: positioning  horizontal panel; forced? true                    
plasma-desktop(3757)/libplasma Plasma::ContainmentPrivate::positionPanel: moved to QPointF(0, -44)                                       
plasma-desktop(3757)/plasma SystemTray::DBusSystemTrayProtocol::registerWatcher: service appeared "org.kde.NotificationItemWatcher"      
QLayout: Attempting to add QLayout "" to QWidget "", which already has a layout                                                          
plasma-desktop(3757)/libplasma Plasma::Containment::restore: ()                                                                          
plasma-desktop(3757)/libplasma Plasma::ContainmentPrivate::positionPanel: positioning non- horizontal panel; forced? false               
plasma-desktop(3757)/libplasma Plasma::ContainmentPrivate::positionPanel: moved to QPointF(11286, -41)                                   
plasma-desktop(3757)/libplasma Plasma::ContainmentPrivate::positionPanel: positioning non- horizontal panel; forced? false               
plasma-desktop(3757)/libplasma Plasma::ContainmentPrivate::positionPanel: moved to QPointF(11286, -41)                                   
plasma-desktop(3757)/libplasma Plasma::ContainmentPrivate::positionPanel: positioning  horizontal panel; forced? true                    
plasma-desktop(3757)/libplasma Plasma::ContainmentPrivate::positionPanel: moved to QPointF(0, -123)                                      
QLayout: Attempting to add QLayout "" to QWidget "", which already has a layout                                                          
plasma-desktop(3757)/libplasma Plasma::Containment::restore: ()                                                                          
plasma-desktop(3757)/libplasma Plasma::Containment::restore: ()                                                                          
QGraphicsLinearLayout::removeAt: invalid index 0                                                                                         
plasma-desktop(3757)/kio (bookmarks) KBookmarkManager::KBookmarkManager: starting KDirWatch for  "/home/paul/.local/share//user-places.xbel"
plasma-desktop(3757)/kio (KDirListerCache) KDirListerCache::listDir: Listing directory: KUrl("trash:/")                                     
findServiceByDesktopPath: /home/paul/.kde/share/apps/RecentDocuments/vmware-root.desktop not found                                          

(snip) - some private docs displayed here which were not found (/snip)

plasma-desktop(3757)/kdecore (KLibrary) kde4Factory: The library "/usr/lib/kde4/solid_hal_power.so" does not offer a qt_plugin_instance function.
plasma-desktop(3757) Solid::Control::ManagerBasePrivate::loadBackend: Backend loaded:  "HAL-Power"                                               
Object::connect: No such slot TaskManager::GroupManager::reconnect()                                                                             
plasma-desktop(3757)/plasma TaskItemLayout::updatePreferredSize: Empty layout!!!!!!!!!!!!!!!!!!                                                  
plasma-desktop(3757)/plasma TaskManager::GroupManager::reconnect:                                                                                
plasma-desktop(3757)/plasma TaskManager::GroupManager::reconnect:                                                                                
plasma-desktop(3757)/plasma TaskManager::GroupManager::reconnect:                                                                                          
plasma-desktop(3756): Communication problem with  "plasma-desktop" , it probably crashed.                                                                  
Error message was:  "org.freedesktop.DBus.Error.ServiceUnknown" : " "The name org.kde.plasma-desktop was not provided by any .service files" "             
                                                                                                                                                           
paul@mantaray Documents$: KCrash: Application 'plasma-desktop' crashing...                                                                                 
sock_file=/home/paul/.kde/socket-mantaray/kdeinit4__0                                                                                                      
QDBusObjectPath: invalid path ""                                                                                                                           
plasma-desktop(3760)/plasma PlasmaApp::PlasmaApp: Setting the pixmap cache size to 30953 kilobytes                                                         
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)                                                     
plasma-desktop(3760)/kdecore (KSycoca) KSycocaPrivate::openDatabase: Trying to open ksycoca from  "/var/tmp/kdecache-paulriearg/ksycoca4"                  
plasma-desktop(3760)/libplasma Plasma::ContainmentPrivate::positionPanel: positioning non- horizontal panel; forced? false                                 
plasma-desktop(3760)/libplasma Plasma::ContainmentPrivate::positionPanel: moved to QPointF(11606, -44)                                                     
plasma-desktop(3760)/libplasma Plasma::ContainmentPrivate::positionPanel: positioning non- horizontal panel; forced? false                                 
plasma-desktop(3760)/libplasma Plasma::ContainmentPrivate::positionPanel: moved to QPointF(11606, -44)                                                     
plasma-desktop(3760)/libplasma Plasma::ContainmentPrivate::positionPanel: positioning  horizontal panel; forced? true                                      
plasma-desktop(3760)/libplasma Plasma::ContainmentPrivate::positionPanel: moved to QPointF(0, -44)                                                         
plasma-desktop(3760)/plasma SystemTray::DBusSystemTrayProtocol::registerWatcher: service appeared "org.kde.NotificationItemWatcher"                        
plasma-desktop(3760)/plasma SystemTray::DBusSystemTrayProtocol::newTask: Registering task with the manager "org.kde.NotificationItem-3433-1"               
plasma-desktop(3760)/plasma SystemTray::Manager::addTask: "org.kde.NotificationItem-3433-1" ( "org.kde.NotificationItem-3433-1" )                          
plasma-desktop(3760)/plasma SystemTray::DBusSystemTrayProtocol::newTask: Registering task with the manager "org.kde.NotificationItem-3439-1"               
plasma-desktop(3760)/plasma SystemTray::Manager::addTask: "org.kde.NotificationItem-3439-1" ( "org.kde.NotificationItem-3439-1" )                          
QLayout: Attempting to add QLayout "" to QWidget "", which already has a layout                                                                            
plasma-desktop(3760)/libplasma Plasma::Containment::restore: ()                                                                                            
plasma-desktop(3760)/libplasma Plasma::ContainmentPrivate::positionPanel: positioning non- horizontal panel; forced? false                                 
plasma-desktop(3760)/libplasma Plasma::ContainmentPrivate::positionPanel: moved to QPointF(11286, -41)                                                     
plasma-desktop(3760)/libplasma Plasma::ContainmentPrivate::positionPanel: positioning non- horizontal panel; forced? false                                 
plasma-desktop(3760)/libplasma Plasma::ContainmentPrivate::positionPanel: moved to QPointF(11286, -41)                                                     
plasma-desktop(3760)/libplasma Plasma::ContainmentPrivate::positionPanel: positioning  horizontal panel; forced? true                                      
plasma-desktop(3760)/libplasma Plasma::ContainmentPrivate::positionPanel: moved to QPointF(0, -123)                                                        
QLayout: Attempting to add QLayout "" to QWidget "", which already has a layout                                                                            
plasma-desktop(3760)/libplasma Plasma::Containment::restore: ()                                                                                            
plasma-desktop(3760)/libplasma Plasma::Containment::restore: ()                                                                                            
QGraphicsLinearLayout::removeAt: invalid index 0                                                                                                           
plasma-desktop(3760)/kio (bookmarks) KBookmarkManager::KBookmarkManager: starting KDirWatch for  "/home/paul/.local/share//user-places.xbel"               
plasma-desktop(3760)/kio (KDirListerCache) KDirListerCache::listDir: Listing directory: KUrl("trash:/")                                                    
findServiceByDesktopPath: /home/paul/.kde/share/apps/RecentDocuments/vmware-root.desktop not found                                                         
plasma-desktop(3760)/kdecore (KLibrary) kde4Factory: The library "/usr/lib/kde4/solid_hal_power.so" does not offer a qt_plugin_instance function.          
plasma-desktop(3760) Solid::Control::ManagerBasePrivate::loadBackend: Backend loaded:  "HAL-Power"                                                         
Object::connect: No such slot TaskManager::GroupManager::reconnect()                                                                                       
plasma-desktop(3760)/plasma TaskItemLayout::updatePreferredSize: Empty layout!!!!!!!!!!!!!!!!!!                                                            
plasma-desktop(3760)/plasma TaskManager::GroupManager::reconnect:                                                                                          
plasma-desktop(3760)/plasma TaskManager::GroupManager::reconnect:                                                                                          
plasma-desktop(3760)/plasma TaskManager::GroupManager::reconnect:                                                                                          
plasma-desktop(3759): Communication problem with  "plasma-desktop" , it probably crashed.                                                                  
Error message was:  "org.freedesktop.DBus.Error.ServiceUnknown" : " "The name org.kde.plasma-desktop was not provided by any .service files" "             


```

Next, did this from konsole:

```

$: sudo apt-get update
(snip)

$: sudo apt-get upgrade
Reading package lists... Done                 
Building dependency tree                      
Reading state information... Done             
The following packages have been kept back:   
  akregator digikam gwenview kaddressbook kdebase-workspace-bin kdebase-workspace-data kdebase-workspace-kgreet-plugins kdegraphics-strigi-plugins
  kdepim-groupware kdepim-kresources kdepim-runtime kdepim-strigi-plugins kdepim-wizards kdepimlibs-data kdepimlibs5 kdm kipi-plugins kmail knode knotes
  kontact konversation kopete korganizer ktimetracker kubuntu-desktop kuser libkdepim4 libkleo4 libkopete4 libkpgp4 libksieve4 libmimelib4              
  plasma-dataengines-workspace plasma-widgets-workspace python-kde4 python-qt4 python-sip4                                                              
0 upgraded, 0 newly installed, 0 to remove and 38 not upgraded.                                                                                         
paul@mantaray Documents$: sudo apt-get install plasma-desktop

Reading package lists... Done                                
Building dependency tree                                     
Reading state information... Done                            
The following packages were automatically installed and are no longer required:
  kdebase-runtime-data-common plasma-widget-lancelot liblancelot0 kdebase-runtime-bin-kde4
Use 'apt-get autoremove' to remove them.                                                  
The following extra packages will be installed:                                           
  akregator kaddressbook kdebase-workspace kdebase-workspace-bin kdebase-workspace-data kdebase-workspace-kgreet-plugins kdepim-groupware
  kdepim-kresources kdepim-wizards kdepimlibs-data kdepimlibs5 kdm kmail knode knotes kontact korganizer ktimetracker libkdepim4 libkleo4 libkpgp4
  libksieve4 libmimelib4 plasma-dataengines-workspace plasma-widgets-workspace                                                                    
Suggested packages:                                                                                                                               
  plasma-scriptengines egroupware procmail kleopatra gnokii kjots                                                                                 
The following packages will be REMOVED                                                                                                            
  libkabcommon4 libkontactinterfaces4                                                                                                             
The following NEW packages will be installed                                                                                                      
  kdebase-workspace plasma-desktop                                                                                                                
The following packages will be upgraded:                                                                                                          
  akregator kaddressbook kdebase-workspace-bin kdebase-workspace-data kdebase-workspace-kgreet-plugins kdepim-groupware kdepim-kresources kdepim-wizards
  kdepimlibs-data kdepimlibs5 kdm kmail knode knotes kontact korganizer ktimetracker libkdepim4 libkleo4 libkpgp4 libksieve4 libmimelib4                
  plasma-dataengines-workspace plasma-widgets-workspace                                                                                                 
24 upgraded, 2 newly installed, 2 to remove and 14 not upgraded.                                                                                        
Need to get 20.6MB of archives.                                                                                                                         
After this operation, 2,085kB disk space will be freed.                                                                                                 
Do you want to continue [Y/n]? y                   

```

Finally, after all of the usual package manager output in konsole:

```

Get: 1 http://ppa.launchpad.net karmic/main ktimetracker 4:4.4.0-0ubuntu1~karmic1~ppa2 [309kB]                                                          
Get: 2 http://ppa.launchpad.net karmic/main kontact 4:4.4.0-0ubuntu1~karmic1~ppa2 [184kB]                                                               
Get: 3 http://ppa.launchpad.net karmic/main knotes 4:4.4.0-0ubuntu1~karmic1~ppa2 [189kB]                                                                
Get: 4 http://ppa.launchpad.net karmic/main kaddressbook 4:4.4.0-0ubuntu1~karmic1~ppa2 [267kB]                                                          
Get: 5 http://ppa.launchpad.net karmic/main kmail 4:4.4.0-0ubuntu1~karmic1~ppa2 [2,643kB]                                                               
Get: 6 http://ppa.launchpad.net karmic/main libkleo4 4:4.4.0-0ubuntu1~karmic1~ppa2 [384kB]                                                              
Get: 7 http://ppa.launchpad.net karmic/main libksieve4 4:4.4.0-0ubuntu1~karmic1~ppa2 [51.9kB]                                                           
Get: 8 http://ppa.launchpad.net karmic/main libmimelib4 4:4.4.0-0ubuntu1~karmic1~ppa2 [104kB]                                                           
Get: 9 http://ppa.launchpad.net karmic/main knode 4:4.4.0-0ubuntu1~karmic1~ppa2 [418kB]                                                                 
Get: 10 http://ppa.launchpad.net karmic/main libkpgp4 4:4.4.0-0ubuntu1~karmic1~ppa2 [123kB]                                                             
Get: 11 http://ppa.launchpad.net karmic/main kdepim-wizards 4:4.4.0-0ubuntu1~karmic1~ppa2 [91.3kB]                                                      
Get: 12 http://ppa.launchpad.net karmic/main kdepim-groupware 4:4.4.0-0ubuntu1~karmic1~ppa2 [638kB]                                                     
Get: 13 http://ppa.launchpad.net karmic/main akregator 4:4.4.0-0ubuntu1~karmic1~ppa2 [504kB]                                                            
Get: 14 http://ppa.launchpad.net karmic/main kdepim-kresources 4:4.4.0-0ubuntu1~karmic1~ppa2 [47.2kB]                                                   
Get: 15 http://ppa.launchpad.net karmic/main korganizer 4:4.4.0-0ubuntu1~karmic1~ppa2 [1,098kB]                                                         
Get: 16 http://ppa.launchpad.net karmic/main libkdepim4 4:4.4.0-0ubuntu1~karmic1~ppa2 [844kB]                                                           
Get: 17 http://ppa.launchpad.net karmic/main kdepimlibs-data 4:4.4.0-0ubuntu1~karmic1~ppa1 [161kB]                                                      
Get: 18 http://ppa.launchpad.net karmic/main kdepimlibs5 4:4.4.0-0ubuntu1~karmic1~ppa1 [2,352kB]                                                          
Get: 19 http://ppa.launchpad.net karmic/main kdebase-workspace-bin 4:4.4.0-0ubuntu1~karmic1~ppa8 [2,078kB]                                                
Get: 20 http://ppa.launchpad.net karmic/main plasma-widgets-workspace 4:4.4.0-0ubuntu1~karmic1~ppa8 [542kB]                                               
Get: 21 http://ppa.launchpad.net karmic/main plasma-dataengines-workspace 4:4.4.0-0ubuntu1~karmic1~ppa8 [401kB]                                           
Get: 22 http://ppa.launchpad.net karmic/main kdebase-workspace-data 4:4.4.0-0ubuntu1~karmic1~ppa8 [5,998kB]                                               
Get: 23 http://ppa.launchpad.net karmic/main kdm 4:4.4.0-0ubuntu1~karmic1~ppa8 [872kB]                                                                    
Get: 24 http://ppa.launchpad.net karmic/main kdebase-workspace-kgreet-plugins 4:4.4.0-0ubuntu1~karmic1~ppa8 [66.1kB]                                      
Get: 25 http://ppa.launchpad.net karmic/main plasma-desktop 4:4.4.0-0ubuntu1~karmic1~ppa8 [228kB]                                                         
Get: 26 http://ppa.launchpad.net karmic/main kdebase-workspace 4:4.4.0-0ubuntu1~karmic1~ppa8 [45.2kB]                                                     
Fetched 20.6MB in 15s (1,346kB/s)                                                                                                                         
Preconfiguring packages ...                                                                                                                               
(Reading database ... 249641 files and directories currently installed.)                                                                                  
Preparing to replace ktimetracker 4:4.3.5-0ubuntu1~karmic1 (using .../ktimetracker_4%3a4.4.0-0ubuntu1~karmic1~ppa2_i386.deb) ...                          
Unpacking replacement ktimetracker ...                                                                                                                    
Replacing files in old package kontact ...                                                                                                                
Preparing to replace kontact 4:4.3.5-0ubuntu1~karmic1 (using .../kontact_4%3a4.4.0-0ubuntu1~karmic1~ppa2_i386.deb) ...                                    
Unpacking replacement kontact ...                                                                                                                         
Preparing to replace knotes 4:4.3.5-0ubuntu1~karmic1 (using .../knotes_4%3a4.4.0-0ubuntu1~karmic1~ppa2_i386.deb) ...                                      
Unpacking replacement knotes ...                                                                                                                          
Preparing to replace kaddressbook 4:4.3.5-0ubuntu1~karmic1 (using .../kaddressbook_4%3a4.4.0-0ubuntu1~karmic1~ppa2_i386.deb) ...                          
Unpacking replacement kaddressbook ...                                                                                                                    
Preparing to replace kmail 4:4.3.5-0ubuntu1~karmic1 (using .../kmail_4%3a4.4.0-0ubuntu1~karmic1~ppa2_i386.deb) ...                                        
Unpacking replacement kmail ...                                                                                                                           
Preparing to replace libkleo4 4:4.3.5-0ubuntu1~karmic1 (using .../libkleo4_4%3a4.4.0-0ubuntu1~karmic1~ppa2_i386.deb) ...                                  
Unpacking replacement libkleo4 ...                                                                                                                        
Preparing to replace libksieve4 4:4.3.5-0ubuntu1~karmic1 (using .../libksieve4_4%3a4.4.0-0ubuntu1~karmic1~ppa2_i386.deb) ...                              
Unpacking replacement libksieve4 ...                                                                                                                      
Preparing to replace libmimelib4 4:4.3.5-0ubuntu1~karmic1 (using .../libmimelib4_4%3a4.4.0-0ubuntu1~karmic1~ppa2_i386.deb) ...                            
Unpacking replacement libmimelib4 ...                                                                                                                     
Preparing to replace knode 4:4.3.5-0ubuntu1~karmic1 (using .../knode_4%3a4.4.0-0ubuntu1~karmic1~ppa2_i386.deb) ...                                        
Unpacking replacement knode ...                                                                                                                           
Preparing to replace libkpgp4 4:4.3.5-0ubuntu1~karmic1 (using .../libkpgp4_4%3a4.4.0-0ubuntu1~karmic1~ppa2_i386.deb) ...                                  
Unpacking replacement libkpgp4 ...                                                                                                                        
Preparing to replace kdepim-wizards 4:4.3.5-0ubuntu1~karmic1 (using .../kdepim-wizards_4%3a4.4.0-0ubuntu1~karmic1~ppa2_i386.deb) ...                      
Unpacking replacement kdepim-wizards ...                                                                                                                  
Preparing to replace kdepim-groupware 4:4.3.5-0ubuntu1~karmic1 (using .../kdepim-groupware_4%3a4.4.0-0ubuntu1~karmic1~ppa2_i386.deb) ...                  
Unpacking replacement kdepim-groupware ...                                                                                                                
Preparing to replace akregator 4:4.3.5-0ubuntu1~karmic1 (using .../akregator_4%3a4.4.0-0ubuntu1~karmic1~ppa2_i386.deb) ...                                
Unpacking replacement akregator ...                                                                                                                       
Preparing to replace kdepim-kresources 4:4.3.5-0ubuntu1~karmic1 (using .../kdepim-kresources_4%3a4.4.0-0ubuntu1~karmic1~ppa2_i386.deb) ...                
Unpacking replacement kdepim-kresources ...                                                                                                               
Processing triggers for hicolor-icon-theme ...                                                                                                            
(Reading database ... 249502 files and directories currently installed.)                                                                                  
Removing libkabcommon4 ...                                                                                                                                
Processing triggers for libc-bin ...                                                                                                                      
ldconfig deferred processing now taking place                                                                                                             
(Reading database ... 249498 files and directories currently installed.)                                                                                  
Preparing to replace korganizer 4:4.3.5-0ubuntu1~karmic1 (using .../korganizer_4%3a4.4.0-0ubuntu1~karmic1~ppa2_i386.deb) ...                              
Unpacking replacement korganizer ...                                                                                                                      
Preparing to replace libkdepim4 4:4.3.5-0ubuntu1~karmic1 (using .../libkdepim4_4%3a4.4.0-0ubuntu1~karmic1~ppa2_i386.deb) ...                              
Unpacking replacement libkdepim4 ...                                                                                                                      
Processing triggers for hicolor-icon-theme ...                                                                                                            
(Reading database ... 249500 files and directories currently installed.)                                                                                  
Removing libkontactinterfaces4 ...                                                                                                                        
Processing triggers for libc-bin ...                                                                                                                      
ldconfig deferred processing now taking place                                                                                                             
(Reading database ... 249495 files and directories currently installed.)                                                                                  
Preparing to replace kdepimlibs-data 4:4.3.5-0ubuntu1~karmic1 (using .../kdepimlibs-data_4%3a4.4.0-0ubuntu1~karmic1~ppa1_all.deb) ...                     
Unpacking replacement kdepimlibs-data ...                                                                                                                 
Preparing to replace kdepimlibs5 4:4.3.5-0ubuntu1~karmic1 (using .../kdepimlibs5_4%3a4.4.0-0ubuntu1~karmic1~ppa1_i386.deb) ...                            
Unpacking replacement kdepimlibs5 ...                                                                                                                     
Replacing files in old package kdepim-runtime-libs4 ...                                                                                                   
Preparing to replace kdebase-workspace-bin 4:4.3.5-0ubuntu1~karmic1 (using .../kdebase-workspace-bin_4%3a4.4.0-0ubuntu1~karmic1~ppa8_i386.deb) ...        
Unpacking replacement kdebase-workspace-bin ...                                                                                                           
Replacing files in old package kdebase-workspace-data ...                                                                                                 
Preparing to replace plasma-widgets-workspace 4:4.3.5-0ubuntu1~karmic1 (using .../plasma-widgets-workspace_4%3a4.4.0-0ubuntu1~karmic1~ppa8_i386.deb) ...  
Unpacking replacement plasma-widgets-workspace ...                                                                                                        
Preparing to replace plasma-dataengines-workspace 4:4.3.5-0ubuntu1~karmic1 (using .../plasma-dataengines-workspace_4%3a4.4.0-0ubuntu1~karmic1~ppa8_i386.deb) ...                                                                                                                                                      
Unpacking replacement plasma-dataengines-workspace ...                                                                                                     
Preparing to replace kdebase-workspace-data 4:4.3.5-0ubuntu1~karmic1 (using .../kdebase-workspace-data_4%3a4.4.0-0ubuntu1~karmic1~ppa8_all.deb) ...        
Unpacking replacement kdebase-workspace-data ...                                                                                                           
Preparing to replace kdm 4:4.3.5-0ubuntu1~karmic1 (using .../kdm_4%3a4.4.0-0ubuntu1~karmic1~ppa8_i386.deb) ...                                             
Unpacking replacement kdm ...                                                                                                                              
Preparing to replace kdebase-workspace-kgreet-plugins 4:4.3.5-0ubuntu1~karmic1 (using .../kdebase-workspace-kgreet-plugins_4%3a4.4.0-0ubuntu1~karmic1~ppa8_i386.deb) ...                                                                                                                                              
Unpacking replacement kdebase-workspace-kgreet-plugins ...                                                                                                 
Selecting previously deselected package plasma-desktop.                                                                                                    
Unpacking plasma-desktop (from .../plasma-desktop_4%3a4.4.0-0ubuntu1~karmic1~ppa8_i386.deb) ...                                                            
Selecting previously deselected package kdebase-workspace.                                                                                                 
Unpacking kdebase-workspace (from .../kdebase-workspace_4%3a4.4.0-0ubuntu1~karmic1~ppa8_all.deb) ...                                                       
Processing triggers for shared-mime-info ...                                                                                                               
Unknown media type in type 'all/all'                                                                                                                       

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

Processing triggers for man-db ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for ureadahead ...        
ureadahead will be reprofiled on next reboot  
Setting up kdepimlibs-data (4:4.4.0-0ubuntu1~karmic1~ppa1) ...

Setting up kdepimlibs5 (4:4.4.0-0ubuntu1~karmic1~ppa1) ...

Setting up libkleo4 (4:4.4.0-0ubuntu1~karmic1~ppa2) ...

Setting up libkpgp4 (4:4.4.0-0ubuntu1~karmic1~ppa2) ...

Setting up libksieve4 (4:4.4.0-0ubuntu1~karmic1~ppa2) ...

Setting up libmimelib4 (4:4.4.0-0ubuntu1~karmic1~ppa2) ...

Setting up plasma-dataengines-workspace (4:4.4.0-0ubuntu1~karmic1~ppa8) ...

Setting up plasma-widgets-workspace (4:4.4.0-0ubuntu1~karmic1~ppa8) ...

Setting up kdebase-workspace-data (4:4.4.0-0ubuntu1~karmic1~ppa8) ...
Setting up kdebase-workspace-kgreet-plugins (4:4.4.0-0ubuntu1~karmic1~ppa8) ...
Setting up kdebase-workspace-bin (4:4.4.0-0ubuntu1~karmic1~ppa8) ...           

Setting up kdm (4:4.4.0-0ubuntu1~karmic1~ppa8) ...
Installing new version of config file /etc/init/kdm.conf ...
Installing new version of config file /etc/kde4/kdm/Xsetup ...
Installing new version of config file /etc/kde4/kdm/kdmrc ... 

Setting up plasma-desktop (4:4.4.0-0ubuntu1~karmic1~ppa8) ...

Setting up kdebase-workspace (4:4.4.0-0ubuntu1~karmic1~ppa8) ...
Setting up libkdepim4 (4:4.4.0-0ubuntu1~karmic1~ppa2) ...       

Setting up ktimetracker (4:4.4.0-0ubuntu1~karmic1~ppa2) ...
Setting up kontact (4:4.4.0-0ubuntu1~karmic1~ppa2) ...     

Setting up knotes (4:4.4.0-0ubuntu1~karmic1~ppa2) ...
Setting up kaddressbook (4:4.4.0-0ubuntu1~karmic1~ppa2) ...

Setting up knode (4:4.4.0-0ubuntu1~karmic1~ppa2) ...

Setting up kdepim-groupware (4:4.4.0-0ubuntu1~karmic1~ppa2) ...

Setting up kdepim-wizards (4:4.4.0-0ubuntu1~karmic1~ppa2) ...
Setting up akregator (4:4.4.0-0ubuntu1~karmic1~ppa2) ...     

Setting up kdepim-kresources (4:4.4.0-0ubuntu1~karmic1~ppa2) ...

Setting up korganizer (4:4.4.0-0ubuntu1~karmic1~ppa2) ...

Setting up kmail (4:4.4.0-0ubuntu1~karmic1~ppa2) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

```

...everything looked happy, so I started plasma again:

```
$: plasma-desktop &
```

Result - the plasma desktop reappeared and things look normal.
So it does appear that some important parts of KDE got removed during the upgrade to KDE 4.4, for some reason which escapes me.

---

### Post by sonfrau on 2010-03-10
I would like just confirm that I had the same problem and I got to fix it with the command (from alt+f2):

$ sudo apt-get install plasma-desktop.

Regards

---

### Post by Bloemetjesgordijn on 2010-03-13
> **sonfrau said:**
> 
$ sudo apt-get install plasma-desktop



Well that didnt work for me: 

$ sudo apt-get install plasma-desktop
plasma-desktop is not available, however referred to by another package. Possibly this package is missing, obsolete or available in another source
E: Package plasma-desktop has no installable candidate 
*Translated*

Finally it worked for me I did the following:

sudo add-apt-repository ppa:kubuntu-ppa/backports 
sudo aptitude update
sudo aptitude upgrade
sudo shutdown -f now (immediate reboot)
sudo apt-get install kubuntu-desktop
sudo aptitude update 
sudo aptitude dist-upgrade
sudo shutdown -f now (immediate reboot)

***solved***

probably a few to many updates and reboots but it worked for me

---

### Post by dyltman on 2010-03-13
I just had this problem, what you can do is once you log in and ctrl+alt+F1

Log in and then type ```
sudo apt-get update && sudo apt-get upgrade
```

Now there should be a list of alot of blocked updats, what you want to do now is to type

```
sudo apt-get install *INSERT THE LIST HERE WITHOUT STARS*
```

for instance ```
sudo apt-get install kubuntu-desktop package2 package3 kopete
```

This worked for me, you can now reboot by typing ```
sudo reboot
```

---

### Post by Minipalmer on 2010-03-25
So I followed all the instructions in this thread, and ended up with this.

[[IMG]http://img682.imageshack.us/img682/9060/snapshot1zr.th.png[/IMG]](http://img682.imageshack.us/i/snapshot1zr.png/)

Notice that my transparency, wallpaper, AND network manager are all gone. This is bad, because I've been trying to fix my wireless. Ugh. Can anyone help?

---

### Post by cespinal on 2010-03-27
This also happened to me when updating to kde 4.4.1, what happened is the the update lacked some dependencies and was therefore, incomplete. I solved it just by running synaptic and erasing and reinstalling plasma-desktop again. 

try to go to kpackage (or synaptic if you have it, since it runs as root) uninstall knetwork manager and reinstall it.
For the wallpapers, just load them again. 
For the transparency, looks like you have composting turned off, go to system settings and try to enable it.

I hope this helps... i know what it feels to run into crashes when updating stuff... I totally hate it!!!!

---

### Post by Chame_Wizard on 2010-03-27
```
sudo apptitude safe-upgrade
```

---

### Post by Minipalmer on 2010-03-27
> **cespinal said:**
> This also happened to me when updating to kde 4.4.1, what happened is the the update lacked some dependencies and was therefore, incomplete. I solved it just by running synaptic and erasing and reinstalling plasma-desktop again. 

try to go to kpackage (or synaptic if you have it, since it runs as root) uninstall knetwork manager and reinstall it.
For the wallpapers, just load them again. 
For the transparency, looks like you have composting turned off, go to system settings and try to enable it.

I hope this helps... i know what it feels to run into crashes when updating stuff... I totally hate it!!!!Well...

I just went back to Ubuntu :D

---

### Post by Ubuntiac on 2010-03-28
It's amazing how many Kubuntu upgrade errors could be safely fixed as simple as:

```
sudo apt-get install kubuntu-desktop
```

*sigh*

---

### Post by cespinal on 2010-03-28
> **Ubuntiac said:**
> It's amazing how many Kubuntu upgrade errors could be safely fixed as simple as:

```
sudo apt-get install kubuntu-desktop
```

*sigh*


Then why the kubuntu team launches incomplete upgrades that pretty much possibly will leave errors that will have to get fixed by us?

If supo apt-get upgrade or sudo apt get kubuntu-desktop are commands that will fix us problems rapidly, then those commands should be highlighted in the how to upgrade tutorials.  

I don't want to start a fire in here, it is just a question I would like to be answred because in my case KDE 4.3 was way more stable than 4.4.1

---

### Post by Minipalmer on 2010-03-28
> **Ubuntiac said:**
> It's amazing how many Kubuntu upgrade errors could be safely fixed as simple as:

```
sudo apt-get install kubuntu-desktop
```

*sigh*
I did this, as well as the plasma-desktop package. Neither of them fixed the problems I was having.

So, it's amazing how many errors can't be fixed by that as well. ;)

---

### Post by webmadman on 2010-03-29
I've got the black desktop- tried:

```
sudo apt-get install kubuntu-desktop
```

And it said all is up to date.

At the command line when I try:

```
plasma-desktop
```

I get:

```
Invalid D-BUS interface name 'org.kde.plasma-desktop.PlasmaApp' found while parsing introspection
```

My other panels are still working though, just no desktop, so things are kind of functional...

---

### Post by webmadman on 2010-03-29
Alright, ended up doing:

```

sudo rm /usr/share/kubuntu-default-settings/kde4-profile/default/share/config/plasma-appletsrc
rm ~/.kde/share/config/plasma-desktop-appletsrc
rm ~/.kde/share/config/plasma-desktoprc
```

And that got plasma to work again- everything back to default, but working again- seems there was a bad applet, made the whole barrel go bad ;)

---

### Post by Ubuntiac on 2010-03-29
> **cespinal said:**
> Then why the kubuntu team launches incomplete upgrades that pretty much possibly will leave errors that will have to get fixed by us?

Generally these come from doing an update just as they're half way through uploading the new packages, so you get 1/2 of the packages you need.


They have to upload sometime, and they have no control over when you update, thus the problem.

A simple rule of thumb is that if you get a whole bunch of upgrades (especially KDE / Xorg related), then make sure you leave 15-20 minutes before shutting down and try another update to see if there's more uploaded. If you get more, then repeat.

Don't have 15-20 minutes before shutting down? Simple. Wait before doing a large update.

---

### Post by Ubuntiac on 2010-03-29
@Webmadman - Glad you got it working!

---

### Post by lstarba on 2010-05-03
> **webmadman said:**
> Alright, ended up doing:

```

sudo rm /usr/share/kubuntu-default-settings/kde4-profile/default/share/config/plasma-appletsrc
rm ~/.kde/share/config/plasma-desktop-appletsrc
rm ~/.kde/share/config/plasma-desktoprc
```

And that got plasma to work again- everything back to default, but working again- seems there was a bad applet, made the whole barrel go bad ;)

It did the trick for me as well :)

---

