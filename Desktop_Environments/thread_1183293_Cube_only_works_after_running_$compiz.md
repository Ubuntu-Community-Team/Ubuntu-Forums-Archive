---
title: "Cube only works after running $compiz"
date: 2009-06-09
forum: Desktop Environments
---

### Post by mhoy06 on 2009-06-09
I must be missing something simple. I had cube working perfectly on this machine right after I installed Ubuntu on it. Then, doing some troubleshooting, I uninstalled all compiz references in the synaptic manager. I know not the smartest way to go about trouble shooting but it was annoying me that my gvim window wasn't expanding right away. There was a delay in it. I was thinking I must have enabled something my video card can't handle.

Anyway I decided to try out cube again and ONLY cube. I hold down <ctrl><alt><left mouse button> and it won't rotate. But if I run the command 'compiz' my screen goes haywire and finally returns to normal and I can use cube again.

I have been using the ccsm command to launch the utility for managing the effects. My question is why aren't the effects taking place immediately after setting them up? Why is it necessary to run compiz from command line to make them work? If I reboot or log out I can't use cube. I have to enter the command again. 

I read the sticky and ran compiz-check and also have the output of 'compiz':
```

Gathering information about your system...

 Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc Mobility Radeon HD 3600 Series
 Driver in use:         fglrx
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia) 

```

I know it's probably not relevant to post compiz check considering it does actually work after manually running compiz, but I thought I'd post them here in case someone asks. Also here's the output of compiz:
```

Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1680x1050) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
Starting gtk-window-decorator

```

Any help appreciated.

---

