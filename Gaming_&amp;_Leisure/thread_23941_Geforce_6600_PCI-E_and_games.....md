---
title: "Geforce 6600 PCI-E and games...."
date: 2005-04-04
forum: Gaming &amp; Leisure
---

### Post by negatory on 2005-04-04
I'm running Hoary for amd64 with the latest nvidia drivers and I'm getting low frame rates.
My computer is a Athlon 64 3500+ 1GB ram with a Geforce 6600 256ram and UT2004 and Doom 3 I'm getting about 40 to 60 FPS...they are still playable because it's a very steady frame rate.I run both games at 1024x768 with all maxed out with full features and when I drop some detail and/or resolution it doesn't make a diference.When I run windows I got 110 FPS in UT2004.Is something I am missing?Are the drivers fully optimized for PCI-Express?Is anyone having the same results?
Thanks!

Pedro Carrico

---

### Post by grendelkhan on 2005-04-04
[QUOTE=negatory]I'm running Hoary for amd64 with the latest nvidia drivers and I'm getting low frame rates.
My computer is a Athlon 64 3500+ 1GB ram with a Geforce 6600 256ram and UT2004 and Doom 3 I'm getting about 40 to 60 FPS...they are still playable because it's a very steady frame rate.I run both games at 1024x768 with all maxed out with full features and when I drop some detail and/or resolution it doesn't make a diference.When I run windows I got 110 FPS in UT2004.Is something I am missing?Are the drivers fully optimized for PCI-Express?Is anyone having the same results?
Thanks!

Pedro Carrico[/QUOTE]
 The PCIe may be the factor there - I have no idea what support in Linux is like for that.  I know AGP has been around so long most of the bugs are worked out.  What kind of chipset are you using?  If it's the NForce4 - good support should be there.

---

### Post by mal on 2005-04-04
[QUOTE=negatory]I'm running Hoary for amd64 with the latest nvidia drivers and I'm getting low frame rates.
My computer is a Athlon 64 3500+ 1GB ram with a Geforce 6600 256ram and UT2004 and Doom 3 I'm getting about 40 to 60 FPS...they are still playable because it's a very steady frame rate.I run both games at 1024x768 with all maxed out with full features and when I drop some detail and/or resolution it doesn't make a diference.When I run windows I got 110 FPS in UT2004.Is something I am missing?Are the drivers fully optimized for PCI-Express?Is anyone having the same results?
Thanks!

Pedro Carrico[/QUOTE]
 I have an Nvidia 6600 based graphics card working quite happily with Hoary.

A few points to consider:

- You will need to execute the following commands to get it working:

# sudo apt-get install nvidia-glx
# sudo nvidia-glx-config enable
# sudo reboot

- You should then get the nvidia splash screen when X starts.

- I have found that I have to re-run "sudo nvidia-glx-config enable" each time I upgrade Hoary, to get the driver working again.

- When I run "glxgears" from a command prompt, I get about 4000 FPS, when the nvidia driver is working.

Edit: Note that I don't think the PCI-E interface is an issue.  I suspect that this is handled at the hardware/bios level and does not cause any concerns with Hoary.

Hope this helps.

Mal

---

### Post by negatory on 2005-04-05
I've no problems with the drivers besides the performance loss in UT2004.Don't know about Doom 3 but in Unreal there is a big diference between Windows performance and Linux.My glxgears gives me 3700fps.Is this diference normal?I remember that when I was running a P3 667 with a riva TNT2 Ultra I could get better fps in Quake 3 Linux than in Windows.My question is,are the Nvidia drivers with PCI-Express running at full speed under linux?AGP has been around for quite some time and I know people having similar performance between operating system with AGP cards. 
Thanks for your replies.

Pedro Carrico

---

### Post by skoal on 2005-04-05
[QUOTE=negatory][...]My question is,are the Nvidia drivers with PCI-Express running at full speed under linux?AGP has been around for quite some time and I know people having similar performance between operating system with AGP cards.[...][/QUOTE]

Well, I know of several people with PCI-E Nvidia 6x00 cards getting 10k+ framerates in 'glxgears' (if that's even a reliable benchmark).  I get ~4500 fps myself with my measly Ti-4600 @24-bit depth.  Sounds like something is misconfigured or missing from your setup.

---

### Post by negatory on 2005-04-05
Hmmm...my point exactly!But I've been upgrading the drivers and have the k8 kernel.Don't know what it can be...
Thanks

---

### Post by grendelkhan on 2005-04-05
Does your board use a VIA or nVidia chipset?

---

### Post by negatory on 2005-04-06
My motherboard is a A8N-SLI Deluxe (Nvidia NForce 4).Any clues?
I had DRI enabled in my xorg.conf but removing it didn't make a diference.
Thanks.

Pedro Carrico

---

### Post by negatory on 2005-04-10
I've changed my ram speed settings in my BIOS to 1T (thank Titus for that) and I notice a big speed improvement in UT2004 (average FPS 90  \\:D/  ) but the glxgears  fps stay the same.

Pedro Carrico

---

### Post by c_dog on 2005-04-11
[QUOTE=negatory]I've no problems with the drivers besides the performance loss in UT2004.Don't know about Doom 3 but in Unreal there is a big diference between Windows performance and Linux.My glxgears gives me 3700fps.Is this diference normal?I remember that when I was running a P3 667 with a riva TNT2 Ultra I could get better fps in Quake 3 Linux than in Windows.My question is,are the Nvidia drivers with PCI-Express running at full speed under linux?AGP has been around for quite some time and I know people having similar performance between operating system with AGP cards. 
Thanks for your replies.

Pedro Carrico[/QUOTE]
I'm not really sure how much of boost the 6600GT is over a 6600, but my glxgears runs 7800fps and 115 in Linux DOOM3. I haven't tweaked anything from stock. This is on a A8N-SLI Deluxe with a Athlon 64 3200+. That was under 7167 drivers. I haven't tried things under 7174 yet. Most people say 7174 is faster.

---

### Post by TheRealEdwin on 2005-04-11
[QUOTE=mal]I have an Nvidia 6600 based graphics card working quite happily with Hoary.

A few points to consider:

- You will need to execute the following commands to get it working:

# sudo apt-get install nvidia-glx
# sudo nvidia-glx-config enable
# sudo reboot

- You should then get the nvidia splash screen when X starts.

- I have found that I have to re-run "sudo nvidia-glx-config enable" each time I upgrade Hoary, to get the driver working again.

- When I run "glxgears" from a command prompt, I get about 4000 FPS, when the nvidia driver is working.

Edit: Note that I don't think the PCI-E interface is an issue.  I suspect that this is handled at the hardware/bios level and does not cause any concerns with Hoary.

Hope this helps.

Mal[/QUOTE]
 I tried what you said but I recieve this error.
> 
Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/xfree86/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.

---

### Post by TheRealEdwin on 2005-04-11
I run a ASUS Z71V laptop (Pentium Mobile [Dothan] 1.86 GHz, 1 gig ram, 6600 Go) and I get this:
15170 frames in 5.0 seconds = 3034.000 FPS
17492 frames in 5.0 seconds = 3498.400 FPS

---

### Post by negatory on 2005-04-11
> I'm not really sure how much of boost the 6600GT is over a 6600, but my glxgears runs 7800fps and 115 in Linux DOOM3. I haven't tweaked anything from stock. This is on a A8N-SLI Deluxe with a Athlon 64 3200+. That was under 7167 drivers. I haven't tried things under 7174 yet. Most people say 7174 is faster. 

**@c_dog:** I've got 7174.What is your ubuntu arch?Is it the AMD64 version?I'm beginning to think that this fps under glxgears are normal and that my card is just kind of slow...the results are very similar to those posted by TheRealEdwin.

If you have more glxgears benchmarks using similar systems please post here.
Thanks for all your replys.

Pedro Carrico

---

### Post by c_dog on 2005-04-12
It doesn't seem to matter whether I'm running glxgears 64-bit or 32 -bit. Runs about the same numbers in both. Composting takes a hit, but the 6600GT still runs about 6,900 fps with composite on under 7174.

---

### Post by jkndrkn on 2005-04-28
TheRealEdwin:

[QUOTE=TheRealEdwin] Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/xfree86/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.[/QUOTE]

If you get this error, simply execute that line:

> md5sum /etc/X11/xorg.conf | sudo tee /var/lib/xfree86/xorg.conf.md5sum

I got this error after manually changing from nv to vesa and then attempting to install nvidia-glx using the procedure Mal described.

Best of luck.

---

### Post by nrwilk on 2005-10-16
I just tryed the series of commands that were suggested here:


```

sudo apt-get install nvidia-glx
sudo nvidia-glx-config enable
sudo reboot
```

I had already gotten the nvidia-glx file from adept, but hadn't known that I had to enable it.

After this, when I rebooted the startup process halted after the initial loading screen, showing me the less-pretty text version of the load-up process (syncing with ntp server, etc...).  After that, it got no further.  So, I hit ctrl-alt F2 to get another console, logged in and tried to start X with the startx command.

I get this error:
```
ERROR: API mismatch: The NVIDIA kernal module is version 1.0.7174, but this X module is version 1.0.7667.  Please be sure that your kernal module and all NVIDIA driver files have the same driver version.
```

Can someone please help me resolve this issue?  I'm using Kubuntu i386 Breezy release on a AMD 64 3500+, GeForce 6600TD, 1GB ram.

Thank you so much for any help!!!

---

