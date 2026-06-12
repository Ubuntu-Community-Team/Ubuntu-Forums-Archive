---
title: "screen resolution"
date: 2009-11-19
forum: Desktop Environments
---

### Post by highinthemountains on 2009-11-19
i just installed 9.10. i am pretty satisfied with it overall, but the desktop screen resolution is driving me crazy. in 9.04 i was able to set a screen resolution for my radeon 9200 card to 1152x864. the only choices i have now are 1024x788 and 1280x1024. the former is too large and the latter is too small, and it's giving me eyestrain. yes, i have played with the fonts and still have eyestrain.

in the past i was able to edit the xorg.conf file to get the screen the way i wanted to, but that file doesn't exist any more. i want my screen to be THE WAY I WANT IT, not how some programmer thinks it should be!

how can i fix this? i'm using the xserver-xorg-video-ati drivers set without the fglrx stuff. i have tried it both with and without it and i get the same resolutions. my monitor, acer al1706, will do this resolution because i have it set to that on my windoze box.

while on the subject of screen resolution, why does ubuntu pick the highest resolution possible to start the boot process? all i get are out of range messages and i can't watch what is going on during boot up. how about picking a lower resolution for boot up and then switching to a higher resolution when the desktop comes up?

---

### Post by highinthemountains on 2009-12-22
isn't there anyone else is having this problem?

---

### Post by bzhao on 2009-12-22
Please make sure use your card driver, and the google search to find out below paramerters(HorizSync,VertRefresh) for your monitor and put them into xorg.conf and then reboot.

The below is my one. 

Section "Monitor"
Identifier "Monitor0"
VendorName "Unknown"
ModelName "PHILIPS 107E5"
HorizSync 30.0 - 71.0
VertRefresh 50.0 - 160.0
EndSection


I also met the same issue as you with Nvidia card.
The problem is caused by your driver cannot communicate with monitor correctly. maybe the driver is not so good, maybe your cable is broken.

For your second question:
you may need to add "Mode line" in xorg.conf like below:

    SubSection "Display"
                Viewport   0 0
                Depth     24
                Modes "1024x768" "800x600"
    EndSubSection


Bill Z

---

### Post by smo0th on 2009-12-22
hi highinthemountains, I agrre with this > while on the subject of screen resolution, why does ubuntu pick the highest resolution possible to start the boot process? all i get are out of range messages and i can't watch what is going on during boot up. how about picking a lower resolution for boot up and then switching to a higher resolution when the desktop comes up?

About your screen configuration you wanna check these files
```

/etc/gdm/gdm.conf
/etc/X11/xorg.conf
```

And use the following command if something gets screwed up:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

That's what I recall at the moment.

---

### Post by highinthemountains on 2009-12-23
umm, i guess the original question wasn't read too closely... THERE ISN'T A XORG.CONF FILE IN 9.10!

in 9.04 there was a xorg.conf file.

oh well, i guess i'm doomed to eyestrain.

---

### Post by slumbergod on 2009-12-24
You can add an xorg.conf yourself in /etc/X11/

The geniuses behind the newest version of xorg or whatever it is no longer include a conf file because auto-detection is supposed to get it right the first time. Bad news is that it doesn't always work. One of my machines worked perfectly, one needed me to paste the following into a newly created file to force the VIA openChrome video driver to display properly. 

Section "Device"
      Identifier "Configured Video Device"
      Option "PanelSize" "1024x600"
EndSection

I think you need to decide which is the problem first...the screen resolution OR the panel size you are displaying it on.

---

