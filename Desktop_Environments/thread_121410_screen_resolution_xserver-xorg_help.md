---
title: "screen resolution xserver-xorg help"
date: 2006-01-25
forum: Desktop Environments
---

### Post by bobbymcsteels on 2006-01-25
Hi, have just installed kubuntu 5.10 breezy but when the login page comes up its all pink/orange and I cant make out anything. I had this problem a while back with hoary 5.04 and cant remember how I sorted it. Have tried this:-

ctl+alt+f1
```
sudo /etc/inint.d/kdm stop
sudo dpkg-reconfigure -phigh xserver-xorg
```

changed the resolution then


```
sudo /etc/inint.d/kdm start
```
 and still nothing
Any help would be great.

---

### Post by heimo on 2006-01-25
Hi!

Here's a howto to get some ideas:
[http://www.ubuntuforums.org/showthread.php?t=83973](http://www.ubuntuforums.org/showthread.php?t=83973)

More information of your system would be helpful. Mainly: graphics card and monitor make / model. Also check the logs (see link above) for hints of what could be wrong.

---

### Post by bobbymcsteels on 2006-01-25
sorry...
amd64 athlon 3200+
graphics card is nvidia 6600gt monitor is... digimate something not too sure on the model number its 17 inch tho.... Cant remember if i said in the last post that I ahd this trouble before and sorted it out, it was where you select the screen resolution in xserver-xorg, I cant remember what res I set it to last time I used ubuntu, I wrote the res down on the hoary cd that worked but I cant find the cd :S I'm sure it was 1280x1080 but I have tried that and has not worked.

---

### Post by heimo on 2006-01-25
If it's "cathode ray tube" CRT (not LCD/TFT) and 17", it probably can do 1024x768 nicely and it may be able to do 1280x1024 with lower refresh rate. I'd try the 1024x768 first. If it's TFT, it's probably 1280x1024.

---

### Post by bobbymcsteels on 2006-01-25
forgot to meantion that it was tft, tried 1280x1024 1st and didnt work and I was sure that was the rez i set it to when I 1st got ubuntu to work.... but doesnt seem to like it or work with breezy.... could it be a bug or something??

This is the monitor
[http://www.digimate.co.uk/product_new/monitor/lcd/L-1715.htm](http://www.digimate.co.uk/product_new/monitor/lcd/L-1715.htm)

have downloaded the user manual and checked the refresh rates
v 30-62
h56-75
@75hz

not sure if that will help

---

### Post by heimo on 2006-01-25
Did you check your xorg.conf file (see the link in my earlier post) has these values for horizsync and vertrefresh?

---

### Post by bobbymcsteels on 2006-01-25
no it didnt(cant remeber them) should I change them to these values??

Was looking at the modeline generators..... Would they help me in this situation??

---

### Post by heimo on 2006-01-25
[quote=bobbymcsteels]no it didnt(cant remeber them) should I change them to these values??
[/quote]
I would.

[quote=bobbymcsteels]
Was looking at the modeline generators..... Would they help me in this situation??[/quote]
Yeah, give it a try. You should not need it, but in reality this has helped many to solve their resolution/refresh rate problems.

---

### Post by bobbymcsteels on 2006-01-26
ok tried that...
changed hor and vert values to the ones listed in my monitor user manual, still nothing.
Added what I got from the modeline gen at the bottom of monitor section, nothing, changed resolution values back to original and left modeline in there, nothing.

Is there anyway to test the resolution and save it if you want it.... something similar in Suse 9.x has this?

---

### Post by bobbymcsteels on 2006-01-26
ok just install fedora core 3(cos i know it works 1st time) and copied this from the xorg.conf

```
Section "Monitor"
        Identifier   "Monitor0"
        VendorName   "Monitor Vendor"
        ModelName    "Unknown monitor"
        HorizSync    31.5 - 37.9
        VertRefresh  50.0 - 70.0
        Option      "dpms"
EndSection

Section "Device"
        Identifier  "Videocard0"
        Driver      "vesa"
        VendorName  "Videocard vendor"
Section "Screen"
        Identifier "Screen0"
        Device     "Videocard0"
        Monitor    "Monitor0"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     16
                Modes    "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     24
                Modes    "800x600" "640x480"

```

So I am gonna try and apply this setting to my ubuntu xorg.conf and see what happens.... I will let you know how I get on.

---

### Post by bobbymcsteels on 2006-01-26
worked nicely

I think it was the GPU driver 
kubuntu had "nv"

and fedora had "vesa" think that is what did it

cheers for the help.

---

