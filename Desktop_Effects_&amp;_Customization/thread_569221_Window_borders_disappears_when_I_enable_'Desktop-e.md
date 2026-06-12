---
title: "Window borders disappears when I enable 'Desktop-effects' after a CF install?"
date: 2007-10-06
forum: Desktop Effects &amp; Customization
---

### Post by Hund on 2007-10-06
It's been a while since I used Compiz Fusion so I installed it today to se whats new since the last time. It didnt work that good so I uninstalled everything with Compiz Fusion.

But now when I enable the standard 'desktop-effects' the window borders disappears? What to do? :|

---

### Post by Sturmeh on 2007-10-08
Compiz is a part of both compiz-fusion and desktop-effects, you probably removed compiz, leading to that effect.

Try install "compiz, compiz-gnome"

---

### Post by Hund on 2007-10-08
I know that. :) All the necessary packages are installed.

---

### Post by Forlong on 2007-10-08
What type of graphics card are you using?

---

### Post by Hund on 2007-10-08
Nvidia 7300 GS.

Compiz Fusion and Beryl works fine. And so did Compiz before I tried CF.

---

### Post by Forlong on 2007-10-08
So you didn't change your xorg.conf since then?
How did you install Compiz Fusion?
Do you have Emerald installed?

---

### Post by Hund on 2007-10-08
No.

I used these sources:
> deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy 
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy

Not at the moment. But it doesnt make any difference.

---

### Post by Forlong on 2007-10-08
So you did disable them? Good.

Post the output of ```
dpkg -l | grep compiz
```

---

### Post by Hund on 2007-10-08
Yepp.

> johan@general-lee:~$ dpkg -l | grep compiz
ii  compiz                                 0.3.6-1ubuntu13                        OpenGL window and compositing manager
ii  compiz-core                            0.3.6-1ubuntu13                        OpenGL window and compositing manager
ii  compiz-gnome                           0.3.6-1ubuntu13                        OpenGL window and compositing manager - GNOM
ii  compiz-gtk                             0.3.6-1ubuntu13                        OpenGL window and compositing manager - Gtk 
ii  compiz-plugins                         0.3.6-1ubuntu13                        OpenGL window and compositing manager - plug
rc  gnome-compiz-manager                   0.10.3-0ubuntu1                        Compiz Gnome Manager
rc  libcompizconfig0                       0.5.2~git20070909+3v1ubuntu3           Settings library for plugins - Compiz Fusion

I dont have libcompizconfig0 installed? :confused:

---

### Post by Forlong on 2007-10-08
Those are just configs, you can remove them like this:
```
sudo dpkg --purge gnome-compiz-manager libcompizconfig0
```

What output gives
```
compiz --replace
```
in the terminal?
And when you run ```
gtk-window-decorator
``` afterwards?

---

### Post by Hund on 2007-10-08
> johan@general-lee:~$ compiz --replace


> johan@general-lee:~$ gtk-window-decorator
gtk-window-decorator: Could not acquire decoration manager selection on screen 0 display ":0.0"

:(

---

### Post by Forlong on 2007-10-08
Weird, I thought you wouldn't have window boarders on Compiz?

What gives ```
gtk-window-decorator --replace
```

---

### Post by Hund on 2007-10-08
I dont. :(

> johan@general-lee:~$ gtk-window-decorator --replace


Nothing happends here to.

---

### Post by Forlong on 2007-10-08
Could you please post the output of ```
grep -v ^# /etc/X11/xorg.conf
```

---

### Post by Hund on 2007-10-08
> johan@general-lee:~$ grep -v ^# /etc/X11/xorg.conf


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/lib/X11/rgb"
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
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7300 GS"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "metamodes" "DFP: 1280x1024_75 +0+0; DFP: 800x600 +0+0; DFP: 640x480 +0+0; DFP: 1280x1024 +0+0"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

.

---

### Post by Forlong on 2007-10-08
Sorry, since there is no error message and everything seems to be set right, I'm officially out of ideas.

What exactly didn't work for you with Compiz Fusion?

---

### Post by Hund on 2007-10-08
To bad. :(

It was slow as ***,, If I moved a window the whole computer frezed. It worked fine when I used one of the first public versions couple of months ago.

Beryl works fine but it feels to old.

---

### Post by Forlong on 2007-10-08
Maybe you should try [Amaranth's packages](https://help.ubuntu.com/community/CompositeManager/CompizFusion) (they are backported from Gutsy, see [here](http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty) for details)

---

### Post by Hund on 2007-10-08
> johan@general-lee:~$ compiz --replaceChecking for Xgl: not present. 
Detected PCI ID for VGA: 05:00.0 0300: 10de:01df (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator

(gtk-window-decorator:28286): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:28286): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:28286): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:28286): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:28286): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:28286): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:28286): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:28286): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:28286): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:28286): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:28286): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:28286): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:28286): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:28286): Wnck-WARNING **: Unhandled action type (nil)


Still no window borders. But the rest works finw now, it doesent frezes. :)

And the update manager want to update compiz-core 1:0.5.2+git20070918-0ubuntu5~ppa1 to 1:0.5.2+git20070918-0ubuntu5~ppa1, the same version, if I install the updates it cames back again.

---

### Post by Forlong on 2007-10-08
> **Hund said:**
> And the update manager want to update compiz-core 1:0.5.2+git20070918-0ubuntu5~ppa1 to 1:0.5.2+git20070918-0ubuntu5~ppa1, the same version, if I install the updates it cames back again.
That's "normal".

Could please post the output of ```
dpkg -l |grep compiz
``` again

---

### Post by Hund on 2007-10-08
> johan@general-lee:~$ dpkg -l |grep compiz
ii  compiz-core                            0.5.2+git20070918-0ubuntu5~ppa1        OpenGL window and compositing manager
rc  compiz-gnome                           0.5.2+git20070918-0ubuntu5~ppa1        OpenGL window and compositing manager - GNOM
rc  compiz-gtk                             0.3.6-1ubuntu13                        OpenGL window and compositing manager - Gtk 
ii  compizconfig-settings-manager          0.5.2+git20070829-0ubuntu1~ppa1        Compiz configuration settings manager
rc  emerald                                0.3~git20070717-0ubuntu1~ppa1          Decorator for compiz-fusion
ii  libcompizconfig-backend-gconf          0.5.2+git20070918-0ubuntu1~ppa1        Settings library for plugins - OpenCompositi
ii  libcompizconfig0                       0.5.2+git20070919-0ubuntu2~ppa1        Settings library for plugins - OpenCompositi
ii  python-compizconfig                    0.5.2+git20070829-0ubuntu1~ppa1        Compiz configuration system bindings
.

---

### Post by Forlong on 2007-10-08
You don't have any window decorator installed, try
```
sudo apt-get install compiz-gnome
```

---

### Post by Hund on 2007-10-08
No luck. :(

---

### Post by Forlong on 2007-10-08
Please install emerald and see if it gives any output when you start compiz then.

---

### Post by Hund on 2007-10-08
Emerald is already installed.

---

### Post by Forlong on 2007-10-08
Not according to the above output... but is there any error message, when you start compiz now?

---

### Post by Hund on 2007-10-08
> johan@general-lee:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 05:00.0 0300: 10de:01df (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald

(emerald:9318): Wnck-WARNING **: Unhandled action type (nil)

(emerald:9318): Wnck-WARNING **: Unhandled action type (nil)

(emerald:9318): Wnck-WARNING **: Unhandled action type (nil)

[...]



> johan@general-lee:~$ sudo apt-get install emerald
Reading package lists... Done
Building dependency tree       
Reading state information... Done
emerald is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
johan@general-lee:~$ 


Do you belive me now? :)

---

### Post by Forlong on 2007-10-08
I didn't say, I don't believe you, I just told you why I thought you haven't installed it.

The last thing I can recommend to you is resetting your xorg.conf
Do a backup first:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```
Then:
```
sudo dpkg-reconfigure xserver-xorg
```
And afterwrds:
```
sudo nvidia-xconfig --add-argb-glx-visuals -d 24
```

Then reboot and see if it helps.

---

### Post by Hund on 2007-10-08
I'm giving up on this now. I'm going to install Gutsy tomorrow anyway. :) Thx for your time.

---

### Post by wesley_of_course on 2007-10-08
Forlong  - Your patience is admirable  and help is noteworthy .

   Thank You for your diligence and being here to help out .


      Cheers - Wesley

---

