---
title: "Unable to use Compiz Destop effects"
date: 2009-05-28
forum: Desktop Environments
---

### Post by abhilash82 on 2009-05-28
I've been using Compiz desktop effects till I upgraded to Ubuntu 9.04.

Now I get the message that its not possible to enable Desktop effects any more.

Any other configuration changes required to activate the desktop effects?

My PC configuration is 
Intel 865GBF with 2.40GHz, 512MB RAM

---

### Post by tacticalbread on 2009-05-28
have you checked here?
[http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)

---

### Post by x33a on 2009-05-28
since you did an upgrade, most likely your graphics drivers are broken and hence the error.

try installing the latest version of your graphics drivers.

---

### Post by abhilash82 on 2009-05-29
This is what I get when I run compiz,

```
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: present. 
Software rasterizer detected, abortingaborting and using fallback: /usr/bin/metacity
```

This is the output for compiz-check.

.```
/compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation 82865G Integrated Graphics Controller (rev 02)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Software Rasterizer in use
```

 What might be the reason for this?

---

### Post by abhilash82 on 2009-06-02
Can someone help me with this issue.

---

### Post by overdrank on 2009-06-02
> **abhilash82 said:**
> Can someone help me with this issue.

Hi and have you seen the [HOWTO: Jaunty Intel Graphics Performance Guide]("http://ubuntuforums.org/showthread.php?t=1130582")

---

