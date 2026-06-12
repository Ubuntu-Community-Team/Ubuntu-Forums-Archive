---
title: "Unity panel launcher broken, missing, gone."
date: 2012-09-26
forum: Desktop Environments
---

### Post by Mycen on 2012-09-26
Hi there!

My Unity stopped functioning properly.
At first, it was working fine. I did some tweaking, had fun with cubes, etc, and all was good. Days later I tried setting up automatic mounting for USB sticks and such. The only thing I changed was my /etc/fstab. I can post what I did exactly, but in my logic what I did and what happened are not connected:

When I rebooted to see if no errors appeared while loading fstab, my panel and launcher never showed up again. Windows don't have titlebars, ctrl+alt+T only works sometimes, ctrl+alt+F1-F6 was already problematic before (monitor in standby status), in short: a hard time. I dropped to ubuntu 2d and tried to fix, using a [tuxgarage thread]("http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html"). I tried all steps, none of them solved my problem, then I removed and reinstalled a) Nvidia drivers i had installed, and b) unity, compiz, ubuntu-desktop, the whole lot. This messed up my display settings in all desktop environments, which I got working again with some difficulty, but still unity was not working. 

According to unity-support everything should be fine, but obviously something is wrong.

> maarten@Maarten-PC:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 8500 GT/PCIe/SSE2
OpenGL version string:  3.3.0 NVIDIA 295.49

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

maarten@Maarten-PC:~$ sudo lshw -c video
[sudo] password for maarten: 
  *-display               
       description: VGA compatible controller
       product: G86 [GeForce 8500 GT]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:fd000000-fdffffff memory:d0000000-dfffffff memory:fa000000-fbffffff ioport:cc00(size=128) memory:fe9e0000-fe9fffff


So 3 questions:
1 Does fstab have anything to do with all this? (I never set it back since i don't believe it connects)
2 Has someone else had this problem before?
3 What do I do now?

---

