---
title: "HELP: Bash script for launching Jedi Knight"
date: 2010-05-31
forum: Gaming &amp; Leisure
---

### Post by LukeLinux on 2010-05-31
So, remember back in 1997 when this game called "Dark Forces II: Jedi Knight" came out? I sure do! And even though by now it is waaaay outdated, it's still fun to play back through from time to time.

Problem is, my PC shipped with Vista, and DF2: JK does **not** like DirectX 10 or 11. Not to mention it's default screen resolution is so low that Vista practically chokes on it. So please don't waste a post telling me to just run the game in a Windows boot.

I have the game installed and running smoothly in WINE, but the only problem is that I have to enter several commands in a terminal to get it running (it could be cut down to just a few, but I use 'cd' and '*' a lot to save time typing). I'm trying to create a script that will shorten the process for me, and here's what I've got at the moment:

```
#!/bin/bash
cd '/home/luke/.wine/drive_c/Program Files/lucasarts/jediknight'
wine jk.exe -windowgui
```

When run in a terminal, this successfully launches the game...but the game only asks for a CD, even though it's already in the drive. I've thought of a couple possibilities, but I don't know a lot of bash script, so even if one of my ideas is correct I can't pull it off.

**Idea #1:**
The game must be run as root *(I installed the game as root because WINE wouldn't launch setup.exe, and then set permissions on all installed files to be able to access them from my normal user)*

**Idea #2:**
I have to define the path to the CD *(I tried just entering '/media/JEDI_1' into the script, but that did nothing)*

**Idea #3:**
All of the above.

But like I said, even if one of those is right, I have no idea how to pull it off...any ideas :confused:

---

### Post by del_diablo on 2010-05-31
Are you sure your cd folder is marked from winecfg? That script should have worked.

---

### Post by LukeLinux on 2010-05-31
Yes, it shows up as drive E: in WINE Config. I even checked the advanced settings to make sure it's defined specifically as a CD-ROM drive. Maybe I should set it to autodetect?

EDIT: autodetect fixes nothing.

EDIT 2: If this helps anything, here's the terminal output once the game is running from the script:

```
fixme:win:EnumDisplayDevicesW ((null),0,0x32f204,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f5d4,0x00000000), stub!
fixme:dplay:DirectPlay3WImpl_EnumConnections (0x133088)->(0x8607f0,0x4306e0,(nil),0x00000000): stub
err:ole:CoGetClassObject class {d8f1eee0-f634-11cf-8700-00a0245d918b} not registered
err:ole:CoGetClassObject no class object {d8f1eee0-f634-11cf-8700-00a0245d918b} could be created for context 0x1
fixme:win:EnumDisplayDevicesW ((null),0,0x32f2a0,0x00000000), stub!
```

---

