---
title: "Two Monitors, Spanning Desktop"
date: 2008-12-16
forum: Desktop Environments
---

### Post by z0kken on 2008-12-16
Hi,

I just switched from Fedora to Ubuntu. My reason is that after moving from Fedora 5 to the newly released Fedora 10 I couldn't get my desktop to span across two monitors. This was easy in Fedora 5: System -> Preferences -> Display, Select a second monitor and then select 'Spanning Desktops'. For some reason this wasn't working in Fedora 10, though. I tried modifying my xorg.conf based on the xorg.conf of my old installation, I tried using xrandr (which worked but had some weirdness), I searched forums, etc and finally gave up and decided to move to Ubuntu, since it's supposed to be easy to do with this distro.

So far, though, I haven't had any luck. First, I'm even sure where to do this, since there's no system-config-display tool (System -> Preferences -> Display). I then noticed under Add/Remove Applications that there's an 'ATI binary X.Org driver' package, so I installed it. This added the 'ATI Catalyst Control Center' under Applications -> Accessories, but when I tried running it told me that either no ATI graphics driver is installed or that it's not working properly. It advised me to download the driver or to configure the hardware using aticonfig. I decided to give aticonfig a shot, since I already downloaded the driver (I also tried using this on the Fedora installation), but it broke X and I had to revert to the default config.

So right now I'm not sure what to do. I could try manually configuring my xorg.conf again, but since I had no luck with that last time I figured I'd ask here first. By the way, both monitors are cloned right now; it's just getting the desktop to span across them that I'm having a problem with.

My Fedora version is 8.10; my video card is an ATI RV370 [Radeon X300SE]. My xorg.conf right now is minimal:

```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

Can anyone provide any help? If you need any other info about my setup, just let me know.

Thanks.

---

### Post by z0kken on 2008-12-17
I finally got this working after a lot of headaches. I downloaded the driver from ATI's site and 'ATI Catalyst Control Center' started working. From there I was able to set this up. Actually, it worked on the login screen but once I logged in it resorted to a cloned desktop. I finally resolved this by renaming my $HOME/.config/monitors.xml file, just to see what would happen, and it started working after a reboot.

---

