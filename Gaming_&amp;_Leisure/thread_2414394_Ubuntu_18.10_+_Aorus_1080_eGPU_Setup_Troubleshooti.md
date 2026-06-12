---
title: "Ubuntu 18.10 + Aorus 1080 eGPU Setup Troubleshooting and Problems"
date: 2019-03-09
forum: Gaming &amp; Leisure
---

### Post by stayandwait on 2019-03-09
I am trying to get my Aorus 1080 eGPU gaming box to display an output to an external monitor with no luck.

The gaming box is detected, led shows as working, gaming box displays as authorized in thunderbolt devices.

When external monitor is plugged in, the monitor shows up in Display's panel as 'unknown'. When I set the external monitor as active, then click apply, the laptop internal monitor goes black for about 15-30 seconds, but the external display never turns on. After I have applied this, the name of my external monitor is named correctly instead of 'unknown'. Clicking 'apply' once again still does nothing.

I have followed this guide with no success of getting the external display to show an output. (I have the latest kernal, gaming box is authorized, Nouveau is disabled, nvidia drivers installed, cuda installed, and xorg.conf is present as instructed.) 
[https://medium.com/@ocampor/setting-egpu-in-ubuntu-18-04-ba789a45d](https://medium.com/@ocampor/setting-egpu-in-ubuntu-18-04-ba789a45d)[e]("https://medium.com/@ocampor/setting-egpu-in-ubuntu-18-04-ba789a45de")

I also did this for DRM:
added "GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nvidia-drm.modeset=1 in /etc/default/grub
added "options nvidia-drm.modeset=1" to /etc/modprobe.d/nvidia.conf
As it was suggested here:
[https://egpu.io/forums/thunderbolt-linux-setup/egpu-in-blender-18-04-works-flawlessly/](https://egpu.io/forums/thunderbolt-linux-setup/egpu-in-blender-18-04-works-flawlessly/)

This was suppose to set/auto generate the xorg.conf configuration for my current pci devices. This gave me a black screen after reboot when setting this, so this change was reverted back to a blank xorg.conf file.
nvidia-xconfig --enable-all-gpus --separate-x-screens

Current Setup:
Ubuntu 18.10
eGPU: Aorus GTX 1080 gaming box.
CPU: Intel Core i7-8550U (laptop only has integrated graphics on board.)
NVIDIA-418 version
The gaming box and external monitor work just fine in Windows, but I prefer Linux, because I hate Windows 10.
Installing drivers for an eGPU in Linux and expecting the monitors to have an output should be an out of the box experience.

Others have had success in getting this to work and I would love to know what I could do to fix this problem or what could I be missing?

Any help would be appreciated. I can provide more detail if needed.

Thank you!

---

### Post by stayandwait on 2019-03-16
Thanks for the help guys, no response after a week... Is no one here knowledgeable in this area? I followed many guides hoping this would work and I still get the same end result. No Idea how anyone had any success in getting this to actually work. I guess I will have to go back to Windows. I would prefer not having to use it due to the forced updates and bloatware/features they force on you without your consent.

---

### Post by wildmanne39 on 2019-03-16
You can bump your thread once every twelve hours to keep it in view of the volunteers on the forum, if you do not please do not blame the volunteers for not seeing your thread, being sarcastic will probably not help your cause any.

---

### Post by stayandwait on 2019-03-24
I finally got this issue corrected and the egpu to work with a display output on nvidia drivers. No one ever mentioned this, but you have to disable 'Thunderbolt Security Level' in bios. This can be marked as solved.

---

### Post by oldrocker99 on 2019-03-25
To mark a thread as [SOLVED], you need to do it yourself; as the OP of the thread, you'll see in the upper left corner where you can do it.

---

