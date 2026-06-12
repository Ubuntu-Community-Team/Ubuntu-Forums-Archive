---
title: "X says &quot;no screens found&quot; after modifying .nvidia-settings-rc in feisty"
date: 2007-05-02
forum: Desktop Environments
---

### Post by vedace on 2007-05-02
Hi everyone,

X was working just fine until I did the following, after which it failed to start on reboot:
One of my startup scripts ( to run beryl-manager) had stopped working after I upgraded to feisty, so I tried running the first command in the script, ```
nvidia-settings
```  to see what it would spit out.  It told me that line 18 in ~/.nvidia-settings-rc was causing trouble.  So I commented out the offending line, which reads ```
0/FlatpanelScaling[DFP-0]=0
``` and nvidia-settings started without a problem.  Afterwards, I ran ```
sudo apt-get install nvidia-settings
``` to see if there was an update; there was, and it installed.  

The next time I rebooted, X failed to start; the log told me "no screens found".  I figured this was because I'd modified ~/.nvidia-settings-rc.  So I opened it to uncomment the line I'd previously commented out, but discovered that the line was missing entirely, not just commented out.  I wrote the line back in where it was supposed to be and tried restarting X, and it still didn't work.  

When I run startx, here's what I get:
```
(EE)Failed to load module "nvidia" (module does not exist, 0)
(EE) No drivers available

Fatal screen error
no screens found.

XI0: Fatal I0 error 104 (Connection reset by peer) on X server ":0.0" after 0 requests (0 known processed) with 0 events remaining
xauth: error in locking authority file /home/vedant/.xauthority

```

The error is the same regardless of whether .nvidia-settings-rc is present and regardless of whether the offending "FlatpanelScaling" line is present.

Any ideas?  I suppose I *could* try to re-install drivers, configuration tools, etc. and re-configure X, but I'd rather not, because I'm almost positive that only the things I've mentioned here could have caused the problem, since I didn't modify anything else even remotely related to X or NVIDIA settings before X stopped working.

In case it's relevant: laptop; Pentium M 2 GHz, NVIDIA GeForce 6800 Go Ultra, 1.25GB ram.

---

### Post by vedace on 2007-05-02
bump

---

### Post by vedace on 2007-05-02
Resolved.

I ran ```
 sudo apt-get install nvidia-kernel-common nvidia-glx 
```
This doesn't explain why X conked out in the first place, but it was easy enough to fix.  If you encounter the same problem, you might want to run ```
sudo nvidia-glx-config enable
nvidia-xconfig
```
as well.  And if the drivers still don't install, try changing "nv" to "nvidia" in /etc/X11/xorg.conf

Cheers.

---

