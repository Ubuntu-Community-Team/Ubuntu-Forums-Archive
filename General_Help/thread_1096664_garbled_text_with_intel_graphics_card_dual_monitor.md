---
title: "garbled text with intel graphics card dual monitor"
date: 2009-03-15
forum: General Help
---

### Post by clres on 2009-03-15
Hi All,

I have a problem with my lenovo T61, which carries an Intel GM965/GL960 graphics card. When using a dual monitor setup with different resolutions for laptop screen and monitor sometimes and only after a while the text becomes practically unreadable like this:

[http://picasaweb.google.com/clrrsnd/UntitledAlbum#5313358945599046610](http://picasaweb.google.com/clrrsnd/UntitledAlbum#5313358945599046610)

it affects all text, menus, terminal windows, etc. When I switch console (ctrl-alt-Fx) and back, it usually is fine again for a short while. 

This only happens in dual-monitor setup, I have xubuntu intrepid, xserver-xorg-video-intel version: 2:2.5.1-1ubuntu5~intrepid. 
My xorg.conf is pasted below.

Any ideas would be appreciated.


Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

Section "Device"
        Identifier      "Intel 965GM"
        Driver         "intel"

        Option          "monitor-VGA" "bar"
        Option          "monitor-LVDS" "foo"
EndSection

Section "Monitor"
        Identifier      "foo"

        Option        "Position" "0 1024"
EndSection

Section "Monitor"
        Identifier      "bar"

        Option "Above"  "foo"
        Option "PreferredMode"  "1280x1024"
        Option        "Position" "0 0"
EndSection

Section "Screen"
        Identifier    "Default Screen"
        Device        "965GM"
        Monitor       "foo"
        DefaultDepth  24
        SubSection "Display"
                Depth          24
                Modes         "1680x1050" "1280x1024"  "1024x768"   "640x480"
                Virtual                 1680 2074
        EndSubSection
EndSection

---

