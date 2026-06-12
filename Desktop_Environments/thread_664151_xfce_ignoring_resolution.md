---
title: "xfce ignoring resolution"
date: 2008-01-10
forum: Desktop Environments
---

### Post by kpkeerthi on 2008-01-10
```

Section "Device"
        Identifier      "Generic Video Card"
        Driver           "vboxvideo"
        BusID           "PCI:0:2:0"
EndSection

```
```

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1440x900" "1280x800" "1024x768"
        EndSubSection
EndSection

```

This is in xubuntu on virtualbox. As you can see I have 1440x900 as the first resolution. The GDM (login manager) is set to 1440x900. But after I login xfce resets to the next lower resolution found in xorg.conf i.e. 1280x800. I checked Desktop -> Settings -> Display Settings. 1440x900 does not exist there. 
[[IMG]http://img174.imageshack.us/img174/6043/screenshotgy5.th.jpg[/IMG]](http://img174.imageshack.us/my.php?image=screenshotgy5.jpg)

I thought may be I should also keep 1680x1050 in xorg.conf. So ran dpkg-reconfigure -phigh xserver-xorg and chose 1680x1050, 1440x900 and 1280x800. This time gdm is at 1680x1050 and after login xfce desktop goes to the next lower resolution i.e. 1440x900.

No matter what, when gdm is at resolution 'x', xfce goes to 'x-1' after login. Desktop -> Settings -> Display Settings also has only 'x-1', 'x-2'... 'x-n'. Why is it ignoring the 'first preferred' resolution. How to I set gdm and xfce use the same resolution? Quite annoying when GDM appears larger and then the screen dances when the resolution scales down. 

Any help is much appreciated.

---

### Post by kpkeerthi on 2008-01-14
Anyone? 
Sorry for bumping this post but I would like to see this fixed.

---

### Post by calixtine on 2008-06-18
It's not immediately obvious from the GUI of the XFCE Display Preferences applet but the "Default" line is not a column header but the default resolution set in the xorg.conf file. In your case that would be 1440x990, in your screenshot you have it set to the next resolution down. This fooled me which is why I came to your post after a google search. I'm surprised that after re-configuring X it still picked the second resolution in the list but I suppose it's possible.

---

