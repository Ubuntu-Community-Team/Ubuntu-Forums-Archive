---
title: "Desktop Effects not working with brand new AMD64 processor with integrated video"
date: 2009-01-02
forum: General Help
---

### Post by toret5 on 2009-01-02
For Christmas, I received the parts to build my own machine.  I've used Ubuntu in the past and decided not to give Microsoft more money so I installed it on my machine.  However, I've seen desktop effects before, and my computer should be capable enough to run them, but when I try to enable them a box comes up that searches for drivers and then it simply says desktop effects cannot be enabled.  I have searched around but all I have found were solutions that didn't work.  I think I have narrowed down the problem to me running a software rasterizer and not the correct driver for my integrated video.

Trying to run compiz shows:
> Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1152x864) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: present. 
Software rasterizer detected, abortingaborting and using fallback: /usr/bin/metacity 


Compiz check shows:

> Gathering information about your system...

 Distribution:          Ubuntu 8.10
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


To solve the problem, I have heard to either install envyng or ATI Catalyst Proprietary Linux x86_64 Display Driver.  I tried installing envyng, but linux wouldn't load which forced me to reinstall the OS, Also, I have found more information about the proprietary display driver but it won't install, I get this message:
> Could not open the file /home/michael/Desktop/at&#8230;aller-8-12-x86.x86_64.run using the Unicode (UTF-8) character coding.

Long story short, I'm at a loss for what else to try.  If anyone has any ideas I'd greatly appreciate your effort.

---

