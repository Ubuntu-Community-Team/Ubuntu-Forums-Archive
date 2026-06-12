---
title: "Pixel artefacts on Compiz wobbly windows"
date: 2010-10-17
forum: Desktop Environments
---

### Post by aust_paul on 2010-10-17
Hi all, this is not critical, but is bugging me nonetheless.

I've noticed when I play with the wobbly windows desktop effect, for example, maximize a window the click and drag down from the top/middle, some nasty little 1px artifacts appear.

See examples here:

[http://picasaweb.google.com.au/lh/photo/_09QcNxlPm3eUTlznk9P4Q?feat=directlink]("http://picasaweb.google.com.au/lh/photo/_09QcNxlPm3eUTlznk9P4Q?feat=directlink")

[http://picasaweb.google.com.au/lh/photo/Yd12gcyAVkd0GhgfX2Ospw?feat=directlink]("http://picasaweb.google.com.au/lh/photo/Yd12gcyAVkd0GhgfX2Ospw?feat=directlink")

I have Ubuntu 10.04 running on 2 different machines and they both do it. One is a Dell Vostro 200 and lspci returns my graphics card as "VGA compatible controller: nVidia Corporation G86 [GeForce 8300 GS] (rev a1)". The other machine... I forget, it's at home. But same issue on that too.

Any ideas for a fix? So far I have tried messing with anti-alias settings in Nvidia X Server Settings but no luck.

Thanks in advance!

Paul.

---

### Post by fbobraga on 2010-10-17
I don't think it's an issue - I've faced it in many machines, and the "solution" was to disable wobbly windows

---

### Post by aust_paul on 2010-10-17
Thanks - I tried that solution and it worked! haha. Any other advice also appreciated though, too.

---

### Post by Turies on 2010-11-28
Why is this not an issue? I have the same problem and i don't want to disable wobbly windows.

---

### Post by mister_playboy on 2010-11-30
These artifacts are like transparent pinholes, showing whatever is underneath the window being moved.  It occurs at the edge between the menu bar and title bar.  I honestly didn't notice this behavior in older Ubuntu releases... maybe it's just because the bar colors are darker in 10.10.

---

### Post by Decatf on 2010-11-30
I think It's a low priority issue for developers. It's only a minor graphical inconsistency for an effect that's no different than a oversized spoiler on your car.

If there was a simple solution it would have been done already but as I understand it there's no simple way around it since window contents and decoration are separate.

---

### Post by grahammechanical on 2010-11-30
I have the radiance theme and it shows a light line to separate the tile bar from the menu bar. This is where these artifacts are showing up. It is where coloration is thinner. If that is at all possible. I did not notice this effect until I saw this post. I do not find it a problem.

Regards.

---

