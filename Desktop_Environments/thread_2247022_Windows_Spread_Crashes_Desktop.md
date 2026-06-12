---
title: "Windows Spread Crashes Desktop"
date: 2014-10-05
forum: Desktop Environments
---

### Post by BJones007 on 2014-10-05
Hey guys, I've been having an issue with my desktop crashing each time I hit the super key + W. At first I thought it was my graphics card, so I added the xorg-edgers/ppa and installed ```
 xserver-xorg-video-intel 
``` but the same thing keeps happening. The screen will flash once when I hit the shortcut on the first try, but afterwards I get the error notification: "Docky requires compositing to work properly. Please enable compositing and restart Docky." and it's stuck on the opened window and I'm unable to get out of that screen or switch to something else. The notification bar at the top also goes missing and the only way I can resolve this is by pressing and holding the power button till the PC is completely off. 

The PC works fine without hitting the windows spread key combination, but I'd love if it went back to normal cos sometimes I forget and I have to reboot all over again. From the notification error it seems there's a problem with compositing, but I don't understand what I could have done to make it crash. What could have caused this and how do I go about fixing it? Am I over working my graphics card?

 I appreciate any advice and help, cheers.

---

### Post by gordintoronto on 2014-10-05
What version of Ubuntu? Do you have Docky installed?

---

### Post by BJones007 on 2014-10-06
I'm running Ubuntu 14.04 and yes I do have Docky installed

---

### Post by BJones007 on 2014-10-06
[COLOR=#000000]I'm running Ubuntu 14.04 and yes I do have Docky installed[/COLOR]

---

### Post by CantankRus on 2014-10-06
Odd you get that docky error, because compiz is an "**OpenGL window and compositing manager**"
What's your terminal output from...
```
/usr/lib/nux/unity_support_test -p
```

---

### Post by BJones007 on 2014-10-07
Here is the output for ```
 [COLOR=#000000][FONT=Ubuntu Mono]/usr/lib/nux/unity_support_test -p 
```[/FONT][/COLOR]


```


OpenGL vendor string:   VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 3.4, 256 bits)
OpenGL version string:  2.1 Mesa 10.1.3


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

---

### Post by CantankRus on 2014-10-07
That seems to indicate a gfx card/driver issue. You are using software rendering.
Installing **inxi** will help to diagnose.
```
sudo apt-get install inxi
```
Then in terminal run **inxi -b** and post results.
eg
```
[COLOR="#008000"]**@Trusty:~$**[/COLOR] **inxi -b**
System:    Host: Trusty Kernel: 3.13.0-36-generic x86_64 (64 bit) Desktop: Gnome Distro: Ubuntu 14.04 trusty
Machine:   Mobo: Gigabyte model: GA-78LMT-USB3 version: x.x Bios: Award version: FA date: 04/23/2013
CPU:       Quad core AMD FX-4300 (-MCP-) clocked at 3800.00 MHz 
Graphics:  Card: NVIDIA GF116 [GeForce GTX 550 Ti] 
           X.Org: 1.15.1 drivers: nvidia (unloaded: fbdev,vesa,nouveau) Resolution: 1680x1050@59.9hz 
           GLX Renderer: GeForce GTX 550 Ti/PCIe/SSE2 GLX Version: 4.4.0 NVIDIA 331.38
Network:   Card: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller driver: r8169 
Drives:    HDD Total Size: 1254.2GB (14.6% used)
Info:      Processes: 230 Uptime: 2:23 Memory: 1208.5/3935.1MB Client: Shell (bash) inxi: 1.9.17
```

I have to go out now but I am sure others will help.

---

### Post by BJones007 on 2014-10-07
This is my output for ```
 **inxi -b **
``` 

```
 System:    Host: brian-Inspiron-3520 Kernel: 3.13.0-36-generic x86_64 (64 bit) Desktop: Gnome Distro: Ubuntu 14.04 trusty
Machine:   System: Dell (portable) product: Inspiron 3520
           Mobo: Dell model: 0G8TPV version: A04 Bios: Dell version: A04 date: 09/28/2012
CPU:       Dual core Intel Core i3-2370M CPU (-HT-MCP-) clocked at 1200.00 MHz 
Graphics:  Card: Intel 2nd Generation Core Processor Family Integrated Graphics Controller 
           X.Org: 1.15.1 drivers: (unloaded: fbdev,vesa) Resolution: 1366x768@60.0hz 
           GLX Renderer: Gallium 0.4 on llvmpipe (LLVM 3.4, 256 bits) GLX Version: 2.1 Mesa 10.1.3
Network:   Card-1: Qualcomm Atheros AR9485 Wireless Network Adapter driver: ath9k 
           Card-2: Realtek RTL8101E/RTL8102E PCI Express Fast Ethernet controller driver: r8169 
           Card-3: Atheros 
Drives:    HDD Total Size: 500.1GB (52.3% used)
Info:      Processes: 248 Uptime: 1:37 Memory: 3155.4/3816.1MB Client: Shell (bash) inxi: 1.9.1 
```

---

### Post by CantankRus on 2014-10-07
Was this a fresh install or upgrade?
Try re-installing xserver-xorg-video-intel and rebooting.
```
sudo apt-get install --reinstall xserver-xorg-video-intel
```

---

### Post by BJones007 on 2014-10-08
It was a fresh install and I just did the re-install, rebooted and I'm still having the same issue. :(

---

### Post by CantankRus on 2014-10-08
I have never had to deal with driver issues.
Only ever had desktops with nvidia cards that just work.
I would just be googling for fixes now.

Try googling "Intel 2nd Generation Core Processor Family Integrated Graphics Controller" +ubuntu to find out why you're not using the intel driver.
Also try [**_[COLOR="#B22222"]googlubuntu[/COLOR]_**]("http://www.googlubuntu.com/")

---

### Post by BJones007 on 2014-10-09
I fixed it! After doing some extensive research I found that it had nothing to do with my intel driver. In fact I have the Cinnamon desktop environment installed and was able to do the windows spread there. The issue was actually with Unity. At first I thought there was a conflict between Unity Tweak tool and CCSM, but I didn't have CCSM installed so I was baffled. Finally I came across this command ```
 dconf reset -f /org/compiz/ && setsid unity 
``` and everything is now back to normal. Apparently this spread issue is a bug with the Unity Tweak tool. Hopefully this helps anyone else having the issue. Cheers! :)

---

### Post by CantankRus on 2014-10-09
Good to see it's working.
Don't understand why the **/usr/lib/nux/unity_support_test -p**  command
shows your using software rendering though.
Out of curiosity what does this command give you.
```
sudo lshw -c video
```

---

### Post by BJones007 on 2014-10-10
Here you go 

```
   *-display                      description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:43 memory:f7800000-f7bfffff memory:e0000000-efffffff ioport:f000(size=64)


 
```

---

### Post by CantankRus on 2014-10-10
> **BJones007 said:**
> Here is the output for ```
 [COLOR=#000000][FONT=Ubuntu Mono]/usr/lib/nux/unity_support_test -p 
```[/FONT][/COLOR]


```


OpenGL vendor string:   VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 3.4, 256 bits)
OpenGL version string:  2.1 Mesa 10.1.3


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
Does this give a different result now.
```
/usr/lib/nux/unity_support_test -p 
```

---

### Post by BJones007 on 2014-10-10
Yeah it does:-k 
```
OpenGL vendor string:   Intel Open Source Technology CenterOpenGL renderer string: Mesa DRI Intel(R) Sandybridge Mobile 
OpenGL version string:  3.0 Mesa 10.1.3


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

### Post by CantankRus on 2014-10-10
That appears to show that for some reason the intel drivers were not being loaded.
and you were falling back to software rendering by [**_[COLOR="#B22222"]llvmpipe[/COLOR]_**]("http://www.mesa3d.org/llvmpipe.html") instead of using your gfx card.
I don't have a full grasp on this but possibly it was a just case of compiz failing to load properly.
Anyway looks like you found a fix by setting compiz back to default and reloading.
If it happens again just try reloading compiz without setting back to defaults so you don't lose any customized compiz settings.
ie 
```
setsid unity
```
before running if needed
```
dconf reset -f /org/compiz/ && setsid unity
```
Goodluck.

---

### Post by colinafletcher on 2014-10-28
I had the same issue.  The symptoms started when I checked the 'click to access desktop' item in the Window Spread section of the Unity Tweak tool.  It was initially greyed out, but became checkable after I toggled Window Spread off and on again.  After checking it, when  window spread was activated the desktop would flash.  Activating window spread again would make the desktop crash.

No amount of unchecking that option (after rebooting) would return the thing to normal.  Neither would ```
dconf reset -f
``` Inspired by that, however, I reset the Unity Tweak package: ```
dpkg-reconfigure unity-tweak-tool
```
Problem solved.  Thanks for sharing, I wouldn't have figured this out otherwise.

---

