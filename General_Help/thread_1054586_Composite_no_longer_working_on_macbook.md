---
title: "Composite no longer working on macbook"
date: 2009-01-29
forum: General Help
---

### Post by WiseElben on 2009-01-29
So I had composite working on my macbook, but now it doesn't. I'm not sure what made it break. I plugged in a second monitor, and rebooted, which turned off composite. But it might have been a kernel upgrade or something (because I just upgraded).

Anyway, here's some info:

> eshira@eshiranix:~$ compiz --replace &
[1] 5932
eshira@eshiranix:~$ Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: present. 
Software rasterizer detected, abortingaborting and using fallback: /usr/bin/metacity 


> eshira@eshiranix:~$ glxinfo | grep direct
direct rendering: Yes

I'm on a Macbook (2.1) with the intel GMA chip on it.

Any suggestions?

---

### Post by Pablo Pablovski on 2009-01-30
My system is different yours (AMD64, nvidia 8800GTS graphics, Intrepid), but I had a similar-ish sounding problem last night, after a kernel update. 

In my case, it looked like the updates overwrote / disabled the glx driver, so I reinstalled the nvidia graphics driver (180.22, in my case) and that fixed it. 

In case it helps, I dropped to a shell prompt (Ctrl-Alt-F1, I think), stopped kdm

> 
sudo /etc/init.d/kdm stop


Obviously, if you're running GNOME, it'd be "gdm stop". On re-running driver installer, some errors about the driver install having been modified appeared, but the installer was able to fix those.

---

