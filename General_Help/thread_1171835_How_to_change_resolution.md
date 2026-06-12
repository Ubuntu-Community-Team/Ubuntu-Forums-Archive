---
title: "How to change resolution"
date: 2009-05-27
forum: General Help
---

### Post by DR AMD on 2009-05-27
I am completely new at Linux
After setup Ubuntu 9.04 X64..My pc run very well,but my resolution is 800x600 too low concerning me so I needed to increase it to 1024x768 but i found that the highest level for me is 800x600 i tried the following 
>>>>>> System>Performance>Display_______________no effect
>>>>>> followed this topic [http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)   but i get problem and had to restore my backup file
Although my device seems to be old and low I could work with higher resolution more than that on vista and xp
My pc component is 
AMD sempron 3000+ 1.8GH on M.B. Via K8M800-M2
512 MB ram
VGA s3g Unichrome pro IGP -built-in
I will be so greatful if you found a solution to my problem

---

### Post by CatKiller on 2009-05-28
Normally, resolution problems are caused by one of the monitor, the graphics card, or the graphics driver not passing the EDID information to X that lets it automatically set the correct refresh rate, and so it defaults to really low values that won't damage any monitors. You can manually set the values for your monitor by putting the VertRefresh and HorizSync ranges in your xorg.conf. You should be able to get these numbers from the manual or specifications for your monitor. These values go in the "Monitor" Section of xorg.conf.

You can edit xorg.conf with ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
gksudo gedit /etc/X11/xorg.conf
``````
Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync       aa-bb
        VertRefresh     cc-dd
EndSection

```You'll need to replace aa-dd with the values for **your** monitor.

---

### Post by Yellow Pasque on 2009-05-28
Install the updated openchrome driver from Ubuntu 9.10: [http://packages.ubuntu.com/karmic/xserver-xorg-video-openchrome](http://packages.ubuntu.com/karmic/xserver-xorg-video-openchrome)
If that doesn't work, try manually specifying the virtual screen size in xorg.conf: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/367442](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/367442)

---

