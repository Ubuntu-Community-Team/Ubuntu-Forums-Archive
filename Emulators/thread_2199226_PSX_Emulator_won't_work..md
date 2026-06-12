---
title: "PSX Emulator won't work."
date: 2014-01-12
forum: Emulators
---

### Post by d-wall08 on 2014-01-12
I downloaded PSX for windows, installed it with wine, and it runs. Yet, when i try to open an .iso with it I get an error saying that it can't read the CD plugin. I also have the Linux version which when i click on it it does nothing. How can i get the windows PSX version to play .iso's? do i really need a plugin? and where do i get it? Any ideas? Has anyone had this problem. I have Ubuntu 12.4, 32bit, no dual boot. Thanks.

---

### Post by deadflowr on 2014-01-12
Isn't psx really old, and possibly dead.
Install pcsx from the repos.
I think it's actually pscxr or pcsx reloaded.
It comes with a bunch of plugins, and a dummy bios.
You then launch it and in the window it opens, you can configure the cd drive.

Another thing to note is that the psx and epsxe and pcsx programs only work for the playstation one games.
If you want to run ps2 games, you'll could try pcsx2, which also require ALOT more system resources.

---

### Post by sffvba[e0rt on 2014-01-12
*Thread moved to **Emulators**.*

---

### Post by varunendra on 2014-01-13
@ d-wall08,

Support questions should always be asked in the threads, not in PM. By doing so, you get more and better, peer-reviewed answers, and the helpers are able to help more people while replying just once. :)

Posting your PM here so others can see and reply if they can -
[QUOTE=d-wall08]Thanks for the tip. For I am new to the community. Well I have a question for who, hopefully you can answer. I have PSX Emulator. the emulator is fine and runs when opened, yet the Roms I download and unzip are .bin and .cue. When I try to open the games in PSX theres an error, pretty much PSX can't read them. Am I doing something wrong? I know PSX needs .ISO games. Do I have to convert the .cue file to .iso?[/QUOTE]
The files you downloaded are probably either in a format that PCSX doesn't understand, or like deadflower pointed out above, could be a version that PCSX can't handle (it can play only playstation 1 games, and even that is not guaranteed for all games).

Your best bet, IMHO, is to burn a CD from those files so that the added complexity of reading the image is eliminated. Either that, or try **[gCDemu]("http://cdemu.sourceforge.net/")** from its ppa. Like DaemonTools in Windows, it can handle a lot of cd/dvd image formats, and is a near-perfect CD/DVD drive emulator for Linux.

---

### Post by d-wall08 on 2014-01-13
Thanks! I'll give it a try.

---

### Post by d-wall08 on 2014-01-13
Thanks! I'll give it a try. I still don't know how what to do with the .tar.bz files though, have no clue.

---

