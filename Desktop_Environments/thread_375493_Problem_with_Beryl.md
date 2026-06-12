---
title: "Problem with Beryl"
date: 2007-03-03
forum: Desktop Environments
---

### Post by afham07 on 2007-03-03
Hi guys,

I just install beryl and facing a problem which is no title bar (no close, minimize/maximize). I followed instruction here: 
> 
 How to install Beryl/AIGLX (Nvidia)

(From Ubuntu Forums)

    * Read #General Notes
    * Read #How to add extra repositories
    * Read #How to install Beta Graphics Driver (NVIDIA) 


    * Ensure all packages up to date 

Install your *ubuntu-desktop metapackage specific to your DE, e.g. sudo apt-get install ubuntu-desktop
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

    * Add repositories 

gksudo gedit /etc/apt/sources.list

    * Add the following line at the end of this file (x86 and amd64): 

deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main

    * Add key 

wget [http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg](http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg) -O- | sudo apt-key add -

    * Save the edited file then update package lists 

sudo apt-get update

    * Install Beryl 

sudo apt-get install beryl emerald-themes

    * Back up xorg.conf 

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
gksudo gedit /etc/X11/xorg.conf

    * Add this to xorg.conf "Screen" section 

# Enable 32-bit ARGB GLX Visuals
    Option "AddARGBGLXVisuals" "True"

# If you are using an older version of compiz that
# does not support rendering into the Composite
# Overlay Window, you will need to disable clipping
# of GLX rendering to the X Root window with this
# option, or you will get a blank screen after
# starting compiz:
    Option "DisableGLXRootClipping" "True"

    * Add this to xorg.conf "Device" section 

Option          "TripleBuffer" "true"

    * Restart X with ctrl+alt+backspace 

    * Start Beryl (if it doesn't start on its own) 

beryl-manager

    * Start Emerald (if it doesn't start on its own) 

emerald --replace

    * Have Beryl and Emerald load on login
          o System -> Preferences -> Sessions
          o Startup Programs -> Add 

beryl-manager

and

emerald --replace

    *
          o If, on reboot, program menus aren't displaying in the correct layer (you can't see them when you select them because they are displaying behind the window) then right click on the 'Beryl Manager' icon in the panel (the red gem icon) and select 'Reload Window Manager'. The problem should be solved the next time you reboot. 

    * Some users have found that the latest beryl packages are not working properly, and beryl fails to load. This can be fixed by: 

Open synaptic package manager, search for beryl, press ctrl+e and select version 0.1.99.2 You have to do this for beryl, beryl-core, beryl-manager, beryl-plugins, beryl-plugins-data, beryl-settings, beryl-settings-binding, libberyldecoration0 and libberylsettings0

Source: [http://ubuntuforums.org/showthread.php?t=353809](http://ubuntuforums.org/showthread.php?t=353809)
[edit]



To settle this problem, I also read this thread but it not fix my problem: [http://ubuntuforums.org/showthread.php?t=367850&page=4](http://ubuntuforums.org/showthread.php?t=367850&page=4)

this is my gpu driver:
> NVRM version: NVIDIA UNIX x86 Kernel Module  1.0-9746  Fri Dec 15 09:54:45 PST 2006


for your information, i think, beryl is working but only no tiltle bar. I said that because I can see the cube rotation when switch workspace, there is nice thumbnail when press Alt+Tab.

Please help me guys! ..

---

### Post by ffxr on 2007-03-03
hvae you tried playing with settings in beryl advanced ooptions..? right click on beryl diamond 


this seems to be a common problem , have a look goood search of these forums im sure i seen fixes for this issue a few times whilst i was troubleshooting my own problem.. 

im too tired to too go back and hunt through my history.

good luck.

---

### Post by ffxr on 2007-03-03
some sections from my xorg.conf that might work.. ve got rid of all my BERYL & NVIDIA bugs now..

```
Section "Module"
    Load           "dbe"
    Load           "extmod"
	
	SubSection  "extmod"
      	Option    "omit xfree86-dga"   # don't initialise the DGA extension
    	EndSubSection

    Load           "freetype"
    Load           "glx"
    Load           "type1"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7100 GS"
    Option 	   "RenderAccel" "true"
    Option         "TripleBuffer" "true" ##only use this with lots of video ram
    Option         "AllowGLXWithComposite" "On"
    Option         "Coolbits"    "true"  ## enables you to use AA settings in nvidia-settings 
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "true"

    Subsection "Display"
        Depth       8
        Modes       "1280x1024" "1024x768" "800x600" "640x480"
        ViewPort    0 0
    EndSubsection
    Subsection "Display"
        Depth       16
        Modes       "1280x1024" "1024x768" "800x600" "640x480"
        ViewPort    0 0
    EndSubsection
    Subsection "Display"
        Depth       24
        Modes       "1680x1050" "1280x1024" "1024x768" "800x600"
        ViewPort    0 0
    EndSubsection
   EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection 
```


this is just a sample from xorg.conf btw, u can use it to give you a few ideas.., and backup and know how to restore your own xorg.conf

i also turned off the fading windows & thumbnail viewer in beryl settings.. , i might see if i can enable one of both of these later


theres a couple of things to get you started in your troubleshooting..  i apologise if it turns out to be something really simple.. ve just spent 4 hours ironing out beryl bugs.. your issue was one of them...


ignore my signature btw , its nearly as out of date as my clothes ; )

---

