---
title: "Adobe Flash on Kubuntu vs. Ubuntu"
date: 2009-11-05
forum: Desktop Environments
---

### Post by Dee.Rez on 2009-11-05
I've got two nearly identical computers, one with a Kubuntu partition and the other with an Ubuntu one (both 64bit, clean installs). I've come to notice that Adobe Flash runs **SO** much more smoother and nicer on KDE then it does in GNOME. 

I'm using the 64bit flash plugin and Firefox, and I swear that even with Kubuntu's Kwin on and Gnome's Compiz off, watching the HD videos on YouTube is almost as painless as it on Windows for Kubuntu! I can't move the mouse in Gnome without the video stuttering and the frames per second is so much better. 

To be sure, I even played around with Kubuntu in my Gnome machine's VM box. The differences is certainly not in hardware, the videos still ran flawless - in any case, Kubuntu is running in a slightly inferior machine. 

I can't find any information on this on the internet. Could anyone please confirm if this is the case (testing out flash on both KDE and Gnome) and I'm not imagining things?  If so, how can I get this in my preferred DE (Gnome)?

Thank you!

---

### Post by lovinglinux on 2009-11-05
I think is just a coincidence. Here I have a low-end notebook with AMD Sempron 3500+, 256 Mb DDR2 667 RAM, nvidia GeForce Go 6150 running Gnome, that plays flash videos pretty fine with compiz disabled. Flash CPU usage is still very high, but it doesn't stutters. On the other hand I have a desktop machine running KDE with Pentium 4 3.06Ghz HT, 2Gb DDR2 667 RAM, nvidia 7300GT and it lags like hell, even with compiz/kwin disabled. I also tested it on a pure Gnome environment, but the result is the same.

This is actually driving me crazy, because I switched ISP yesterday and the new one offers a lot of flash videos, since the company is owned by the major TV channel in the country. I can't watch the videos, unless I download them and play with mplayer.

---

### Post by 3Miro on 2009-11-05
KDE + Flash works better for me (I should add Konqueror). Both tested on the same machine. I don't get stutter on either one, but KDE is faster and smoother.

lovinglinux, which KDE are you using, I am using the 4.3 one, I don't think 4.3 would run well on Pentium 4 anyway.

My personal observation is that Gnome is getting outdated. Since 4.2, KDE is the clear winner for me.

---

### Post by lovinglinux on 2009-11-05
> **3Miro said:**
> lovinglinux, which KDE are you using, I am using the 4.3 one, I don't think 4.3 would run well on Pentium 4 anyway.

I'm using KDE 4.3.2. It works pretty fine, including compiz effects and emerald. Actually KDE works better than Gnome. My only problem is with flash.

---

### Post by 3Miro on 2009-11-05
> **lovinglinux said:**
> I'm using KDE 4.3.2. It works pretty fine, including compiz effects and emerald. Actually KDE works better than Gnome. My only problem is with flash.

That's odd. I have no problem with flash. I wonder if it could be compiz related. I am using kwin, it gives me all the effects that I need + it is much faster then compiz.

---

### Post by Dee.Rez on 2009-11-05
I don't know if it is, if anything the machine running Kubuntu is just so slightly inferior to that running Ubuntu, yet the difference in watching Flash videos is unmistakable. Even from inside a VM, full screen HD is painless, something I cannot say the same for Ubuntu. This isn't just true for Karmic, but have noticed this in Jaunty as well (when I first noticed this).

---

### Post by Dee.Rez on 2009-11-05
> **3Miro said:**
> KDE + Flash works better for me (I should add Konqueror). Both tested on the same machine. I don't get stutter on either one, but KDE is faster and smoother.

Are you saying that KDE is just itself faster and smoother (I'll agree it is, Kwin is so much better then compiz) or that Flash videos on it are?

The quality of YT videos in Ubuntu is acceptable, but for some reason it isn't as smooth as in KDE, and moving the mouse when watching a fullscreen HD video won't cause it to stutter as much.

---

### Post by jward3010 on 2009-11-05
This is very much a co-incidence. I installed Kubuntu on a modern Sony Vaio (Core 2 Duo E5500, 2GB DDR2, runs Vista like stink until it crashes and dies anyway) and Kubuntu ran like a pig with no legs. I even implemented the UXA driver fix for Intel graphics which made Ubuntu run beautifully. It was abysmal and I was disappointed as it was good hardware, Gnome ran way better. Depends on the hardware, Kubuntu runs great on some, rubbish on others, vice versa with Ubuntu and Gnome.

---

### Post by Dee.Rez on 2009-11-05
> **jward3010 said:**
> This is very much a co-incidence. I installed Kubuntu on a modern Sony Vaio (Core 2 Duo E5500, 2GB DDR2, runs Vista like stink until it crashes and dies anyway) and Kubuntu ran like a pig with no legs. I even implemented the UXA driver fix for Intel graphics which made Ubuntu run beautifully. It was abysmal and I was disappointed as it was good hardware, Gnome ran way better. Depends on the hardware, Kubuntu runs great on some, rubbish on others, vice versa with Ubuntu and Gnome.

If it is the case that different DE run better on different hardware then it isn't a coincidence, it's a bug in one or both of them, but even then I'm not too sure if it is the case. For everything else, Gnome and KDE runs almost as fine as each other, full KDE is only slightly heavier then Gnome, start up times for most software is indistinguishable and both are just as snappy as each other.

For what it's worth, both machines are AMD x86-64 bit and use the same Nvidia drivers.

---

### Post by 3Miro on 2009-11-05
> **Dee.Rez said:**
> Are you saying that KDE is just itself faster and smoother (I'll agree it is, Kwin is so much better then compiz) or that Flash videos on it are?

The quality of YT videos in Ubuntu is acceptable, but for some reason it isn't as smooth as in KDE, and moving the mouse when watching a fullscreen HD video won't cause it to stutter as much.

I meant to say that both KDE and Gnome work fine for me (Flash and everything else). However, KDE seems to be smoother and more responsive.

If you have stutter with Flash, it is some misconfiguration/bug and not the desktop in general.

---

### Post by lovinglinux on 2009-11-05
My flash playback is much better now. Apparently, the dust in the fan was a contributing factor. I clean it up frequently, so it wasn't actually growing spider webs, but cleaning it today helped. I can at least watch the videos now.

---

### Post by jward3010 on 2009-11-06
Well I tried this on the same hardware - A Sony VAIO VGN-A "something or other" and Gnombuntu was much more complete and quicker than Kubuntu ON THE SAME MACHINE - it probably is a bug somewhere but that sounds odd as the kernel should handle hardware and drivers and hence hardware performance.

In another case on some Dell PC, Kubuntu ran beautifully and "U"buntu ran like a pig.

---

### Post by jward3010 on 2009-11-06
> **Dee.Rez said:**
> If it is the case that different DE run better on different hardware then it isn't a coincidence, it's a bug in one or both of them, but even then I'm not too sure if it is the case. For everything else, Gnome and KDE runs almost as fine as each other, full KDE is only slightly heavier then Gnome, start up times for most software is indistinguishable and both are just as snappy as each other.

For what it's worth, both machines are AMD x86-64 bit and use the same Nvidia drivers.

Well I tried this on the same hardware - A Sony VAIO VGN-A "something or other" and Gnombuntu was much more complete and quicker than Kubuntu ON THE SAME MACHINE - it probably is a bug somewhere but that sounds odd as the kernel should handle hardware and drivers and hence hardware performance in regards the DE's, but something strange happens all the time.

In another case on some Dell PC, Kubuntu ran beautifully and "U"buntu ran like a pig.

---

