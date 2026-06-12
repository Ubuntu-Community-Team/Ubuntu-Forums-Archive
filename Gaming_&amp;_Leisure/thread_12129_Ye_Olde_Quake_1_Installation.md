---
title: "Ye Olde Quake 1 Installation"
date: 2005-01-22
forum: Gaming &amp; Leisure
---

### Post by bobumf on 2005-01-22
Hi peps, 

I know its a little old but has anyone had any luck installing quake 1 on Ubuntu? It doesn't seem to be in the repositries - is this an indication of how much of a nightmare it is to run?

I've got all the files (manually), installed the libc 5 libaraies via synaptic, even tried adding them to the library path but to no luck. Any help would be very appriciated

Rob

-------------------
Freelance dreamer

---

### Post by jdodson on 2005-01-24
[QUOTE=bobumf]Hi peps, 

I know its a little old but has anyone had any luck installing quake 1 on Ubuntu? It doesn't seem to be in the repositries - is this an indication of how much of a nightmare it is to run?

I've got all the files (manually), installed the libc 5 libaraies via synaptic, even tried adding them to the library path but to no luck. Any help would be very appriciated

Rob

-------------------
Freelance dreamer[/QUOTE]

hey rob.  what i would suggest is snagging a gnu/linux sourceport of quake like [http://www.quakeforge.net/](http://www.quakeforge.net/) and then just plugging in the quake .wad or whatever files you need to play the game.

i want to snag a copy of quake so i can run it on my new gnu/linux box.  i LOVED playing the shareware version at lan parties, was only 4 player, but so much fun..... man those were the days.

---

### Post by fng on 2005-01-24
I just downloaded fuhquake ([www.fuhquake.net](www.fuhquake.net)), unzipped it and it worked like a charm.

---

### Post by bobumf on 2005-01-26
Cheers Guys, that furquake works a charm, and looks good. I can once again relive my happy youthful days.

---

### Post by pseudonym on 2005-01-27
Hi. I downloaded the file FuhQuake_Installer_v0.31_linux.bin from fuhquake.net but I'm having a hell of a time trying to get it to run. I know that, for security reasons, Ubuntu makes the running of executable files like this something more complex than a simple point-and-click operation, so I decided to use the Nautilus gksudo script from -

[http://www.ubuntulinux.org/wiki/NautilusScriptsHowto](http://www.ubuntulinux.org/wiki/NautilusScriptsHowto) 

but it keeps failing with the error 'subprocess ended with status 1'.

Any clues on how I can get this to work? I've played around with the permissions but without luck...

---

### Post by fng on 2005-01-28
i didnt use the installer for fuhquake.  I just downloaded the zipfile ([http://www.fuhquake.net/files/releases/v0.31/fuhquake-linux-v0.31.zip](http://www.fuhquake.net/files/releases/v0.31/fuhquake-linux-v0.31.zip)) unzipped it in a directory and .... taadaaa fuhquake works.

---

### Post by pseudonym on 2005-01-28
Thanks. I've tried that and it still doesn't work. If I try to run fuhquake-gl.glx from the command line I get 'command not found'; if I run it using the gksudo script I get the same problem as before. 

What could I be doing wrong? I unzipped the file to an empty directory I named 'quake', remembering to maintain its structure, so that can't be the problem. I copied over a pak0.pak from a quake installation on a windows partition (even though fuhquake appears to include the sharewareversion of this). I even tried copying over the id1 folder which contains both pak0 and pak1 but that didn't work either (I notice that the zip file puts its pak0 in a 'fuhquake' folder. Is there supposed to be an 'id1' folder at all in this, like in the original Quake?)

It's starting to annoy me a bit. I've installed about 6 games in Ubuntu and they've all given me some kind of grief. :(

---

### Post by TravisNewman on 2005-01-29
I just went to the fuhQuake website and checked out some screens. It's **fuh**gly. I appreciate the desire to add new effects to the classic game, but those new effects weren't done very well. I'll stick to Quakeforge. If I ever get around to installing it again, that is.

---

### Post by jkka on 2005-01-29
For Quake1 there is still an active community, mostly because it is simply the best (easy to learn - very hard to master) FPS made for online play. 

Fuhquake is the only q1-client today that is allowed for official online gaming. The graphical effects are all optional and there is also the "vga-version" that looks quite much similar to the original and it is included in the fuhquake packet.

You might want to check out sites [http://equake.quakeworld.nu/](http://equake.quakeworld.nu/) and [http://www.quakeworld.nu/](http://www.quakeworld.nu/)

Equake is just fuhquake with addons needed for online gaming and quakeworld is the #1 site for european quakeplayers.

btw. the equake/fuhquake works fine in ubuntu - tested it, havent had time to play anymore

---

### Post by TravisNewman on 2005-01-29
Gave it a shot, I'm still not a big fan. Straight up GLQuake was the best.

I just don't know why people want to change things like that and end up making them cheesy.
That HUD is terrible.

---

### Post by gil-galad on 2005-04-12
[http://www.liflg.org/?catid=6&gameid=12](http://www.liflg.org/?catid=6&gameid=12)

That has some nice loki installers for fuhquake and tenenbrae quake.

---

### Post by damaged on 2005-07-24
[QUOTE=fng]i didnt use the installer for fuhquake.  I just downloaded the zipfile ([http://www.fuhquake.net/files/releases/v0.31/fuhquake-linux-v0.31.zip](http://www.fuhquake.net/files/releases/v0.31/fuhquake-linux-v0.31.zip)) unzipped it in a directory and .... taadaaa fuhquake works.[/QUOTE]

I'm very new to Linux and Ubuntu, I downloaded fuhquake-linux-v0.31.zip and unzipped it but I have no idea what to do with it now. 

Can someone help...I've looked all over the place for additional info.

---

### Post by DanielSmith604 on 2006-11-23
any tips on getting sqpro to work with the mouse configured and getting it to play without using 'sudo'?

Game runs fine when I run it using sudo:
```
daniel@ubuntu:/usr/local/games/quake$ sudo ./sqpro
Added packfile ./id1/pak0.pak (339 files)
Added packfile ./id1/pak1.pak (85 files)
PackFile: ./id1/pak1.pak : gfx/pop.lmp
Playing registered version.
PackFile: ./id1/pak0.pak : gfx.wad
Console initialized.
Security module initialized
UDP Initialized
Exe: 09:38:19 Sep 18 2002
 8.0 megabyte heap
PackFile: ./id1/pak0.pak : gfx/palette.lmp
PackFile: ./id1/pak0.pak : gfx/colormap.lmp
Warning: you have not yet configured your mouse type. If you have no mouse,
setting the type to `none' in /etc/vga/libvga.config will get rid of this
annoying message.
No mouse found
[svgalib: allocated virtual console #8]
```

Here's my output running it normally without super user privs:
```
daniel@ubuntu:/usr/local/games/quake$ ./sqpro
Added packfile ./id1/pak0.pak (339 files)
Added packfile ./id1/pak1.pak (85 files)
PackFile: ./id1/pak1.pak : gfx/pop.lmp
Playing registered version.
PackFile: ./id1/pak0.pak : gfx.wad
Console initialized.
Security module initialized
UDP Initialized
Exe: 09:38:19 Sep 18 2002
 8.0 megabyte heap
PackFile: ./id1/pak0.pak : gfx/palette.lmp
PackFile: ./id1/pak0.pak : gfx/colormap.lmp
Warning: you have not yet configured your mouse type. If you have no mouse,
setting the type to `none' in /etc/vga/libvga.config will get rid of this
annoying message.
No mouse found
svgalib: Cannot get I/O permissions.
```

Any suggestions? Answers or links to answers? thanks! ](*,)

---

