---
title: "Video Accelleration OK, but Firefox performance quite poor!"
date: 2012-05-16
forum: Desktop Environments
---

### Post by razor7 on 2012-05-16
After following this excellent support thread [http://ubuntuforums.org/showthread.php?t=1980663](http://ubuntuforums.org/showthread.php?t=1980663) I got my ATi card working ok, but now I'm facing great performance issues in Firefox (12.0) in plain html pages (like this one), nothing about flash or animations or videos.

When scrolling the page up and down the scrolling gets pretty slow! Also this issue appears when browsing HTML5 pages like games, it get's really slow!

Thanks in advise!

---

### Post by QIII on 2012-05-16
Try starting Firefox in safe mode to rule out problems with add ons.

```
firefox -safe-mode
```

---

### Post by razor7 on 2012-05-16
Nope, ran 
```
firefox -safe-mode
```

But no luck

On pages like this [http://9to5mac.com/](http://9to5mac.com/), scroll sucks. Very poor performance!

---

### Post by razor7 on 2012-05-16
I ran it again on console and got this

> Failed to open VDPAU backend libvdpau_nvidia.so: no se puede abrir el archivo del objeto compartido: No existe el archivo o el directorio
Failed to open VDPAU backend libvdpau_nvidia.so: no se puede abrir el archivo del objeto compartido: No existe el archivo o el directorio
Failed to open VDPAU backend libvdpau_nvidia.so: no se puede abrir el archivo del objeto compartido: No existe el archivo o el directorio
Failed to open VDPAU backend libvdpau_nvidia.so: no se puede abrir el archivo del objeto compartido: No existe el archivo o el directorio
Failed to open VDPAU backend libvdpau_nvidia.so: no se puede abrir el archivo del objeto compartido: No existe el archivo o el directorio
Failed to open VDPAU backend libvdpau_nvidia.so: no se puede abrir el archivo del objeto compartido: No existe el archivo o el directorio
NOTE: child process received `Goodbye', closing down


It says that failed to open  VDPAU backend libvdpau_nvidia.so, and can not find that file.

---

### Post by QIII on 2012-05-16
VDPAU is an NVIDIA technology.

Do you have an NVIDIA driver installed?

We just got your ATI card going yesterday!

---

### Post by razor7 on 2012-05-16
Hi, no Nvidia at all...really don't know why is that error displayed

---

### Post by QIII on 2012-05-16
Well....

I'll have to think on that a bit.

---

### Post by QIII on 2012-05-16
Well....

I'll have to think about this a bit.

---

### Post by razor7 on 2012-05-16
Good, will waith for any hint.

---

### Post by brainwash on 2012-05-16
```
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
```

Hardware acceleration for Flash videos is enabled by default, but it is only supported by NVIDIA cards. So this error message will appear, if the library for NVIDIA's VDPAU backend is installed on your AMD/ATI based system. So either delete the library or ignore the messages.

I'm not sure what might cause the slow performance (even on sites without flash content). Try to monitor the running processes while browsing some websites.

---

### Post by QIII on 2012-05-16
I just experimented and got the same message.  So you are right in part.

However, it is not correct that only NVIDIA supports Flash.  The relationship is the other way around.  Adobe chose VDPAU.

Adobe supports VDPAU. NVIDIA does not support Flash.

ATI cards will accelerate Flash in gnash and have since 2010, but I never had good luck with gnash -- but I haven't used it in a long time.  Certainly not since 2010.

Edit:  I installed gnash on a machine with an ATI card.  It did, in fact, allow acceleration and put a really good load off on the GPU -- putting as much as a 30% load on the GPU.  Unfortunately, I could not get 1080p content to play (the little spinning balls went on forever) and not all sites recognized it (on 3dgameman, for instance, I got gray boxes and no video.)  So, it's not an inherent problem with ATI, but simply that Adobe has chosen to use VDPAU.

---

### Post by razor7 on 2012-05-17
Hi, please, lets no divert the topic, The issue is that firefox gets slow on pages with or without flash, it gets slow on even html5 pages, or pages like [http://ubuntuforums.org/showthread.php?t=1980663](http://ubuntuforums.org/showthread.php?t=1980663)

---

### Post by QIII on 2012-05-17
Just some side chatter since I haven't found anything yet.  Still looking.

While you wait, try using Chrome or another browser so that we can see if we can isolate this to Firefox.

If another browser works, we will try creating a new Firefox profile.

---

### Post by flemur13013 on 2012-05-17
"The issue is that firefox gets slow on pages with or without flash,  ..."

Yup. 

I had that happening until I disabled the flash plugin - gnash, too.  

Now those pages without flash don't hang.

---

### Post by razor7 on 2012-05-17
Hi, disabled flash, restarted, no luck,  still HUGE slowness on test site [http://9to5mac.com/](http://9to5mac.com/)

---

### Post by QIII on 2012-05-17
Try with a different browser for a moment.  Let's make sure it's FF.

---

### Post by razor7 on 2012-05-17
> **QIII said:**
> Just some side chatter since I haven't found anything yet.  Still looking.

While you wait, try using Chrome or another browser so that we can see if we can isolate this to Firefox.

If another browser works, we will try creating a new Firefox profile.
Well, I think this is huge!

Tested [http://9to5mac.com/](http://9to5mac.com/) on Chromium and performance is poor.

Chromium	18.0.1025.151 (Build para desarrolladores 130497) Ubuntu 12.04
SO	Linux
WebKit	535.19 (trunk@106313)
JavaScript	V8 3.8.9.16
Flash	11.2 r202
Agente de usuario	Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/535.19 (KHTML, like Gecko) Ubuntu/12.04 Chromium/18.0.1025.151 Chrome/18.0.1025.151 Safari/535.19
Línea de órdenes	 /usr/lib/chromium-browser/chromium-browser --flag-switches-begin --flag-switches-end
Ruta ejecutable	/usr/lib/chromium-browser/chromium-browser
Ruta del perfil	/home/martin/.config/chromium/Default

---

### Post by QIII on 2012-05-17
Try a site in Argentina (as near by you as possible) and see how well it performs.

---

### Post by razor7 on 2012-05-17
> **QIII said:**
> Try a site in Argentina (as near by you as possible) and see how well it performs.

Well, I think I will not thest that, because once the site is loaded, the rendering process is handled by the browser rendering engine.

Just to clarify, the slowness happens after the site is completely loaded, so there is nothing to do with network performance, it is a video acceleration issue.

---

### Post by QIII on 2012-05-17
> **razor7 said:**
> Well, I think I will not thest that, because once the site is loaded, the rendering process is handled by the browser rendering engine.

Just to clarify, the slowness happens after the site is completely loaded, so there is nothing to do with network performance, it is a video acceleration issue.

I realize that once it is downloaded, rendering is on the browser.

Part of diagnosis is ruling other things out.

---

### Post by razor7 on 2012-05-17
To confirm that is not a network issue, GIMP 2.8 is also slow. If I load a descent picture let's say 1200x1200 GIMP gets really slow, and if I try to use the aerographer, on moving the mouse, it gets really slow.

So again, I think that installing my video drivers was a partial fix.

Can you tell me how to uninstall them and install ATi open source drivers? just to test GIMP and Firefox performance and give feedback

Thanks a lot!

---

### Post by QIII on 2012-05-18
If you 

```
sudo apt-get remove --purge fglrx*
```

you will remove the driver.  If you log out (I usually restart) and log back in, you will be using the open source driver by default.

Don't be alarmed if you see that xvba-va-driver is also listed for removal.  That is normal.  If you reinstall the fglrx driver, you can reinstall xvba-va-driver.

---

### Post by razor7 on 2012-05-18
Well, rolled back to gallium 0.4 and performance issues gone!

Just to recap, in this thread i had issues with gallium, but to solve them i had to just kill compiz and the issues where gone. [http://ubuntuforums.org/showthread.php?t=1980663](http://ubuntuforums.org/showthread.php?t=1980663)

I think that ATi driver caused the Firefox and Gimp slowness, any idea to solve this?

Best regards!

PS: Why the open driver is gallium, shouldn't be radeon?

---

### Post by razor7 on 2012-05-18
Well, just readed the radeon driver help page ([https://help.ubuntu.com/community/RadeonDriver#Testing_The_Driver](https://help.ubuntu.com/community/RadeonDriver#Testing_The_Driver)) and got this on terminal dmesg | grep drm

> [   10.057814] [drm] Initialized drm 1.1.0 20060810
[   10.172556] [drm] radeon defaulting to kernel modesetting.
[   10.172559] [drm] radeon kernel modesetting enabled.
[   10.172724] [drm] initializing kernel modesetting (RV770 0x1002:0x9460 0x1002:0x0502).
[   10.172743] [drm] register mmio base: 0xFBDE0000
[   10.172744] [drm] register mmio size: 65536
[   10.172846] [drm] Detected VRAM RAM=1024M, BAR=256M
[   10.172847] [drm] RAM width 256bits DDR
[   10.172930] [drm] radeon: 1024M of VRAM memory ready
[   10.172932] [drm] radeon: 512M of GTT memory ready.
[   10.172940] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   10.172941] [drm] Driver supports precise vblank timestamp query.
[   10.173030] [drm] radeon: irq initialized.
[   10.173033] [drm] GART: num cpu pages 131072, num gpu pages 131072
[   10.173620] [drm] Loading RV770 Microcode
[   10.922124] [drm] PCIE GART of 512M enabled (table at 0x0000000000040000).
[   10.968406] [drm] ring test succeeded in 1 usecs
[   10.968492] [drm] radeon: ib pool ready.
[   10.968609] [drm] ib test succeeded in 0 usecs
[   10.968836] [drm] Radeon Display Connectors
[   10.968837] [drm] Connector 0:
[   10.968838] [drm]   DVI-I
[   10.968839] [drm]   HPD2
[   10.968841] [drm]   DDC: 0x7e60 0x7e60 0x7e64 0x7e64 0x7e68 0x7e68 0x7e6c 0x7e6c
[   10.968842] [drm]   Encoders:
[   10.968843] [drm]     DFP1: INTERNAL_UNIPHY
[   10.968844] [drm]     CRT2: INTERNAL_KLDSCP_DAC2
[   10.968845] [drm] Connector 1:
[   10.968846] [drm]   DIN
[   10.968847] [drm]   Encoders:
[   10.968848] [drm]     TV1: INTERNAL_KLDSCP_DAC2
[   10.968849] [drm] Connector 2:
[   10.968850] [drm]   DVI-I
[   10.968850] [drm]   HPD1
[   10.968852] [drm]   DDC: 0x7e20 0x7e20 0x7e24 0x7e24 0x7e28 0x7e28 0x7e2c 0x7e2c
[   10.968853] [drm]   Encoders:
[   10.968854] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[   10.968855] [drm]     DFP2: INTERNAL_KLDSCP_LVTMA
[   10.968891] [drm] Internal thermal controller with fan control
[   10.968921] [drm] radeon: power management initialized
[   11.106847] [drm] fb mappable at 0xE0142000
[   11.106849] [drm] vram apper at 0xE0000000
[   11.106850] [drm] size 8294400
[   11.106851] [drm] fb depth is 24
[   11.106851] [drm]    pitch is 7680
[   11.106997] fbcon: radeondrmfb (fb0) is primary device
[   11.107145] fb0: radeondrmfb frame buffer device
[   11.107147] drm: registered panic notifier
[   11.107151] [drm] Initialized radeon 2.12.0 20080528 for 0000:04:00.0 on minor 0

I think there are issues with both drivers, radeon get slow somehow on certain app running, and ATi gets slow on opening web pages and GIMP.

---

### Post by QIII on 2012-05-18
I think there is something else afoot here.

Both the open source and the proprietary drivers work very well for me.

I'll keep looking.

---

### Post by razor7 on 2012-05-18
If you tell me wich program to use, I can record some screencast of the two drivers performance.

---

### Post by razor7 on 2012-10-13
This is a real shame for Ubuntu, after months of trying, the problem persists. If you want to support hardware acceleration, please suscribe to this bug report [https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1066313](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1066313)

PS: Steam on Ubuntu, YES! but warning, you won't be able to surf the web descently!

---

