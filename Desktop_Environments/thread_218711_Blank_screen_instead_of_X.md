---
title: "Blank screen instead of X ?"
date: 2006-07-18
forum: Desktop Environments
---

### Post by xyuri on 2006-07-18
Bank screen after loading bit.

I have booted to the ubuntu desktop cd on both my machines which share the same monitor (Samsung SyncMaster 713n), one has a GeForce 4 and the other an X800 pro (one Nvidia and other ATI), but both get a blank screen where X should be loading.

I have (obviously) not installed this, it is running straight from the cd and being the unix noob that I am lack the knowlege to get this working properly...

Any assistance would be greatly appreicated. Thanks :)

---

### Post by mattisking on 2006-07-18
Sorry xyuri, but you have tried both machines using the final Ubuntu Dapper Live CD (which is also the installation CD)? What systems are you trying this from? I'll ask the first couple of easy questions. If I can help that's great. If not, some other, better techy user will certainly be able to help you better.

---

### Post by xyuri on 2006-07-19
Yes, it is the newest ubuntu desktop boot disk, and it acts the same on both machines, which share the same monitor, keyboard and mouse. (kvm setup).

The first is as follows:
Asus A7N8X-E Deluxe mobo
AMD Athlon XP 2600+
512MB RAM
Nvidia Geforce 4 440 MX (AGP 8x)

Second machine:
Asus N8X Deluxe mobo
AMD Athlon64 3600+
1024MB RAM
ATI X800 Pro (AGP 8x)

I currently have ubuntu running in a virtual machine and plan on deploying it as a desktop environment on the first machine mentioned above.

is there something I should be doing in addition to just running the disk?

Thank you for your response by the way :)

---

### Post by roshan.s on 2006-07-19
You might have X driver problem. Could you try the "safe graphics mode" option (or something similar) from the initial boot menu on the Desktop CD?

---

### Post by goobers on 2006-07-19
it might be a problem with the monitor- i get the same problem when booting a live cd in an iMac G3. Have you got another monitor to try?


try pressing CTRL+F1, then typing

```

sudo pico /etc/X11/xorg.conf

```

then under the section monitor, change HorizSync to 30-81
and under VertRefresh change it to 56-75

then save it and quit.

then type:

```

sudo /etc/init.d/gdm restart

```

I know its a really random suggestion, but it worked for me...

(i found out the refresh rates for your monitor by the way, they're not just random values :P i just figured as you're having the same prob on both computers, that might be it)

---

### Post by 3rdalbum on 2006-07-19
Add to the above poster's advice: Under Section "Device", change the driver to "vesa" if it isn't already.

---

### Post by xyuri on 2006-07-20
Thank you all for your help :)

I changed the config file as you two have said, but X will not load, it fails. The log file errors say that it could not find device /dev/wacom which afaik is an nvidia driver?

I have found this which only explains how to load the driver using the gui: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

But is there a way to do this from command line?

Almost there ... :rolleyes:

---

### Post by xyuri on 2006-07-20
Ok, so I rebooted and went away for a bit ... and when I returned GNOME was loading! Slowly though. Took about 10-15 minutes untill the desktop is usable ... This was unexpected because in a virtual machine it loaded as if it was already installed :-? 

Anyways, after modifying /etc/X11/xorg.conf again, reloading X works, although I cant go above 1024x768 which is not my monitor's native res.

Thats ok though I will look at my other X config file which is correct and make some modifications ;)

Thank you all for your help :) much appreciated.

---

### Post by goobers on 2006-07-20
If you need anymore help with this, just post up your xorg.conf

---

### Post by xyuri on 2006-07-20
Well, I added "1280x1024" to the list of resolutions at the "Display" subsections, but it caused a parsing error on that file, so just took it out to allow any resulution, which is ok but my monitor needs "1280x1024" but was starting with 1900 something which i just turn down. But, that setting only kicks in once gnome has started, and the login screen is still at that high res. Is there a way to turn it down?

---

### Post by goobers on 2006-07-20
In your xorg.conf, the first resolution listed for the default colour depth is used, try removing all resolutions higher than 1280x1024?

---

