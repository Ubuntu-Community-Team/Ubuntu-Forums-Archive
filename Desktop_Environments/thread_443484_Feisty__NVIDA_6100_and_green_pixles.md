---
title: "Feisty / NVIDA 6100 and green pixles"
date: 2007-05-14
forum: Desktop Environments
---

### Post by ahickey on 2007-05-14
Hi,

I have a working Ubuntu Feisty install with a couple of strange things.
One of them is the fact that I get green pixels on the screen at random.

I have attached two images.
One shows the green pixels in the pie chart while the other has no green pixels.
I 'scrubbed' the pixels using the Mines window.

This makes me think it is a driver issue or some silly configuration thing.

I am using integrated graphics on an Asrock AliveNF6G-DVI, so it is an NVIDIA 6100.

I am using the NVIDIA drivers as selected by the Restricted Drivers Manager.

I get the problem with default Metacity desktop and in Compiz/Beryl. (different problem with no cube.... for another day.

Any help with this would be much appreciated.

Thanks,
Albert.

---

### Post by Kobalt on 2007-05-14
I can see the problem on the first screenshot (the left one) but not the other one... Anyway : have you checked in Synaptic wether you have the *nvidia-glx* or *nvidia-glx-new* package installed ? I believe your card supports both, so you can try swithching from one to another... 
You mention Beryl/Compiz : have you tried disabling such things as ArgbGLX or the composite extension in your xorg.conf ?

---

### Post by ahickey on 2007-05-15
Thanks for the information below.


> **Kobalt said:**
> I can see the problem on the first screenshot (the left one) but not the other one... Anyway : have you checked in Synaptic wether you have the *nvidia-glx* or *nvidia-glx-new* package installed ? I believe your card supports both, so you can try swithching from one to another... 
You mention Beryl/Compiz : have you tried disabling such things as ArgbGLX or the composite extension in your xorg.conf ?

Sorry, I wasn't very clear in my post.
In the first screen the green pixels are visible.
In the second screen I moved  the Mines window around the screen over the pixels and they disappeared.

I am running the nvidia-glx drivers.  

I have the problem in Beryl/Compiz, but also with the standard Gnome system, so it is not related to them.

Whether right or wrong.  I have just sent the package manager off to remove the nvidia-glx drivers and install the nvidia-glx-new drivers.

Hopefully, my system will come back up...

---

### Post by ahickey on 2007-05-21
Back on this after a bit of a break.

I tried changing to the -new NVIDIA drivers, but it just killed XWindows, so after some command line fun I am back with X again.

The problem still persists.  I get green pixels on the screen using the standard Gnome desktop.

Since it only happens in some graphics and the desktop I was wondering if it could be a scaling or jpeg decoding issue.

As I have said before the system works and if I use another windowed application I can 'rub' the green pixels away.  Effectively, move the application window over the affected desktop area and the pixels disappear.  But then they appear on a different part fo the screen.

So, to summarize
Green Pixels on the desktop
No funky Windowing system involved
Can rub them out with another application window
They appear again.

Usung NVIDIA glx drivers with an onboard video solution (6100)

Againm any assistance much appreciated.

Albert.

---

### Post by ronacc on 2007-05-21
does the problem occur with the NV driver ? or with a different OS ? have you tried the driver from Nvidia.com ?do you have a different monitor you can try ?

---

### Post by ahickey on 2007-05-30
I think I have narrowed down the problem.
It looks like it is to do with scaling JPEGs.

 I am using the standard Gnome Desktop - nothing fancy
NVIDIA accelerated graphics driver (not the -new ones)

When I am working with a JPEG that has to be made bigger or smaller I get the green dots or tearing.  So, it looks to me like the problem is with rendering JPEGs.

Again, any advice much appreciated.

---

### Post by ahickey on 2007-05-30
> **ronacc said:**
> does the problem occur with the NV driver ? or with a different OS ? have you tried the driver from Nvidia.com ?do you have a different monitor you can try ?

I didn't address these questions.

I am using the NVIDIA driver through the package manager.  I tried changing to the -new one at it messed up my XWindows, so I reverted
I ran Puppy Linux from a Live CD  - no problem.  Also, I can 'rub' put the pixels by moving a window over them.

I only have the one monitor and since I can 'rub' out the pixels it is not an issue with the specific pixels on the LCD monitor.

From my previous post it looks like an issue rendering JPEGs

---

### Post by FuturePilot on 2007-05-30
Try booting the live CD and see if you still have the same problem.

---

### Post by ahickey on 2007-06-21
I know it's been a while since I responded.

The Green Pixels are still there.
But I have a feeling it is not Ubuntu

I installed PuppyLinux on a USB memory stick and with that running at 1024x768 (not my screens native resolution) I still got some Green Pixels.

So with the VESA driver as well as the NVIDIA driver I am getting the pixels.

My current suspension is that the motherboard may not be earthed correctly.
I know the grounding tabs around the ports at the back are not on right.
So, I think next will be to take the motherboard out and sort out the tabs and see if it makes a difference.

I have also bought a DVI-15 pin adaptor.  I know it only passes through the video signal but if it is a signal rather than driver issue it may help me fix it.

---

### Post by ahickey on 2008-07-22
I have now sorted this.
It was a memory problem.
Replaced my memory and all is working well now.

It was a real intermittent error so took a while to sort out.  Yes, it is shared memory on the video.

I even replaced my motherboard thinking that might be the problem.

Thanks to everybody on the forum for your advice and help.

Albert.

---

