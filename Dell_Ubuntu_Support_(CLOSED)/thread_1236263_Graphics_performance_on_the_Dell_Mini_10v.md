---
title: "Graphics performance on the Dell Mini 10v"
date: 2009-08-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by karamu on 2009-08-10
I recently received my new Dell Mini 10v and I have to say I am very happy with the machine- I am still running the stock Dell Ubuntu 8.04 that was installed on the machine- I will probably replace it with Karmic or Jaunty sometime soon.

I am a little unsure about the Intel gma946 video hardware on the machine- Ubuntu tells me there are no restricted drivers to install but I cannot get desktop effects to work and the performance is not very good when opening windows so I am wondering if the machined is actually using the correct drivers.

Also, Compiz will not run- I have installed all the packages but when I try to run it I get the following error:

Checking for Xgl: not present. 
FATAL: Module battery not found.
Detected PCI ID for VGA: 00:02.0 0300: 8086:27ae (rev 03) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x600) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Error: Could not acquire compositing manager selection on screen 0 display ":0.0"
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

Can anybody point me in the right direction to get the graphics working properly? I would appreciate any info, thanks,

---

### Post by Talon2 on 2009-08-10
I have a Mini 9.  I just checked the Mini 10v specs which say you have a GMA 950 chipset.  This is the same graphics chipset as the Mini 9.

I use Ubuntu 9.04 Netbook Remix on my Mini 9.  Graphics performance is very good for how I use the system.  Compiz works fine.

If I recall correctly, 8.04 had some Intel chipsets blacklisted for some reason.

Good luck.

---

### Post by karamu on 2009-08-11
Yes, you're right the graphics chips are the same- don't know why I wrote 946!!

Did you have to enable any restricted drivers for the Intel chipset in your Mini?

---

### Post by Talon2 on 2009-08-11
I do not have to activate any restricted drivers.  The GMA 950 is a fully Intel supported chipset.

The problem out there right now that is giving Intel a black eye is the GMA 500 chipset which seems to be standard on the Mini 10 and Mini 12.  Evidently the GMA 500 chipset is not really an Intel chipset and there are problems providing support.

People should avoid the Mini 10 (not to be confused with Mini 10v) and the Mini 12.

I'd like to see Dell wake up and stop using Broadcom products and GMA 500 video chipsets.

---

### Post by karamu on 2009-08-12
OK, thanks for the clarification- I wonder why I cannot get Compiz to run- Dell's version of Ubuntu sucking again I wonder?

You are right about the Mini 10/ 12- after some research about them I went for the Mini 10v because it wasn't the GMA 500 GPU.

It's looking increasingly like I'll be getting rid of Dellbuntu and going for a fresh install of "regular" Ubuntu.

---

### Post by Talon2 on 2009-08-12
I tried to stay with Delbuntu on my Mini 9 but there were just too many annoying little problems that were not being fixed and there is no upgrade path to this day.

Dell and Canonical do not have this pre-load thing figured out.

I blew away the pre-load and went with 9.04 Netbook Remix.  I do not have a single bug to tell you about.  Everything that I use just works.

---

### Post by karamu on 2009-08-13
Good to know, thanks a lot!

I agree- the lack of upgrade is deal breaker in my book. I can see myself installing Jaunty very soon!

---

### Post by karamu on 2009-08-15
So, I installed Jaunty yesterday from a USB stick- went fine, the graphics are now looking much better- Compiz run "out of the box".

Apparently there is a glitch where the webcam mic doesn't work but as I use a headset for SKype I neither know if that is true or care.

I do have one problem but it is completely unrelated to this so I will look elsewhere or start a new thread.

---

