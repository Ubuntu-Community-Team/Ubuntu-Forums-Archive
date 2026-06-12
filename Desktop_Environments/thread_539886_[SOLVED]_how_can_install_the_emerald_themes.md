---
title: "[SOLVED] how can install the emerald themes"
date: 2007-08-31
forum: Desktop Environments
---

### Post by tropcky on 2007-08-31
hi   
cam plez some body tell me how can install the emerald themes 

thank u

---

### Post by Lord Illidan on 2007-08-31
Which ones? Are you referring to a specific emerald theme?

---

### Post by tropcky on 2007-08-31
i dont knwo i just got a theme from a web site its names like that 65057-Whiteline.emerald
its not tar.gz   so how can install it 
p.s : i am new as hell in linux

---

### Post by Lord Illidan on 2007-08-31
Don't worry about being as new as hell, we were all there once.

Er, did you install Beryl or Compiz, and emerald in the first place? If you did, go to System -> Preferences -> Emerald Theme Manager and use the Import button to select your downloaded theme.

---

### Post by tropcky on 2007-08-31
oky after i did chose it the emerald themer   what i have 2 do i trayed to press enter but nothin happend

---

### Post by tropcky on 2007-09-01
need help here guys

---

### Post by Geekberg on 2007-09-01
Try installing beryl this way, when you finish reboot and you should see a red emerald or ruby in your task bar by the time.  Right click on it and emerald theme manager should be an option.  If it not you can install it from the list in the Synaptic package manager after you complete the install of beryl below. 


Ubuntu 7.04 makes installing beryl/compiz extremely easy , to install beryl type the following command in the terminal window (Application ->Accesories -> Terminal) :-

" sudo aptitude install beryl beryl-manager emerald-themes ¨

After installation is over restart X Server/Computer and launch beryl-manager by going into (Application -> System tools -> Beryl Manager)

If you want to avoid starting beryl-manager manually every time you can make beryl-manager start automatically when gnome starts to do this go to (System->Preferences->Sessions) you will get a window like this
Press New and in windows that appears next in Name type Beryl Manager(or what ever you like) and in command type beryl-manager . Now every time gnome starts Beryl Manager should load automatically.

---

### Post by tropcky on 2007-09-01
thank u man i will tray thes and i gonna post back if i had any proplim

---

### Post by tropcky on 2007-09-01
thank u man really thanks but plez tell me how tp make have thes really great 3d stuff like i sow in youtube 
u know like making the desk top like a boks flaying in a space wow 
u know what i mean

---

### Post by Lord Illidan on 2007-09-01
Er, can you rephrase that again - in English please?

---

### Post by tropcky on 2007-09-01
lol
i meant i wanna do stuff like that [http://www.youtube.com/watch?v=684OLRsTrrs&mode=related&search=](http://www.youtube.com/watch?v=684OLRsTrrs&mode=related&search=)
but i have viga card : ati 128 
so can do it 
and if i can   how can do that
  

about my bad english 
 dude i am from egypt  so thanks god that i am even talken english

---

### Post by Lord Illidan on 2007-09-01
Well, if you put some effort into it, more can help. Can you put lspci into a terminal and post the output here, so we can see what your graphics card is?

---

### Post by tropcky on 2007-09-01
here it is bro 


00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (rev 01)
01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (Secondary) (rev 01)
02:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:0a.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
tropcky@tropcky-linux:~$

---

### Post by Lord Illidan on 2007-09-01
I must warn you, this is not going to be that easy, and you can mess up your system. ATI is not well known for its good Linux drivers.

Try this link below :
[http://ubuntuforums.org/showthread.php?t=488385&highlight=ATI+XGL](http://ubuntuforums.org/showthread.php?t=488385&highlight=ATI+XGL)

Any probs, post in this thread or the other one.

---

### Post by tropcky on 2007-09-01
thank u man 
really thanks if i got any proplim ( i know that i will )  i will post it

---

### Post by tropcky on 2007-09-01
now i cant close or move any window  lol  take alook of that 
[[img]http://www.upload2world.com/pic39/upload2world_bb4f0.png[/img]](http://www.upload2world.com)

---

### Post by Milk &amp; Toast &amp; Honey on 2007-09-01
All right, here I am, answering your *other* thread :), now please post your /etc/X11/xorg.conf file.

Some note, I'm a newbie too, I'll try to help you as best as I can, so don't be too happy all right ? :)

---

### Post by tropcky on 2007-09-01
how can do 
give me the command line

---

### Post by tropcky on 2007-09-01
oky i  got it 

tropcky@tropcky-linux:~$ cat /etc/X11/xorg.conf
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
        FontPath        "/usr/share/fonts/X11/misc"
        FontPath        "/usr/share/fonts/X11/cyrillic"
        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/Type1"
        FontPath        "/usr/share/fonts/X11/100dpi"
        FontPath        "/usr/share/fonts/X11/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "ATI Technologies Inc RV280 [Radeon 9200 SE]"
        Driver          "ati"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "710E"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc RV280 [Radeon 9200 SE]"
        Monitor         "710E"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666
EndSection
tropcky@tropcky-linux:~$

---

### Post by Milk &amp; Toast &amp; Honey on 2007-09-01
Open "Application -> Accessories -> Terminal", then type this:
```

gedit /etc/X11/xorg.conf

```
That will bring you the "Text Editor", select all text from there, and post it here.

---

### Post by Milk &amp; Toast &amp; Honey on 2007-09-01
Ok, now please post the output from this command (from terminal):
```

glxinfo | grep -i direct

```

---

### Post by tropcky on 2007-09-01
thats it
direct rendering: Yes

---

### Post by Milk &amp; Toast &amp; Honey on 2007-09-01
Ok, now close the "xorg.conf" file.
And re-open with this command:
```

sudo gedit /etc/X11/xorg.conf

```
I've modified your xorg.conf file, just erase everything, and paste this line:
```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
# sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
FontPath "/usr/share/fonts/X11/misc"
FontPath "/usr/share/fonts/X11/cyrillic"
FontPath "/usr/share/fonts/X11/100dpi/:unscaled"
FontPath "/usr/share/fonts/X11/75dpi/:unscaled"
FontPath "/usr/share/fonts/X11/Type1"
FontPath "/usr/share/fonts/X11/100dpi"
FontPath "/usr/share/fonts/X11/75dpi"
# path to defoma fonts
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
Load "i2c"
Load "bitmap"
Load "ddc"
Load "dri"
Load "extmod"
Load "freetype"
Load "glx"
Load "int10"
Load "vbe"
EndSection

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "us"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ImPS/2"
Option "ZAxisMapping" "4 5"
Option "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "stylus"
Option "Device" "/dev/input/wacom"
Option "Type" "stylus"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "eraser"
Option "Device" "/dev/input/wacom"
Option "Type" "eraser"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "cursor"
Option "Device" "/dev/input/wacom"
Option "Type" "cursor"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "Device"
Identifier "ATI Technologies Inc RV280 [Radeon 9200 SE]"
Driver "ati"
BusID "PCI:1:0:0"
############################################
# ERASE THIS IF YOU CAN'T START THE DISPLAY
# BEGIN: ERASE
Option "AddARGBVisuals" "True"
Option "AddARGBGLXVisuals" "True"
# END: ERASE
############################################
EndSection

Section "Monitor"
Identifier "710E"
Option "DPMS"
EndSection

Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies Inc RV280 [Radeon 9200 SE]"
Monitor "710E"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
InputDevice "stylus" "SendCoreEvents"
InputDevice "cursor" "SendCoreEvents"
InputDevice "eraser" "SendCoreEvents"
EndSection

Section "DRI"
Mode 0666
EndSection

```
Now save the file, logout, and press "CTRL-ALT-BACKSPACE", or you can restart the computer.

IF YOU CAN'T LOGIN, or the display doesn't start, press this:
```

Ctrl-Alt-F1

```
Then login to the terminal, and edit the xorg.conf with this command:
```

sudo nano /etc/X11/xorg.conf

```
and remove the lines with "BEGIN: ERASE" to "END: ERASE", save the file, and restart the computer again.

---

### Post by tropcky on 2007-09-01
ooooooooooooooooh  i did it and no changs
is ther a way to role back 
u know restor the system like it was 2 days ago u know what i mean 
and just dont get off ur pc stay with me pleeeeeeeeeeez

---

### Post by Milk &amp; Toast &amp; Honey on 2007-09-01
> 
ooooooooooooooooh i did it and no changs

Have you restart the computer ?

> 
and just dont get off ur pc stay with me pleeeeeeeeeeez

What do you mean with "pc" ?

---

### Post by Milk &amp; Toast &amp; Honey on 2007-09-01
> 
and just dont get off ur pc stay with me pleeeeeeeeeeez

Ahh, I understand, this what you mean right:
"and just don't get off from your PC, stay with me please"

---

### Post by tropcky on 2007-09-01
will i didn't restart my computer but i did alt-ctrl-back space 
and pc means personal computer   and i mean 2 say dont get up from ur computer cuz i need ur help

---

### Post by Milk &amp; Toast &amp; Honey on 2007-09-01
> 
and pc means personal computer and i mean 2 say dont get up from ur computer cuz i need ur help

Ok, relax dude, I'll try my best.

Now post the output of this command (execute from command line)
```

beryl --replace

```

---

### Post by tropcky on 2007-09-01
tropcky@tropcky-linux:~$ beryl --replace
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (2048x2048)

Reloading options

---

### Post by Milk &amp; Toast &amp; Honey on 2007-09-01
Now open another terminal (don't close the previous terminal), and type:
```

emerald --replace

```
and post the output.

---

### Post by tropcky on 2007-09-01
The program 'emerald' is currently not installed.  You can install it by typing:
sudo apt-get install emerald
Make sure you have the 'universe' component enabled
bash: emerald: command not found

---

### Post by Milk &amp; Toast &amp; Honey on 2007-09-01
Now, that's explained why you don't have windows border.
Open another terminal window, and type this:
```

sudo apt-get install emerald emerald-themes

```

After that, try to type this again:
```

emerald --replace

```
and post the output.

---

### Post by tropcky on 2007-09-01
here it is the post of emerald --replace

tropcky@tropcky-linux:~$ emerald --replace

(emerald:8915): Wnck-WARNING **: Unhandled action type (nil)

(emerald:8915): Wnck-WARNING **: Unhandled action type (nil)

(emerald:8915): Wnck-WARNING **: Unhandled action type (nil)

(emerald:8915): Wnck-WARNING **: Unhandled action type (nil)

(emerald:8915): Wnck-WARNING **: Unhandled action type (nil)

(emerald:8915): Wnck-WARNING **: Unhandled action type (nil)

---

### Post by Milk &amp; Toast &amp; Honey on 2007-09-01
type this:
```

emerald-theme-manager

```

If the output similar to 
```

The program 'emerald-theme-manager' is currently not installed. You can install it by typing:
sudo apt-get install emerald-theme-manager
Make sure you have the 'universe' component enabled

```

then type this:
```

sudo apt-get install emerald-theme-manager

```

After you installed emerald-theme-manager, type
```

emerald-theme-manager

```
in terminal, and then one window will appear, then, just select ANY theme from the list.
And make sure the terminal with "emerald --replace" is still running.

---

### Post by tropcky on 2007-09-01
look man i trayed to chios any theme from it but nothin happned

---

### Post by Milk &amp; Toast &amp; Honey on 2007-09-01
Try to logout and login again.

---

### Post by tropcky on 2007-09-01
nothing deeeeeeeeem i gonna shot my self here 
i am thinkn about reinstall the system all over agen

---

### Post by Milk &amp; Toast &amp; Honey on 2007-09-01
Have you load the beryl-manager?

```

beryl-manager

```

---

### Post by tropcky on 2007-09-01
ya i did

---

### Post by Milk &amp; Toast &amp; Honey on 2007-09-01
Now load beryl, just see the attachment.

---

### Post by tropcky on 2007-09-01
wow woooooooooow man thank for god anf thanks alot of thanks 4 u 
its works now 
but give me a way that is make me sure that thes deeeeeep **** will never ever happen agen cuz in the next time i gonna shot my self

---

### Post by tropcky on 2007-09-01
and ya send me that theme that u use i like it and tell me how 2 install it

---

### Post by tropcky on 2007-09-01
and ya can u plez make a profile in brayle with that all 3d stuff and send 2 me  cus i really dont wanna miss with stuff agen by my self lol 
i am scary as hell :lolflag:

---

### Post by Milk &amp; Toast &amp; Honey on 2007-09-01
> 
... but give me a way that is make me sure that thes deeeeeep **** will never ever happen agen cuz in the next time i gonna shot my self

I saw Geekberg already mentioned (in the first page) how to load beryl at startup (through the Session properties), and I think, it will loaded automatically everytime you login.

I use the theme from here [http://gnome-look.org/content/show.php/GSM+GTK?content=56104]("http://gnome-look.org/content/show.php/GSM+GTK?content=56104")

Well, happy 3D Desktop & Beryl for you :) .
Don't worry, if you have some problem regarding this issue, just post again in this thread, I'm watching.


Since the main problem already solved, please mark this thread as SOLVED, by pressing this "Thread Tools -> Mark this thread as solved", so others can benefit.
(I'm doing a favor to mods, I hope mods don't mind :) )

---

### Post by tropcky on 2007-09-01
thank u all

---

### Post by PmDematagoda on 2007-09-01
Could you elaborate on that question? But I think you might do better at solving the problem if you opened up a new thread since this is labelled as Solved, don't you?

---

### Post by Milk &amp; Toast &amp; Honey on 2007-09-01
Actually, he/she [had]("http://ubuntuforums.org/showthread.php?t=540114") done it.

I'll post the answer there.

---

