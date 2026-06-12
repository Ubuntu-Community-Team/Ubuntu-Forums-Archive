---
title: "Compiz crash"
date: 2007-08-18
forum: Desktop Effects &amp; Customization
---

### Post by Dark Neutron on 2007-08-18
I had Compiz/Beryl working on a previous version of linux, but I have not been able to get it working with Ubuntu. I used [this]("http://ubuntuforums.org/showthread.php?t=481314") install guide.

When I try to run compiz --replace, I get the error message below. Also, the update manager says there is a new version of compiz-core avaiable, but it never manages to install it. It says it was installed, but it is still in the update list (same version).

Any idea what is causing this? And what is a Wnck-WARNING? Was I playing too many games of Wnck-a-mole?

I am running the AMD64 version of Ubuntu 7.04 and the nVidia restricted driver. If it makes a difference, I am no longer using the monitor(HMD A240R) listed in the xorg.conf file below. I was going to change it to my new one, but was not sure how. I now have a Hanns.G HW194D.

(Apologies if this is the wrong was to post long bits of text)

Error text:

```
user@host:~$ compiz --replace
Checking for Xgl: not present. 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Converting gconf plugin list: '' 
Checking for nVidia: present. 
Checking for Xgl: not present. 

(gtk-window-decorator:7416): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7416): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7416): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7416): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7416): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7416): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7416): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7416): Wnck-WARNING **: Unhandled action type (nil)
Backend     : gconf
Integration : true
Profile     : default
Adding plugin water (water)
Adding plugin group (group)
Adding plugin scaleaddon (scaleaddon)
Adding plugin blur (blur)
Adding plugin switcher (switcher)
Adding plugin resizeinfo (resizeinfo)
Adding plugin fade (fade)
Adding plugin imgjpeg (imgjpeg)
Adding plugin crashhandler (crashhandler)
Adding plugin fs (fs)
Adding plugin rotate (rotate)
Adding plugin inotify (inotify)
Adding plugin neg (neg)
Adding plugin put (put)
Adding plugin bench (bench)
Adding plugin expo (expo)
Adding plugin screenshot (screenshot)
Adding plugin showdesktop (showdesktop)
Adding plugin trailfocus (trailfocus)
Adding plugin fadedesktop (fadedesktop)
Adding plugin splash (splash)
Adding core settings (General Options)
Adding plugin glib (glib)
Adding plugin decoration (decoration)
Adding plugin cube (cube)
Adding plugin animation (animation)
Adding plugin firepaint (firepaint)
Adding plugin clone (clone)
Adding plugin move (move)
Adding plugin dbus (dbus)
Adding plugin annotate (annotate)
Adding plugin ring (ring)
Adding plugin wall (wall)
Adding plugin resize (resize)
Adding plugin snap (snap)
Adding plugin winrules (winrules)
Adding plugin video (video)
Adding plugin extrawm (extrawm)
Adding plugin minimize (minimize)
Adding plugin opacify (opacify)
Adding plugin svg (svg)
Adding plugin regex (regex)
Adding plugin scale (scale)
Adding plugin place (place)
Adding plugin zoom (zoom)
Adding plugin plane (plane)
Adding plugin cubereflex (cubereflex)
Adding plugin text (text)
Adding plugin wobbly (wobbly)
Adding plugin reflex (reflex)
Adding plugin vpswitch (vpswitch)
Adding plugin thumbnail (thumbnail)
Adding plugin mblur (mblur)
Adding plugin png (png)
Adding plugin addhelper (addhelper)
Initializing core options...done
Initializing imgjpeg options...done
Initializing bench options...done
Initializing screenshot options...done
Initializing decoration options...done

(gtk-window-decorator:7416): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7416): Wnck-WARNING **: Unhandled action type (nil)
*** glibc detected *** /usr/bin/compiz.real: malloc(): memory corruption: 0x0000000000873d60 ***
======= Backtrace: =========
/lib/libc.so.6[0x2adc6793b1d1]
/lib/libc.so.6(__libc_calloc+0x96)[0x2adc6793c636]
/usr/lib/compiz/libanimation.so[0x2aaaad9fc714]
/usr/bin/compiz.real(initPluginForScreen+0x46)[0x4258b6]
/usr/lib/compiz/libccp.so[0x2aaaaabdddb2]
/usr/bin/compiz.real(initPluginForDisplay+0x5b)[0x42598b]
/usr/lib/compiz/libccp.so[0x2aaaaabdde82]
/usr/bin/compiz.real(pushPlugin+0x107)[0x4260c7]
/usr/bin/compiz.real(eventLoop+0x1ac)[0x40ef2c]
/usr/bin/compiz.real(main+0x436)[0x40c0e6]
/lib/libc.so.6(__libc_start_main+0xf4)[0x2adc678e88e4]
/usr/bin/compiz.real[0x40b6d9]
======= Memory map: ========
00400000-00435000 r-xp 00000000 08:17 787675                             /usr/bin/compiz.real
00635000-00636000 rw-p 00035000 08:17 787675                             /usr/bin/compiz.real
00636000-009e4000 rw-p 00636000 00:00 0                                  [heap]
40000000-40002000 rwxp 00000000 00:0d 2629                               /dev/zero
2aaaaaaab000-2aaaaabdc000 rw-p 2aaaaaaab000 00:00 0 
2aaaaabdc000-2aaaaabdf000 r-xp 00000000 08:17 900263                     /usr/lib/compiz/libccp.so
2aaaaabdf000-2aaaaaddf000 ---p 00003000 08:17 900263                     /usr/lib/compiz/libccp.so
2aaaaaddf000-2aaaaade0000 rw-p 00003000 08:17 900263                     /usr/lib/compiz/libccp.so
2aaaaadf0000-2aaaaae07000 r-xp 00000000 08:17 787414                     /usr/lib/libcompizconfig.so.0.0.0
2aaaaae07000-2aaaab006000 ---p 00017000 08:17 787414                     /usr/lib/libcompizconfig.so.0.0.0
2aaaab006000-2aaaab008000 rw-p 00016000 08:17 787414                     /usr/lib/libcompizconfig.so.0.0.0
2aaaab008000-2aaaab012000 r-xp 00000000 08:17 900264                     /usr/lib/compizconfig/backends/libgconf.so
2aaaab012000-2aaaab212000 ---p 0000a000 08:17 900264                     /usr/lib/compizconfig/backends/libgconf.so
2aaaab212000-2aaaab214000 rw-p 0000a000 08:17 900264                     /usr/lib/compizconfig/backends/libgconf.so
2aaaab214000-2aaaab215000 rw-p 2aaaab214000 00:00 0 
2aaaab224000-2aaaab25d000 r-xp 00000000 08:17 786404                     /usr/lib/libgconf-2.so.4.1.2
2aaaab25d000-2aaaab45c000 ---p 00039000 08:17 786404                     /usr/lib/libgconf-2.so.4.1.2
2aaaab45c000-2aaaab461000 rw-p 00038000 08:17 786404                     /usr/lib/libgconf-2.so.4.1.2
2aaaab461000-2aaaab4bd000 r-xp 00000000 08:17 786147                     /usr/lib/libORBit-2.so.0.1.0
2aaaab4bd000-2aaaab6bc000 ---p 0005c000 08:17 786147                     /usr/lib/libORBit-2.so.0.1.0
2aaaab6bc000-2aaaab6cf000 rw-p 0005b000 08:17 786147                     /usr/lib/libORBit-2.so.0.1.0
2aaaab6cf000-2aaaab6d3000 r-xp 00000000 08:17 786570                     /usr/lib/libgthread-2.0.so.0.1200.11
2aaaab6d3000-2aaaab8d2000 ---p 00004000 08:17 786570                     /usr/lib/libgthread-2.0.so.0.1200.11
2aaaab8d2000-2aaaab8d3000 rw-p 00003000 08:17 786570                     /usr/lib/libgthread-2.0.so.0.1200.11
2aaaab8d3000-2aaaab8db000 r-xp 00000000 08:17 278097                     /lib/librt-2.5.so
2aaaab8db000-2aaaabada000 ---p 00008000 08:17 278097                     /lib/librt-2.5.so
2aaaabada000-2aaaabadc000 rw-p 00007000 08:17 278097                     /lib/librt-2.5.so
2aaaabadc000-2aaaabb1c000 r-xp 00000000 08:17 786516                     /usr/lib/libgobject-2.0.so.0.1200.11
2aaaabb1c000-2aaaabd1c000 ---p 00040000 08:17 786516                     /usr/lib/libgobject-2.0.so.0.1200.11
2aaaabd1c000-2aaaabd1e000 rw-p 00040000 08:17 786516                     /usr/lib/libgobject-2.0.so.0.1200.11
2aaaabd1e000-2aaaabdbe000 r-xp 00000000 08:17 786462                     /usr/lib/libglib-2.0.so.0.1200.11
2aaaabdbe000-2aaaabfbd000 ---p 000a0000 08:17 786462                     /usr/lib/libglib-2.0.so.0.1200.11
2aaaabfbd000-2aaaabfbf000 rw-p 0009f000 08:17 786462                     /usr/lib/libglib-2.0.so.0.1200.11
2aaaabfbf000-2aaaabfd4000 r-xp 00000000 08:17 278091                   Aborted (core dumped)

```

xorg.conf file:

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder26)  Thu Nov  9 17:55:59 PST 2006

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
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
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
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
    Option         "XkbVariant" "dvorak"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "HMD-A240R"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVidia Corporation NV43 [GeForce 6600 GT]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV43 [GeForce 6600 GT]"
    Monitor        "HMD-A240R"
    DefaultDepth    24
    Option         "AddARGBVisuals" "True"
    Option         "NoLogo" "True"
    Option         "RandRRotation" "on"
    Option         "RenderAccel" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "DisableGLXRootClipping" "true"
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1440x900" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "DAMAGE" "Enable"
    Option         "RENDER" "Enable"
    Option         "Composite" "Enable"
EndSection

```

---

### Post by azidrane on 2007-08-18
I had some probs with that guide and repository. Try this:

First, remove all compiz bins, libs and conf files:

```

sudo apt-get --purge remove compiz* libcompizconfig*

```

remove this from your /etc/apt/sources.list

```

eb http://ppa.dogfood.launchpad.net/amaranth/ubuntu feisty main restricted universe multiverse
deb-src http://ppa.dogfood.launchpad.net/amaranth/ubuntu feisty main restricted universe multiverse

```

replace with this:

```

deb http://download.tuxfamily.org/3v1deb feisty eyecandy-amd64
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy-amd64

```

Save, close then update:

```

sudo apt-get update
sudo apt-get upgrade

```

Then install the new packages:

```

sudo apt-get install compiz  # compiz-gnome AND/OR compiz-kde
sudo apt-get install compizconfig-settings-manager # libcompizconfig-backends-* ?!
sudo apt-get install compiz-fusion-*

```

Then launch in the normal way

```

compiz --replace

```


Full walkthrough here: [http://forum.compiz-fusion.org/showthread.php?t=1012]("http://forum.compiz-fusion.org/showthread.php?t=1012")

---

### Post by Dark Neutron on 2007-08-18
That worked! Thanks.

I also managed to enable emerald by going into the window decoration plug-in and adding "emerald --replace" to the command section.

In a sort of related question, does it matter if the xorg.conf file lists the wrong monitor?

---

### Post by azidrane on 2007-08-19
Really couldn't say. If it works that means its using the correct drivers. I wouldn't worry.

Cheers!

P.S. Can you put SOLVED in the thread name?

---

