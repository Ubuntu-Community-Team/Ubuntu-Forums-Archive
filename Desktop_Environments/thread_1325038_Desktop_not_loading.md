---
title: "Desktop not loading"
date: 2009-11-13
forum: Desktop Environments
---

### Post by belier on 2009-11-13
Hello.

I installed Kubuntu 9.10 some days ago. Been using GNome for a long time and I decided to give a try to KDE with the release of KK.
The first installation ended with plasma-desktop dead. I decided to forget KDE and stick again to GNome. But then I considered that retreating was for sissies and installed KDE again.
And KDE has awarded my perseverance with same problem. My user desktop is gone again. I boot with a black screen and a little arrow...
I can access KRunner. I open a Konsole and launch **plasma-desktop**. No success. I try then **kdesudo plasma-desktop**. The desktop is back but with the default aspect. No theme, no wallpaper, no nothing...
If I click on the K menu icon it says that who's logged in is root user. If I go to **Leave** and try to logout in order to enter with my user account it does nothing. If I log with my user in Konsole I only get a Konsole with **user@ubuntu**.

This is what I get when I launch **kdesudo plasma-desktop**

```
xavier@Kubuntu:~$ kdesudo plasma-desktop

QDBusObjectPath: invalid path ""
kephald starting up             
XRANDR error base:  162         
RRInput mask is set!!           
RandRScreen::loadSettings - adding mode:  63 1680 x 1050 
RandRScreen::loadSettings - adding mode:  64 1680 x 1050 
RandRScreen::loadSettings - adding mode:  65 1280 x 1024 
RandRScreen::loadSettings - adding mode:  66 1280 x 1024 
RandRScreen::loadSettings - adding mode:  67 1440 x 900  
RandRScreen::loadSettings - adding mode:  68 1440 x 900  
RandRScreen::loadSettings - adding mode:  69 1280 x 960  
RandRScreen::loadSettings - adding mode:  70 1152 x 864  
RandRScreen::loadSettings - adding mode:  71 1024 x 768  
RandRScreen::loadSettings - adding mode:  72 1024 x 768  
RandRScreen::loadSettings - adding mode:  73 832 x 624   
RandRScreen::loadSettings - adding mode:  74 800 x 600   
RandRScreen::loadSettings - adding mode:  75 800 x 600   
RandRScreen::loadSettings - adding mode:  76 800 x 600   
RandRScreen::loadSettings - adding mode:  77 640 x 480   
RandRScreen::loadSettings - adding mode:  78 640 x 480   
RandRScreen::loadSettings - adding mode:  79 720 x 400   
RandRScreen::loadSettings - adding crtc:  57             
RandRScreen::loadSettings - adding crtc:  58             
RandRScreen::loadSettings - adding output:  59           
Setting CRTC 0 on output "VGA1" (previous 0 )            
RandRScreen::loadSettings - adding output:  60           
Setting CRTC 0 on output "DVI1" (previous 0 )            
RandRScreen::loadSettings - adding output:  61           
Setting CRTC 0 on output "VGA2" (previous 0 )            
RandRScreen::loadSettings - adding output:  62           
Setting CRTC 57 on output "DVI0" (previous 0 )           
CRTC outputs: (62)                                       
Output name: "DVI0"                                      
Output refresh rate: 59.8833                             
Output rect: QRect(0,0 1680x1050)                        
Output rotation: 1                                       
XRandROutputs::init                                      
  added output  59                                       
  added output  60                                       
  added output  61                                       
got a valid edid block...                                
vendor code: "GSM"                                       
product id: 22068                                        
serial number: 457154
  added output  62
output: "DVI0" QRect(0,0 1680x1050) 0 false false
output: "DVI1" QRect(0,0 0x0) 0 false false
output: "VGA1" QRect(0,0 0x0) 0 false false
output: "VGA2" QRect(0,0 0x0) 0 false false
load xml
connected: 1
looking for current "DVI0"
known "*" has score: 0.125
screen: 0 QRect(0,0 1680x1050)
looking for a matching configuration...
connected: 1
looking for current "DVI0"
known "*" has score: 0.125
found outputs, known: false
connected: 1
looking for current "DVI0"
known "*" has score: 0.125
activate external configuration!!
registered the service: true
screens registered on the bus: true
outputs registered on the bus: true
configurations registered on the bus: true
QLayout: Attempting to add QLayout "" to QWidget "", which already has a layout
findServiceByDesktopPath: /root/.kde/share/apps/RecentDocuments/root.desktop not found
Object::connect: No such signal SystemTray::Manager::jobStateChanged(SystemTray::Job*)
Invalid D-BUS interface name 'org.kde.plasma-desktop.PlasmaApp' found while parsing introspection
kdeinit4: preparing to launch /usr/lib/kde4/kio_trash.so
kdeinit4: preparing to launch /usr/lib/kde4/kio_desktop.so
xavier@Kubuntu:~$ Error: "/var/tmp/kdecache-xavier" is owned by uid 1000 instead of uid 0.
Error: "/tmp/ksocket-xavier" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-xavier" is owned by uid 1000 instead of uid 0.
kdeinit4: preparing to launch /usr/lib/kde4/kio_file.so

xavier@Kubuntu:~$

```

Any suggestion? 

KK on GNome works flawlessly on same computer.

Thanks in advance

---

