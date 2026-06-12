---
title: "Help wanted for PrBoom"
date: 2007-08-19
forum: Gaming &amp; Leisure
---

### Post by Chuckles8732 on 2007-08-19
Hi,

I just installed prboom through synaptic package manager, and was excited to be able to play doom on my laptop, but I have a couple of  problems. The first is that the program will only work with the freedoom wad it came with, and only if it's in the directory it installed in, if I move it, it will not work, even if I add "-iwad (location of freedoom wad).wad" to the command to start it. It doesn't even work if I replace the freedoom wad with the doom 2 wad.  My second problem is music. My sound works, but I have no music. I downloaded the timidity instruments and unzipped them to the directory I was told to, but they do not work.

My executable is in /usr/games.

My freedoom and prboom wads are in usr/share/games/freedoom and usr/share/games/doom, respectively.

My timidity instruments are in /usr/local/lib/timidity.

I can move these files anywhere if needed. Any help would be greatly appreciated.

---

### Post by Chuckles8732 on 2007-08-19
Well, I just found out what wine does, so I think I'll try to run a windows source port through it. Any help with prboom is still appreciated, though I may not need it soon. :)

---

### Post by CowzRule on 2007-08-19
See the following site about a Linux port for Doom
[http://www.doomsdayhq.com/]("http://www.doomsdayhq.com/")

---

### Post by ChrisNiemy on 2009-11-08
Make sure you have installed timidity and freepats.

Then edit the prboom conifguration in your home directory:

cd ~
cd .prboom
gedit prboom.cfg

Search for "# Sound Settings", I guess it's the sixth paragraph in that config file.


Change the values of sound_card and music_card from -1 to 1

Change the value of samplerate to 44100

That worked for me. I guess it's a misconfiguration which is installed by default.

---

### Post by Louigi Verona on 2011-01-31
Thanks. This helped. Although I must say the way it plays midi is so horrible that I have to turn off music anyway. Pity.

---

### Post by Perfect Storm on 2011-01-31
[[img]http://s4.postimage.org/jbyj0j85e/Thread_Necromancer.jpg[/img]](http://www.postimage.org/)

---

