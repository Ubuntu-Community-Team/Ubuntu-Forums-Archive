---
title: "[SOLVED] 'Corrupt' lines on desktop in x"
date: 2008-01-22
forum: Desktop Environments
---

### Post by sandr- on 2008-01-22
Hey everybody, let me please desbribe my situation:

I'm using gutsy ubuntu on a toshiba notebook. Installation, configuration, etc all went smoothly, also the desktop effects. When I'm at home I hook my laptop up to a dockingstation and my widescreen monitor ( samsung syncmaster 22" ).
To switch between 'setups': notebook only, monitor only : I use xrandr to turn off a certain display.

So far my current situation and needs. The problem i'm having can be seen in this [picture]("http://imagebin.ca/img/BkZQWTh.png") or on this [video ]("http://users.telenet.be/sandr/video.avi")( bad quality, don't blame me ). As you can see I get this weird, annoying lines on my desktop: while on desktop, while browsing, while watching movies, ... 
I get no lines when not using x ( terminal ) so it isnt my hardware. The lines come up when i'm at the loginscreen, disappear while the system is logging me on ( ubuntusound etc ), but then reappear when I'm logged on and my desktop is shown.

**Edit**
*I'm pretty sure now it has something to do with xrandr: when I don't use xrandr, while dualheading, I don't have any lines. The problem is: I need xrandr to work! Does anyone know what's wrong with my **xrandr** ? Thanks !*

Can someone help me please? Thanks in advance !

**_xrandr output_**
```

sander@sander-laptop:~$ xrandr
Screen 0: minimum 320 x 200, current 1680 x 1050, maximum 1680 x 1680
VGA connected 1680x1050+0+0 (normal left inverted right) 474mm x 296mm
   1680x1050      60.0*+   59.9  
   1280x1024      75.0     59.9  
   1280x960       59.9  
   1152x864       75.0     74.8  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     66.7     60.0  
   720x400        70.1  
LVDS connected 1280x800+0+0 (normal left inverted right) 331mm x 207mm
   1280x800       60.0*+   60.0  
   1280x768       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
TV disconnected (normal left inverted right)

```

**_xorg.conf_**
```
Section "Device"
        Identifier      "Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics
 Controller"
        Driver          "intel"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics
 Controller"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1680x1050" "1200x800" "1024x768"
        EndSubSection
EndSection

```
And these are the commands I use for switching from notebook to monitor
```
xrandr --output VGA --auto && xrandr --output LVDS --off
compiz
```
And from monitor to notebook
```
xrandr --output LVDS --auto && xrandr --output VGA --off
compiz
```

---

### Post by sandr- on 2008-01-23
I found out the solution to this problem after extensive search on the xrandr configuration.
The problem was this line in xrandr output:
```

Screen 0: minimum 320 x 200, current 1680 x 1050, maximum 1680 x 1680

```
As you can see the maximum output defined is 30 pixels 'higher' then my actual screensize.
After adding the marked line in my xorg.conf, everything works like a charm !
```
Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation Mobile 945GM/GMS, 943/940GML Express 
Integrated Graphics Controller"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1680x1050" "1200x800" "1024x768"
                **Virtual 2048 2048**
        EndSubSection
EndSection
```

I keep subscribed to this thread, so should anyone ever have the same problem I did, I'll be glad to help out.

---

