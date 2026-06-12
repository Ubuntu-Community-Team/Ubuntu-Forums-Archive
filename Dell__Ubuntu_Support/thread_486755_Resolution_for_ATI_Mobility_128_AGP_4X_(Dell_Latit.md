---
title: "Resolution for ATI Mobility 128 AGP 4X (Dell Latitude C800)"
date: 2007-06-28
forum: Dell  Ubuntu Support
---

### Post by kensan on 2007-06-28
I need help setting screen resolution in xorg.conf on Kubuntu 7.04 for the ATI Mobility 128 AGP 4X graphics in my Dell Latitude C800.  

I've found the specifications at <[http://www.ualr.edu/fsrc/Equipment](http://www.ualr.edu/fsrc/Equipment) Pictures/Lattitude C800 User's Guide/specs.htm#video> but haven't had much success editing xorg.conf.  

I changed the refresh rates until I finally got 1600x1200 working with xorg.conf.1.txt (see attachment).

I can't get any other resolution working, so I'm stuck with 1600x1200.  I tried to use kcontrol to reconfigure my settings for the detected ATI Rage 128 Mobility graphics card, but the resulting xorg.conf.2.txt (see attached) doesn't work (graphics ripped in 3 vertical/overlapping bands).

Can someone please help me correct my xorg.conf so I can use display modes other than the 1600x1200 I'm stuck with.  I've installed the fglrx upgrade.  I'm totally new to Kubuntu and haven't used Linux since the very early years.

Thanks for any help.

---

### Post by Rocket2DMn on 2007-06-28
The typical way to reset screen resolutions is to run the command
```
sudo dpkg-reconfigure xserver-xorg
```
This will take you through hardware setup.  When you get to the resolution page, you should enable the resolutions you monitor supports (usually the maximum plus the resolutions less than that.
You will then have to restart the xserver.  close out yout programs and hit CTRL+ALT+BACKSPACE.

You can make a backup of your xorg.conf file first like so:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
if the setup fails for some reason, you can restore your backup:
```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```

---

### Post by kensan on 2007-06-28
Thanks Rocket2DMn, but my xorg.conf.1.txt was created using the "dpkg-reconfigure xserver-xorg" method you describe.

---

### Post by phuncadelic on 2008-01-23
I had the same issue and I made the following changes (I found them on a fedora forum:

Section "Monitor"
...
    HorizSync     31.5 - 90.0
    VertRefresh     59.0 - 75.0
...
End Section

Section "Screen"
...
    SubSection "Display"
        ...
        Modes    "1400x1050"
        ...
    EndSubSection
...
EndSection

---

