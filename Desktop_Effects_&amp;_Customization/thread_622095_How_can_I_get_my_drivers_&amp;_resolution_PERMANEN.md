---
title: "How can I get my drivers &amp; resolution PERMANENTLY right...?"
date: 2007-11-24
forum: Desktop Effects &amp; Customization
---

### Post by Ecthelion on 2007-11-24
Hi,

To put it as it is, I'm deseperate and this issue is eating my nerves.

Since I upgraded to Gutsy Gibbon I've had noting but trouble with my nvidia drivers & my resolution.

I got the resolution correct for a while, untill I noticed I had no acceleration and installed the latest nvidia drivers. Everything works... Untill I reboot my computer, then I have to do it all over again.

I've tried changing my xorg.conf at hand, with dpkg-reconfigure xserver-xorg, ...
I've tried with the drivers that nvidia provides, with the open source drivers, with the propriary drivers (nvidia-glx-new).

...But each time I restart... 
> Ubuntu is running in low-graphics mode

Well I don't know what to do anymore.

Anyone who still has any ideas?

I suspect it's the new "Screens & Graphics" tool that messes everything up. Not sure though.

[EDIT]
To be clear: I do get my resolution & acceleration, but only when I reinstall the nvidia drivers(provided by nvidia).
And it works only untill the next reboot.

---

### Post by tonyhawz on 2007-11-24
maybe your card isnt new enough to use nvidia-glx-new ;)
are you sure those are the correct drivers , and no the nvidia-glx ones ?

---

### Post by Ecthelion on 2007-11-24
My card is a GForce 6 series, a GeForce 6600 GT

The correct driver should be the nvidia-glx-new. The nvidia-glx is for GeForce 4 or older only (I think)

---

### Post by tonyhawz on 2007-11-25
as always, you should start trying with:
```
sudo dpkg-reconfigure xserver-xorg -phigh
```
to take xorg.conf to the "default" configuration, and then change "nv" to "nvidia" there.
then you can start customizing your xorg.conf, to see what is breaking it.

---

### Post by AsoSako on 2007-11-25
You can try this great application called Envy:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
It does the whole job for you...  It is quite helpful with graphic drivers and so on.  I recommend it to you, and anyone that is playing around with their graphic drivers.
After you have installed your drivers and rebooted all you need to do is go to Applications > System Tools > Nvidia Settings ( Make sure you enter with Root Privileges) > X Server Display Configuration > Set it as you wish > Click on Save to X Configuration File
That should do the trick ;)

---

### Post by Ecthelion on 2007-11-26
> **tonyhawz said:**
> as always, you should start trying with:
```
sudo dpkg-reconfigure xserver-xorg -phigh
```
to take xorg.conf to the "default" configuration, and then change "nv" to "nvidia" there.
then you can start customizing your xorg.conf, to see what is breaking it.

I already tried everything with dpkg-reconfigure etc...

The only thing I noticed is that it didn't changed anything...

Conclusion: my xorg.conf IS correct!
When it doesn't work, changing the xorg.conf by one that I know works doesn't solve the problem at all

So the problem is somewhere else...


I'll try Envy. I heard of it before but it's rare to have a script that can do things better then yourself at hand :-S

But I'll give it a shot.

I'll tell you what the results are :-)

---

### Post by Ecthelion on 2007-11-26
Well...

Looks like I'll have to change my judgement on automated scripts.

My computer started for the first time since gutsy without me reinstalling the drivers!

I am amazed

I checked, and I have video acceleration and everything. You cant' imagine how happy something this simple makes me.

I noticed that envy downloads a driver version from nvidia that I couldn't find.
Last time I checked it was version 19, now it seems to be 24.
Maybe I didn't checked enough...

---

### Post by AsoSako on 2007-11-26
I am glad it helped.  Don't worry this really is the latest official Nvidia driver, it isn't some customized one...

---

