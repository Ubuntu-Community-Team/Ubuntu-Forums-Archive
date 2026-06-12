---
title: "AutoMount HowTo?!?! (Workaround found)"
date: 2005-06-05
forum: Desktop Environments
---

### Post by Jvaldezjr on 2005-06-05
In GNOME, when I put a CD into the drive or plugged a USB/FIREWIRE device
into my PC, the device was mounted, and an icon popped up onto my desktop.

Nice feature, but I use KDE and it doesn't do that.  So if you use KDE the rest of this applies.

First I needed to make sure that my removable media was configured for
detection in my /etc/fstab file.  Without the correct lines, KDE will
not know what to do.

Explanation:
For you novices/newbies like me, heres what this means-
/dev/hdc is the device for my CD-ROM, /dev/hdd is my CD-RW
```
/dev/hdc        /media/Rcd	auto	ro,user,noauto,exec  0       0
/dev/hdd        /media/Wcd	auto	ro,user,noauto,exec  0       0

``` 
I have a firewire port connected to my motherboard and in Ubuntu by default pmount creates a mount point for ieee devices as /media/ieee1934device (something to that effect).  Here I just remapped it to /media/firewire so I know what it's plugged into.  (That way if I have more than one firewire device, like my IPOD, etc, they will get mapped to that point).
```
/dev/sdb2	/media/firewire	auto	noauto,user,exec,rw,sync	0	0
```
Instead when I open up "Storage Media" in Konqueror, a similiar thing happens.  When I plug my device into my PC it popped up as an unmounted device (i.e. "Unmounted Removable Medium").  When I double clicked the corresponding icon, KDE mounted it and I was able to use it as normal and an icon appeared on my desktop.

I do not know why this "plug and mount" feature in KDE does not operate like its GNOME counterpart, but at least now you have some way to get at your removable mediums.

There is a HAL applet in KDE you can add to your panel by right clicking on your panel/taskbar and select Panel Menu -> Add to Panel -> Applet -> Storage Media.  It will pop up with several mediums are, or are not mounted.  You can configure it to show whatever medium you want.

Alternatively you can also control what icons you want to have displayed on your desktop.  Right click your desktop and select "Configure Desktop".  In the left panel click on "Behavior" and select the Device Icons Tab.  If you want device icons to appear on your desktop, then make sure you click "show desktop icons".  Below that there will be a list of all devices KDE supports.  Putting a check mark in the box will put the appropriate icon on your desktop aswell.

As far as putting a CD in, or plugging in your IPOD and having an icon pop up ready for its use only works in GNOME with Ubuntu.  In KDE+Ubuntu/Kubuntu, it doesn't do that.  Other versions of linux might have that feature supported (Mandrake did when I used it over a year ago...) but I dont know which ones, and I'm a Ubuntu fan that would rather use KDE instead of GNOME.

Good Luck
JValdezjr

---

