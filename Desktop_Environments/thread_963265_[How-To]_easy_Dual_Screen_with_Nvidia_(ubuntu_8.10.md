---
title: "[How-To] easy Dual Screen with Nvidia (ubuntu 8.10)"
date: 2008-10-30
forum: Desktop Environments
---

### Post by mike16889 on 2008-10-30
[PDF Version]("http://flashplace.net/dualscreen.pdf")

[CENTER][SIZE="5"]Configure Dual Screen on 
Ubuntu 8.10
Nvidia graphics[/SIZE]

[SIZE="4"]By Michael Richards[/SIZE][/CENTER]

in this tutorial I'll teach you how to enable dual-screen  in Ubuntu 8.10 (I'm using the release candidate but should be same when 8.10 is officially released).

First you will want to make sure you are running the right drivers for the video card. To do this click “System > Administration > Hardware Drivers” (as in fig: 1)

[CENTER][[IMG]http://img258.imageshack.us/img258/8443/gettohardwaredriversms9.th.png[/IMG]](http://img258.imageshack.us/my.php?image=gettohardwaredriversms9.png)[/CENTER]

you should be faced with a window looking like this (fig:2)

[CENTER][[IMG]http://img258.imageshack.us/img258/5700/screenshothardwaredrivene6.th.png[/IMG]](http://img258.imageshack.us/my.php?image=screenshothardwaredrivene6.png)[/CENTER]

selecting the recommended Nvidia Driver should do the trick. Make sure you activate it and then you will need to restart your computer or X for the changes to take effect. Its your choice. Restarting X is easyer and faster but sometimes X fails to reload and will require you to do a hard reboot.

To restart X save all documents as if you are going to restart the PC and then press: “Crtl + Alt + Backspace”

once you log back in everything should seem as it did before. The second screen may be black instead of a clone of the first but thats normal.

Next you will want to install the “Nvidia X Server Settings” from the package manager.

First you will need to enable all avalible applications in the package manager to do this open it and click the “Show” dropdown at the top of the window. (fig: 3)

[CENTER][[IMG]http://img185.imageshack.us/img185/2920/enableallavalibleappliczn7.th.png[/IMG]](http://img185.imageshack.us/my.php?image=enableallavalibleappliczn7.png)[/CENTER]

once you have selected “All available applications” the package manager will update and you will then be able to search for “nvidia” in the search box.

When the search result show up you will be able to select “NVIDIA X Server Settings” (the one below the one hi-lighted in Fig: 4)

[CENTER][[IMG]http://img265.imageshack.us/img265/6277/nvidiaxserverfl7.th.png[/IMG]](http://img265.imageshack.us/my.php?image=nvidiaxserverfl7.png)[/CENTER]

Check the box next to it a and click “Apply Changes”.

Once that is installed, you can then open a terminal Window and type “sudo nvidia-settings” (fig: 5)

[CENTER][[IMG]http://img300.imageshack.us/img300/8294/luanchnvidiasettingsfn0.th.png[/IMG]](http://img300.imageshack.us/my.php?image=luanchnvidiasettingsfn0.png)[/CENTER]

a window will launch and it will you will need to chose “X Server Display Configuration” (Fig: 6)

[CENTER][[IMG]http://img171.imageshack.us/img171/6620/selectxsertverconfigbb6.th.png[/IMG]](http://img171.imageshack.us/my.php?image=selectxsertverconfigbb6.png)[/CENTER]

Then Select “Enable Xinerama” and then select the disabled screen and click “Configure...” and you will be faced with a window as follows (Fig: 7)

[CENTER][[IMG]http://img522.imageshack.us/img522/8517/configuredisplaydeviceyi4.th.png[/IMG]](http://img522.imageshack.us/my.php?image=configuredisplaydeviceyi4.png)[/CENTER]

Select “Separate X screen” and click “OK”.

You will be taken back to the main window and you will then need to click “Save to X Configuration File”.

A window will popup like (Fig: 8 )

[CENTER][[IMG]http://img522.imageshack.us/img522/5159/confirmsavesr6.th.png[/IMG]](http://img522.imageshack.us/my.php?image=confirmsavesr6.png)[/CENTER]

Click Save and then close all windows.

If all went well you are ready to restart. Again you can ether do a full reboot or just restart X.

Then when you load back up you should have dual screen.



[CENTER][SIZE="6"]The End[/SIZE][/CENTER]


if your having trouble with video on a TV screen see Temis' second post.

---

### Post by Temis on 2008-11-03
Thank you for the instruction which I followed to the letter, but on the second monitor (TV) I get the sound and the wallpaper, videos do not show up. My graphics card is eGEFORCE FX 5500. Do I have to tweak something
in x config?

---

### Post by mike16889 on 2008-11-03
not sure. you may want to disable "Xinerama&#8221; for that etup see if that works. i'v never actualy set a tv up as a second screen. let me know how u go.

also when setting it up without "Xinerama" you may need to setup the following script to get menu's working properly

[QUOTE=mike16889]some ppl are having problems with menu's and things on one monitor being slow heres the fix:

somewere make a file called 'whatever.sh' and place in it:

#!/bin/bash
# start compiz
DISPLAY=:0.0 compiz --only-current-screen --replace &
disown $!
sleep 3
DISPLAY=:0.1 compiz --only-current-screen --replace &
disown $!

save it and set the permissions so anyone can edit/run it and allow it to run as a program.
then go into 'System > Preferances > Sessions" and create a new one. call it somthing and then link to the file you made.

finnaly restart X by hitting 'Ctrl + Alt + Backspace' BEWARE restarting X is like Restarting the whole system but faster. save all work and bookmark all webpages that you want to go back to.[/QUOTE]

---

### Post by Temis on 2008-11-04
I found the solution here:

[http://globalsyzygy.wordpress.com/2007/12/31/how-to-set-up-dual-screens-twin-view-on-ubuntulinux/](http://globalsyzygy.wordpress.com/2007/12/31/how-to-set-up-dual-screens-twin-view-on-ubuntulinux/)

Inserted this;

Open up your xorg.conf file:
sudo gedit /etc/X11/xorg.conf
Navigate to the video card section of the file, it should start as:
Section “Device”
Identifier “nVidia [Model Name Here]“
Driver “nvidia”
At the bottom of this section, before the “Endsection” line, add the following:
# TwinView Options:
Option “TwinView” “True”
Option “TwinViewOrientation” “Clone”
#”Clone” for two identical screens, “LeftOf” or “RightOf” for one long,
# fused screen.
Option “UseEdidFreqs” “True”
Option “MetaModes” “1280×1024,1280×1024; 1024×768,1024×768&#8243;
Option “UseDisplayDevice” “CRT, TV”
# End of TwinView Options

Restart X:
Hit “CTR+ALT+BACKSPACE” or restart your computer and you should be all set!

The video showed up on the TV. But when I rebooted the PC went into safe mode and there was something about  going into low resolution.
Unfortunately I do understand what all these lines mean.Probably something has to be edited.
I did not try the script you suggested. I do not use compiz and uninstalled it.
Thank you.
Cannot find PDF

---

### Post by mike16889 on 2008-11-05
sorry did'nt take much notice when i was uploading the pdf. it was to big so i uploaded it on my website the link to the file is at the top of the post.

---

### Post by Temis on 2008-11-05
Mike, thank you. Can I ask you for a favor and have a look at the xorg.conf
which has the addtion I mentioned in the previous post.The addittion is between tripel parentheses under device 0. I did  remove this addtion althuogh it did work
and I had video on the TV. However the boot up was all messed up and I removed it. Now there is no video only sound.

# nvidia-settings: X configuration file generated by nvidia-settings 
# nvidia-settings:  version 1.0  (buildd@palmer)  Mon Nov  3 08:46:46 UTC 2008 

Section "ServerLayout" 
    Identifier     "Layout0" 
    Screen      0  "Screen0" 0 0 
    Screen      1  "Screen1" RightOf "Screen0" 
    InputDevice    "Keyboard0" "CoreKeyboard" 
    InputDevice    "Mouse0" "CorePointer" 
EndSection 

Section "Files" 
EndSection 

Section "Module" 
    Load           "dbe" 
    Load           "extmod" 
    Load           "type1" 
    Load           "freetype" 
    Load           "glx" 
EndSection 

Section "ServerFlags" 
    Option         "Xinerama" "0" 
EndSection 

Section "InputDevice" 
    # generated from default 
    Identifier     "Mouse0" 
    Driver         "mouse" 
    Option         "Protocol" "auto" 
    Option         "Device" "/dev/psaux" 
    Option         "Emulate3Buttons" "no" 
    Option         "ZAxisMapping" "4 5" 
EndSection 

Section "InputDevice" 
    # generated from default 
    Identifier     "Keyboard0" 
    Driver         "kbd" 
EndSection 

Section "Monitor" 
    # HorizSync source: edid, VertRefresh source: edid 
    Identifier     "Monitor0" 
    VendorName     "Unknown" 
    ModelName      "DELL P780" 
    HorizSync       30.0 - 85.0 
    VertRefresh     48.0 - 120.0 
    Option         "DPMS" 
EndSection 

Section "Monitor" 
    # HorizSync source: xconfig, VertRefresh source: xconfig 
    Identifier     "Monitor1" 
    VendorName     "Unknown" 
    ModelName      "TV-0" 
    HorizSync       28.0 - 33.0 
    VertRefresh     43.0 - 72.0 
    Option         "DPMS" 
EndSection 

Section "Device" 
    Identifier     "Device0" 
    Driver         "nvidia" 
    VendorName     "NVIDIA Corporation" 
    BoardName      "GeForce FX 5500" 
    BusID          "PCI:1:0:0" 
    Screen          0 
    Option         "NoLogo" 
    ((( # TwinView Options: 
    Option “TwinView” “True” 
    Option “TwinViewOrientation” “Clone” 
    #”Clone” for two identical screens, “LeftOf” or “RightOf” for one long, 
    # fused screen. 
    Option “UseEdidFreqs” “True” 
    Option “MetaModes” “1280×1024,1280×1024; 1024×768,1024×768&#8243; 
    Option “UseDisplayDevice” “CRT, TV” 
    # End of TwinView Options )))
    EndSection 

Section "Device" 
    Identifier     "Device1" 
    Driver         "nvidia" 
    VendorName     "NVIDIA Corporation" 
    BoardName      "GeForce FX 5500" 
    BusID          "PCI:1:0:0" 
    Screen          1 
EndSection 

Section "Screen" 
    Identifier     "Screen0" 
    Device         "Device0" 
    Monitor        "Monitor0" 
    DefaultDepth    24 
    Option         "TwinView" "0" 
    Option         "TwinViewXineramaInfoOrder" "CRT-0" 
    Option         "metamodes" "CRT: nvidia-auto-select +0+0; CRT: 1024x768_85 +0+0" 
    SubSection     "Display" 
        Depth       24 
    EndSubSection 
EndSection 

Section "Screen" 
    Identifier     "Screen1" 
    Device         "Device1" 
    Monitor        "Monitor1" 
    DefaultDepth    24 
    Option         "TwinView" "0" 
    Option         "metamodes" "TV: nvidia-auto-select +0+0" 
    SubSection     "Display" 
        Depth       24 
    EndSubSection 
EndSection

---

### Post by mike16889 on 2008-11-06
i don't  realy know much about setting it up i only have about 2 months exptriance with linux. but to me the res looks to high for a crt tv. sorry i cant help that much. what interface is the tv connected to? s-video?

---

### Post by Temis on 2008-11-07
Thank you  again Mike, the TV has s-video connection. But as I mentioned before I do get the video after I added the lines in parentheses, but on
boot up the computer goes in safe mode first and the goes in low resolution.
I will add 80x600 resolution and see what happens.Probably the computer will crash.
Resolution shoul read 800x600

---

### Post by SilverOne on 2008-11-10
i have followed the steps in this guide, and when i click "save to X configuration file" it just closes the window... nothing else, and when i open again "sudo nvidia-settings the settings are the same has the old 1 , any ideas ?

---

### Post by SilverOne on 2008-11-10
> **Temis said:**
> I found the solution here:

[http://globalsyzygy.wordpress.com/2007/12/31/how-to-set-up-dual-screens-twin-view-on-ubuntulinux/](http://globalsyzygy.wordpress.com/2007/12/31/how-to-set-up-dual-screens-twin-view-on-ubuntulinux/)

Inserted this;

Open up your xorg.conf file:
sudo gedit /etc/X11/xorg.conf
Navigate to the video card section of the file, it should start as:
Section “Device”
Identifier “nVidia [Model Name Here]“
Driver “nvidia”
At the bottom of this section, before the “Endsection” line, add the following:
# TwinView Options:
Option “TwinView” “True”
Option “TwinViewOrientation” “Clone”
#”Clone” for two identical screens, “LeftOf” or “RightOf” for one long,
# fused screen.
Option “UseEdidFreqs” “True”
Option “MetaModes” “1280×1024,1280×1024; 1024×768,1024×768&#8243;
Option “UseDisplayDevice” “CRT, TV”
# End of TwinView Options

Restart X:
Hit “CTR+ALT+BACKSPACE” or restart your computer and you should be all set!

The video showed up on the TV. But when I rebooted the PC went into safe mode and there was something about  going into low resolution.
Unfortunately I do understand what all these lines mean.Probably something has to be edited.
I did not try the script you suggested. I do not use compiz and uninstalled it.
Thank you.
Cannot find PDF

problem solved by doing the steps above. ty.

---

### Post by mike16889 on 2008-11-10
be sure to thank temis then. sorry my tutorial didn't work for you. not rly sure why it didn't thow, what type of setup is it? eg. screens, mobo, gcard?

---

### Post by SilverOne on 2008-11-18
hehe i forgot.. ther u go :popcorn:

---

### Post by Temis on 2008-11-20
Hi mike16889 and SilverOne. I tried again my suggested procedure but no luck.I get this message after start up

"Ubuntu is running in low-graphics mode.
The following error was encountered. You may need to update your 
configuration to solve this.
Problem parsing the config file.
Error parsing the config file."

I have no clue how to get about it. I do get the Video on the TV after the 
PC boots up in lower graphics mode. It is just annoying to start all over
again.

---

### Post by mike16889 on 2008-11-21
sorry, i have no idea why this is happening, maybe you should open a thread asking for help? someone is sure to know.

---

### Post by Temis on 2008-11-21
Thanks mike 16889. Its no big deal, I might try another thread as you suggested.

---

