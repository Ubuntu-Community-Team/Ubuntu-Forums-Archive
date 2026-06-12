---
title: "REALLY fuzzy fonts on 1200x800 res only"
date: 2005-11-10
forum: Desktop Environments
---

### Post by daveyl on 2005-11-10
Ive had this problem now for months, and have just settled with 1152x768 resolution - but videos dont look good in it. 

Whenever I try to change to 1200x800, ALL fonts, thumbnails, menus, buttons and small photos are so blurry  I can barely even see them - however, video works fine.    I really would like to have the 1200x800 res - it works booted in Windows...

I have already tried the small font changes mentioned in other posts about anti-aliasing and TTF's, but I think my problem is different that that, since my menu buttons and thumbnails are also blurry.

I am happy to supply more info if needed - this is my first post.

Thanks in advance for any replies,

Dave

---

### Post by mcmuffy on 2005-11-10
I have a similar problem with bluring on my monitor when I run it out of its native resolution. Is your monitor a TFT and if so what resolution is it made for?

---

### Post by daveyl on 2005-11-11
[QUOTE=mcmuffy]I have a similar problem with bluring on my monitor when I run it out of its native resolution. Is your monitor a TFT and if so what resolution is it made for?[/QUOTE]

It is a laptop monitor, widescreen, made specifically for 1200x800 resolution...and thats why I feel it is strange. I though it might be some 'widescreen support' driver that I need which the Ubuntu did not autoinstall....but I am given the option of 1200x800 resolution in the GNOME screen resolution options. I have also tried looking at some configuration files (I forget their names at this moment) in gedit dealing with display issues, and 1200x800 resolution support is there.

Still stumped!

---

### Post by bryan986 on 2005-11-11
Are you sure it is not 1280x800? 1200x800 seems kind of odd. Is it a 1.5 or 1.6 aspect ratio for the screen? 1200/800=1.5 and 1280/800=1.6

If that is not the case, try System->Preferences->Font and try some of the different font rendering options...

---

### Post by pataphysician on 2005-11-11
what kind of laptop do you have? this may not be the same issue, but something like what you're describing happened to my toshiba once after installing a bunch of updates through synaptic. to fix it i reinstalled the nvidia-glx package, restarted X (probably not necessary...), did *sudo nvidia-glx-config enable *and restarted x again. if you have an nvida display adapter, maybe give that a try?

---

### Post by daveyl on 2005-11-16
PROBLEM SOLVED!
Trying out the solution pataphsician gave me, I realized that Synaptic didnt have the nvidia-glx package installed in the first place, although my laptop does use nvidia (Satellite M30, NVIDIA G-FORCE FX)...so, I installed this package, then tried the *sudo nvidia-glx-config enable*....and got a termina error saying something along the lines of 'system could not automatically do this, but if you think you have nvidia, then manually edit /etc/X11/xorg.conf drivers from nv to nvidia.....
So I sudo'd this file in gedit, changed the driver from nv to nvidia, rebooted, and presto! NVIDIA screen popped up, and my screen is INCREDIBLY clear in its native screen resolution of 1280x800 (thanks bryan986 for pointing out that it wasnt 1200x800 i was going for).

Ubuntuforums is awesome....now that this thread is solved, is there something I should do to 'archive' it? Ill try looking now....

Dave

---

### Post by CarbonPlexus on 2005-11-17
Perhaps you can help me too?  I'm having a similar problem.  When I'm in 1280x1024 everything is fuzzy (not just the fonts but everything) so I'm forced to use 1024x768 or 800x600 to make it less noticeable.  This doesn't make sense because I'm using a CRT and Windows looked fine with 1280x1024.  I'd use your solution but I don't have an nvidia card I have an ATI Radeon 7200.  Any suggestions? I noticed in the xorg.conf file it detected it correctly but is it possible I still need to install/reinstall some kind of ATI driver?

---

### Post by Beernut on 2005-11-17
I had an issue with my Viewsonic LCD screen where it looked like liquid waves in the middle of the screenwhich was making things look fuzzy, it was really annoying.  I found out that I had to adjust my refresh rate lower and that cleared it up.

---

### Post by CarbonPlexus on 2005-11-18
Right now my refresh rate is 60htz and the back of the CRT says it should be around 60 too.

EDIT: *found the problem after all*
Hmm funny thing happened... I took my computer home for break and now that I'm using a different CRT the 1280x1024 looks fine!  I'll be switching CRTs now that I know it's a hardware and not a software problem. But it's still odd how this CRT (same model as the other) works at 1280x1024 in both Linux and Windows but the other one only works at that res. in Windows...

---

