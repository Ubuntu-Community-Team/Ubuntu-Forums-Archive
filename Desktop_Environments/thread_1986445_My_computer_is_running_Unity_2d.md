---
title: "My computer is running Unity 2d"
date: 2012-05-24
forum: Desktop Environments
---

### Post by Races1986 on 2012-05-24
Hi All, 

After having some problems with my Nvidia Card and two monitors.
My Ubuntu 12.04 is working.
However, I booted my computer and it magically switched to Unity 2D.
Can anyone let me know how I can switch back to the beautiful Unity 3d?

Thanks
Races1986

---

### Post by papibe on 2012-05-24
Hi Races1986.

What is your graphic card model?

Could you post the result of these commands?
```
lspci -nnk | grep -iA2 vga

sudo lshw -C display
```
Regards.

---

### Post by paulkiss on 2012-05-25
> **Races1986 said:**
> Can anyone let me know how I can switch back to the beautiful Unity 3d?It should be very simple. You log out, then near your name you see a gear, you push it and see "Unity", you choose it and proceed as usually.

---

### Post by cuyo01 on 2012-05-25
> **Races1986 said:**
> Hi All, 

After having some problems with my Nvidia Card and two monitors.
My Ubuntu 12.04 is working.
However, I booted my computer and it magically switched to Unity 2D.
Can anyone let me know how I can switch back to the beautiful Unity 3d?

Thanks
Races1986

any chance you updated ubuntu today? in my case along other things in the update was a x server update wich broke my propietary driver nvidia install, even after doing a sudo nvidia-xconfig the driver was not used, solution was to unistall completely nvidia driver and reinstall it again.

---

### Post by Races1986 on 2012-05-25
Hi Guys, 

Thank you for trying to helping me.

> It should be very simple. You log out, then near your name you see a  gear, you push it and see "Unity", you choose it and proceed as usually.     The first thing I did was log out and log in with the small gear. When I clicked there, there are only two options: Ubuntu and Ubuntu 2D.

 >  any chance you updated ubuntu today? I did updated as I usually do every day, but the problem came up after I click on "Enable Xinerama" which I have no idea about what it does but at least it made my two monitor work.

> Could you post the result of these commands?@Papibe.... here it goes:
```

races@races-Ubuntu:~$ lspci -nnk | grep -iA2 vga
07:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF116 [GeForce GTX 550 Ti] [10de:1244] (rev a1)
    Subsystem: eVga.com. Corp. Device [3842:1559]
    Kernel driver in use: nvidia
    Kernel modules: nvidia_current, nvidia_current_updates, nouveau, nvidiafb
--
    Subsystem: eVga.com. Corp. Device [3842:1559]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel
races@races-Ubuntu:~$ sudo lshw -C display
[sudo] password for races: 
  *-display               
       description: VGA compatible controller
       product: GF116 [GeForce GTX 550 Ti]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:f4000000-f5ffffff memory:e8000000-efffffff memory:f0000000-f3ffffff ioport:c000(size=128) memory:f6000000-f607ffff

```Thanks again



** Update **
I searched on internet and found out that that Xinerama creates this problems.
So I ran: sudo nvidia-settings and disabled it.
Outcome: Now, my second monitor is not working, it shows a white background and a old fashion black X as a mouse pointer.
Unity 3D is still missing in the monitor that does work.

Thanks

---

### Post by haresear on 2012-05-25
Older Nvidia cards are blacklisted by Unity. You might want to run the unity test script in a terminal to see why Unity 3D won't run:

```
 /usr/lib/nux/unity_support_test -p
```

---

### Post by Races1986 on 2012-05-25
Hi haresear, 

My Nvidia card is 550 ti... it is actually pretty new.. it was released last year. As I said before... Unity 3d was working fine before I made the two monitors work together.

Thanks
Races

---

### Post by papibe on 2012-05-25
Take a look at this [thread]("http://ubuntuforums.org/showthread.php?t=1967201&highlight=nvidia+site+edge+swat") on how to upgrade your nvidia driver to an newer version, but at the same time trying to play it as safe as possible.

Regards.

---

### Post by nikio on 2012-08-06
Hello all,
I have the same problem and I ran:
```
 /usr/lib/nux/unity_support_test -p
```
this was the output:
```

OpenGL vendor string:   Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Mobile 
OpenGL version string:  1.4 (3.0 Mesa 8.0.2)

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  no
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       no

```

It did work a couple of months ago, is there some way to make it work again?
Thank you!

---

