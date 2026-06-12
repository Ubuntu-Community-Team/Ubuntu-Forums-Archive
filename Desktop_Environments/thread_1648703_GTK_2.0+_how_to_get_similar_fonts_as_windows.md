---
title: "GTK 2.0+: how to get similar fonts as windows ?"
date: 2010-12-19
forum: Desktop Environments
---

### Post by honeybear on 2010-12-19
Please find the cool fonts that I would like to have for the whole fonts of linux. (fonts into ultraiso, menu... )
their size is cool too

Any help for those fonts is welcome. 

Wishign a nice day

---

### Post by 3Miro on 2010-12-19
I am not sure I understand exactly what the problem is. You can check this link, if you install only the GTK desktop theme you will get the windows fonts only (you don't have the install the rest and I am not sure even if it will install on Ubuntu 10.10).

[http://ubuntuforums.org/showthread.php?t=1571371](http://ubuntuforums.org/showthread.php?t=1571371)

If this doesn't help, can you elaborate on what is it that you want.

---

### Post by Laysan_A on 2010-12-19
I think she just wants a better font collection...

Go into your package manager and search fonts. There are several packages available in the various repositories. Make sure you have the universe and multiverse repositories checked in sources.
(Don't get font packages for specific programs, look for something more general in nature).

---

### Post by honeybear on 2010-12-21
> **Laysan_A said:**
> I think she just wants a better font collection...

Go into your package manager and search fonts. There are several packages available in the various repositories. Make sure you have the universe and multiverse repositories checked in sources.
(Don't get font packages for specific programs, look for something more general in nature).

hello, 

yeah indeed. A finer font collection closer to that shot would be great. I use now 
Liberation or others. but well, not that cute as windows xp for instance 

 ```
~$ ls -1 .fonts/
aquafont.ttf
aqua_pfont.ttf
ATARCC__.ttf
ATARCE__.ttf
ATARCS__.ttf
digitalk-mono.ttf
Lucida_Grande_Bold.ttf
```



@ the link you gave , the font are not so so great. big and not sharp
[http://linux.softpedia.com/screenshots/Win2-7_1.jpg](http://linux.softpedia.com/screenshots/Win2-7_1.jpg)

kidn regards

---

### Post by Laysan_A on 2010-12-22
Here's a couple of resources for you: [ Here]("http://ubuntuforums.org/showthread.php?t=694039") and [ here.]("http://embraceubuntu.com/2007/05/21/300-easily-installed-free-fonts-for-ubuntu/")

The link to the open font library (referenced in one of the pages I gave you) is old. [ Here](http://openfontlibrary.org/) is a new one.

---

### Post by kwiadnyana on 2011-02-19
Your question is:

Re: GTK 2.0+: how to get similar fonts as windows ?

I wonder if the real question that you want to ask is what the best font settings to have a "windows" look on your desktop.

I struggled with this when I first installed Ubuntu 8.04 (yes, that ancient), I fixed it by downloading and everything was fine and dandy until I upgraded to Ubuntu 10.10 netbook. Downloading msttcorefonts didn't fix it, nor installing tahoma.ttf (which is not included in msttcorefonts).

So, the problem lies in the settings of the fonts, really. It may depend on your hardware, but it may be worth your time to investigate your font types, smoothing, hinting, and RGB as well as DPI settings. These are all available from within "Apearance" under system menu in ubuntu.

I found that I like these 2 settings better:

1. Use these settings:
- application font: sans 10
- document font: sans 10
- desktop: sans 10
- windows: sans bold 10
- fixed width: monospace 10
advanced settings are: 96 dpi, no smoothing, full hinting, RGB.

2. Another set of settings that may work (after installing tahoma to mimic windows):
- use tahoma 8 for application, document, desktop
- use trebuchet ms 10 for desktop
- fixed width: monospace 10
This is basically the same settings with my windows.

Another thing is that fixed width seems to be ugly either way, so I tried Andale Mono (mono seems to mean fixed width).

Good luck!
kwiadnyana

---

