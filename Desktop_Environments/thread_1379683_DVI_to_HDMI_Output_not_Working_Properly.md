---
title: "DVI to HDMI Output not Working Properly"
date: 2010-01-12
forum: Desktop Environments
---

### Post by killercoderninja on 2010-01-12
EDIT: skip down four posts

Greetings Ubuntu community,

This is my first post to this community. Hopefully someone can help :-)

I just installed Mythbuntu on an old PC to use as an HTPC in my apartment. I got it all configured the way I wanted it, but it won't connect to my television properly.

I'm running mythbuntu 9.10 on an amd sempron with an ati Radeon 9550, which has a vga and dvi connector. I did all of my configuration with an old crt on the vga output. Everything worked fine. When I unplugged the vga and connected my dvi to hdmi cable between the card and the television, the system failed to boot. It would show the BIOS on the tv, then "grub loading...," then I get "no signal" on the television while the computer just sits there. No hard drive, no processor, no disk. Just 100% idle.

When I connect both the vga monitor and the television, GRUB comes up on the vga just fine, while the tv shows "no signal," with a quick microsecond flash of grub every couple seconds. I hit enter, and the mythbuntu splash shows only on the vga. The tv shows straight "no signal," no flashing. Then the pinwheel on BOTH monitors, then the mythbuntu loading screen with the little ticker. It goes for about half of its time, then the tv goes "no signal" again, this time for good. The vga monitor flashes, changes resolution, then stretches everything out. It is still at 1024x768 according to the display settings, and it looks right, but the fonts are all very small. The computer then runs as normal, just with really small font and only on the vga monitor.

After playing around non-stop for two days, I have discovered that if I boot with both monitors but unplug the vga during the splash screen (before loading starts) the tv will work perfectly, automatically at its perfect resolution and everything. How do I make this happen without involving the vga monitor at all? Kinda sucks having it sitting in the middle of the living room :-D

I have basic familiarity with linux commands, but that's it. If a file needs to be edited or a configuration changed, please ALSO TELL ME WHERE TO FIND IT! Again, I am on Mythbuntu 9.10, which only has an applications menu.

Thanks all!!

---

### Post by killercoderninja on 2010-01-12
Alright, I'm really not sure what I'm doing, but some more hours on Google have lead me to a command called xrandr. It can be used to do manual configurations of resolutions and settings. With the tv display working properly, I plugged in the vga monitor and ran

xrandr --output VGA-0 --mode 1024x768 --rate 75

and now I have cloned the tv onto the vga! I'm going to try booting up into the vga monitor, and see if I can use xrandr to bring up the tv...

---

### Post by killercoderninja on 2010-01-12
When I boot to the vga and use xrandr to clone to the tv, it SAYS via xrandr -q that the tv is connected and outputting properly at 1920x1080 @ 60, but the tv says "no signal"

I am at a loss...

---

### Post by killercoderninja on 2010-01-13
Bump

---

### Post by killercoderninja on 2010-01-14
It would seem that the problem is not with Ubuntu at all. Rather, GRUB is what hangs without the vga monitor connected. What is strange is that grub will accept the vga monitor on the vga output, or through a converter on the dvi output, so I know the tv is the problem, not the monitor.

How do I configure GRUB to go totally automatically, without hanging to draw the selection menu? menu.lst is not where it usually lives... :-\

---

### Post by killercoderninja on 2010-01-18
Hello?

---

### Post by ricerider1 on 2010-01-19
I have just been working on a similar situation and configuration for a long time...I am not positive but it seems as tho the most recent update helped a lot and also after plugging in a vga (separate monitor instead of vga and dvi to hdmi to same tv/monitor), everything finally came together. I had to turn on tv ,(listed as FNI in display preferences), adjust refresh and settings a little, but am up and running. Don't know as yet whether I will have other problems, (3d acceleration and dvd operation), but all looks good so far. Primary is Gateway 17" vga in 1024*768 with 85 Hz refresh and other is 32" Sylvania HDTV in 1280*720 with 60 Hz refresh. I am pretty much a noob with linux, so if anyone wants system info, you might have to tell me what and how. Good luck and don't get discouraged it will work, just be patient. I was / did and am and was fond of my KARMIC experience!

---

### Post by ricerider1 on 2010-01-19
By the way, my grub is a little slow since the update awhile back. (beta). But if I want to boot quicker to my xp, I just change hard drive priority in bios as grub is not on the same drive. By the way, check out your tv capability specs...i.e. my hdtv hooked up with vga cable only supported 2 modes...800*600 and 1280*768 and only with 60Hz refresh

---

### Post by efflandt on 2010-01-19
I experienced that issue too when switching DVI monitors around with different resolutions.  After the grub menu, I got a blinking cursor for a few seconds, then blank screen with no disk activity.  If I booted a recovery entry, or removed splash as a boot parameter, everything worked fine.  Or if I switched from DVI to VGA boot worked fine, but then X was not optimum resolution.

The problem seems to be that, splash halts the boot if the resolution in /etc/usplash.conf does not match the "native" resolution of a digitally connected monitor (even if the monitor is capable of the listed resolution).  Apparently this has been an unresolved issue for quite some time.

So either fix /etc/usplash.conf, or if it is something like a USB drive you boot on various computers disable splash as a boot parameter like as follows in /etc/default/grub:

#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
# optionally remove "quiet" to see boot messages
GRUB_CMDLINE_LINUX_DEFAULT="quiet"
GRUB_CMDLINE_LINUX=""

---

