---
title: "Compiz trouble"
date: 2009-06-19
forum: Desktop Environments
---

### Post by M3TAL1QU1D on 2009-06-19
Hmmm... After some messing around I was able to install compiz. After enabling the effects, i began to realise only some of them are working and some aren't (such as the 3D cube for example). So I set out to find some answers. I found the website that shows you how to check if compiz is working on your system and this is what i get:

> dylan@dylan-laptop:~$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc Mobility Radeon HD 3400 Series
 Driver in use:         fglrx
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia) 


I have also read too that ubuntu does not seem to play well with ATI... But, i do have some of the effects working. 

Is it possible to get the rest by using a sort of rendering method since it states i have none? 

If so, how do i go about this? I am a bit of a noob too btw. 

Thanks for any help and it is definitely appreciated!

---

### Post by M3TAL1QU1D on 2009-06-20
anyone...?

---

### Post by M3TAL1QU1D on 2009-06-22
Ok, i did a fresh reinstall on the system and ran the check again without setting up the fglrx driver and this is what i came up with...

> ubuntu@ubuntu:~$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc Mobility Radeon HD 3400 Series
 Driver in use:         radeon
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Software Rasterizer in use 



I don't quite understand the above error... Can anyone help???

---

### Post by raymondvillain on 2009-06-23
I have the same problem.

> ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc Radeon HD 3200 Graphics
 Driver in use:         radeon
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Software Rasterizer in use 


What is to be done?

If I select system>preferences>appearance>visual effects tab the only option is "none".  Selecting normal or extra gets me message box that says "desktop effects could not be anabled.

Any and all suggestions would be greatly appreciated.

---

