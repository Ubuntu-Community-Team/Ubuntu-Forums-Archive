---
title: "Most reliable NES &amp; SNES emulators in ubuntu?"
date: 2008-12-14
forum: Gaming &amp; Leisure
---

### Post by BastardNamban on 2008-12-14
I play a lot of NES & SNES, well, at least I did before I converted to ubuntu from XP.

I now know there are indeed emulators for linux, but I'm unsure which ones are the most stable/popular for ubuntu. I want to put these on 8.04. Also, do linux emulators use the same ROMS and Zip files that XP did?

Given the (perhaps unfounded?) reputation linux unfortunately has for gaming, I'm worried I won't get them to work without mucking up my install.

Which NES & SNES emulators does everyone recommend as most popular/stable?
Which ones do you guys use? Aside from NES & SNES, are their working reliable emulators for other systems, like PSX, PS2, etc? The reason I ask, is that even on searching around, it seems that those for linux often get abandoned/forgotten, and go unsupported, while XP ones get all the attention. Thus, I feel it's valid to ask here.

Thanks.

---

### Post by hikaricore on 2008-12-14
IMHO

Mednafen for NES
Zsnes for SNES

---

### Post by BastardNamban on 2008-12-14
Thanks, and since you're an administrator, your opinion carries some good weight for me.

Do the emulators in linux use the same ROMS my ZNES and NNNesterJ used in XP?

How about PSX, PS2 emulators? Anyone?

---

### Post by .arean on 2008-12-14
Yeah, you use the same roms as you would on windows. Zsnes is in the ubuntu repositories so it's easily installed from the Add/Remove manager. You'll likely have to choose 'All Available Applications" from the drop down box at the top to see it.

For PSX, PCSX is in the repositories as well, though I never had much luck getting it to run quite right. If was playable but didn't look it's best. ePSXe works great though and there's even a [script](http://ubuntuforums.org/showthread.php?t=550304) that gets everything you need (minus the bios, of course) to get up and running quickly.

I've never used any of the PS2 emulators on linux but the likely candidate is [PCSX2](http://www.pcsx2.net/).

---

### Post by jbullfrog on 2008-12-14
ZSNES is the best emulator for the Super Nintendo.

I do not recommend you install you using the Ubuntu repositories.

Many people do not hear sound after installing ZSNES. 

There is supposed to be a fix by running "zsnes -ad sdl" in the terminal, but this is a hit or miss.

My suggestion is to download ZSNES for Windows, and then run it under WINE.  You must first install WINE in Ubuntu using the Adding/Removing Applications.

This has worked perfectly for me.

---

### Post by hikaricore on 2008-12-14
> **jbullfrog said:**
> My suggestion is to download ZSNES for Windows, and then run it under WINE.  You must first install WINE in Ubuntu using the Adding/Removing Applications.

I've never had any sound issues and I think that running zsnes under WINE is just silly.
If you have any problems with zsnes you can always download an older version or compile it yourself.
Running it under WINE is just a waste of resources and could cause even more trouble that it's worth for most.

---

### Post by mister_k81 on 2008-12-14
I completely agree with Mednafen for NES emulation. But for the SNES I use [Snes9x-gtk]("http://www.snes9x.com/phpbb2/viewtopic.php?t=3703").

---

### Post by Phenax on 2008-12-14
Nestopia for nes
zsnes for snes

---

### Post by BastardNamban on 2008-12-15
Thanks for all the tips guys. I had no idea about the sound issue with SNES, but I don't know if I'd compile an earlier version- I have NO IDEA how to compile code yet!

---

### Post by grossaffe on 2008-12-15
> **mister_k81 said:**
> I completely agree with Mednafen for NES emulation. But for the SNES I use [Snes9x-gtk]("http://www.snes9x.com/phpbb2/viewtopic.php?t=3703").

I second the vote for GTK SNES9x.

The only thing I use ZSNES for (in wine) is for online play.

---

### Post by BastardNamban on 2008-12-16
ZSNES for Online play?!??? Huh? You mean I could load one of my SNES ROMS, and play against someone online with them?

Trying to imagine Castlevania X with multiplayer....sweet.

Also, has anyone else here experienced this supposed sound glitch with ZNES when downloading it from the repositories?

---

### Post by .arean on 2008-12-16
The online feature of zsnes is kind of flaky and kind of a pain to get going but it's fun when it does work.

I never had any problems with sound after getting it from the repositories in 8.04, but maybe I was just lucky. If it doesn't work you can easily uninstall it download an older version or compile it yourself. The version in the 8.10 repositories is broken but there's a link to a working version on launchpad. Just something to keep in mind if you ever upgrade to 8.10.

---

