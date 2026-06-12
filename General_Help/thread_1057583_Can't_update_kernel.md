---
title: "Can't update kernel"
date: 2009-02-01
forum: General Help
---

### Post by bluejeansummer on 2009-02-01
I've been putting off asking this question in hopes that a newer kernel would fix this, but it's no use. In GRUB, I have several different kernels listed, but the only one that will actually boot is the oldest one on the list, 2.6.24-19-generic. When I try to boot any other kernels, the loading bar stops at 5-10%. When I try recovery mode, lots of text scrolls by, and then the screen is filled with "Segmentation fault", interspersed with occasional messages that are gone too quickly to read. I really need to get a more recent kernel to work, because my Nvidia driver quit working, and I need the headers to recompile it. However, the headers for my kernel are no longer in the repos. Does anybody have any idea what's wrong?

EDIT: I'm running a Dell Optiplex 260.

---

### Post by lidex on 2009-02-02
What version of Ubuntu do you have installed?

---

### Post by bluejeansummer on 2009-02-02
I run 8.10. Do you need any other info?

---

### Post by lidex on 2009-02-02
So you're on Intrepid. Do you have the latest updates? Go to menu system > administration > software sources. On the "Ubuntu Software" tab check off the top 5 boxes. On the "Updates" tab check off the top 3 boxes (and the 4th if you're brave). Click on close. Open a terminal and enter ```
sudo apt-get update
```

If you're fully updated go to system > administration > hardware drivers and see what that tells you about your nvidia drivers. You can enable\disable from there.

---

### Post by T3kG33k on 2009-02-02
> **lidex said:**
> So you're on Intrepid. Do you have the latest updates? Go to menu system > administration > software sources. On the "Ubuntu Software" tab check off the top 5 boxes. On the "Updates" tab check off the top 3 boxes (and the 4th if you're brave). Click on close. Open a terminal and enter ```
sudo apt-get update
```

If you're fully updated go to system > administration > hardware drivers and see what that tells you about your nvidia drivers. You can enable\disable from there.

Also.  You may need to run:

sudo apt-get install -f

There was an issue that I had with the kernel update not being applied.
I hope that this helps.

---

### Post by bluejeansummer on 2009-02-02
There was nothing new to install. It said that the "nvidia-settings" package is no longer necessary. I know it should be, but I think that means that some dependency isn't met. Any ideas as to what it might be?

---

### Post by lidex on 2009-02-02
What kernels/headers do you have installed?

---

### Post by bluejeansummer on 2009-02-02
Here's the list of installed kernels, which I got using a terminal. ```
$ aptitude search linux | grep '^i'
i   linux-firmware                  - Firmware for Linux kernel drivers         
i   linux-generic                   - Complete Generic Linux kernel             
i   linux-headers-2.6.27-11         - Header files related to Linux kernel versi
i   linux-headers-2.6.27-11-generic - Linux kernel headers for version 2.6.27 on
i A linux-headers-2.6.27-7          - Header files related to Linux kernel versi
i A linux-headers-2.6.27-7-generic  - Linux kernel headers for version 2.6.27 on
i   linux-headers-2.6.27-9          - Header files related to Linux kernel versi
i   linux-headers-2.6.27-9-generic  - Linux kernel headers for version 2.6.27 on
i   linux-headers-generic           - Generic Linux kernel headers              
i   linux-image-2.6.24-19-generic   - Linux kernel image for version 2.6.24 on x
i   linux-image-2.6.27-11-generic   - Linux kernel image for version 2.6.27 on x
i A linux-image-2.6.27-3-rt         - Linux kernel image for version 2.6.27 on I
i   linux-image-2.6.27-7-generic    - Linux kernel image for version 2.6.27 on x
i   linux-image-2.6.27-9-generic    - Linux kernel image for version 2.6.27 on x
i   linux-image-generic             - Generic Linux kernel image                
i   linux-image-rt                  - Rt Linux kernel image                     
i   linux-libc-dev                  - Linux Kernel Headers for development      
i   linux-restricted-modules-2.6.24 - Non-free Linux 2.6.24 modules on x86/x86_6
i   linux-restricted-modules-2.6.27 - Non-free Linux kernel modules for version 
i   linux-restricted-modules-2.6.27 - Non-free Linux kernel modules for version 
i   linux-restricted-modules-2.6.27 - Non-free Linux kernel modules for version 
i   linux-restricted-modules-2.6.27 - Non-free Linux kernel modules for version 
i A linux-restricted-modules-common - Non-free Linux 2.6.27 modules helper scrip
i   linux-restricted-modules-generi - Restricted Linux modules for generic kerne
i   linux-restricted-modules-rt     - Restricted Linux modules for rt kernels   
i   linux-rt                        - Complete rt Linux kernel                  
i   linux-sound-base                - base package for ALSA and OSS sound system
i   linux-ubuntu-modules-2.6.24-19- - Ubuntu supplied Linux modules for version
```
(Note: There were a few more items in that list, but they didn't have much to do with this)

The only one that will boot is the 2.6.24-19, which is what I'm using right now.

---

### Post by DougieFresh4U on 2009-02-03
Just curious, but why do you have these installed when you are using the 'generic kernel'?

```
   linux-image-rt                  - Rt Linux kernel image 
 linux-rt                        - Complete rt Linux kernel    
```

---

### Post by bluejeansummer on 2009-02-03
They seem to be installed every time they're available to update. I know several of them installed when I upgraded from Hardy to Intrepid. If I remember correctly, the "generic" packages automatically depend on the latest kernel. I don't use the latest kernel (or any kernel past 2.6.24-19) because it segfaults every time I try to boot it.

To answer your question, I think the main reason I have those is because I haven't bothered to uninstall them, hoping that someday I might get one of them working.

---

### Post by DougieFresh4U on 2009-02-03
But I wonder if that's what is causing "confusion" and not letting update properly.

---

### Post by occams_beard on 2009-02-03
I can't update mine either.  The newest one from the update is apparently
2.6.27-11.  It keeps showing up in the update manager.

I'm stuck on 2.6.27-9.   The first time the update ran, some sort of GUI dialog box popped up asking something about what to do with GRUB. At least I think that's what it was asking, I was in a hurry and didn't read it and just hit ok. I figured the default would be correct... Obviously not.

Anyway, the kernel just won't update. The only reason I can think of it, is because I installed VirutalBox, and it compiled some modules. Maybe the new kernel installer isn't liking those modules, or something?

Anyone know how to get it to update?

---

### Post by DougieFresh4U on 2009-02-03
> **occams_beard said:**
> I can't update mine either.  The newest one from the update is apparently
2.6.27-11.  
MY Intrepid machine updated just fine. I always use terminal
[B]dougie@DougiesLeanMachine:~$ uname -r
2.6.27-11-generic
[/B]
```
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get -f install
sudo dpkg --configure -a
```

---

### Post by bluejeansummer on 2009-02-03
If I get a chance tonight, I'm going to reinstall all the other kernels to see if that makes a difference.

---

### Post by SteveNorman on 2009-09-10
bumping this for solution, I cant get past 11

---

### Post by Elie-M on 2010-04-15
reviving old thread instead of creating a new one. I have the same problem on 9.10. i'm on 2.6.31-16 generic, and 2.6.31-21 is available and I cant upgrade. if I do distro-upgrade the update wants to remove 176 package I have and install 9 new ones to upgrade. I need those packages, and ubuntu is acting like a retarted. what's up with that?

---

