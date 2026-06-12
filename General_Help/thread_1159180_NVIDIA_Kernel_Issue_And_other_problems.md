---
title: "NVIDIA Kernel Issue And other problems"
date: 2009-05-14
forum: General Help
---

### Post by ThAt0n36Uy on 2009-05-14
Well, this is my first post. And I wasn't sure if this topic should've gone in the Hardware & Laptops forum or not. So I decided on the General Help forum.

I've got quite a few issues I'm having, and I'd like to get them all cleared up. But instead of making a topic for each I'll just keep posting them in this topic. Less clutter for the Mods here.


Anyways, I've having some trouble. I've used Linux before, but I had certain issues that turned me off of Linux, not because I didn't like Linux, but because it made using it way too hard. Like the old piece of crap computer I had first installed it on (BIOS problems).

Well, this time I decided to install it on a fairly new laptop, new as in 3 years old. It's a Toshiba Tecra M2, uses an NVIDIA G-Force FX 32/64MB Gfx card.  Anyways when I first installed Linux on it, the Drivers for the card wouldn't install (Proprietary Drivers). Which would've installed from the Hardware Driver Manager on Ubuntu itself. So I went to NVIDIA' site to install the drivers myself.

These are the drivers: [NVIDIA Driver Webpage]("http://www.nvidia.com/object/linux_display_ia32_173.14.18.html")

Well, I installed it, and it cleared up the Resolution issue I was having. Well, somehow I was able to installed the drivers from the program on Ubuntu. So I was happy with that. All seemed well, until I installed wine, at which point I installed Steam (Program to distribute games). 

I tried to install any game I have on my list of games, and every time, Steam would crash. I did some research, not paying attention to the info in Terminal when it crashed. And came across something about OpenGL incompatible or something. I didn't really read into it, that's just something I remember from that quest to get help.

So, on to the error message I get when Steam crashes. From what I read, it's pretty obvious the Kernel is older or younger than the drivers. So I need information on how to fix this issue. I'm not affraid of Terminal, I have some basic understanding of how Linux works, so don't be worry about it being to complicated. If it is, I'll tell you.

> err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
Error: API mismatch: the NVIDIA kernel module has version 173.14.16,
but this NVIDIA driver component has version 173.14.18.  Please make
sure that the kernel module and all NVIDIA driver components
have the same version.
NVIDIA: Direct rendering failed; attempting indirect rendering.
Error: API mismatch: the NVIDIA kernel module has version 173.14.16,
but this NVIDIA driver component has version 173.14.18.  Please make
sure that the kernel module and all NVIDIA driver components
have the same version.
NVIDIA: Direct rendering failed; attempting indirect rendering.
fixme:win:EnumDisplayDevicesW ((null),0,0x32cd30,0x00000000), stub!

---

### Post by ThAt0n36Uy on 2009-05-14
I wasn't sure if I'm allowed to bump. But I posted this topic 4 hours ago and it ended up on page 6.

---

### Post by 4Orbs on 2009-05-14
If I understand correctly, you manually installed the .18 driver then went to the Hardware Drivers Mgr and clicked on the Activate button? If that is what you did, then that is where the driver conflict error is coming from. When you installed the driver from nVidia's website it was already activated when the installation finished. The Hardware Drivers Mgr does not work with manually installed drivers, so just leave it alone if you installed the driver with one of the nVidia .run packages.

---

