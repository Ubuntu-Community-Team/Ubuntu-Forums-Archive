---
title: "desktop effects could not be enabled (again!)"
date: 2009-08-02
forum: Desktop Environments
---

### Post by Paperfairy on 2009-08-02
This is the same old bug from before - they worked in Intrepid but refuse to work in Jaunty. I have tried installing he xorg intel 2.4 drivers, I tried turning off blacklisting from Compiz, and just about everything else short of reinstall.

I should point out that when I FIRST switcheed to Jaunty, disabling the blacklist worked, but after trying to install compiz-fusion, it stopped. I assume I either accidentally removed a dependency or I messed up a configuration file. BTW, I did attempt to recreate my xorg.conf, but to no avail.


```

Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1440x900) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz: 455: /usr/bin/compiz.real: not found

```


```

Gathering information about your system...

 Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

```


any ideas?

---

### Post by rainwalker on 2009-08-02
If I had to guess I would blame your video card; I haven't heard anything good about Intel video drivers in Jaunty. If you haven't already, I would recommend looking into rolling back to a previous driver version.

---

### Post by Paperfairy on 2009-08-02
Could you walk me through that process?

---

### Post by rainwalker on 2009-08-02
> **Paperfairy said:**
> Could you walk me through that process?

I actually have no idea how to do it, because I've never had an Intel card :?
I know you're not the only one who has had issues, though, so I'm sure you could find someone who has already done it on the forums or even Google. Sorry I can't be more help than that :(

---

### Post by Paperfairy on 2009-08-02
Thanks. The Google has proven usless, hopefully bumping this will help~

---

### Post by rainwalker on 2009-08-02
Found these with google, might be worth checking out:
[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)
[http://www.myubuntu.ca/?p=256&cpage=1](http://www.myubuntu.ca/?p=256&cpage=1)
[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

---

### Post by Paperfairy on 2009-08-02
For anybody curious, none of the aforementioned had any impact.

---

### Post by Paperfairy on 2009-08-09
I believe a bump is in order?


Used sudo apt-get install compiz and it seems to have worked.

---

