---
title: "Doom 3"
date: 2008-07-13
forum: Gaming &amp; Leisure
---

### Post by lordhaworth on 2008-07-13
Heya
I'm trying to install doom3 i have the game (consists of 3 cds). I popped in the first and began the install, and eventually the computer was telling me that installation was complete- how can this be when there are 3 disks required for installation?
Anyway the game obviously doesnt work, I've seen that doom 3 is playable on linux. I have wine but have never really directly used it- could something using this be required?

Here is the path to the doom 3 folder

/home/lordhaworth/.wine/drive_c/Program Files/Doom 3

and these are the contents of the folder, i think possibly there may be some missing files in the base folder? Should i try and copy those across from other disks?

.
|-- Docs
|   |-- License.txt
|   |-- MSR.txt
|   |-- help.htm
|   |-- htm
|   |   |-- Default.htm
|   |   |-- credits.htm
|   |   |-- cs.htm
|   |   |-- cs_files
|   |   |   |-- filelist.xml
|   |   |   |-- image001.gif
|   |   |   |-- image002.gif
|   |   |   `-- image003.gif
|   |   |-- left.htm
|   |   |-- man_def.htm
|   |   |-- man_left.htm
|   |   |-- man_top.htm
|   |   |-- pad.htm
|   |   |-- readme.htm
|   |   |-- side_ie.css
|   |   |-- style_ie.css
|   |   |-- techhelp.htm
|   |   `-- top.htm
|   |-- images
|   |   |-- ATVIsmall.jpg
|   |   |-- D3_logo_small.jpg
|   |   |-- Flashlight.png
|   |   |-- Lore1.png
|   |   |-- Lore2.png
|   |   |-- Lore3.png
|   |   |-- Lore4.png
|   |   |-- Lore6.png
|   |   |-- PDA1.png
|   |   |-- PDA2.png
|   |   |-- Tip1.png
|   |   |-- Tip2.png
|   |   |-- Tip3.png
|   |   |-- Tip4.png
|   |   |-- h01.gif
|   |   |-- h02.gif
|   |   |-- h03.gif
|   |   |-- h04.gif
|   |   |-- h05.gif
|   |   |-- h06.gif
|   |   |-- h07.gif
|   |   |-- h08.gif
|   |   |-- h09.gif
|   |   |-- h10.gif
|   |   |-- h11.gif
|   |   |-- h12.gif
|   |   |-- h13.gif
|   |   |-- h14.gif
|   |   |-- h14a.gif
|   |   |-- h_def.gif
|   |   |-- h_sup.gif
|   |   |-- h_tec.gif
|   |   |-- h_top.gif
|   |   |-- hmp.gif
|   |   |-- id_logo_small.jpg
|   |   |-- ingamedisplay.png
|   |   |-- line1.gif
|   |   |-- line1_b.gif
|   |   |-- line2.gif
|   |   |-- line2_b.gif
|   |   |-- machinegun.png
|   |   |-- multiplayer.png
|   |   |-- pad.gif
|   |   |-- pistol.png
|   |   |-- save.png
|   |   |-- shotgun.png
|   |   |-- soulcube.png
|   |   |-- symbol01.jpg
|   |   |-- symbol02.jpg
|   |   |-- symbol03.jpg
|   |   |-- symbol04.jpg
|   |   |-- symbol05.jpg
|   |   `-- watermark2.png
|   |-- manual.htm
|   `-- readme.txt
|-- Doom3.exe
|-- Doom3Ded.exe
|-- base
|   |-- doomkey
|   |-- game00.pk4
|   |-- pak002.pk4
|   `-- pak005.pk4
`-- version.inf



Thanks all

---

### Post by grossaffe on 2008-07-13
you're not supposed to install doom3 through wine; Doom3 is natively supported in linux.  There are files you need from the internet that allows you to install doom3 in linux.  after that is installed then you'll have to manually copy over the .pk4 files from the CDs.  just do a google search on doom3 and linux and you'll eventually come upon a site that'll show you how to do it.

---

### Post by lordhaworth on 2008-07-13
Ok so im now following this guide 
[http://ubuntuforums.org/showthread.php?t=262004](http://ubuntuforums.org/showthread.php?t=262004)

ive set it to install to /home/Doom3 etc
 
and now its asking me where i want to set up the path in which to create the symbolic links ----> default /usr/local/bin
seeing as ive just changed from installing doom 3 to that location I assume i need to change this path...

Where to anyone?

Thanks for all your help

---

### Post by kdorf on 2008-07-13
The links are only there to link to the executable files.. like a shortcut basically. /usr/local/bin is in your PATH by default, so if you put the links there and type "doom3" in the console, Doom will load.

---

### Post by lordhaworth on 2008-07-13
the install is not allowing me to continue with that due to permission problems, and i cannot apply sudo because it is running from the terminal as another program-some kind of setup.
Would it hurt for me to just place the symbolic links any old place? like in the home directory

---

### Post by kdorf on 2008-07-13
It wouldn't hurt, no, but if you aren't going to put them in /usr/local/bin I would put them in the bin folder in your home directory. Ubuntu's default scripts will add this to your path if it exists.

---

### Post by grossaffe on 2008-07-13
> **lordhaworth said:**
> the install is not allowing me to continue with that due to permission problems, and i cannot apply sudo because it is running from the terminal as another program-some kind of setup.
Would it hurt for me to just place the symbolic links any old place? like in the home directory

do you run the program with sudo?

---

### Post by lordhaworth on 2008-07-13
Yeah cheers
So simple but i keep doing it!
Ill get used to ubuntu one day

Thanks a lot for everyones help (again)

---

### Post by zeller on 2008-07-21
I'm getting this problem:

```
zeller@zd8000 ~ $ sudo ./doom3
DOOM 1.3.1.1304 linux-x86 Jan 16 2007 21:58:02
found interface lo - loopback
found interface eth0 - 10.30.34.98/255.255.255.0
------ Initializing File System ------
Loaded pk4 /home/zeller/base/game01.pk4 with checksum 0x51c6981f
Loaded pk4 /home/zeller/base/game02.pk4 with checksum 0xf3ec6f7
Loaded pk4 /home/zeller/base/game03.pk4 with checksum 0x5d4230ea
Loaded pk4 /home/zeller/base/pak005.pk4 with checksum 0x8ffc3621
Loaded pk4 /home/zeller/base/pak006.pk4 with checksum 0x95b65ab
Loaded pk4 /home/zeller/base/pak007.pk4 with checksum 0x666bdb3c
Loaded pk4 /home/zeller/base/pak008.pk4 with checksum 0x23ae5993
Current search path:
/home/zeller/.doom3/base
/home/zeller/base
/home/zeller/base/pak008.pk4 (3 files)
/home/zeller/base/pak007.pk4 (38 files)
/home/zeller/base/pak006.pk4 (48 files)
/home/zeller/base/pak005.pk4 (63 files)
/home/zeller/base/game03.pk4 (2 files)
/home/zeller/base/game02.pk4 (2 files)
/home/zeller/base/game01.pk4 (2 files)
game DLL: 0x0 in pak: 0x0
Addon pk4s:
file system initialized.
--------------------------------------
Unknown command 'vid_restart'
idRenderSystem::Shutdown()
Sys_Error: Couldn't load default.cfg
```

What now?

---

### Post by grossaffe on 2008-07-21
have you tried just using the command:
```
doom3
```

you don't have to locate the binary to play it, and you don't have to run it as a super user.  just open a terminal window and type doom3

---

### Post by Sockerdrickan on 2008-07-21
why the heck do you **sudo** ./doom3 ?

---

### Post by grossaffe on 2008-07-21
> **Tux0r said:**
> why the heck do you **sudo** ./doom3 ?

Doesn't that enable god mode? :confused:
:D

---

### Post by Cresho on 2008-07-22
interesting but no.  Sad to say it does not.

---

### Post by Brebs on 2008-07-22
You're missing pak004 - see [wiki](http://zerowing.idsoftware.com/linux/doom/).

---

### Post by grossaffe on 2008-07-22
> **Brebs said:**
> You're missing pak004 - see [wiki](http://zerowing.idsoftware.com/linux/doom/).

I actually installed doom3 without putting in pak004.pk4 as well.  The instructions i used, I think, left out the pak004.pk4 file.  anyways, the game still ran without that file, it just was missing a lot of textures making the entire game look very dark.

---

### Post by lordhaworth on 2008-07-23
yeah im having trouble with textures and darkness now, ill check to see if i have that package transferred from the disks. If that solves that it would be great!

---

