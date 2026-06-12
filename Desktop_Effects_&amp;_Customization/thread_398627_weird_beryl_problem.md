---
title: "weird beryl problem"
date: 2007-04-01
forum: Desktop Effects &amp; Customization
---

### Post by kno712 on 2007-04-01
Hi, I've tried to find a solution for my problem in the forums, but I did not find any.

I use Ubuntu Dapper. I installed beryl and it did not work properly. I though it was my poor graphic card (Geforce Fx Go with 64 Mbs dedicated), so I decided to revert all the changes. 

At some point, when I had reverted back the xorg.conf and the gdm.conf-custom files (or partially reverted, I don't remember now), I decided to try to manually start beryl  by typing beryl-manager in a console window... and for my surprise, beryl started to work properly and smothly, even the cube!

So, again, I tried to put everything in order: back to modify the xorg.conf and the gdm.conf-custom, and to, make it work when I logon, I added a /usr/bin/beryl-manager entry in System->Preferences->Sessions->Startup Programs.

To my desesperation, beryl is not working; after login in, the x-system restarts and I face again the logon screen. 


This is my xorg.conf. In the "Device" section I've tried commenting and un-commenting the "Option" lines, with no result

```
Section "Device"
    Identifier     "NVIDIA Corporation NV34M [GeForce FX Go5200 32M/64M]"
    Driver         "nvidia"
    #Option         "RenderAccel" "True"
    #Option         "AllowGLXWithComposite" "True"
    #Option         "backingstore" "True"
    #Option         "TripleBuffer" "True"
    #Option         "AddARGBGLXVisuals" "True"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV34M [GeForce FX Go5200 32M/64M]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1280x800"
    EndSubSection
EndSection

Section "Extensions"
    Option "Composite" "Enable"
EndSection
```

And this is my gdm.conf-custom file

```
[daemon]

[security]

[xdmcp]

[gui]

[greeter]
GraphicalThemedColor=#1f236e
Browser=true
GraphicalTheme=Avio-GDM
GraphicalThemes=circles/:LandingClearance

[chooser]

[debug]

[servers]
#0=Xgl

[server-Xgl]
#name=Xgl server
#command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo -kb
#flexible=true

```


Please, help!!!!

---

### Post by kno712 on 2007-04-01
Some extra info:

I know that Dapper is not officially supported. I wanted to give it a try.

I installed beryl following this instructions:

[http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit]("http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit")

Thanks a lot for any help!

---

### Post by kno712 on 2007-04-01
Update:

I manage to logon in the beryl environment! Though it doesn't work, it no longer crash and reboot in the logon screen anymore.

I did the following: instead of starting up beryl as a default in the standard gnome session, I created a new session where to try beryl without fear of crashing the X.

First, I created this script:

gksudo gedit /usr/bin/startberyl.sh

```

#!/bin/sh
beryl-manager
sleep 4
exec gnome-session

```

Then, I created the new Xsession:

gksudo gedit /usr/share/xsessions/Beryl.desktop

```

[Desktop Entry]
Encoding=UTF-8
Name=Beryl
Exec=/usr/bin/startberyl.sh
Icon=
Type=Application

```

I made some modifications to the xorg.conf (I uncommented some lines); the changes are the following


```

Section "Device"
    Identifier     "NVIDIA Corporation NV34M [GeForce FX Go5200 32M/64M]"
    Driver         "nvidia"
    Option         "RenderAccel" "true"
    Option         "AllowGLXWithComposite" "true"
    #Option         "backingstore" "true"
    Option         "TripleBuffer" "true"
    #Option         "AddARGBGLXVisuals" "true"
EndSection

```

same for gdm.conf-custom: I uncommented the following:

```

[servers]
0=Xgl

[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo
flexible=true


```


But still beryl refuses to work properly; I have the diamond but nothing happens; besides, now it takes a long to start-up when I choose it at the logon window.

---

### Post by kno712 on 2007-04-01
In the condition described above

- if I login in the beryl session; beryl does not work
- if I login in the normal gnome session and then I type "beryl-manager" then beryl works; the only problem is that I can not configure it (if I click "beryl setting manager" in preferences, a windows open, but whatever I choose there, does not have any effect)

Can anyone help, please?

---

