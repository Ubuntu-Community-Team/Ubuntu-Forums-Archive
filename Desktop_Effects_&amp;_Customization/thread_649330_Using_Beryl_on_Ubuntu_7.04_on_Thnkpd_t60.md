---
title: "Using Beryl on Ubuntu 7.04 on Thnkpd t60"
date: 2007-12-24
forum: Desktop Effects &amp; Customization
---

### Post by glopv2 on 2007-12-24
Hi!

I followed this tutorial to install Ubuntu and then to install Beryl:
[http://www.thinkwiki.org/wiki/Installing_Ubuntu_6.10_(Edgy_Eft)_on_a_ThinkPad_T60](http://www.thinkwiki.org/wiki/Installing_Ubuntu_6.10_(Edgy_Eft)_on_a_ThinkPad_T60)

I know it's for 6.10 and I have 7.04, but I figured it would be okay and I subbed "7.04" for "6.10" where appropriate.

I installed Beryl according to their instructions, went to "System->Pref.->Desktop Effects" and turned on the cube and the wobbly windows. Worked perfectly! Then I restarted the computer. Now only the wobbly windows work. When I turn on "cube", the # of desktops goes from 2 down to 1, but no cube shows up. Wobbly windows still works. What did I do to stop it from working? Or, how can get it to keep working?

Thanks!

---

### Post by glopv2 on 2007-12-24
Hi, sorry for the update:
I found that the cube setting in "System->Preferences->Desktop Effects" works only if I have 4 desktops when I turn it on.

However, installing Beryl put a settings program in "Applications->System Tools->Beryl Settings Manager". Changing these settings seems to have absolutely no affect on anything. Only the "System->Preferences->Desktop Effects" seems to do anything. Does anybody know why this is, and how I can utilize the full Beryl?

Thanks very much!

---

### Post by Sef on 2007-12-25
I would uninstall Beryl since it is no longer being maintained, i.e., no one is working on it.  Instead I would install Compiz-Fusion.  To do so read [Forlong's Blog]("http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty").

---

### Post by glopv2 on 2007-12-25
Thank you! It works much better!

---

### Post by glopv2 on 2007-12-25
... Except now, I've lost the title bar thing with the X/minimize/max buttons, resize, etc.

I kinda miss that bar. Even when I click "reset to defaults" the bar doesn't show up.

If I log in GNOME, they're there, but not in Xgl.

Thanks!

---

### Post by Forlong on 2007-12-25
If you are using a Nvidia card, try this:
```
sudo nvidia-xconfig --add-argb-glx-visuals -d 24
```
Then restart X and see if it worked.

---

### Post by glopv2 on 2007-12-25
Unfortunately I have an ATi card. And one that requires a proprietary driver.

Is there a similar command for me?

---

### Post by Forlong on 2007-12-25
> **glopv2 said:**
> Is there a similar command for me?
I'm afraid not.

What's the output of ```
compiz
``` in a terminal?

You also might want to post your xorg.conf:
```
grep -v ^# /etc/X11/xorg.conf
```
Please use the forum's CODE tag (# button) then.

---

### Post by glopv2 on 2007-12-25
The output of "compiz" is:
```
robert@johnnycash:~$ compiz
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
Starting emerald
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

```

The output of "grep -v ^# /etc/X11/xorg.conf

```

Section "Files"
        Fontpath        "/usr/share/fonts/X11/misc"
        Fontpath        "/usr/share/fonts/X11/cyrillic"
        Fontpath        "/usr/share/fonts/X11/100dpi/:unscaled"
        Fontpath        "/usr/share/fonts/X11/75dpi/:unscaled"
        Fontpath        "/usr/share/fonts/X11/Type1"
        Fontpath        "/usr/share/fonts/X11/100dpi"
        Fontpath        "/usr/share/fonts/X11/75dpi"
        # path to defoma fonts
        Fontpath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load            "i2c"
        Load            "bitmap"
        Load            "ddc"
        Load            "dri"
        Load            "extmod"
        Load            "freetype"
        Load            "glx"
        Load            "int10"
        Load            "vbe"
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
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ImPS/2"
        Option          "ZAxisMapping"  "4 5"
        Option          "Emulate3Buttons"       "true"
        Option          "EmulateWheel" "true"
        Option          "EmulateWheelButton" "2"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"        "/dev/psaux"
        Option          "Protocol"      "auto-dev"
        Option          "HorizScrollDelta"      "0"
        Option          "SHMConfig"             "on"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "stylus"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "eraser"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "cursor"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "Generic Video Card"
        Driver          "fglrx"
        Busid           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "Generic Monitor"
        Defaultdepth    24
        SubSection "Display"
                Depth   1
                Modes           "1024x768"      "(pitch"        "1024)"
        EndSubSection
        SubSection "Display"
                Depth   4
                Modes           "1024x768"      "(pitch"        "1024)"
        EndSubSection
        SubSection "Display"
                Depth   8
                Modes           "1024x768"      "(pitch"        "1024)"
        EndSubSection
        SubSection "Display"
                Depth   15
                Modes           "1024x768"      "(pitch"        "1024)"
        EndSubSection
        SubSection "Display"
                Depth   16
                Modes           "1024x768"      "(pitch"        "1024)"
        EndSubSection
        SubSection "Display"
                Depth   24
                Modes           "1024x768"      "(pitch"        "1024)"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen "Default Screen"
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"
        Inputdevice     "stylus"        "SendCoreEvents"
        Inputdevice     "cursor"        "SendCoreEvents"
        Inputdevice     "eraser"        "SendCoreEvents"
        Inputdevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection
Section "Extensions"
        Option          "Composite"     "0"
EndSection

```

---

### Post by Forlong on 2007-12-26
I guess it's because you (still) have Beryl's Emerald installed, which not compatible with Compiz.

Please post the output of ```
dpkg -l | grep emerald
```

Additionally, let's have a look at your sources.list: ```
cat /etc/apt/sources.list
```

---

### Post by glopv2 on 2007-12-26
dpkg -l | grep emerald
```

rc  emerald                                    0.3~git20070717-0ubuntu1~ppa1             Decorator for compiz-fusion
rc  libemeraldengine0                          0.2.1-0ubuntu1                            Decoration engines for beryl

```

I saw a package for beryl, and I did "sudo apt-get remove <package name>"
then restarted the computer and the title bars are back! Thank you so much, I really appreciate it!

I hope you don't mind if I ask another question:

When I choose the "Xgl" session instead of the "GNOME" session, and then I go to "system" and to "quit", the "Shutdown" button doesn't appear as an option. But, when I choose "GNOME" it does. Why does the shutdown button disappear?

---

### Post by glopv2 on 2007-12-26
Sorry, I also have a 2nd question (sheepish grin):

In the Compiz config program, I want to set one of the buttons as "Alt-Tab", so I disabled the normal alt-tab and tried to change another feature to "Alt-Tab". But it just beeps at me, it won't let me do it. Even if I change the normal window switcher away from "Alt-Tab", Compiz won't let me change it back. For some reason I cannot assign anything to "Alt-Tab" "Super-Tab", things like that .... How can I get around this?

Again, thanks!

---

### Post by Forlong on 2007-12-26
> **glopv2 said:**
> When I choose the "Xgl" session instead of the "GNOME" session, and then I go to "system" and to "quit", the "Shutdown" button doesn't appear as an option. But, when I choose "GNOME" it does. Why does the shutdown button disappear?
That's because of Xgl.
Use this for your Xgl script:
```
#!/bin/sh
Xgl :1 -nolisten tcp -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec gnome-session
```
> **glopv2 said:**
> In the Compiz config program, I want to set one of the buttons as "Alt-Tab", so I disabled the normal alt-tab and tried to change another feature to "Alt-Tab". But it just beeps at me, it won't let me do it. Even if I change the normal window switcher away from "Alt-Tab", Compiz won't let me change it back. For some reason I cannot assign anything to "Alt-Tab" "Super-Tab", things like that .... How can I get around this?
Oh yeah, don't you hate it, when your Thinkpad beeps at you? It's so unbelievably annoying. :-s :)

Anyway... just double-click on Initiate and set it manually with **<Alt>Tab**

---

### Post by glopv2 on 2007-12-26
Haha. Okay, so the shutdown button is back, but now if I log out of Xgl, I have to restart the computer before I can log back in using Xgl (Otherwise, when I try it, Gnome fails to initialize and I have to use GNOME). 

Are you sure that's the correct script for my ATi card?

---

### Post by Forlong on 2007-12-27
> **glopv2 said:**
> Haha. Okay, so the shutdown button is back, but now if I log out of Xgl, I have to restart the computer before I can log back in using Xgl (Otherwise, when I try it, Gnome fails to initialize and I have to use GNOME). 
Ah, yes... Xgl is so horrible.
That's because of a temporary file from the X-server. Since the /tmp directory gets deleted only on reboot, it's still there when logging out.

The file I'm talking about is this one: /tmp/.X11-unix/X1
So if you want to log out and back in without rebooting, you'll have to delete the file:
```
rm /tmp/.X11-unix/X1
```
I guess you could try adding it to the script. Make sure it's in the very first line, though (right after the shebang), so it should look like this:
```
#!/bin/sh
rm -f /tmp/.X11-unix/X1
Xgl :1 -nolisten tcp -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec gnome-session
```
Hope this works...

---

### Post by glopv2 on 2007-12-27
Okay this is a bit crazy: It works! But I just realized that now my Super button doesn't seem to work... My laptop doesn't seem to notice when I am pressing the "Super" key.

It was working earlier.. Did something I do disable the Super key?

---

### Post by glopv2 on 2007-12-29
<bumb> Sorry, is there a way to re-enable my "Super" key?

I really appreciate this help!

Thanks

---

### Post by Forlong on 2007-12-29
Check *System &#8594; Preferences &#8594; Keyboard* if the proper layout is selected. Xgl is known to mess with that config.

---

### Post by MaindotC on 2008-01-13
> **glopv2 said:**
> Hi, sorry for the update:
I found that the cube setting in "System->Preferences->Desktop Effects" works only if I have 4 desktops when I turn it on.

However, installing Beryl put a settings program in "Applications->System Tools->Beryl Settings Manager". Changing these settings seems to have absolutely no affect on anything. Only the "System->Preferences->Desktop Effects" seems to do anything. Does anybody know why this is, and how I can utilize the full Beryl?

Thanks very much!

I also have a T60 and Beryl is working pretty well for me - I have wobbly windows, fading in and out pop-ups, and alt+tab switcher, but I cannot get the cube to work.  What key settings did you implement to use the cube?  I want to see it so much :(

---

