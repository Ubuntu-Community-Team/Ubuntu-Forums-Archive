---
title: "Minecraft when connecting to online server"
date: 2012-03-07
forum: Gaming &amp; Leisure
---

### Post by Banzask on 2012-03-07
Hello, recently i have gone back to ubuntu and installed 11.10, i love minecraft and i have downloaded it for ubuntu it loads up all fine logs in fine alows me to go on to single player and start a world but then crashes and dissapears and its the same for connecting online aswell could anyone help me please?


Thanks 

banzask

---

### Post by regor210 on 2012-03-07
Could you run Minecraft in terminal and post the output?

Howto
If your using the newest Ubuntu 11.10 Oneiric Ocelot just click on the Ubuntu icon on the upper left side of your desk top and type term in the search window to bring up your terminal options. Any of them should work fine.

Ubuntu 10.04
Applications > Accessories > Terminal

After you have a terminal open just cut and past or type in the line you would like to run minus the $

# regular MC
$ cd ~/Downloads/ && java -jar minecraft.jar

# ALLOC's
$ cd ~/.minecraft/ && java -jar minecraft.jar

---

### Post by Banzask on 2012-03-07
thanks this is what i got 

cd ~/Desktop/ && java -jar minecraft.jar

(java:13328): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(java:13328): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(java:13328): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(java:13328): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
27 achievements
177 recipes
Setting user: banzaskfyou, -2762536025595334246
Loading: net.java.games.input.LinuxEnvironmentPlugin
Failed to open device (/dev/input/event7): Failed to open device /dev/input/event7 (13)

Failed to open device (/dev/input/event6): Failed to open device /dev/input/event6 (13)

Failed to open device (/dev/input/event5): Failed to open device /dev/input/event5 (13)

Failed to open device (/dev/input/event4): Failed to open device /dev/input/event4 (13)

Failed to open device (/dev/input/event3): Failed to open device /dev/input/event3 (13)

Failed to open device (/dev/input/event2): Failed to open device /dev/input/event2 (13)

Failed to open device (/dev/input/event1): Failed to open device /dev/input/event1 (13)

Failed to open device (/dev/input/event0): Failed to open device /dev/input/event0 (13)

Linux plugin claims to have found 0 controllers

Starting up SoundSystem...
Initializing LWJGL OpenAL
    (The LWJGL binding of OpenAL.  For more information, see [http://www.lwjgl.org](http://www.lwjgl.org))
OpenAL initialized.

Aborted

---

### Post by regor210 on 2012-03-07
[http://askubuntu.com/questions/66356/gdk-gtk-warnings-and-errors-from-the-command-line](http://askubuntu.com/questions/66356/gdk-gtk-warnings-and-errors-from-the-command-line)


There was a bug in Ubuntu 11.10, see if this is installed?

$ sudo apt-get update
$ sudo apt-get upgrade
$ sudo apt-get install gtk2-engines-pixbuf

The update and upgrade should fix it. After running all 3 lines try minecraft again and it should work.

---

### Post by Banzask on 2012-03-07
thanks, but i ran all those lines and it didn't make any difference (that i can see) i found another forum saying about graphic card drivers causing the problem so i uninstalled mine and it loads in to single player and multilayer but the worlds do not render correctly all i see is black and white blocks and some with blue lines

---

### Post by regor210 on 2012-03-07
Run these in a terminal minus the $

$ sudo apt-get update
$ sudo apt-get upgrade

$ sudo apt-get install mesa-utils

video driver 3D test FPS

$ glxgears

video card and driver information

$ lspci -vmk | grep -A 8 -B 2 VGA

$ cd ~/Desktop/ && java -jar minecraft.jar

And post what you get.

---

### Post by Banzask on 2012-03-07
Thank you very much it works fine now thanks for your help and this is everything that happend

> banzask@banzask-System-Product-Name:~$ sudo apt-get update
[sudo] password for banzask: 
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric InRelease
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease                                 
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) oneiric InRelease                             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security InRelease                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release.gpg                           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg                               
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) oneiric-updates InRelease                     
Ign [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) oneiric-backports InRelease                   
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) oneiric Release.gpg                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release.gpg                    
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release                                   
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg [316 B]                     
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) oneiric-updates Release.gpg                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release                        
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release [9,757 B]                       
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) oneiric-backports Release.gpg                 
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner i386 Packages                 
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) oneiric Release                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Sources                              
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner TranslationIndex              
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) oneiric-updates Release                       
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources [1,296 B]                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Sources                   
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) oneiric-backports Release                     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main i386 Packages                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main TranslationIndex                     
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) oneiric/main Sources                          
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) oneiric/restricted Sources                    
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) oneiric/universe Sources                      
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) oneiric/multiverse Sources                    
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) oneiric/main i386 Packages                    
Get:4 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages [1,908 B]            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main i386 Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted i386 Packages       
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) oneiric/restricted i386 Packages              
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) oneiric/universe i386 Packages                
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) oneiric/multiverse i386 Packages              
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) oneiric/main TranslationIndex                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe i386 Packages         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main TranslationIndex          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe TranslationIndex      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Translation-en            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Translation-en      
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) oneiric/multiverse TranslationIndex           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Translation-en      
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) oneiric/restricted TranslationIndex           
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) oneiric/universe TranslationIndex             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Translation-en        
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) oneiric-updates/main Sources                  
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) oneiric-updates/restricted Sources            
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) oneiric-updates/universe Sources              
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) oneiric-updates/multiverse Sources            
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en_IE             
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) oneiric-updates/main i386 Packages            
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) oneiric-updates/restricted i386 Packages      
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) oneiric-updates/universe i386 Packages        
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en                
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en_IE                    
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) oneiric-updates/multiverse i386 Packages
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) oneiric-updates/main TranslationIndex
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) oneiric-updates/multiverse TranslationIndex
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_IE          
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) oneiric-updates/restricted TranslationIndex
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) oneiric-updates/universe TranslationIndex
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) oneiric-backports/main Sources
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) oneiric-backports/restricted Sources
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) oneiric-backports/universe Sources
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) oneiric-backports/multiverse Sources
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) oneiric-backports/main i386 Packages
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) oneiric-backports/restricted i386 Packages
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) oneiric-backports/universe i386 Packages
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) oneiric-backports/multiverse i386 Packages
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) oneiric-backports/main TranslationIndex
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) oneiric-backports/multiverse TranslationIndex
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) oneiric-backports/restricted TranslationIndex
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) oneiric-backports/universe TranslationIndex
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) oneiric/main Translation-en
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) oneiric/multiverse Translation-en
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) oneiric/restricted Translation-en
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) oneiric/universe Translation-en
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) oneiric-updates/main Translation-en
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) oneiric-updates/multiverse Translation-en
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) oneiric-updates/restricted Translation-en
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) oneiric-updates/universe Translation-en
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) oneiric-backports/main Translation-en
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) oneiric-backports/multiverse Translation-en
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) oneiric-backports/restricted Translation-en
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) oneiric-backports/universe Translation-en
Fetched 13.3 kB in 1s (9,169 B/s)
Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9A06AEF9CB8DB0
banzask@banzask-System-Product-Name:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  wine1.3 wine1.3-gecko
2 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 62.7 MB of archives.
After this operation, 18.2 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  wine1.3 wine1.3-gecko
Install these packages without verification [y/N]? y
Get:1 [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/) oneiric/main wine1.3 i386 1.4~rc6-0ubuntu1~ppa1~oneiric1 [13.1 MB]
Get:2 [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/) oneiric/main wine1.3-gecko i386 1.4.0+1 [49.6 MB]
Fetched 62.7 MB in 1min 57s (535 kB/s)                                         
Preconfiguring packages ...
(Reading database ... 178285 files and directories currently installed.)
Preparing to replace wine1.3 1.3.28-0ubuntu2~oneiric1 (using .../wine1.3_1.4~rc6-0ubuntu1~ppa1~oneiric1_i386.deb) ...
Unpacking replacement wine1.3 ...
Preparing to replace wine1.3-gecko 1.3.0+1 (using .../wine1.3-gecko_1.4.0+1_i386.deb) ...
Unpacking replacement wine1.3-gecko ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Setting up wine1.3 (1.4~rc6-0ubuntu1~ppa1~oneiric1) ...
procps stop/waiting
Setting up wine1.3-gecko (1.4.0+1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
banzask@banzask-System-Product-Name:~$ sudo apt-get install mesa-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libvncserver0 virtualbox-dkms
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  mesa-utils
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 27.6 kB of archives.
After this operation, 135 kB of additional disk space will be used.
Get:1 [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) oneiric/universe mesa-utils i386 8.0.1+git20110129+d8f7d6b-0ubuntu2 [27.6 kB]
Fetched 27.6 kB in 0s (40.5 kB/s)
Selecting previously deselected package mesa-utils.
(Reading database ... 178300 files and directories currently installed.)
Unpacking mesa-utils (from .../mesa-utils_8.0.1+git20110129+d8f7d6b-0ubuntu2_i386.deb) ...
Processing triggers for man-db ...
Setting up mesa-utils (8.0.1+git20110129+d8f7d6b-0ubuntu2) ...
banzask@banzask-System-Product-Name:~$ glxgears
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
302 frames in 5.0 seconds = 60.287 FPS
300 frames in 5.0 seconds = 59.908 FPS
300 frames in 5.0 seconds = 59.906 FPS
300 frames in 5.0 seconds = 59.898 FPS
300 frames in 5.0 seconds = 59.902 FPS
300 frames in 5.0 seconds = 59.912 FPS
300 frames in 5.0 seconds = 59.904 FPS
300 frames in 5.0 seconds = 59.869 FPS
300 frames in 5.0 seconds = 59.940 FPS
300 frames in 5.0 seconds = 59.897 FPS
300 frames in 5.0 seconds = 59.907 FPS
300 frames in 5.0 seconds = 59.903 FPS
300 frames in 5.0 seconds = 59.910 FPS
300 frames in 5.0 seconds = 59.899 FPS
300 frames in 5.0 seconds = 59.905 FPS
300 frames in 5.0 seconds = 59.902 FPS
299 frames in 5.0 seconds = 59.706 FPS
300 frames in 5.0 seconds = 59.914 FPS
300 frames in 5.0 seconds = 59.904 FPS
300 frames in 5.0 seconds = 59.895 FPS
298 frames in 5.0 seconds = 59.514 FPS
297 frames in 5.0 seconds = 59.306 FPS
300 frames in 5.0 seconds = 59.903 FPS
300 frames in 5.0 seconds = 59.897 FPS
300 frames in 5.0 seconds = 59.911 FPS
298 frames in 5.0 seconds = 59.500 FPS
300 frames in 5.0 seconds = 59.904 FPS
300 frames in 5.0 seconds = 59.901 FPS
300 frames in 5.0 seconds = 59.907 FPS
300 frames in 5.0 seconds = 59.905 FPS
300 frames in 5.0 seconds = 59.904 FPS
300 frames in 5.0 seconds = 59.901 FPS
300 frames in 5.0 seconds = 59.909 FPS
300 frames in 5.0 seconds = 59.904 FPS
300 frames in 5.0 seconds = 59.903 FPS
297 frames in 5.0 seconds = 59.308 FPS
300 frames in 5.0 seconds = 59.909 FPS
300 frames in 5.0 seconds = 59.899 FPS
300 frames in 5.0 seconds = 59.905 FPS
300 frames in 5.0 seconds = 59.887 FPS
297 frames in 5.0 seconds = 59.322 FPS
300 frames in 5.0 seconds = 59.902 FPS
300 frames in 5.0 seconds = 59.910 FPS
300 frames in 5.0 seconds = 59.901 FPS
300 frames in 5.0 seconds = 59.910 FPS
298 frames in 5.0 seconds = 59.496 FPS
299 frames in 5.0 seconds = 59.711 FPS
299 frames in 5.0 seconds = 59.703 FPS
300 frames in 5.0 seconds = 59.903 FPS
300 frames in 5.0 seconds = 59.901 FPS
300 frames in 5.0 seconds = 59.904 FPS
297 frames in 5.0 seconds = 59.309 FPS
300 frames in 5.0 seconds = 59.903 FPS
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 32094 requests (32094 known processed) with 0 events remaining.
banzask@banzask-System-Product-Name:~$ lspci -vmk | grep -A 8 -B 2 VGA

Device:    02:00.0
Class:    VGA compatible controller
Vendor:    ATI Technologies Inc
Device:    Redwood PRO [Radeon HD 5500 Series]
SVendor:    XFX Pine Group Inc.
SDevice:    Device 3051
Driver:    radeon
Module:    radeon

Device:    02:00.1
banzask@banzask-System-Product-Name:~$ cd ~/Desktop/ && java -jar minecraft.jar
27 achievements
177 recipes
Setting user: banzaskfyou, -5142476978817388996
Loading: net.java.games.input.LinuxEnvironmentPlugin
Failed to open device (/dev/input/event7): Failed to open device /dev/input/event7 (13)

Failed to open device (/dev/input/event6): Failed to open device /dev/input/event6 (13)

Failed to open device (/dev/input/event5): Failed to open device /dev/input/event5 (13)

Failed to open device (/dev/input/event4): Failed to open device /dev/input/event4 (13)

Failed to open device (/dev/input/event3): Failed to open device /dev/input/event3 (13)

Failed to open device (/dev/input/event2): Failed to open device /dev/input/event2 (13)

Failed to open device (/dev/input/event1): Failed to open device /dev/input/event1 (13)

Failed to open device (/dev/input/event0): Failed to open device /dev/input/event0 (13)

Linux plugin claims to have found 0 controllers

Starting up SoundSystem...
Initializing LWJGL OpenAL
    (The LWJGL binding of OpenAL.  For more information, see [http://www.lwjgl.org](http://www.lwjgl.org))
OpenAL initialized.

Connecting to 176.31.213.0, 25609
Stopping!

SoundSystem shutting down...
    Author: Paul Lamb, [www.paulscode.com]("http://www.paulscode.com")

Exception in thread "Minecraft main thread" org.lwjgl.LWJGLException: X Error - disp: 0x8324fc8 serial: 18112 error: GLXBadWindow request_code: 155 minor_code: 32
    at org.lwjgl.opengl.LinuxDisplay.globalErrorHandler(LinuxDisplay.java:268)
    at org.lwjgl.opengl.LinuxDisplay.nDestroyWindow(Native Method)
    at org.lwjgl.opengl.LinuxDisplay.destroyWindow(LinuxDisplay.java:484)
    at org.lwjgl.opengl.Display.destroyWindow(Display.java:352)
    at org.lwjgl.opengl.Display.destroy(Display.java:967)
    at net.minecraft.client.Minecraft.d(SourceFile:520)
    at net.minecraft.client.Minecraft.run(SourceFile:681)
    at java.lang.Thread.run(Thread.java:679)


---

