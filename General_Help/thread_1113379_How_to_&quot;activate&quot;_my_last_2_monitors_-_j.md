---
title: "How to &quot;activate&quot; my last 2 monitors - just installed my 2nd dual video card"
date: 2009-04-01
forum: General Help
---

### Post by PsychedelicWonders on 2009-04-01
Ok I just installed my 2nd dual Asus Nvidia card.

I went to Nvidia Server settings under admin, but it wasnt showing the other 2 monitors at all?

This will put me at a total of 4.

---

### Post by norwoods on 2009-04-02
you probably have to modify xorg.conf by hand.
there is information at nvidia in a README file for each driver and running man xorg.conf in a terminal window on your system.

---

### Post by PsychedelicWonders on 2009-04-03
> **norwoods said:**
> you probably have to modify xorg.conf by hand.
there is information at nvidia in a README file for each driver and running man xorg.conf in a terminal window on your system.

So since I have both a 9600 GT & now a 9800 GT is that going to be an issue for this xorg.conf setup?

---

### Post by PsychedelicWonders on 2009-04-07
> **norwoods said:**
> you probably have to modify xorg.conf by hand.
there is information at nvidia in a README file for each driver and running man xorg.conf in a terminal window on your system.

I am still not able to get this going.  I've tried looking for these README files on Nvidia to help with the xorg.conf but cant find anything?

Can someone help me with an easy walk through to activate these 2addtional monitors?

I should state that I've had some issues with my video drivers with what ever I currently have and have been advised to use this walk thru for new drivers:

[http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978)

So since I have both a 9600 GT & now a 9800 GT is that going to be an issue for this xorg.conf setup and this new driver walk thru?

---

### Post by norwoods on 2009-04-07
i suggest you start with a 180.44 or 185.13 nvidia video driver installed with synaptic, not the nvidia install procedure, so that it will not crash when you update the kernel.  
here is a web address for an nvidia README:
[ftp://download.nvidia.com/XFree86/Linux-x86_64/185.13/README/index.html](ftp://download.nvidia.com/XFree86/Linux-x86_64/185.13/README/index.html)
i suggest that you read at least the following chapters:
6. Configuring X for the NVIDIA Driver
7. Frequently Asked Questions
8. Common Problems
9. Known Issues
14. Configuring GLX in Xinerama
15. Configuring Multiple X Screens on One Card
24. Using the nvidia-settings Utility
B. X Config Options
you may need to read your motherboard manual to set the BIOS.
also, information is available at man nvidia-xconfig and man xorg.conf

---

### Post by PsychedelicWonders on 2009-04-30
Still not able to understand how to get these 2 extra monitors going.
 
Can anyone help me with an easy walk thru?

---

### Post by PsychedelicWonders on 2009-05-05
anyone?

---

### Post by PsychedelicWonders on 2009-05-11
bump

---

### Post by PsychedelicWonders on 2009-05-12
Bump...

---

### Post by PsychedelicWonders on 2009-05-13
bump

---

### Post by PsychedelicWonders on 2009-05-15
bump

---

### Post by PsychedelicWonders on 2009-05-17
bump

---

### Post by PsychedelicWonders on 2009-05-24
bump

---

### Post by PsychedelicWonders on 2009-05-25
Can anyone help on this at all?

I havent used Ubuntu for 2 months because I can only get 2 monitors to work.

Ubuntu blows windows out of the water, especially with the way I have modified it. 

But I'm totally stuck on this one.

Thanks.

---

### Post by PsychedelicWonders on 2009-05-25
I just ran back through this walk-thru:

[https://help.ubuntu.com/community/NvidiaMultiMonitors](https://help.ubuntu.com/community/NvidiaMultiMonitors)

Now that walk thru is the one I need I believe to get this to work.

I could have sworn I have seen the all 4 monitors show up in the Nvidia X Server Settings before, (at least I think so) but now I am only seeing the two ones that are currently active?

Any ideas?

---

### Post by PsychedelicWonders on 2009-05-25
Also, how can I check to make sure I have the right drivers for the 2nd video card?

I went to system/admin/hardware drivers 

And nothing comes up?

This is really starting to drive me crazy.

---

### Post by PsychedelicWonders on 2009-05-25
Ive been reading some things about editing the x.config and I think something like this is whats needed:

> Nvidia/ATI boards? First see if the NVIdia Xserver Settings utility (or the ATI equivalent) do this for you. You have to log as root or it won't be able to change the xorg.conf file.

By hand:

If your monitors are equal you already have the configuration in xorg.conf, just replicate the "Monitor" section and give a different Identifier to each, as in "Monitor[0]", Monitor[1], etc.

You'll have to do the same with the "Device" section, differentiating the boards by Identification ("Card0, "Card1", etc.) and the BusID. That's the tricky part, you'll have to search a bit for how to do it for boards with two video outputs, I've only used single boards. Probably the Hardware info module in Yast will show you the BusId for each video.

And again with the "Screen" section, where you "attach" each monitor to it's corresponding card.

Lastly you have to edit the "ServerLayout", which is where the configuration you want is actually activated, all previous sections being descriptive only. For example, if you had this line in it:

Screen "Screen[0]"

it could change to:

Screen 0 "Screen[0]" 0 0
Screen 1 "Screen[1]" RightOf "Screen0"
Screen 2 "Screen[2]" Above "Screen0"
Screen 3 "Screen[3]" RightOf "Screen2"

Then make sure not to run sax2 again, or at least backup your xorg.conf file before you do.

It's been a while since I did this, so you'll certainly find more up-to-date ways. Do search OpenSUSE's How-to site.

Or do I just need to install the driver or something?  I'm just fishing at this point...

This guy said he got it, but I dont think its for Ubuntu, look at his x.config

[http://forums.opensuse.org/install-boot-login/400566-nvidia-xinerama-compiz-almost-there.html#post1900785](http://forums.opensuse.org/install-boot-login/400566-nvidia-xinerama-compiz-almost-there.html#post1900785)

---

### Post by PsychedelicWonders on 2009-05-25
I do remember now, I believe the current card that is actually working is the 9800 GT.

That was the 2nd card I installed, so the drivers must be working for it properly since it is overriding the 9600 GT card.

So how do I get the 9600 GT to populate so I can activate it along with the 9800 GT?

---

### Post by PsychedelicWonders on 2009-05-26
I'm not getting any resopnses over at Nvidias website either... is this just not common practice to go with 4 monitors?

---

