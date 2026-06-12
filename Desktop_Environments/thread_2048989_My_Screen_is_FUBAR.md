---
title: "My Screen is FUBAR"
date: 2012-08-27
forum: Desktop Environments
---

### Post by Ampy on 2012-08-27
Ok, so I'm stupid and stuff, and I need to post another desktop thread.

I thought I had everything working! In fact, everything was working beautifully until I restarted my computer. Now [attached] shows up. I actually have no idea what went wrong. I remember something about installing nvidia-settings or something while trying to configure my conky, and although that works now, my screen is f'ed up. I tried uninstalling nvidia-settings and nvidia-common, but nothing changed. Um what did I do? And how do I fix it?

---

### Post by drmrgd on 2012-08-27
It looks like the screen is no longer set up for higher resolution.  Can you adjust the resolution from the System Settings > Displays menu?

---

### Post by ibuclaw on 2012-08-27
> **Ampy said:**
> Ok, so I'm stupid and stuff, and I need to post another desktop thread.

I thought I had everything working! In fact, everything was working beautifully until I restarted my computer. Now [attached] shows up. I actually have no idea what went wrong. I remember something about installing nvidia-settings or something while trying to configure my conky, and although that works now, my screen is f'ed up. I tried uninstalling nvidia-settings and nvidia-common, but nothing changed. Um what did I do? And how do I fix it?

Can't see anything wrong with the screenshot from here, other than it appears to be of a smaller resolution than what you would consider common to modern graphics cards.  What exactly are you seeing?

---

### Post by Ampy on 2012-08-28
Sorry, forgot to mention that in Displays it says the res is 640x480 or something similar, but I know my screen is 1366x768. The thing is, there's no option to change it (or at least not that I can see - the resolution cuts off the last part of the displays menu, but 640 is the only option. Maybe I have to run as root?)

But yeah, I can't adjust the settings. Going to try some google fu (it's hard to post and search with such a small resolution) but I'll get on it. In the meantime any suggestions?

EDIT - UPDATE: Alright, so I managed to get the screen resolution back to the way it was - sort of. It's back to a relatively readable resolution, but I notice unity2d popping up on my conky. I remember before I had this problem compiz was taking up the most data on my conky, so I did some digging and discovered for some reason unity3d was no longer running. So I tried unity --reset in the terminal and got 
```
Compiz (opengl) - Fatal: Root visual is not a GL visual
```

So I'm kind of stuck. I mean, it works but it doesn't look as good as I want it to and everything's off-center - and computing isn't about bare-bones! It's about getting your computer to do exactly what you want exactly the way you want it. So is there any help you wise gurus could bestow upon my feeble mind?

---

### Post by stinkeye on 2012-08-28
So you uninstalled the nvidia driver?
Whats the output of 
```
/usr/lib/nux/unity_support_test -p
```

eg my output with nvidia drivers
```
[COLOR="Olive"]glen@Precise:~$[/COLOR] **/usr/lib/nux/unity_support_test -p**
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 9400 GT/PCIe/SSE2
OpenGL version string:  3.3.0 NVIDIA 304.37

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes
```

---

### Post by Ampy on 2012-08-28
```
GLX isn't available on the system
```

I recall that was output as well after the compiz error was spit out. Missing package or repository or something?

---

### Post by stinkeye on 2012-08-28
Open up additional drivers and reinstall the nvidia driver.
Some nvidia cards will run compiz with the nouveau driver,
others will drop you back to the 2d session if the nvidia driver is not in use.

---

### Post by Ampy on 2012-08-28
Additional Drivers shows the no proprietary thing (maybe I should get the driver from the nvidia site?)

But I did reinstall nvidia-settings and nvidia-current and updated everything. Still gives me unity2d. Additionally I also got this error on startup

```
colord crashed with SIGSEGV in dbus_message_getreply_serial() 
```

Jeez, my system is just a big ol' can of worms now. Sorry for the difficulty, gentlemen! But I do appreciate all of the help.

Oh, and I'm still getting this error when I try to access the unity_support_test

```
Xlib:  extension "GLX" missing on display ":0".
Error: GLX is not available on the system

```

I'm off to do some more self-diagnosing, but I feel safer when complete strangers on the internet tell me what to do (usually because they've forgotten more than I know about computers ;))

---

### Post by Ampy on 2012-08-28
And I found this thread:
[http://ubuntuforums.org/archive/index.php/t-1741783.html](http://ubuntuforums.org/archive/index.php/t-1741783.html)

Which seems to recommend the opposite of what you suggest, stinkeye: to purge nvidia from the system. Well, I tried both things. I tried purging nvidia* and I tried reinstalling nvidia*. Nothing. My desktop is still visible, but the resolution's still a little bit off and no matter the means I'm STILL running unity2d. I'm at a loss here. Any ideas?

EDIT: Holy crap, something happened when I ran unity_support_test:

```
OpenGL vendor string:   VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 0x300)
OpenGL version string:  2.1 Mesa 8.0.2

Not software rendered:    no
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       no

```

Ummm, so what's the deal here?

---

### Post by Ampy on 2012-08-29
And now everything is ok. This man should be given a gold medal:
[http://nerdysermons.blogspot.com/2011/11/solve-graphic-driver-errors-unity-3d.html](http://nerdysermons.blogspot.com/2011/11/solve-graphic-driver-errors-unity-3d.html)

(I also had to remove nomodeset from /etc/default/grub for unity3d to work)

---

### Post by stinkeye on 2012-08-29
> **Ampy said:**
> And now everything is ok. This man should be given a gold medal:
[http://nerdysermons.blogspot.com/2011/11/solve-graphic-driver-errors-unity-3d.html](http://nerdysermons.blogspot.com/2011/11/solve-graphic-driver-errors-unity-3d.html)

(I also had to remove nomodeset from /etc/default/grub for unity3d to work)

Glad you got it sorted.
Out of curiosity, what is your output for...
```
sudo lshw -c video
```

eg mine
```
[COLOR="Olive"]glen@Quantal:~$[/COLOR] **sudo lshw -c video**
[sudo] password for glen: 
  *-display               
       description: VGA compatible controller
       product: G96 [GeForce 9400 GT]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: [COLOR="Red"]driver=nvidia[/COLOR] latency=0
       resources: irq:18 memory:fa000000-faffffff memory:d0000000-dfffffff memory:f8000000-f9ffffff ioport:ef00(size=128) memory:fb000000-fb07ffff
```

---

