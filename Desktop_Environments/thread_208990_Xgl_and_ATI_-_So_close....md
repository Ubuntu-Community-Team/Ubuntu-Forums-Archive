---
title: "Xgl and ATI - So close..."
date: 2006-07-04
forum: Desktop Environments
---

### Post by JedTheHead on 2006-07-04
I'll get right to it.  Thanks in advance for any help given!!!

Compaq nx7000 with an ATI Mobility Radeon 9200

fglrxinfo output (without Xgl loaded):
```

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY/RADEON 9200 DDR Generic
OpenGL version string: 1.3.1072 (X4.3.0-8.25.18)

```

I followed this howto to the letter:

[http://wiki.cchtml.com/index.php/Xgl-Compiz-Dapper](http://wiki.cchtml.com/index.php/Xgl-Compiz-Dapper)

I choose "Xgl" from the sessions list at the GDM and log in.  Things are really slow and cumbersome.

fglrxinfo output WITH Xgl loaded:
```

Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY/RADEON 9200 DDR Generic
OpenGL version string: 1.3.1072 (X4.3.0-8.25.18)

```

ps ax | grep Xgl:
```

 6753 ?        SL     0:04 Xgl -fullscreen :1 -ac -accel glx:pbuffer -accel xv:pbuffer
 6968 pts/0    S+     0:00 grep Xgl

```

I then run this script:
```

 #!/bin/bash
   gnome-window-decorator --replace &
   compiz --replace $1 gconf &
   xmodmap /usr/share/xmodmap/xmodmap.us

```

Things flash, I get no output / errors, my window decorations are gone and nothing happens.  I don't see any reference to compiz in my process list and I can't find any errors in any logs.  Any ideas?  Should I see compiz as running?  	

Here is a ps ax after running the above script with the unimportant bits taken out:
```

  PID TTY      STAT   TIME COMMAND
 4508 ?        Ss     0:00 /usr/sbin/gdm
 4520 ?        S      0:00 /usr/sbin/gdm
 4525 tty7     SLs+   0:12 /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
 4766 ?        Ss     0:00 /sbin/mdadm -F -i /var/run/mdadm.pid -m root -f -s
 4813 ?        Ss     0:00 /usr/sbin/atd
 4826 ?        Ss     0:00 /usr/sbin/cron
 6753 ?        SL     0:13 Xgl -fullscreen :1 -ac -accel glx:pbuffer -accel xv:pbuffer
 6758 ?        S      0:00 /usr/bin/gnome-keyring-daemon
 6760 ?        Ss     0:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-fd=17
 6762 ?        Ss     0:00 /usr/bin/esd -terminate -nobeeps -as 1 -spawnfd 18
 6766 ?        Sl     0:00 /usr/lib/control-center/gnome-settings-daemon --oaf-activate-iid=OAFIID:GNOME_SettingsDaemon --oaf-ior-fd=25
 6768 ?        S      0:00 /usr/lib/vino/vino-server --oaf-activate-iid=OAFIID:GNOME_RemoteDesktopServer --oaf-ior-fd=26
 6778 ?        Ssl    0:00 gnome-panel --sm-client-id default1
 6780 ?        Ssl    0:00 nautilus --no-default-window --sm-client-id default2
 6803 ?        Ss     0:00 gnome-volume-manager --sm-client-id default4
 6807 ?        Sl     0:00 /usr/lib/gnome-vfs-2.0/gnome-vfs-daemon --oaf-activate-iid=OAFIID:GNOME_VFS_Daemon_Factory --oaf-ior-fd=33
 6821 ?        Ss     0:01 gnome-cups-icon --sm-client-id default3
 6828 ?        Ss     0:00 gnome-power-manager
 6800 ?        Sl     0:05 beagled --debug /usr/lib/beagle/BeagleDaemon.exe --bg
 6843 ?        Sl     0:00 mono /usr/lib/tomboy/Tomboy.exe --panel-applet --oaf-activate-iid=OAFIID:TomboyApplet_Factory --oaf-ior-fd=39
 6847 ?        S      0:00 /usr/lib/nautilus-cd-burner/mapping-daemon
 6859 ?        S      0:00 /usr/lib/gnome-panel/clock-applet --oaf-activate-iid=OAFIID:GNOME_ClockApplet_Factory --oaf-ior-fd=41
 6867 ?        Sl     0:00 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid=OAFIID:GNOME_Panel_TrashApplet_Factory --oaf-ior-fd=43
 6876 ?        Sl     0:01 python /usr/lib/deskbar-applet/deskbar-applet --oaf-activate-iid=OAFIID:Deskbar_Applet_Factory --oaf-ior-fd=45
 6878 ?        S      0:00 /usr/lib/gnome-utils/gnome-dictionary-applet --oaf-activate-iid=OAFIID:GNOME_DictionaryApplet_Factory --oaf-ior-fd=47
 6880 ?        S      0:00 /usr/lib/gnome-applets/mixer_applet2 --oaf-activate-iid=OAFIID:GNOME_MixerApplet_Factory --oaf-ior-fd=49
 6882 ?        S      0:00 /usr/lib/gnome-applets/gweather-applet-2 --oaf-activate-iid=OAFIID:GNOME_GWeatherApplet_Factory --oaf-ior-fd=50
 6887 ?        Sl     0:00 /usr/lib/evolution/evolution-data-server-1.6 --oaf-activate-iid=OAFIID:GNOME_Evolution_DataServer_BookFactory:1.2 --oaf-ior-fd=49
 6894 ?        Sl     0:00 /usr/lib/evolution/2.6/evolution-exchange-storage --oaf-activate-iid=OAFIID:GNOME_Evolution_Exchange_Connector_BookFactory:1.2 --oaf-ior-fd=55
 6899 ?        Sl     0:01 gnome-terminal
 6900 ?        S      0:00 gnome-pty-helper
 6901 pts/0    Ss     0:00 bash
 6913 ?        S      0:03 gedit file:///home/jasonk/Desktop/Unsaved%20Document%201
 6950 ?        S      0:00 /usr/lib/notification-daemon/notification-daemon
 6961 ?        Ss     0:00 gnome-screensaver
 7069 ?        Sl     0:01 beagled-helper --debug /usr/lib/beagle/IndexHelper.exe
 7357 pts/0    S      0:00 gnome-window-decorator
 7382 pts/0    R+     0:00 ps -ax

```

My xorg.conf: (Note: when I UNcomment the extensions section, I get mesa rendering, NOT direct with fglrx)

```


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
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	Option	    "DPMS"
       Modeline "640x350"  119.12  640 1728 1760 1840  350 1052 1058 1080
       Modeline "640x400"  119.12  640 1728 1760 1840  400 1052 1058 1080
       Modeline "720x400"  119.12  720 1728 1760 1840  400 1052 1058 1080
       Modeline "640x480"  119.12  640 1728 1760 1840  480 1052 1058 1080
       Modeline "800x600"  119.12  800 1728 1760 1840  600 1052 1058 1080
       Modeline "1024x768"  119.12  1024 1728 1760 1840  768 1052 1058 1080
       Modeline "1152x864"  119.12  1152 1728 1760 1840  864 1052 1058 1080
       Modeline "1280x960"  119.12  1280 1728 1760 1840  960 1052 1058 1080
       Modeline "1280x1024"  119.12  1280 1728 1760 1840  1024 1052 1058 1080
       Modeline "832x624"  119.12  832 1728 1760 1840  624 1052 1058 1080
       Modeline "1280x768"  119.12  1280 1728 1760 1840  768 1052 1058 1080
       Modeline "1280x800"  119.12  1280 1728 1760 1840  800 1052 1058 1080
       Modeline "1152x768"  119.12  1152 1728 1760 1840  768 1052 1058 1080
       Modeline "1400x1050"  119.12  1400 1728 1760 1840  1050 1052 1058 1080
       Modeline "1440x900"  119.12  1440 1728 1760 1840  900 1052 1058 1080
       Modeline "1600x1024"  119.12  1600 1728 1760 1840  1024 1052 1058 1080
       Modeline "1680x1050"  119.12  1680 1728 1760 1840  1050 1052 1058 1080
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
       Modeline "640x350"  119.12  640 1728 1760 1840  350 1052 1058 1080
       Modeline "640x400"  119.12  640 1728 1760 1840  400 1052 1058 1080
       Modeline "720x400"  119.12  720 1728 1760 1840  400 1052 1058 1080
       Modeline "640x480"  119.12  640 1728 1760 1840  480 1052 1058 1080
       Modeline "800x600"  119.12  800 1728 1760 1840  600 1052 1058 1080
       Modeline "1024x768"  119.12  1024 1728 1760 1840  768 1052 1058 1080
       Modeline "1152x864"  119.12  1152 1728 1760 1840  864 1052 1058 1080
       Modeline "1280x960"  119.12  1280 1728 1760 1840  960 1052 1058 1080
       Modeline "1280x1024"  119.12  1280 1728 1760 1840  1024 1052 1058 1080
       Modeline "832x624"  119.12  832 1728 1760 1840  624 1052 1058 1080
       Modeline "1280x768"  119.12  1280 1728 1760 1840  768 1052 1058 1080
       Modeline "1280x800"  119.12  1280 1728 1760 1840  800 1052 1058 1080
       Modeline "1152x768"  119.12  1152 1728 1760 1840  768 1052 1058 1080
       Modeline "1400x1050"  119.12  1400 1728 1760 1840  1050 1052 1058 1080
       Modeline "1440x900"  119.12  1440 1728 1760 1840  900 1052 1058 1080
       Modeline "1600x1024"  119.12  1600 1728 1760 1840  1024 1052 1058 1080
       Modeline "1680x1050"  119.12  1680 1728 1760 1840  1050 1052 1058 1080
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon R250 Lf [Radeon Mobility 9000 M9]"
	Driver      "ati"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx" 
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon R250 Lf [Radeon Mobility 9000 M9]"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1680x1050"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1680x1050"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1680x1050"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1680x1050"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1680x1050"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1680x1050"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

#Section "Extensions"
#Option "Composite" "Enable"
#EndSection

```


glxinfo:
```

name of display: :1.0
display: :1  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_ATI_pixel_format_float, 
    GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_multisample
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY/RADEON 9200 DDR Generic
OpenGL version string: 1.2 (1.3.1072 (X4.3.0-8.25.18))
OpenGL extensions:
    GL_ARB_multitexture, GL_ARB_texture_border_clamp, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_dot3, GL_ARB_transpose_matrix, GL_EXT_abgr, 
    GL_EXT_blend_color, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

```

Any help you can provide will be GREATLY appreciated!!!!

---

### Post by Mike_N on 2006-07-04
I didn't read yer whole post but i'm guessing that yer having trouble, setting up XGL. I have an ATI 9550 and i got it working, after trying a few different methodes, this is what worked for me...

I first got my ATI driver and 3D rendering going by following tihs guide... [https://help.ubuntu.com/pdf/ubuntu/C/desktopguide.pdf](https://help.ubuntu.com/pdf/ubuntu/C/desktopguide.pdf) and then got XGL going by following this guide... [http://www.compiz.net/viewtopic.php?id=389](http://www.compiz.net/viewtopic.php?id=389)

Hope this helps, Mike

---

### Post by JedTheHead on 2006-07-05
Mike,
Thanks for the quick response!  Actually, the [http://www.compiz.net/viewtopic.php?id=389]("http://www.compiz.net/viewtopic.php?id=389")
is the howto I followed.  (I pasted the wrong one in my original post here... I have looked at so many of them as of late... ;)

Feel free to see my long(er) drawn out post on page 14 of that thread.

Still no luck though.  I have Xgl up and running but compiz is a no-go.  I have tried everything I can find in the compiz and Ubuntu forums... my biggest frustration is that I can't seem to get any errors or messages from compiz to see why its not happy.  I can't even determine if it should be showing in my ps list...

Still working on it.....

---

### Post by besada on 2006-07-05
Try with this other script to start compiz:


#!/bin/sh
killall gnome-window-decorator
wait

gnome-window-decorator &
compiz --replace gconf &

---

### Post by JedTheHead on 2006-07-05
Thanks Besdada...  I have tried that one, tried it with and without gconf, tried it manually, tired it with sudo, tried it on different displays (other than :1), etc...

Same thing each time... things refresh, window decorations gone, and no fanciness  ;)  I issue metacity --replace & my decorations come back.. no signs of compiz running anywhere.

If I try the script you provided (same one in the original howto) with sudo I get:

```

compiz.real: Connection Error (No reply within specified time)
compiz.real: Couldn't initiate D-BUS connection
compiz.real: Disabling D-BUS Service

```

which, from what I have read, isn't a big deal (am I wrong?). 

If I run it as a normal user, I don't get any errors...  ugh. 

I'd like to think its NOT the video card since Xgl is running fine... I could be wrong.  Anyone else successful with an ALI Mobility Radeon 9200?

Thanks!

---

### Post by porchcth on 2006-07-05
Hi!

My starting script looks a little different. I don't know if if helps you, but maybe you can try it...

Regards,

porch.

```
#!/bin/sh
killall gnome-window-decorator
wait
DISPLAY=:1 LD_PRELOAD=/usr/share/fglrx/diversions/libGL.so.1.2 compiz --replace gconf &
gnome-window-decorator & 
```

---

### Post by JedTheHead on 2006-07-05
Thanks for the quick reply!

I have seen that script kicking around other places.  I don't have a /usr/share/fglrx/... dir.  Not sure what the "diversions" are all about.  What does your version of libGL.so.1.2 look like?

Mine is thus from a previous version of xorg-fglrx-driver that I found in the forums.  It was the only way to get direct rendering going.

```

jasonk@guyute:~$ ls -al /usr/lib/libGL.so.1.2
-rw-r--r-- 1 root root 635084 2006-07-04 19:36 /usr/lib/libGL.so.1.2

```

I have also noticed that /usr/bin/compiz :
```

#!/bin/bash

if [ -f /usr/lib/nvidia/libGL.so.1.2.xlibmesa ]; then
        LD_PRELOAD=/usr/lib/nvidia/libGL.so.1.2.xlibmesa compiz.real $@ & exit;
fi

if [ -f /usr/lib/fglrx/libGL.so.1.2.xlibmesa ]; then
        LD_PRELOAD=/usr/lib/fglrx/libGL.so.1.2.xlibmesa compiz.real $@ & exit;
fi

compiz.real $@ & exit;


```

Just points to/usr/lib/fglrx/libGL.so.12.xlibmesa which on my system is a symlink to the above file (/usr/lib/libGL.so.1.2).

Where does the diversions version come from?

Thanks again!

---

### Post by porchcth on 2006-07-07
Ooops. I just realized that I don't have a /usr/share/fglrx as well.
So the LD_PRELOAD probably does not do anything.
Sorry about the confusion...

Did you try the DISPLAY=:1?

In my starting scripts (see below), the gnome-session is also started on display 1 and somehow I remember that for ATI cards you have to use display 1, not 0.

So, I start xgl with
```
#!/bin/bash
Xgl -fullscreen :1 -ac -accel glx:pbuffer -accel xv:pbuffer & sleep 2 && DISPLAY=:1 gnome-session
```

and compiz with
```
#!/bin/sh
killall gnome-window-decorator
wait
DISPLAY=:1 LD_PRELOAD=/usr/share/fglrx/diversions/libGL.so.1.2 compiz --replace gconf &
gnome-window-decorator & 
xmodmap /usr/share/xmodmap/xmodmap.de &
```

(ok, forget about the LD_PRELOAD part and about the German xmodmap... :)  



Regards,

porch.

---

### Post by lmzmendes on 2006-07-11
> **JedTheHead said:**
> 
I'd like to think its NOT the video card since Xgl is running fine... I could be wrong.  Anyone else successful with an ALI Mobility Radeon 9200?
Thanks!

Hi, I've got exactly the same machine as you (NX7000 + ATI Mobility Radeon 9200) and I've tried a bunch of tutorials and HOW TOs last month, with absolutely no luck. I was starting to think it was the video card so I gave up.

However, your thread gave me new hope, and I'll probably start trying again.

Have you had any luck ever since your last post?

---

### Post by JedTheHead on 2006-07-11
Good luck man!  Don't give up!!!  Some pointers:

To get the card working with the correct rendering using xorg-driver-fglrx, install the driver and make the changes to the appropriate places in your xorg.conf (there are lots of threads about this).  

Then: 

Download the older libGL.so from: [http://www.ground-impact.com/libGL.so.1.2]("http://www.ground-impact.com/libGL.so.1.2") 

Do this (or use symlinks):

```

sudo mv /usr/lib/libGL.so.1.2 /usr/lib/old-libGL.so.1.2
sudo cp ./libGL.so.1.2 /usr/lib/
sudo cp ./libGL.so.1.2 /usr/lib/fglrx/
Check /usr/lib/libGL.so.1 link and make sure it points to /usr/lib/libGL.so.1.2

```

Another method for the card (I have not tried - See kvonb's post #5):
[http://www.ubuntuforums.org/showthread.php?t=204728&highlight=libgl.so.1.2+ati]("http://www.ubuntuforums.org/showthread.php?t=204728&highlight=libgl.so.1.2+ati")


For XGL / Compiz I followed method two here: [http://www.compiz.net/viewtopic.php?id=389]("http://www.compiz.net/viewtopic.php?id=389")

**UPDATE:** The above link is where I got things working and where I have followed up with my success.  Be sure to read all my posts - it works - works fine, I just have to try to start compiz over and over until it starts once I am logged in (compiz --replace gconf)

Also, with this ATI card, to speed things up (once running), I turned off the screen "zoom out" (set it to zero) in the switcher plugin (alt+tab app switcher: gconf-editor /apps/compiz/plugins/switcher/....) and removed the animation from opening apps in from the panel (the wire frames you see when opening apps from the panel).  I'm on a friends WinXP laptop at lunch right now, so I can't check the gconf path for those.  Search for JedTheHead on these forums and you will find the related posts.

Good luck!!!

---

