---
title: "Can't get 1680x1050 resolution to work with my LG screen... Help..."
date: 2007-05-24
forum: Desktop Effects &amp; Customization
---

### Post by isaac_s on 2007-05-24
Hello there guys,
I tried. I really tried. I have read so many articles, made so many attempts but it just doesn't work.

I have an **LG 226WA** - 22" wide-screen monitor with a maximum resolution of 1680x1050.
My machine has an on-board Intel chipset (i845).
Installed Ubuntu Desktop 7.04.

I have attempted to use **915resolution** - it didn't help. The funny thing is that it did work on Fedora Core 6... (for a couple of days I was so frustrated that I turfed Ubuntu and installed Fedora Core, only to realize that Fedora Core is, how to say, disappointing).

Installed the **xserver-xorg-video-intel** package instead of **xserver-xorg-video-i810** - didn't help either.

Tried setting modelines... Didn't help either.

**What happens is this**: When I switch to 1680x1050 using KDE's control-center, my monitor does indeed show that it receives a 1680x1050 image, **but the desktop appears to be "cut"**. In other words, I suspect that what the video card actually does is showing a higher-resolution - say 1920x1200 - and since my monitor can't display it** it only shows a portion of it**.

How do I make this work, guys? I am currently operating on 1440x900, which works fine.

Anybody cares to guide me through?


Thanks,


          Isaac

---

### Post by Baka no Kami on 2007-05-24
The only thing I can tell you is what worked for my widescreen (1360x768).  It wouldn't work at widescreen resolutions at all.  I removed all display options from my xorg.conf except 24bit 1360x768 and 1024x768 as a backup.  And still nothing.  I changed it to 16bit color, restarted X and it worked.  Changed it back to 24 and restarted X again and this time it used the resolution with no problem.

That was the end of a long string of failures.  I tried the same settings time and time again without it working.  I don't know why it suddenly worked. Ubuntu still shows my refresh rate as 50mhz when it's actually putting out 60.

---

### Post by Schluppy on 2007-05-25
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/116514](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/116514) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
I'm having similar problems with a different LG monitor and the intel 965 chipset.

Please add your comments to the bug report linked above.

---

### Post by Baka no Kami on 2007-05-25
I was getting my second monitor to work and noticed something else. I didn't have 1360x1024 listed as a resolution in the xorg.conf section for my widescreen, but X used that resolution as long as there was any other one with 1024 listed.  When I removed 1280x1024 from the list of resolutions X finally used the 1360x768 I configured it for.

---

