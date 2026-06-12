---
title: "DisplayLink monitor ignores xorg.conf settings"
date: 2011-02-03
forum: Desktop Environments
---

### Post by robodude666 on 2011-02-03
Hey guys,

I've got the [Ubuntu Maverick 10.10 demo image]("http://elinux.org/BeagleBoardUbuntu#Maverick_10.10_2") on a BeagleBoard C3. I installed the DisplayLink drivers based on [Mulchman's blog post]("http://mulchman.org/blog/?p=90"). Everything worked fine before I had a GUI installed. I would startx and the terminal would appear on the DisplayLink monitor (DoubltSight DS-70U).

I then tried to install the GUI using the following command:

```

sudo apt-get install xfce4 gdm xubuntu-gdm-theme xubuntu-artwork xserver-xorg-video-omap3

```

After restarting, I saw the screen fade from black to a dark brown and a cursor appeared, but no login window. In fact, the login box appears to be outside of the view area:

[img]http://i55.tinypic.com/29llbhw.jpg[/img]

You can see the cursor in the center, and the white strip in the top left corner I believe is the bottom right corner of the login box.

Below is my /etc/X11/xorg.conf file:

```

#################################################                                                                 

Section "ServerLayout"
        Identifier      "Server Layout"
        Screen  0       "DisplayLinkScreen" 0 0
		Option "Xinerma" "off"
EndSection

#################################################                                                                 

Section "Files"
        ModulePath      "/usr/lib/xorg/modules"
        ModulePath      "/usr/local/lib/xorg/modules"
		ModulePath		"/usr/local/lib/xorg/modules/drivers
EndSection

############### DisplayLink Stuff ###############                                                                 

Section "Device"
        Identifier      "DisplayLinkDevice"
        driver          "displaylink"
        Option  "fbdev" "/dev/fb3"
EndSection

Section "Monitor"
        Identifier      "DisplayLinkMonitor"
EndSection

Section "Screen"
    Identifier      "DisplayLinkScreen"
	Device          "DisplayLinkDevice"
	Monitor			"DisplayLinkMonitor"
	SubSection "Display"
		Depth 24
		Modes "800x480"
	EndSubSection
EndSection

```

The 800x480 resolution I selected seems to be ignored by the DisplayLink monitor. If I use the following xorg.conf based on the [recommended](http://elinux.org/BeagleBoardDebian#Xorg_omapfb_Drivers) file for the BeagleBoard:

```

Section "ServerLayout"
        Identifier      "Server Layout"
        Screen  0       "Default Screen" 0 0
EndSection

Section "Monitor"
    Identifier "Configured Monitor"
EndSection

Section "Screen"
    Identifier "Default Screen"
    Device "Configured Video Device"
    DefaultDepth 16
EndSection

Section "Device"
    Identifier "Configured Video Device"
    Driver "omapfb"
    Option "fb" "/dev/fb0"
EndSection

```

the Beagleboard uses the HDMI output (defaults to 1280x720) and works fine.

Any thoughts? I've been scratching my head for a few days on this.

Cheers,
-robodude666

---

