---
title: "Problems with my low resolution"
date: 2009-05-20
forum: Desktop Environments
---

### Post by Pungsopp on 2009-05-20
Hi guys!

Here's the situation. I'm sitting on a HP pavilion laptop. My problem is that the resolution is way too low, it looks completely stupid and is very annoying.

Here is my xorg.conf:
```


Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"fglrx"
EndSection

```

I am using the ATI proprietary drivers. In screen setting my monitor is not detected, and the highest resolution available is 1280*800. i want *1024 at least.

I have tried with xrandr with no success, of course i could try editing my xorg file, but i didn't want to do that without asking here first.

So, anyone have some suggestions?

Thanks! :)

---

### Post by khelben1979 on 2009-05-20
Have you tried to download the ATi drivers from their homepage and installing it this way?

---

### Post by Pungsopp on 2009-05-20
No, i haven't. But what's the difference from that?

Svenskejävler :)

---

### Post by khelben1979 on 2009-05-20
Well, from what I can see in that xorg.conf file it doesn't contain much information. Way less than it should, so I suspect that you just have installed the ATi drivers through the Synaptic package manager and perhaps gotten the open source drivers instead. Have you?

---

### Post by Pungsopp on 2009-05-20
I have used the System - Admin - Hardware drivers tab.

I may have used envy the first time, to install the drivers.

Anyways, i cant find any drivers through ati websites

---

### Post by khelben1979 on 2009-05-20
```
sudo lspci | grep VGA
```
to show what graphic card/chip you have over there.

Just check out [this page]("http://support.amd.com/us/gpudownload/Pages/index.aspx") for the drivers. It's important that you get drivers which works correctly for your platform also (x86 or x86_64bit)

Using EnvyNG is probably better than messing with a manual install of the drivers. In the worst case scenario your x server configuration file can get messed up and then you have no working graphics, so always make sure that you back up the /etc/X11/xorg.conf file before proceeding.

---

### Post by Pungsopp on 2009-05-21
The driver is already installed. 

01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3400 Series

---

### Post by khelben1979 on 2009-05-21
> **Pungsopp said:**
> The driver is already installed. 

01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3400 Series

Yes. But you didn't follow my instructions, did you? If you didn't, you can always edit the /etc/X11/xorg.conf file by hand and adding a new resolution, but your configuration file is missing so much information so I can't help you with this.

By installing the ATi drivers in the way I mentioned, you will have a bigger configuration file with a lot more options within in it.

---

### Post by Pungsopp on 2009-05-21
Ok, i thought you ment that i shoud use envy instead.

But imma try Ati

There is no driver for my graphics card there ;)

But what is the diffence between using envy and just a normal install?

---

