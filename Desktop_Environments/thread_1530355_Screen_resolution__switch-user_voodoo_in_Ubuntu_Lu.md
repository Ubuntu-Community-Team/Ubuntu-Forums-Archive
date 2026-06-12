---
title: "Screen resolution / switch-user voodoo in Ubuntu Lucid"
date: 2010-07-13
forum: Desktop Environments
---

### Post by yashaneiman on 2010-07-13
I ran into some cryptic trouble when trying to set my screen resolution. I hope the solution will help others.

I'm running Ubuntu 10.04, my video card is ATI Radeon HD 3450, and the monitor is LG Flatron W1952TQ.

The monitor's native resolution is 1440x900, which is too much both for my eyes and for the rest of my hardware. So I wanted to set a lower resolution with the same aspect ratio, e.g. 1280x800. The open-source driver that came with Ubuntu didn't recognize this resolution. The proprietary ATI driver did, but it caused weird display problems when switching users: the cursor turned into a large square, and another striped square appeared at a corner of the screen. So I gave up on the proprietary driver, and went to look for a patch using the open-source one.

The suggested ways to set a new resolution are:
1. Editing /etc/X11/xorg.conf - didn't work. It defaulted to the closest resolution recognized by the driver.
2. Using xrandr commands, as explained in [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution). This worked.

Now the question became how to apply the xrandr commands automatically. Again, I found two recommendations for where to place them:
1. In /etc/gdm/Init/Default
2. In /etc/X11/Xsession.d/45custom_xrandr_settings

Both options worked on the face of it, and by editing /etc/gdm/Init/Default it's possible to change the login screen's resolution as well. BUT - at this point, the login screen started freezing every time I switch back to a user that's already logged in. I saw several old threads describing similar symptoms, so this could be relevant. The problem might also apply to other resolutions which are recognized  by the driver (e.g. 1152x864), and not just my custom resolution, but  I haven't tested enough to be sure.

Eventually, I diagnosed that the login screen freezes unless the monitor's native resolution (1440x900) is used either upon the initial login, or the first user-switch. So after a few tries, here's the solution I came up with:

1. Add the following lines to /etc/gdm/Init/Default, before the line "IFS=$OLD_IFS":
```

xrandr --newmode "1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
xrandr --addmode DVI-1 1280x800@60

xrandr --newmode "1024x640@60" 51.90 1024 1056 1248 1280 640 653 660 673
xrandr --addmode DVI-1 1024x640@60

xrandr --output DVI-1 --mode 1280x800@60

```This creates two new resolutions, and sets one of them as the resolution of the login screen. (Use your name for the monitor output instead of DVI-1. You can find it by calling xrandr with no parameters.)

2. Write the following line in /etc/X11/Xsession.d/45custom_xrandr_settings (create the file if necessary):
```
xrandr --output DVI-1 --mode 1440x900
```This sets the resolution to the native one.

3. Set the desired resolution for each user through the GUI in System->Preferences->Monitors. The custom resolutions will appear in the list.

As a result, the line in /etc/X11/Xsession.d/45custom_xrandr_settings is enough to appease the login screen at the right time, but it gets overridden during login so that we only see the desired resolution. And now everything works. 

Damn.

---

### Post by uligraf on 2010-08-26
Solution 1 worked very well for me, but I had to find the modline (the numbers after --newmode in the line below). Found that this could be done using 
       [FONT=monospace]
cvt --verbose

maybe you could add this to your instructions.
[/FONT]

---

### Post by yashaneiman on 2010-09-05
Actually, I built the modelines using the web-based tool at:
[http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl)

---

