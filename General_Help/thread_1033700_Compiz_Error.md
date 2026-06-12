---
title: "Compiz Error"
date: 2009-01-07
forum: General Help
---

### Post by anxiousdog on 2009-01-07
I get the following error when I try to run Compiz:

```
anxiousdog@ubuntu1:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: Segmentation fault
not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: Segmentation fault
not present. 
aborting and using fallback: /usr/bin/metacity 
```

I noticed today that when I upgraded my Nvidia drivers and rebooted, my AWN dock won't start. Or, it's starting but not showing. I assumed it was an issue with Compiz so I checked and got the above error.

Also, when I try to run compiz, the window bars disappear and my keyboard stops working. I log out and back in and things look normal (except no AWN).

---

### Post by Forlong on 2009-01-07
Please post the output of this: [http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)

---

### Post by gettinoriginal on 2009-01-07
Have you checked System > Admin > Hardware Drivers, sometimes during a driver change it becomes deactivated, just reactivate it and all should be fine. (if thats the problem) :P

---

### Post by anxiousdog on 2009-01-07
> **Forlong said:**
> Please post the output of this: [http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)

Thanks for the script, it's great! 

Of course, the output... well... not so much: 

```
Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation NV44A [GeForce 6200] (rev a1)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [FAIL]
 Checking for non power of two support...          [FAIL]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [FAIL]
 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: Unable to detect maximum 3D texture size 

```

---

### Post by anxiousdog on 2009-01-07
Also I ran this:

```
anxiousdog@ubuntu1:~$ dpkg -l | grep 'nvidia\|fglrx'
ii  nvidia-173-modaliases                      173.14.12-1-0ubuntu4                    Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-177-kernel-source                   177.82-0ubuntu0.1                       NVIDIA binary kernel module source
ii  nvidia-177-modaliases                      177.82-0ubuntu0.1                       Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-71-modaliases                       71.86.04-0ubuntu10                      Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-96-modaliases                       96.43.09-0ubuntu1                       Modaliases for the NVIDIA binary X.Org drive
ii  nvidia-common                              0.2.4                                   Find obsolete NVIDIA drivers
ii  nvidia-glx-177                             177.82-0ubuntu0.1                       NVIDIA binary Xorg driver
ii  nvidia-glx-177-dev                         177.82-0ubuntu0.1                       NVIDIA binary Xorg driver development files
rc  nvidia-glx-new                             169.12+2.6.24.14-21.51                  NVIDIA binary XFree86 4.x/X.Org 'new' driver
rc  nvidia-kernel-common                       20051028+1+nmu2ubuntu2                  NVIDIA binary kernel module common files
ii  nvidia-settings                            177.78-0ubuntu2.1                       Tool of configuring the NVIDIA graphics driv

```

---

### Post by Forlong on 2009-01-07
It appears you have the intrepid-updates repository enabled, is there any particular reason for that?

---

### Post by anxiousdog on 2009-01-07
Probably because I'm using Intrepid and they were turned on? Should that cause a problem?

---

### Post by Forlong on 2009-01-07
No, sorry... I meant intrepid-proposed. But that's not the case.
Forget what I said. Gotta go to bed now. ;)

Your problem is purely driver related.
I'd suggest starting a thread in the proper section with a descriptive title, that your Nvidia card is no longer working after an update.

Good luck.

---

### Post by gettinoriginal on 2009-01-08
Don't know if this helps, but I also run intrepid, and my compiz works fine, and this is the result of mine:
```
~$ dpkg -l | grep 'nvidia\|fglrx'
ii  fglrx-modaliases                           2:8.552-0ubuntu0.1                          Identifiers supported by the ATI graphics driver
ii  nvidia-173-kernel-source                   173.14.12-1-0ubuntu5.1                      NVIDIA binary kernel module source
ii  nvidia-173-modaliases                      173.14.12-1-0ubuntu5.1                      Modaliases for the NVIDIA binary X.Org driver
ii  nvidia-177-modaliases                      177.82-0ubuntu0.1                           Modaliases for the NVIDIA binary X.Org driver
ii  nvidia-71-modaliases                       71.86.04-0ubuntu10                          Modaliases for the NVIDIA binary X.Org driver
ii  nvidia-96-modaliases                       96.43.09-0ubuntu1.1                         Modaliases for the NVIDIA binary X.Org driver
ii  nvidia-common                              0.2.4                                       Find obsolete NVIDIA drivers
ii  nvidia-glx-173                             173.14.12-1-0ubuntu5.1                      NVIDIA binary Xorg driver
ii  nvidia-kernel-common                       20051028+1+nmu2ubuntu2                      NVIDIA binary kernel module common files
ii  nvidia-settings                            177.78-0ubuntu2.1                           Tool of configuring the NVIDIA
```

---

### Post by anxiousdog on 2009-01-08
Thanks for the help... I don't really know what's going on and I'm a little frustrated. I'll have to read more and see if I stumble upon a fix. Ugh.

---

### Post by sceo on 2009-01-09
+1 on this exact same problem.  I upgraded the drivers through regular synaptic updates (to the newest 177) and then I lost my config.  I struggled and, using Envy-NG, was able to get my drivers installed again just fine and get TwinView back and working.

However, compiz won't really work - exact same behavior as described above.

---

### Post by sceo on 2009-01-09
After upgrading a couple days ago to the newest 177 via Synaptic, I lost all my config.  I finally used envy-ng to reinstall the latest 177 and get my config back (I have dual monitors using TwinView on an NVidia 7600GS).

Except, compiz/AWN - everything as described above in the first post is the same behavior I see.  I have SKIP_CHECKS=yes from before I got the nVidia and wanted to use Compiz with my on-board Intel, and so I get this output:

> 
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: Segmentation fault
not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: Segmentation fault
not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for Software Rasterizer: Segmentation fault
Not present. 
Checking for nVidia: present. 
Checking for FBConfig: Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Segmentation fault
not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for Xgl: not present. 
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
/usr/bin/compiz.real (core) - Fatal: glXCreateContext failed
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0


---

