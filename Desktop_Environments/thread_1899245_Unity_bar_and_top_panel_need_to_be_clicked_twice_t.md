---
title: "Unity bar and top panel need to be clicked twice to work"
date: 2011-12-23
forum: Desktop Environments
---

### Post by igurev on 2011-12-23
Hi,
I'm using Ubuntu 11.10 and there are some issues I'd like to solve:

When I move to the left edge the pointer Unity bar appears but if I click on an icon on it (dash button, trash, Chromiuim, etc.) nothing happens, I have to click on the icon a second time for make it work... the same issue happens with the tray icons which don't work until I click on them a second time, and also when I move the pointer on the top panel for make the "Close, Minimize, Maximize" buttons appear... nothing appears! To see them I have to click on the "empty" top panel and then move the pointer away from it, so when I put the pointer again on it the "Close, Minimize, Maximize" buttons appear!


P.S.
I've never had these kind of issues on Natty.

Thanks a lot to everyone who will try to help me!


igurev

---

### Post by sikander3786 on 2011-12-23
Strange issues. I mean there have been many issues with Unity but I am hearing about this one for the first time.

Probably, the things that matter are your graphics card and the version of graphics drivers. I know that Unity behaved strange on older Nvidia cards with latest drivers and to make Unity work on those cards, nvidia-173 drivers were needed.

And we are talking about regular Unity (3D) and not Unity 2D, right?

As a start, please post the output of these commands:

```
/usr/lib/nux/unity_support_test -p
lshw -c video
```

---

### Post by igurev on 2011-12-23
[COLOR="black"]These are the two outputs:[/COLOR]

igurev@igurev:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon HD 3430
OpenGL version string:  3.3.11005 Compatibility Profile Context

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

igurev@igurev:~$ lshw -c video
WARNING: you should run this program as super-user.
  *-display               
       description: VGA compatible controller
       product: ATI Technologies Inc
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:48 memory:c0000000-cfffffff ioport:d000(size=256) memory:d0020000-d002ffff memory:d0000000-d001ffff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

[COLOR="Black"]The second command, with "sudo":[/COLOR]

igurev@igurev:~$ sudo lshw -c video
[sudo] password for igurev: 
  *-display               
       description: VGA compatible controller
       product: ATI Technologies Inc
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:48 memory:c0000000-cfffffff ioport:d000(size=256) memory:d0020000-d002ffff memory:d0000000-d001ffff

---

### Post by igurev on 2012-01-04
...nothing? :sad:

---

### Post by igurev on 2012-01-13
I've upgraded Unity to the 5.0 version and the problem has been disappeared!

---

