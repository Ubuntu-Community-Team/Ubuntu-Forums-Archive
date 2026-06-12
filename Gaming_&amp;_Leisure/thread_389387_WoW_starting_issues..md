---
title: "WoW starting issues."
date: 2007-03-20
forum: Gaming &amp; Leisure
---

### Post by steevz on 2007-03-20
Alright, so I copied all the data from all the WoW and WoW:BC cds to my harddrive and installed the game and expansion with Wine.
The file /World of Warcraft/wtf/Config.wtf doesn't exist for me yet so I haven't edited it. I try to login so it will update and create that file to edit it. When I try to run the program it just doesn't load. When I run it from the terminal this is what I get:


$ wine ~/.wine/drive_c/Program\ Files/World\ of\ Warcraft/WoW.exe
fixme:advapi:SetSecurityInfo stub
fixme:powrprof:DllMain (0x7d300000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7d300000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x33ede4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f328,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5ec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5ec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f05c,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x1900b0) : stub, simulating 64MB for now, returning 64MB left
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XRandR)
fixme:win:EnumDisplayDevicesW ((null),0,0x33f05c,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:sync:CreateIoCompletionPort (0xffffffff, (nil), 00000000, 00000000): stub.


Can anyone tell me what is going on here? What I must do to get WoW working with Wine.
Thanks in advance.

Steve

---

### Post by hikaricore on 2007-03-20
For any info I don't mention you can find the Ubuntu WoW Community How-To Guide here: [http://help.ubuntu.com/community/WorldofWarcraft](http://help.ubuntu.com/community/WorldofWarcraft)

The first thing you'll want to check is that you have installed the latest video drivers for you card, I could be wrong but this looks to be the issue:

> err:  x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XRandR)

If you have already done this you'll want to start the game in "opengl" mode, as d3d mode doesn't work for most people.

Config.wtf is created automaticly the first time you start the game, but there are many sites that can give you a good starting list of what should be in your config.wtf, you can find one by searching the [wine application database]("http://appdb.winehq.org") for "world of warcraft", as well as searching google.

---

### Post by steevz on 2007-03-21
I got it running fine now in OpenGL.. but my frame rate is about 15-20 frames per second slower than when I was running it on Windows. So it's stuck around 40fps .. anyway to increase this?

---

### Post by hikaricore on 2007-03-21
There are a number of tweaks and modifications you can make to increase your fps.

Personally I would love to get 40fps... since my pci gforce get around 20 inside and 9-25 outside... lol

Have you tried lowering some of the graphic settings and looked into the tweaks in the guide I linked to?

You may have to edit your config.wtf file by hand to change the settings if you can't run in d3d mode, as the game crashes when editing video setting in opengl mode.

---

### Post by steevz on 2007-03-21
Well.. I'm running a Intel Core Duo 1.83Ghz, 2gb ram, 256mb geforce go 7600.. In Windows I was getting a steady 60fps, which was great. I'd love to get that with Wine if it's possible.. I've tried acouple of the tweaks, making that script didn't work for me and coolbits is screwing around, I can change the frequencies but when I click apply my card doesn't stay overclocked.. Don't know why..

---

### Post by hikaricore on 2007-03-22
Answered your question in the coolbits thread, hopefully this works for ya.

---

### Post by lakersforce on 2007-03-22
I would say that 40 fps is decent. It certainly makes the game playable. When you get above 13 fps the human eye cant really tell the difference anyway.

---

### Post by steevz on 2007-03-22
I have Windows dual booted so I'm just going to run WoW from Windows. It was a good try but it runs so much smoother. Maybe when wine has a few more kinks worked out I can give it another go.

---

### Post by Sammi on 2007-03-23
Strange thing for me is that even though Wine runs WoW at 5-10 fps lower than native win, it still feels much smoother in Wine. In Wine I've got around 30 fps in regular outside gameplay with a p4, 2 gb RAM, and a geforce 6800 with 256 mb ram.

---

### Post by kainlongshot on 2007-03-23
I'm going with one of the OP posts. I can consistantly run at 60fps, full screen, and full details in windows (doesnt' matter if I'm in IF, OR, Raiding (Nax, MC, BWL). My current hardware is an OC'd Opteron 165, 7900gtx, 2gb of ram and about 500gb of HD. It aint the latest and greatest hardware but it was built to game.

I came to ubuntu looking at what it had to offer. Great community, awesome software, security, and freebies.

Not to thread jack, but it would answer a lot of questions if someone here can confirm that they can sustain 50-60fps in the game with full details in ubuntu using 6.10 and Wine. If there is a definate no or high improbability then that will answer my question about dual booting to windows. Its not to say ubuntu is a failure in my eyes but if someone bought a lot of semi high end hardware and not being able to take full advantage of it due to a piece of software than  . . . well as much as I want ubuntu and wine work, I'll have to boot to windows for my satisfaction. 

I do fully plan to use ubuntu as main OS for productivity (spreadsheets, word processing, surfing, burning, ripping, media, etc).

---

### Post by steevz on 2007-03-23
Kainlongshot.. haha we're basically looking at the exactly same thing. I run at a constant 60fps ingame in Windows, outside, inside, raiding, you name it. That was dropped down to about 40fps in Wine and then when I was in barrens and could seen an Oasis it dropped down to about 20-25 and in Windows that would still be at 60fps. I can see good things for Wine, but at this time I'd rather be able to run the game as smooth as possible.

---

