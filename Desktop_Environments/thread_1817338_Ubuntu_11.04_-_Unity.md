---
title: "Ubuntu 11.04 - Unity"
date: 2011-08-03
forum: Desktop Environments
---

### Post by galtech on 2011-08-03
Hi there, 

I am just looking for some information regarding Unity. I would like to get a better understanding of how it works, prerequisite requirements etc. I have Unity working perfectly on my home PC. My laptop however continues to use the classic desktop environment (older hardware). The details below are the result of the unity support test on my laptop. 

I would be very grateful if anyone has any information or useful links that I can find out more as to whether this laptop can be updated to eventually run Unity.

```
Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  no
GL npot or rect textures: no
GL vertex program:        no
GL fragment program:      no
GL vertex buffer object:  yes
GL framebuffer object:    no
GL version is 1.4+:       no

Unity supported:          no

```

Thanks,
galtech

---

### Post by Duncan Williams on 2011-08-03
graphics card (chip) and video drivers are usually the biggest culprit. You probably need to explain what ones you are using on the laptop.

---

### Post by galtech on 2011-08-03
Hi Duncan, 

Thanks for the reply. 
The laptop is an IBM Thinkpad T23 - an Internet search for specs yielded these results:

Display 
* Display Type: TFT (Active Matrix) 
* Display Size (inches): 14.1 
* Screen: Regular 

Video 
* Graphics Type: XGA 
* Maximum Internal Resolution: 1024 x 768 
* Maximum Internal Colors: 16M 
* Maximum External Resolution: 1600 x 1200 
* Maximum External Colors: 16M 
* Graphics Bus Interface: AGP 4x 
* Video RAM Size: 16 MB 
* Video RAM Type: SDRAM 
* Video Chipset: S3 Graphics SuperSavage / IXC16 

galtech

---

### Post by Blasphemist on 2011-08-03
Please use this to get details on your video.
```
sudo lshw -c Display
```

There may me nothing you can do to bring your video up enough to run Unity 3D but we need details to verify that. Have you tried unity 2D? I don't know of a test with results like you posted for it.

---

### Post by Duncan Williams on 2011-08-03
from what little I know.
You need opengl and a more robust graphics solution than you seem to have to run compiz/unity.

Unity 2D is probably a good solution as suggested.
(I used 2D with an old nvidia fx5200 (128mb) and was quite impressed - unity 3D would fall on the fx5200)

unity 2D should be available in `software manager'
After it is installed you can choose at the start screen 
(where you type your user-name and password)
ie/  ubuntu classic, unity, unity 2D
should be available.

---

### Post by wildmanne39 on 2011-08-03
Hi, the clue it in the information you posted it says your hardware does not support unity.

However you can open synaptic and install unity 2d.

---

### Post by galtech on 2011-08-07
Thanks for your help. I installed Unity2D and it seems to work well. 

Just for information, my display specs are: 
```
  *-display UNCLAIMED
       description: VGA compatible controller
       product: SuperSavage IX/C SDR
       vendor: S3 Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 05
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-2.0 vga_controller bus_master cap_list
       configuration: latency=64 maxlatency=255 mingnt=4
       resources: memory:c0100000-c017ffff memory:e8000000-ebffffff memory:e4000000-e7ffffff memory:e0000000-e1ffffff memory:e2000000-e200ffff
```

---

### Post by wildmanne39 on 2011-08-07
Hi, I am glad you have 2d working.

---

