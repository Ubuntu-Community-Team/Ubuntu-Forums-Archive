---
title: "Fatal server error: no screens found"
date: 2007-03-08
forum: Desktop Environments
---

### Post by chipdip on 2007-03-08
During the last kernel update, my X -Server stopped running. I had no problem using it without X, as it is only a server. I do have some needs for it sometimes, so I would like to know how I can recover from this error. I am using a Dell B110, not sure of the chipset, but its connected to a generic 17" LCD.

chipdip@ChipServ:~$ sudo startx

xauth:  creating new authority file /home/chipdip/.serverauth.5459
X: unable to open wrapper config file /etc/X11/Xwrapper.config


X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686
Current Operating System: Linux ChipServ 2.6.17-11-generic #2 SMP Thu Feb 1 19:52:28 UTC 2007 i686
Build Date: 07 July 2006
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Mar  8 08:26:23 2007
(==) Using config file: "/etc/X11/xorg.conf"
Data incomplete in file /etc/X11/xorg.conf
        Undefined InputDevice "stylus" referenced by ServerLayout "Default Layout".
(EE) Problem parsing the config file
(EE) Error parsing the config file

Fatal server error:
no screens found
XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"
      after 0 requests (0 known processed) with 0 events remaining.
chipdip@ChipServ:~$

My /etc/X11/xorg.conf is as follows:


Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        FontPath        "/usr/share/fonts/X11/misc"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
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

Section "Device"
        Identifier      "Onboard Video Card"
        Driver          "vga"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-70
        VertRefresh     50-160
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Onboard Video Card"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
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
EndSection

Section "DRI"
        Mode    0666
EndSection

---

### Post by aa.ivanov on 2007-03-08
I have no idea what the answer to your question is. I would investigate the /etc/X11/Xwrapper.config file, since I see this in your output
> X: unable to open wrapper config file /etc/X11/Xwrapper.config

As far as I see this file determines who can use the X server. It must have been generated by a post-install script of x11-common. so dpkg-reconfigure should be able fix an issue with it.

But I've started writing mainly 'cause I was surprised by the 'sudo startx'. Why? I have always used startx as an ordinary user.

---

### Post by taurus on 2007-03-08
Reconfigure your X again with

```
sudo dpkg-reconfigure -phigh xserver-xorg
```
p.s.  You shouldn't have to use "sudo" when you want to get into X.

```
startx
```

---

### Post by chipdip on 2007-03-08
I just did sudo dpkg-reconfigure -phigh xserver-xorg and I am sure there is a problem with permissions, I type startx and get:
```

chipdip@ChipServ:~$ startx
xauth:  creating new authority file /home/chipdip/.serverauth.5808
xauth:  error in locking authority file /home/chipdip/.Xauthority
xauth:  error in locking authority file /home/chipdip/.Xauthority
xauth:  error in locking authority file /home/chipdip/.Xauthority
xauth:  error in locking authority file /home/chipdip/.Xauthority
X: unable to open wrapper config file /etc/X11/Xwrapper.config
X: user not authorized to run the X server, aborting.
xinit:  Server error.
xauth:  error in locking authority file /home/chipdip/.Xauthority
Couldnt get a file descriptor referring to the console
```
The file /etc/X11/Xwrapper.config does not exist, and /home/chipdip/.Xauthority is empty.

---

### Post by aa.ivanov on 2007-03-09
Standard Xwrapper.config should give any local user rights to start X. As far as I see X is parsing that file and based on the settings there is rejecting user chipdip. Man page for Xwrapper.config should come handy ([http://lyre.mit.edu/cgi-bin/man/man2html?Xwrapper.config+5]("http://lyre.mit.edu/cgi-bin/man/man2html?Xwrapper.config+5")). Normal setting for allowed_users is 'console'. If it's not working and if the 'anybody' setting is not working too... well... than I must be wrong and the issue should be somewhere else on the system.
In either case keep me informed.

/edit:
Thinking it over, I think I'll add a couple more things to this post:
1. permissions for  /etc/X11/Xwrapper.config 
```
$ ls -l /etc/X11/Xwrapper.config 
-rw------- 1 root root 614 2006-12-26 11:19 /etc/X11/Xwrapper.config

```
2. permissions for /usr/bin/X
```

$ ls -l `which X`
-rwsr-sr-x 1 root root 17880 2006-12-07 07:59 /usr/bin/X

```

---

### Post by aa.ivanov on 2007-03-10
Oh!

And check the permissions of /home/chipdip/.Xauthority
```
$ ls -l .Xauthority 
-rw------- 1 andrew andrew 116 2007-03-10 09:53 .Xauthority

```

'sudo startx' might have changed the owner to root. I've had similar issues when trying to run GUI programs with sudo.... Helped me learn the lesson that all GUI stuff should use gksudo :)

---

### Post by confusador on 2007-08-09
I just want to give a quick thank you to Taurus, your post here saved me from having to start a thread!  And it's a scary error, so I was greatly relieved to have fixed it.

---

