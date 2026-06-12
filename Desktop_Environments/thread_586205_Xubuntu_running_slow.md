---
title: "Xubuntu running slow"
date: 2007-10-22
forum: Desktop Environments
---

### Post by piratesmack on 2007-10-22
This weekend, I installed xubuntu 7.10 on an old computer (Celeron 677MHz, 128mb RAM, intel 810L) and it ran at a pretty fast speed.

So then I decided to install it on another computer (celeron 1.8GHz, 128mb RAM, intel 845GL) but it's running incredibly slow. I seriously think even Vista would run faster on this computer. I don't think it's RAM curruption because I ran a memory test and everything passed. This computer runs XP faster than the other one but it's extremely slow with xubuntu.

Any ideas on what's causing this thing to run so slow?

Also, would I be able to run compiz on an intel 810? I was able to enable compositing on it and use the window manager tweaks

---

### Post by overdrank on 2007-10-23
> **piratesmack said:**
> This weekend, I installed xubuntu 7.10 on an old computer (Celeron 677MHz, 128mb RAM, intel 810L) and it ran at a pretty fast speed.

So then I decided to install it on another computer (celeron 1.8GHz, 128mb RAM, intel 845GL) but it's running incredibly slow. I seriously think even Vista would run faster on this computer. I don't think it's RAM curruption because I ran a memory test and everything passed. This computer runs XP faster than the other one but it's extremely slow with xubuntu.

Any ideas on what's causing this thing to run so slow?

Also, would I be able to run compiz on an intel 810? I was able to enable compositing on it and use the window manager tweaks

Hi and I am glad to see you installed with that amount of ram on both systems. =D> Did you use the live cd or the alternate for the installation? I have yet to try the installation on that amount of ram. I would say you can run compiz on the intel 810 (because I did install and run on a system yesterday with 256mb) . That would be the only hold as I see is the amount of ram.

---

### Post by TeaSwigger on 2007-10-23
> **piratesmack said:**
> This weekend, I installed xubuntu 7.10 on an old computer (Celeron 677MHz, 128mb RAM, intel 810L) and it ran at a pretty fast speed.

So then I decided to install it on another computer (celeron 1.8GHz, 128mb RAM, intel 845GL) but it's running incredibly slow. I seriously think even Vista would run faster on this computer. I don't think it's RAM curruption because I ran a memory test and everything passed. This computer runs XP faster than the other one but it's extremely slow with xubuntu.

Any ideas on what's causing this thing to run so slow?

Also, would I be able to run compiz on an intel 810? I was able to enable compositing on it and use the window manager tweaks

celeron 1.8GHz, 128mb RAM, intel 845GL is very close to my 2nd PC with one huge exception: I have twice the ram at 256. It's a lousy performer, frankly. And 256 isn't enough ram to get it moving comfortably under a sophisticated modern OS like ubuntu, kubuntu or xubuntu. My older (built in 2000) 933mhz PIII with 384mb ram runs ubuntu just fine however. For one thing, a 933mhz PIII is superior to a 1.6ghz Celeron, for another there's 3x the ram, and finally there's the 64mb dedicated video card with the PIII whereas the Celeron just has internal graphics. 

Ideas why the older and supposedly slower PC is actually performing better: 
- Hard drive in newer unit is failing.
- Shared memory internal graphics card on the newer one, dedicated graphics on the older one. 
- Less optimal installation, less swap for example.
- You need to install 915resolution patch or the intel or nvidia graphics "drivers" and possibly bump color depth to 16bits.
- Bad memory chip or other fault.
- Sound card issue.

No it won't run Vista faster, because Vista won't run at all on less than four times the ram, 512mb. Seriously, that's its (optimistic) minimum spec. 256min for XP or 2k. You'd need windows 95 or 98, and there's way, way better choices nowdays.

Suggest a really light OS. Puppy Linux, Damn Small Linux, DeLi Linux, etc. Maaaybe Debian's xfce. Xubuntu is a bit lighter than ubuntu or kubuntu, but not nearly light enough for a 128mb system. If you're determined to have ubuntu or its relatives on 128mb ram, see the appropriate sections on [http://www.psychocats.com](http://www.psychocats.com) for low specs installations. You will also want to run Fluxbox, WindowMaker or IceWM for instance on it as window manager instead of Gnome (ubuntu), KDE (kubuntu) or Xfce (xubuntu). That will help a little, but noticeably.

Hope that helps.

---

