---
title: "Can't login after installing xserver-xgl"
date: 2008-01-06
forum: Desktop Effects &amp; Customization
---

### Post by fizban9 on 2008-01-06
I installed xserver-xgl so I could use the nifty features of compiz but after it's installed, every time I try to login it goes to a blank screen with a spinning cursor and then goes back to the login screen.  The only way to get back in is to remove xserver-xgl.

Any ideas why xgl would cause the system to reset every time I login?

---

### Post by xeth_delta on 2008-01-06
> **fizban9 said:**
> I installed xserver-xgl so I could use the nifty features of compiz but after it's installed, every time I try to login it goes to a blank screen with a spinning cursor and then goes back to the login screen.  The only way to get back in is to remove xserver-xgl.

Any ideas why xgl would cause the system to reset every time I login?

As far as I know xserver-xgl is not needed to run compiz (At least not two last versions of Ubuntu). Are you able to login to a command line terminal?

---

### Post by xeth_delta on 2008-01-06
I'll quote from the Ubuntu documentation:

> 
Install Compiz & Compiz Fusion plugins

If you're on Feisty, we need to add a third party repository to your /etc/apt/sources.list. (Not needed on Gutsy) (Help for this available at AddingRepositoriesHowto) 
```
deb [http://ppa.launchpad.net/amaranth/ubuntu](http://ppa.launchpad.net/amaranth/ubuntu) feisty main universe 
deb-src [http://ppa.launchpad.net/amaranth/ubuntu](http://ppa.launchpad.net/amaranth/ubuntu) feisty main universe

```

Then run 
```
sudo apt-get update 

```
That will update the package cache. 

Now to install the packages: 

From Ubuntu: 
```
sudo apt-get install compiz compizconfig-settings-manager 

```
If you are running Kubuntu then use this command 
```
sudo apt-get install compiz-kde compiz-fusion-plugins-main compiz-fusion-plugins-extra 
compizconfig-settings-manager emerald librsvg2-common

```
Or you won't get any window decorations. 
Run Compiz

To run Compiz for the current session, hold Alt, then press F2, then enter the command 
```
compiz --replace
```
Configure

To configure Compiz and associated plugins, hold Alt, then press F2, then enter the command 
```
ccsm 

```
Alternatively, for Ubuntu: System -> Preferences -> CompizConfig Settings Manager 

And for Kubuntu: KMenu -> Settings -> CompizConfig Settings Manager or KMenu -> Settings -> Advanced Desktop Effects Settings 

You can select different themes with the emerald-theme-manager tool. To download the themes for emerald You must first install subversion, then activate the theme repositories. 
```
sudo apt-get install subversion 
svn ls https://svn.generation.no/emerald-themes

```
You can then use the "Fetch GPL'd themes" button of The "emerald-theme-manager" tool. 
Add Compiz Startup (optional)
For Ubuntu

Go to System -> Preferences -> Desktop Effects and click 'Enable Desktop Effects' 
For Kubuntu

Open Konsole (KMenu -> System -> Konsole) and type in these commands: 
```
echo "compiz --replace" > ~/.kde/Autostart/startcompiz.sh 
chmod +x ~/.kde/Autostart/startcompiz.sh
```
Troubleshooting

Under Kubuntu, some settings in the Compiz Settings Manager may not be selectable unless you enable the "Flat-File Configuration Backend" Under the CCSM tool -> Preferances -> (Backend drop down menu) 

If you ran nvidia-settings, then your xorg.conf lost some info. To fix your compiz window decorations (titlebars) with an nVidia graphics card, run 
```
sudo nvidia-xconfig --add-argb-glx-visuals -d 24 

```
then restart X by logging out and back in again and selecting "Restart X Server" from the login menu. 

If you want to stop Compiz and start the old window manager (metacity or kwin), just press Alt+F2 and put in the following for Ubuntu 
```
metacity --replace 

```
Or for Kubuntu 
```
kwin --replace
``` 
Fullscreen windows bug

It may happen that windows of specific programs might fully cover the desktop including the taskbar. This is due to a bug in the "workaround" plugin. 

This display default may be fixed by turning off the "Legacy Fullscreen Support" in the "workaround" plugin, opening your programs which were displayed improperly, and turning the "Legacy Fullscreen Support" option back on. For more details:[http://www.moleculargeek.net/blog/compiz-fusion-workarounds-for-workarounds.html]("http://www.moleculargeek.net/blog/compiz-fusion-workarounds-for-workarounds.html")


To find more documentation: [https://help.ubuntu.com/community/]("https://help.ubuntu.com/community/")
Xeth

---

### Post by fizban9 on 2008-01-06
What happens is that when I try to turn on advanced desktop effects, I get alot of screen blinking and then a fail message.  If I type compiz from a terminal I get:

signal9@RedMage:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 04:00.0 0300: 10de:0291 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 

So I assumed it was the lack of xgl that was thwarting me.  What else could it be?

---

### Post by xeth_delta on 2008-01-06
> **fizban9 said:**
> What happens is that when I try to turn on advanced desktop effects, I get alot of screen blinking and then a fail message.  If I type compiz from a terminal I get:

signal9@RedMage:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 04:00.0 0300: 10de:0291 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 

So I assumed it was the lack of xgl that was thwarting me.  What else could it be?

Maybe an incorrectly configured video driver. What is your card?
```
lshw -C video
```
What is the output of
```
glxinfo | grep -i direct
```

---

### Post by fizban9 on 2008-01-06
Thanks for everyones help.  Heres the output from those two commands.

signal9@RedMage:~$ lshw -C video
  *-display               
       description: VGA compatible controller
       product: G71 [GeForce 7900 GT/GTO]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga bus_master cap_list
       configuration: driver=nvidia latency=0 module=nvidia

signal9@RedMage:~$ glxinfo | grep -i direct
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

---

### Post by xeth_delta on 2008-01-06
> **fizban9 said:**
> Thanks for everyones help.  Heres the output from those two commands.

signal9@RedMage:~$ lshw -C video
  *-display               
       description: VGA compatible controller
       product: G71 [GeForce 7900 GT/GTO]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga bus_master cap_list
       configuration: driver=nvidia latency=0 module=nvidia

signal9@RedMage:~$ glxinfo | grep -i direct
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

Strange, for glxinfo I was expecting an output of the form
```
glxinfo | grep -i direct
direct rendering: Yes
```
or a statement about indirect rendering. I don't have much experience with nVidia drivers, but there are a couple of question I can ask.
-What drivers are you using, standard X open source, restricted drivers or Envy? I understand many people have good results with the latter.
-How did you install the drivers?

I will help you as I can, but hopefully someone more knowledgeable than me on nVidia drivers will write a post quite soon. In the meantime search in the forum for driver instructions for your card.

---

### Post by fizban9 on 2008-01-07
-What drivers are you using, standard X open source, restricted drivers or Envy? I understand many people have good results with the latter.

Right now I'm using the restricted drivers.  I had attempted to install the drivers as downloaded directly from Nvidia but that was a six hour fiasco to get back to a workable state and back to the restricted drivers.  I don't know wthat teh X open source or the Envy drivers are.  Any links?

-How did you install the drivers?

The restricted drivers installed automagically, I think I just checked a box or two.  The ones I downloaded from nvidia I followed the instructions found in one of the forums.  

Something I probably should have mentioned earlier is that xserver-xgl worked before I attempted to install the drivers from nvidia.  It only stopped working after  I f****ed everything up and got back to the restricted drivers.

---

### Post by phmcguin on 2008-01-07
Hey you're going through the exact same problems I'm experiencing. You might want to do a search for my username and have read through them.

you don't need xgl with nVidia which is why the login screen was looping. As for the rest..I'm still lost in the woods. One piece of advice..while I've had great success with the terminal I did find that i needed to set my display and driver under Administration > Screens and Graphics.

sorry I can't help more.

---

### Post by Forlong on 2008-01-07
Try resetting your xorg.conf:
```
sudo dpkg-reconfigure xserver-xorg
```
And afterwards run this:
```
sudo nvidia-xconfig --add-argb-glx-visuals -d 24
```
Restart X and see if it worked.

If not, post your xorg.conf
You can use this command for that:
```
grep -v ^# /etc/X11/xorg.conf
```
and use the forum's CODE tag please (# button)

---

### Post by xeth_delta on 2008-01-07
> **fizban9 said:**
> -What drivers are you using, standard X open source, restricted drivers or Envy? I understand many people have good results with the latter.

Right now I'm using the restricted drivers.  I had attempted to install the drivers as downloaded directly from Nvidia but that was a six hour fiasco to get back to a workable state and back to the restricted drivers.  I don't know wthat teh X open source or the Envy drivers are.  Any links?

-How did you install the drivers?

The restricted drivers installed automagically, I think I just checked a box or two.  The ones I downloaded from nvidia I followed the instructions found in one of the forums.  

Something I probably should have mentioned earlier is that xserver-xgl worked before I attempted to install the drivers from nvidia.  It only stopped working after  I f****ed everything up and got back to the restricted drivers.

It was quite some time ago (maybe years) that I installed nVidia drivers from their website. After a recompilation of the driver interface due to custom kernel, it worked great.

I don't know much about envy besides what I was able to tell you. I looked in the forum and found a thread on envy:[http://ubuntuforums.org/showthread.php?t=624358&highlight=envy+drivers]("http://ubuntuforums.org/showthread.php?t=624358&highlight=envy+drivers")

---

### Post by fizban9 on 2008-01-07
Thanks for the continued help everyone.  I tried the command that forlong suggested and it didn't work.  Heres my xorg.conf file, as requested.  

```
signal9@RedMage:~$ cat /etc/X11/xorg.conf | grep -v ^#


Section "ServerLayout"

        # Uncomment if you have a wacom tablet
        #       InputDevice     "stylus"        "SendCoreEvents"
        #       InputDevice     "cursor"        "SendCoreEvents"
        #       InputDevice     "eraser"        "SendCoreEvents"
        Identifier      "Default Layout"
  screen 0 "Default Screen" 0 0
  screen 1 "screen1" rightof "Default Screen"
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
        Load            "glx"
        Load            "v4l"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc101"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ExplorerPS/2"
        Option          "Emulate3Buttons"       "false"
        Option          "Buttons"       "7"
        Option          "ButtonMapping" "1 2 3 4 5"
        Option          "ZAxisMapping"  "6 7"
EndSection

Section "InputDevice"
        Identifier      "stylus"
        Driver          "wacom"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "stylus"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Identifier      "eraser"
        Driver          "wacom"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "eraser"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Identifier      "cursor"
        Driver          "wacom"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "cursor"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
        Identifier      "Q9-2 Series"
        Vendorname      "Generic LCD Display"
        Modelname       "LCD Panel 1280x1024"
        Horizsync       31.5-64.0
        Vertrefresh     56.0 - 65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
        Gamma   1.0
EndSection

Section "Device"
        Identifier      "nVidia Corporation G71 [GeForce 7900 GT/GTO]"
        Boardname       "nv"
        Busid           "PCI:4:0:0"
        Driver          "nvidia"
        Screen  0
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation G71 [GeForce 7900 GT/GTO]"
        Monitor         "Q9-2 Series"
        Defaultdepth    24
        Option          "UseFBDev"      "true"
        Option          "AddARGBGLXVisuals"     "True"
        SubSection "Display"
                Depth   24
                Virtual 1280    1024
                Modes           "1280x1024@60"  "1280x960@60"   "1024x768@60"   "800x600@60"    "800x600@56"    "640x480@60"
        EndSubSection
EndSection

Section "device" #  
        Identifier      "device1"
        Boardname       "nv"
        Busid           "PCI:4:0:0"
        Driver          "nvidia"
        Screen  1
EndSection
Section "screen" #  
        Identifier      "screen1"
        Device          "device1"
        Defaultdepth    24
        Monitor         "monitor1"
        SubSection "Display"
                Depth   24
                Modes           "1280x1024@60"  "1280x960@60"   "1024x768@60"   "800x600@60"    "800x600@56"    "640x480@60"
        EndSubSection
EndSection
Section "monitor" #  
        Identifier      "monitor1"
        Vendorname      "Generic LCD Display"
        Modelname       "LCD Panel 1280x1024"
        Horizsync       31.5-64.0
        Vertrefresh     56.0 - 65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
        Gamma   1.0
EndSection
Section "ServerFlags"
        Option          "Xinerama"      "true"
EndSection

```

---

### Post by Forlong on 2008-01-08
> **fizban9 said:**
> I tried the command that forlong suggested and it didn't work.
Certainly not the first one. There are lots of custom configurations in your xorg.conf including xinerama that may be the cause of your problem.

---

### Post by gerstrong on 2008-02-09
I had the same Problem and solved it that way:

```
sudo nvidia-glx-config enable
```

maybe it says to you, that your checksum is wrong, but also tells you how to update it.

For me it worked very well. My nVidia Geforce 8600GT is working super with compiz!

I wish you a lot of success!

Greetings

---

