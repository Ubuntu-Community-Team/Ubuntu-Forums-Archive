---
title: "Dell Latitude E6500 + Ubuntu 9.10 =&gt; screen freeze"
date: 2009-12-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Aleksey Y on 2009-12-11
Hello,

I've installed the 9.10 at my laptop, then upgraded it via "Ubuntu Software Center" (GRUB actually says the version was 2.6.31-14, then became 2.6.31-16). All went well, but - the screen got frozen after 5-7 minutes!! In the middle of presentation!!! :(

Symptoms: the screen looks OK, all the windows are intact, mouse pointer is moving, but no clicks are accepted by the machine. The only way to continue is to power it off.

The machine: dual boot (Windows XP + Ubuntu 9.10), integrated display adapter Intel GMA 4500MHD, was connected to an external projector, external USB mouse has been used.

Also I have to confess - I've chosen System -> Appearance Preferences -> Visual Effects -> Extra, because I liked these "trembling" windows.

There are many possible things to blame - X, display adapter, external screen, USB mouse, some missed drivers, right? 

Please give me some direction
Thank you
Aleksey

---

### Post by gomyhr on 2009-12-11
Sounds like you got the typical freeze bug. This happens when the GPU of the graphics cards hangs. There is more information about troubleshooting this kind of bugs at [https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze) . For a list of other freeze bugs reported on that chipset, see [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bugs?field.tag=gm45+freeze&field.tags_combinator=ALL](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bugs?field.tag=gm45+freeze&field.tags_combinator=ALL) .

---

### Post by Aleksey Y on 2009-12-14
Oh, thank you

It looks like I've hit an old bump! 

The strange thing is that I don't have any screen freezes when I'm working without connection to an external projector. By the way, I had to lower my laptop screen resolution when I was connecting to this projector, because it didn't support my laptop native resolution 1920x1200 - so, may be that contributed to the freeze?

Another possibility - I connect my laptop to our computing system via WiFi using ssh and tunnelling, but as I can see the Dell Latitude E6500 WiFi adapter (Intel 5300 AGN) is also not supported by Linux drivers (anyway, I'm typing via this connection now ;)).

I'm new to Ubuntu and I'd like to know how to diagnose that. For example, what system logs to look at, what options to turn on/off?

Thank you
Aleksey

---

