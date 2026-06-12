---
title: "X won't start with nvidia driver"
date: 2006-11-19
forum: Desktop Environments
---

### Post by jewishj on 2006-11-19
I have seen a few threads on this, but none of the resolutions found in them have worked for me.  I have looked for hours and still get the same issue.  I restarted my computer for the first time in about a month and a half today and right after Ubuntu gets past the splash screen, X starts up for a split second (see a flash of a gray screen with a mouse cursor) and then crashed with the error:

```

Error: API mismatch: the NVIDIA kernel module has the version 1.0-8762, but this X module has the version 1.0-8776.  Please make sure that the kernel module and all NVIDIA driver components have the same version.
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module!  Please ensure that there is a supported NVIDIA GPU in this system, and that the NVIDIA device files have been created properly.  Please consult the NVIDIA README for details.
*** Aborting ***
(EE) Screen(s) found, but none have a usable configuration

Fatal server error:
No screens found

```

I have a Nvidia GeForce 5550 FX and am running whatever the latest k7 branch kernel is.  I have tried reinstalling any packages i could come across related to the problem in posted such as nvidia-glx, linux-restricted-modules-k7, and probably about 10 more like that.  I have also tried running "nvidia-xconfig" and "dpkg-reconfigure -phigh xserver-xorg".

Nothing is fixing this for me.  Does anyone have any suggestions?

Any help is very much appreciated.

---

### Post by OffHand on 2006-11-19
[http://www.ubuntuforums.org/showpost.php?p=1743791&postcount=7](http://www.ubuntuforums.org/showpost.php?p=1743791&postcount=7)

Try following this little guide (except for installing the drivers again).

---

### Post by jewishj on 2006-11-19
It still does the same thing although with a different error now:

FATAL: Could not open '/lib/modules/2.6.15-26-k7/volatile/nvidia.ko': No such file or directory
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0): *** Aborting ***
(EE) Screen(s) found, but none have a usable configuration

Fatal server error:
No screens found

Also, an error that had come up the first couple of times, but has since gone away has come back.

Right after the splash screen, I get a message like this

[17179603.016000] Buffer I/O error on device sda1, logical block 36304864
[17179603.016000] Buffer I/O error on device sda1, logical block 36304864

Then it shows a shell login, but within a second or so tries to start x, at which point i get the blue X error screen with the NVIDIA error previously described.

Thanks again for any help

---

### Post by OffHand on 2006-11-20
[http://www.ubuntuforums.org/showthread.php?t=268036&highlight=nvidia+install](http://www.ubuntuforums.org/showthread.php?t=268036&highlight=nvidia+install)

Go to section 'Install & Configure nVidia Drivers' and follow the guide.

If it still doesn't work try booting into recovery mode and run command ```
dpkg-reconfigure xserver-xorg
```

Answer all the questions as accurate as possible. If you do not know the answer pick the default.

---

### Post by jewishj on 2006-11-20
Thanks!

that did the trick, strangely after doing that, I was actually able to replace the xorg.conf that it created with the one that I had before (when the problem occured) and it still worked fine. :D

---

### Post by OffHand on 2006-11-20
> **jewishj said:**
> Thanks!

that did the trick, strangely after doing that, I was actually able to replace the xorg.conf that it created with the one that I had before (when the problem occured) and it still worked fine. :D

Glad it worked  :)

(btw, what did the trick?)

---

### Post by jewishj on 2006-11-20
Well, actually last night I tried installed the latest Nvidia driver from their site.  At that point, when I tried to run startx the Nvidia splash screen would come up before it would die with a different error (actually several - i forget what they were, but there were alot of things about missing fonts).  Then after some more searching, I tried running

dpkg-reconfigure xserver-xorg

chose "nvidia" as the driver, and then did as many defaults as I could.  It generated everything new.. then everything worked (I know startx still failed at this point.. i had to use "/etc/init.d/gdm restart" to get it to start - probably will just work on reboot though).  Of course when I first logged in, I had lost alot of the custom stuff I did (twinview, forward/back buttons on microsoft laser mouse, etc. etc.) so I tried to replace the new xorg.conf with the one I had been running, and ran "/etc/init.d/gdm restart" again and I was back home.

One more question though, if you don't mind.

Is the buffer I/O error I saw:

```

[17179603.016000] Buffer I/O error on device sda1, logical block 36304864
[17179603.016000] Buffer I/O error on device sda1, logical block 36304864

```

right after the splash screen a major thing.. my drive is a SATA RAID 0 (using DMRAID) with 2x 74GB WD Raptor.  Does this indicate that the one of the drives is going bad?  Anything that would warrant daily backups to an external machine?

Thanks

---

### Post by OffHand on 2006-11-20
> **jewishj said:**
> Well, actually last night I tried installed the latest Nvidia driver from their site.  At that point, when I tried to run startx the Nvidia splash screen would come up before it would die with a different error (actually several - i forget what they were, but there were alot of things about missing fonts).  Then after some more searching, I tried running

dpkg-reconfigure xserver-xorg

chose "nvidia" as the driver, and then did as many defaults as I could.  It generated everything new.. then everything worked (I know startx still failed at this point.. i had to use "/etc/init.d/gdm restart" to get it to start - probably will just work on reboot though).  Of course when I first logged in, I had lost alot of the custom stuff I did (twinview, forward/back buttons on microsoft laser mouse, etc. etc.) so I tried to replace the new xorg.conf with the one I had been running, and ran "/etc/init.d/gdm restart" again and I was back home.

One more question though, if you don't mind.

Is the buffer I/O error I saw:

```

[17179603.016000] Buffer I/O error on device sda1, logical block 36304864
[17179603.016000] Buffer I/O error on device sda1, logical block 36304864

```

right after the splash screen a major thing.. my drive is a SATA RAID 0 (using DMRAID) with 2x 74GB WD Raptor.  Does this indicate that the one of the drives is going bad?  Anything that would warrant daily backups to an external machine?

Thanks
That doesn't look good. You might want to make another thread for that error. And of course always make back ups of important stuff.

---

