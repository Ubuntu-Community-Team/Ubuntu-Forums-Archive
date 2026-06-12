---
title: "XGL Problems"
date: 2006-07-03
forum: Desktop Environments
---

### Post by Loomy on 2006-07-03
Alright I have been having difficulties getting XGL to work.  I am following this guide:
[http://ubuntuforums.org/showthread.php?t=131267&highlight=xgl+nvida]("http://ubuntuforums.org/showthread.php?t=131267&highlight=xgl+nvida")

In the second step it says to:
> Find the &#8220;Module&#8221; section. Comment out the &#8220;Glcore&#8221; and &#8220;dri &#8220; modules and make sure a &#8220;glx&#8221; module is there.

But look at my Module section in my Xorg file:
> Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"

Could this be my issue, if not does anyone have any suggestions?

---

### Post by jvictor on 2006-07-04
It looks ok to me , even I didnt have GLCore in my xorg.conf; 

What is the problem u r facing ?

Edit 

I used this guide on a fresh install of dapper and it worked fine


[http://ubuntuguide.org/wiki/Dapper#How_to_install_Xgl.2FCompiz_.28Nvidia.29](http://ubuntuguide.org/wiki/Dapper#How_to_install_Xgl.2FCompiz_.28Nvidia.29)

---

### Post by Loomy on 2006-07-04
> **jvictor]It looks ok to me , even I didnt have GLCore in my xorg.conf said:**
> http://ubuntuguide.org/wiki/Dapper#How_to_install_Xgl.2FCompiz_.28Nvidia.29[/url]

Alright I am trying the same guide also then.

I will post my errors here:

Okay I get all the way to where I actually have to run "thefuture" and when I try to run it this happens.

> brian@Brians:~$ sudo chmod 755 /usr/bin/thefuture
brian@Brians:~$ thefuture
gnome-window-decorator, Failed to load shadow images
brian@Brians:~$ compiz.real: No composite extension


---

### Post by Loomy on 2006-07-04
Now when I restarted my computer upon startup I get some "Xserver error".  This is the third time this has happened and every other time I just reinstalled Ubuntu.  Is there an easier fix.  Help me please!! :cry:

---

### Post by jvictor on 2006-07-04
Ok can u give the following info and try out te following commands ?

Have u enabled the universe and multiverse repositories ?

Have u installed all the prerequsites ? If not use this command

```
sudo apt-get install compiz xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 compiz-gnome

```

First whats ur GFX card ?

Are u using the properietary drivers or GPL drivers ?

After u login can u type the following command in a terminal and give its o/p

```
ps -el | grep Xgl
```


Does ur Device section look like this ?
```

Section "Device"
        Identifier      "NVIDIA Corporation NV34 [GeForce FX 5200]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Option          "NoLogo" "true"
        Option          "RenderAccel"           "true"
        Option          "AllowGLXWithComposite" "true"
EndSection
```

Can u add this to the end of /etc/X11/xorg.conf file ?
```

Section "Extensions"
        Option  "Composite" "Enable"
EndSection
```

Edit:
For ref 'thefuture' script looks like this for me 

```

gnome-window-decorator &  compiz --replace gconf decoration wobbly fade minimize
 cube rotate zoom scale move resize place switcher &
xmodmap /usr/share/xmodmap/xmodmap.us
```

Can u tell us what the X error log contains ? I mean not the entire thing, but as much relevant info as possible

---

### Post by Loomy on 2006-07-04
[QUOTE=jvictor]Ok can u give the following info and try out te following commands ?

Have u enabled the universe and multiverse repositories ?

Have u installed all the prerequsites ? If not use this command

```
sudo apt-get install compiz xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 compiz-gnome

```

First whats ur GFX card ?

Are u using the properietary drivers or GPL drivers ?

After u login can u type the following command in a terminal and give its o/p

```
ps -el | grep Xgl
```


Does ur Device section look like this ?
```

Section "Device"
        Identifier      "NVIDIA Corporation NV34 [GeForce FX 5200]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Option          "NoLogo" "true"
        Option          "RenderAccel"           "true"
        Option          "AllowGLXWithComposite" "true"
EndSection
```

Can u add this to the end of /etc/X11/xorg.conf file ?
```

Section "Extensions"
        Option  "Composite" "Enable"
EndSection
```

Edit:
For ref 'thefuture' script looks like this for me 

```

gnome-window-decorator &  compiz --replace gconf decoration wobbly fade minimize
 cube rotate zoom scale move resize place switcher &
xmodmap /usr/share/xmodmap/xmodmap.us
```

Can u tell us what the X error log contains ? I mean not the entire thing, but as much relevant info as possible[/QUOTE]
Heres the error it gives me when it trys to start Ubuntu:

> Couldn't open RGB_DB '/usr/share/X11/rgb

---

### Post by Loomy on 2006-07-04
Well I think I may have found a solution, but I'm not certain.  I found this thread:
[]("http://ubuntuforums.org/showthread.php?t=194375")

From the thread:

> The answer is that XGL makes GDM take longer to boot. Therefore it was a timeout that was causing my GDM session to crash. The rgb_db error is still there but it is not in fact the cause of the crash. It is also possible that the error was a result of the GDM consistently crashing in the middle of opening the file, but I'm not sure on that one. In order to stop the crash update the following value in /etc/X11/gdm/gdm.conf

The question is how can I edit that file if I can't get Ubuntu to boot?

---

### Post by jvictor on 2006-07-04
Loomy, again can u tell us what is the nature of the problem ? Just telling I get an error and one line error may not help always

Can u give point to point answers to the question I posted ? If the thread suggestion doesnt work?

Also we have no clue abt ur hardware , which is v imp.


Ubuntu booting is a different question here, Its just that X is not working.. X is just a service that runs on Ubuntu

U can edit a file by typing CTL+ALT+F1, logging in into ur shell and edit it using the vi or nano editor.

nano will be easier for new users

---

### Post by Loomy on 2006-07-04
> Have u enabled the universe and multiverse repositories ?
Yes

> Have u installed all the prerequsites ?
Yes

> First whats ur GFX card ?
XFX Nvidia 7800 GTX

> Are u using the properietary drivers or GPL drivers ?
I think GPL not sure what that means though?

> After u login can u type the following command in a terminal and give its o/p

Couldn't get to work what is that dividing character in the middle?

> Does ur Device section look like this ?
I followed the guide step by step so it should, but I don't know how to open files now that X doesn't load. (once again I am very new)

> Can u tell us what the X error log contains ? I mean not the entire thing, but as much relevant info as possible
> Can u add this to the end of /etc/X11/xorg.conf file ?
I don't know how.. :oops:

---

### Post by RawMustard on 2006-07-04
He seems to be running the factory drivers from another post of his, but I think he's got his xorg.conf file not right.  Loomy, please post your xorg.conf file found in /etc/X11 so we can see how you've set it up!

---

### Post by Loomy on 2006-07-04
[QUOTE=RawMustard]He seems to be running the factory drivers from another post of his, but I think he's got his xorg.conf file not right.  Loomy, please post your xorg.conf file found in /etc/X11 so we can see how you've set it up![/QUOTE]
Is there like a safe mode type thing I can boot into to get this?

---

### Post by jvictor on 2006-07-04
Unlike windows the GUI is not Linux, Windows lives on the GUI whereas Linux doesnt. The GUI for Linux is XServer , which is just a process that provides windowing capabilities to your application.

On that base , what we are doing here is a trying to use another layer on top of Xserver that uses hardware capabilites to do some cool animations in the GUI.

To be honest I tried it and and switched bac to the good 'ol X after 2-3 days, but since it has picked ur interest lets go ahead.



Now since X server doesnt start u r getting thrown to a shell (black and white) with a notice ..


it may look something like this 

<machineName> login :
here u need type ur username and press enter

provide ur password (it wont be displayed when u type) and press enter

now u will be logged in to a shell (Shell is a commd interface to the machine)


We would like to have a look at ur xorg.conf file first

If u have a USB thumbdrive, u can plug it in after u log in and copy the file using the command

cp /etc/X11/xorg.conf /media/FLASHDRIVE/

and then boot into win and post it here

If u get an error FLASHDRIVE is not present use the command

**mount /dev/sda1 /media/FLASHDRIVE**

---

### Post by jvictor on 2006-07-04
Is there like a safe mode type thing I can boot into to get this?

Did u try the recovery mode in the boot ? I'm not sure of it .. coz i manually edit the files..

---

### Post by Loomy on 2006-07-04
[QUOTE=jvictor]Unlike windows the GUI is not Linux, Windows lives on the GUI whereas Linux doesnt. The GUI for Linux is XServer , which is just a process that provides windowing capabilities to your application.

On that base , what we are doing here is a trying to use another layer on top of Xserver that uses hardware capabilites to do some cool animations in the GUI.

To be honest I tried it and and switched bac to the good 'ol X after 2-3 days, but since it has picked ur interest lets go ahead.



Now since X server doesnt start u r getting thrown to a shell (black and white) with a notice ..


it may look something like this 

<machineName> login :
here u need type ur username and press enter

provide ur password (it wont be displayed when u type) and press enter

now u will be logged in to a shell (Shell is a commd interface to the machine)


We would like to have a look at ur xorg.conf file first

If u have a USB thumbdrive, u can plug it in after u log in and copy the file using the command

cp /etc/X11/xorg.conf /media/FLASHDRIVE/

and then boot into win and post it here

If u get an error FLASHDRIVE is not present use the command

**mount /dev/sda1 /media/FLASHDRIVE**[/QUOTE]
My flashdrive must be incompatable.  Trying the first command it says "no such directory".  Trying the second command as a fix it says "mount point /media/FLASHDRIVE does not exist"

Any other way I can get you this file?

---

### Post by jvictor on 2006-07-04
no its not that :)

login and follow these commands in bold

[B]
sudo mkdir /media/flash
password <give_ur_pwd>[/B]

plugin ur flashdrive

**mount /dev/sda1 /media/flash**

**cp /etc/X11/xorg.conf /media/flash**

after the copy is done unmount the drive using

**umount /media/flash**

remove ur flash drive

then issue this command

**sudo rmdir /media/flash**


reboot into win and paste the files contents,


Im waiting , so I hope u will do this now. Its pretty late nite here ;)

---

### Post by Loomy on 2006-07-04
[QUOTE=jvictor]no its not that :)

login and follow these commands in bold

[B]
sudo mkdir /media/flash
password <give_ur_pwd>[/B]

plugin ur flashdrive

**mount /dev/sda1 /media/flash**

**cp /etc/X11/xorg.conf /media/flash**

after the copy is done unmount the drive using

**umount /media/flash**

remove ur flash drive

then issue this command

**sudo rmdir /media/flash**


reboot into win and paste the files contents,


Im waiting , so I hope u will do this now. Its pretty late nite here ;)[/QUOTE]
Alright I will go try this right now one minute.

---

### Post by Loomy on 2006-07-04
Ugh new error, but I'm getting closer I think.

> Can not create regular file '/media/flash': Permission Denied

---

### Post by jvictor on 2006-07-04
Are u in the shell after the X failed or r u in the recovery mode shell ?

---

### Post by Loomy on 2006-07-04
[QUOTE=jvictor]Are u in the shell after the X failed or r u in the recovery mode shell ?[/QUOTE]
I think I'm in shell, Im new lol is there a way to tell?

---

### Post by jvictor on 2006-07-04
:) :) 

Ok can u IM me now ? at jubygetsmail yahoo ? i think thats faster :)

---

### Post by Loomy on 2006-07-04
You don't happen to have an aim or gmail account do you?

---

### Post by Loomy on 2006-07-04
okay here it is
> # nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Mon May 15 13:23:42 PDT 2006

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
    BusID          "PCI:1:0:0"
    Option         "RenderAccel"	   "true"
    Option	   "AllowGLXWithComposite" "true"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
EndSection



---

### Post by RawMustard on 2006-07-04
loomy, can you give me the output of this command?

nvidia-xconfig --query-gpu-info

---

### Post by Loomy on 2006-07-05
Problem Fixed!!

I will post how later I don't remember what exactly all I did. :eek:

---

