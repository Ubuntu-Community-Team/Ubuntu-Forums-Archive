---
title: "Problems with 3D games."
date: 2005-05-05
forum: Gaming &amp; Leisure
---

### Post by SparkyDawg on 2005-05-05
I've recently become a Ubuntu user, and absolutely love it. Yet there is one problem I've been having with Ubuntu that I can't seem to figure out. I have Wolfenstein: Enemy Territory and Counter Strike: Source. I run CSS through Cedega and Wolfenstein was made for Linux.

Both of those games run great, I have an AMD Athlon 2500+ and a GeForce TI 500. The only problem is the game will only run for 30 seconds to 10 minutes, then it just closes without any error message. Anyone know any solutions? I've tried unoverclocking my processor, but no dice.

Thanks in advance.

---

### Post by 23meg on 2005-05-05
hi and welcome. i'm not very proficient with games or emulation, but i'd advise you to try launching enemy territory from terminal, and see if it reports any error messages there before it quits.

---

### Post by SparkyDawg on 2005-05-05
Tryed with Terminal, it didn't close yet booted me off the server and game me an "R_addentitysurfaces bad retype.

Strange?

EDIT: Still closes, and it closes terminal to when I run it in terminal therefore I can't see the error message.

---

### Post by SparkyDawg on 2005-05-06
...anyone?

---

### Post by jensyt on 2005-05-06
If it kills the terminal to where you can't see what it outputs, try redirecting the output to a file for later use.

```

et &> /home/YOUR_USERNAME/et.error

```
Note that 'YOUR_USERNAME' needs to be replaced with your username (so it goes to your home directory). Or you could just, if you want to save it to the directory you're currently in, type 'et.error', instead of the whole '/home/', etc..

Either way, after it crashes, open that file in your favorite text editor and paste the file contents here.

---

### Post by SparkyDawg on 2005-05-06
Got the terminal fixed, here are the last lines of the terminal:
stack:
c41e5781 a548c9f4 00000000 a542ff38 ab4f2858 ab4fff90 a86cfcc0 a542fa83
bffff5f0 a7d91b60 a8ae0a80 08084f62 bffff560 c20cd8d0 a7d91f60 a53e4e40
00000000 00000720 00000000 a53e4dfc 40dbfc96 a86cfcc0 3f93fe58 a53e55e6
00000000 0000000d 00000082 00000000 00000000 00000000 a86d0354 a86d0350
code:
89 42 10 8b 56 10 85 d2 74 06 8b 46 0c 89 42 0c c7 46 0c 00 00 00 00 8b 93 10
fd ff ff c7 46 10 00 00 00 00 c7 46 04 00 00 00 00 8b 02 89 06 8b 02 85 c0 74
Stack trace: 1 entries
/home/ryanomalley/.etwolf/etpro/cgame.mp.i386.so[0xa53c0797]
------------- CUT HERE --------------
Trying to clean up...
Received signal 11, exiting...
Shutdown tty console
Segmentation fault

---

### Post by SparkyDawg on 2005-05-07
What might be the problem for the segmentation fault?

Sorry for double posting.

---

### Post by SparkyDawg on 2005-05-07
Aha, when I turn down the graphics in ET, it takes a lot longer to crash. When I turn them up to max, it's only a matter of seconds. Something to do with my ram frying up maybe? Any suggestions?

---

### Post by SparkyDawg on 2005-05-07
Whoa, I unoverclocked it another 100 mhz, everything works fine now.

---

### Post by crane on 2005-05-07
[QUOTE=SparkyDawg]Whoa, I unoverclocked it another 100 mhz, everything works fine now.[/QUOTE]

Cool, glad you got it all worked out for yourself. Sorry I missed the post. I had the same problem with quake3 for a while. Then one day while poking around inside my compter I noticed that my memeory was in slots 2 and three not one and two. I didn't think much of it at the time but swapped them non the less. After doing this however Q3 has not crashed since then.

---

### Post by SparkyDawg on 2005-05-08
[QUOTE=crane]Cool, glad you got it all worked out for yourself. Sorry I missed the post. I had the same problem with quake3 for a while. Then one day while poking around inside my compter I noticed that my memeory was in slots 2 and three not one and two. I didn't think much of it at the time but swapped them non the less. After doing this however Q3 has not crashed since then.[/QUOTE]

No prob.

I had mine overclocked quite a bit  ](*,)

---

### Post by freakez on 2005-11-12
Did you tried to install the ubuntuaddon package, this comes with XFCE and works for me.

I tried to install ET to gnome not working also with option + alow opengl you know.

Also KDE crashed wheni tried to launch the game.

In XFCE it woked just fine. no errors.
Only exetute your game in your terminal:

./et +set r_allowSoftwareGL 1
:D

---

