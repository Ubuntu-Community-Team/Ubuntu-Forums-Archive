---
title: "can't run applications as root"
date: 2006-12-31
forum: Desktop Environments
---

### Post by toxic-hero on 2006-12-31
a strange problem appeared on my system. i can't run applications (synaptics, adept, kate, krusader...) with root privileges from kde su window anymore. when i enter the correct password, the window dissapear and then nothing happens. if i enter an incorrect password (for a test), i get an incorrect password window.

funny thing is, that i can still act as a root if i work from konsole with sudo command.

i have no idea what could be the reason for this strange behavior and when exactly this started (no more than 14 days ago).

any help appreciated!!!

toxic


my status:
semi-newby
my system:
laptop, HP NX8220
kubuntu edgy

---

### Post by bapoumba on 2006-12-31
What kind of error message do you get running** kdesu kate** for example ? (I am not familiar with KDE, please adapt if not correct). Are you still in admin group ?

---

### Post by toxic-hero on 2006-12-31
running "kdesu kate" i don't get any error message. just a window to enter the password and when i enter it - nothing! 

yes, i am in admin group (always was, just checked to be sure).


thanks for your response & happy new year!

toxic

---

### Post by taurus on 2006-12-31
What's the output of this command?

```
groups
```

---

### Post by toxic-hero on 2006-12-31
the output is:
"myusername" adm dialout cdrom floppy audio dip video plugdev lpadmin scanner admin

---

### Post by taurus on 2006-12-31
What happens when you run this command?

```
sudo nano -w /etc/apt/sources.list
```
Do you see your /etc/apt/sources.list at all?

---

### Post by toxic-hero on 2006-12-31
deb [http://kubuntu.org/packages/amarok-144](http://kubuntu.org/packages/amarok-144) edgy main
deb [http://kubuntu.org/packages/kde-355](http://kubuntu.org/packages/kde-355) edgy main
deb [http://aircrack-ng.le-vert.net/ubuntu](http://aircrack-ng.le-vert.net/ubuntu) branch main
deb [http://kubuntu.org/packages/amarok-143](http://kubuntu.org/packages/amarok-143) edgy main
deb [http://kubuntu.org/packages/amarok-142](http://kubuntu.org/packages/amarok-142) edgy main
deb [http://kubuntu.org/packages/kde-354](http://kubuntu.org/packages/kde-354) edgy main
deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free
deb [http://kubuntu.org/packages/amarok-141](http://kubuntu.org/packages/amarok-141) edgy main

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy universe multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy-backports main restricted unive$
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy-backports main restricted u$

# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy-backports main restricted unive$
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy-backports main restricted u$

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe multiverse
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

#AUTOMATIX REPOS START

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe mu$

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe mult$

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe mul$

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe mul$

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse
#AUTOMATIX REPOS END

---

### Post by taurus on 2006-12-31
Well, seems like sudo is working just fine!!!  What about 

```
kdesu synaptic
```

---

### Post by toxic-hero on 2006-12-31
FIRST:

MYUSERNAME@:~$ kdesu synaptic
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
xauth: (argv):1:  bad display name ":0.0" in "list" command
kdesu (kdelibs): WARNING: No X authentication info set for display :0.0

THAN KDESU WINDOW APPEAR AND I ENTER MY PASSWORD.
THEN:

xauth: (argv):1:  bad display name ":0.0" in "list" command
kdesu (kdelibs): WARNING: No X authentication info set for display :0.0
xauth: (argv):1:  bad display name ":0.0" in "list" command
kdesu (kdelibs): WARNING: No X authentication info set for display :0.0
Xlib: connection to ":0.0" refused by server
Xlib:
No protocol specified


(synaptic:15738): Gtk-WARNING **: cannot open display:
MYUSERNAME@:~$

---

### Post by bapoumba on 2006-12-31
```
ls -la .X*
-rw------- 1 isabella isabella 119 2006-12-31 11:09 .Xauthority
```

Your user should own .Xauthority.

If this is not the case, logout from your session. When on KDM login screen > CTRL+ALT+F1 > login in tty > rename the .Xauthority file :
```
~$ mv .Xauthority .Xauthority.bak
```

> CTRL+ALT+F7 will bring you back to KDM. A new .Xauthority will be created when login into KDM.

If this is the problem, you should be fine.
Happy New Year to you too ;)

---

### Post by toxic-hero on 2006-12-31
i guess this is not the case.

MYUSERNAME@:~$ ls -la .X*
-rw------- 1 MYUSERNAME MYUSERNAME 314 2006-12-31 17:33 .Xauthority

thanks anyway.

t

toxic

---

### Post by bapoumba on 2006-12-31
Okay, guess I should have searched the web before ;)

This is due to wacom devices in /etc/X11/xorg.conf. Backup your file and comment out all the wacom thing :
```
#Section "InputDevice"

# /dev/input/event
# for USB
    #Identifier     "stylus"
    #Driver         "wacom"
    #Option         "Device" "/dev/wacom"          # Change to 
    #Option         "Type" "stylus"
    #Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
#EndSection

#Section "InputDevice"

# /dev/input/event
# for USB
    #Identifier     "eraser"
    #Driver         "wacom"
    #Option         "Device" "/dev/wacom"          # Change to 
    #Option         "Type" "eraser"
    #Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
#EndSection

#Section "InputDevice"

# /dev/input/event
# for USB
    #Identifier     "cursor"
    #Driver         "wacom"
    #Option         "Device" "/dev/wacom"          # Change to 
    #Option         "Type" "cursor"
    #Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
#EndSection
```

Save the file, log out and log back in. Hope this one is the good one ;)

---

### Post by toxic-hero on 2007-01-01
hm. i'm not quite sure if i understood correctly what to do.

this is the contents of the file that you mentioned:

```

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "si"
        Option          "XkbOptions"    "lv3:ralt_switch"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY

  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "ATI Technologies, Inc. M24 1P [Radeon Mobility X600]"
        Driver          "ati"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-84
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. M24 1P [Radeon Mobility X600]"

        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. M24 1P [Radeon Mobility X600]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1680x1050"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1680x1050"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1680x1050"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1680x1050"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1680x1050"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1680x1050"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection

        InputDevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection
```



what should i do with it? editing it; is it possible to destroy something?


thanks!

toxic

---

### Post by bapoumba on 2007-01-01
Hello :)

I've posted the relevant part of xorg.conf, with the wacom entries in the inputdevice section.

Backup your file : **sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak** or any other name that suits you. You'll be able to restore it ;)

Then edit the file, you'll need to be root : **sudo nano /etc/X11/xorg.conf**. nano is a text editor working from a terminal (so no root mode in graphic session). Comment all the wacom entries, adding a **#** at the beginning of the lines. These lines wont be taken into account anymore (if you do have a graphic tablet and use the wacom thing, then I do not know what to recommend). CTRL +O to save the file (same name), then CTRL+X to exit.

Resart your xserver : CTRL+ALT+backspace. Cheers :)

---

### Post by toxic-hero on 2007-01-01
unfortunately this didn't help. i did exactly what you've said but xorg couldn't be restarted after i edit the file. so i rebooted my machine and it started in command line mode.

any other idea?

thank you for your time and patience!!!

toxic

---

### Post by bapoumba on 2007-01-01
Well, I'm out of ideas :/
Really sorry. I'll post if I come across something interesting.

---

### Post by L_V on 2007-04-02
I agree that these Kdesu and unreliable sudo problems are real nigthmare.

Also have a message like "**su return with an error**" when trying to open Adept, before being able to give any password, and this with a fresh Dapper net-installation.

Although I have a correct root and user account perfectly working in terminal mode, impossible to understand why user/password is so weird in X mode.

I think the installation process should be much clearier about YES or NO, do you want a root access to offer two possibilities:

1. normal linux behavior with root and users access;
2. no root access (default ubuntu).

And then, correctly match user/passwords in X environement with KDE or gnome.
Much too complex to workaround these problems / never found clear answers.

---

