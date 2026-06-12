---
title: "[SOLVED] Ripping PS2 Games"
date: 2008-08-13
forum: Gaming &amp; Leisure
---

### Post by DeathOnJuice on 2008-08-13
I'm trying to rip my copy of FFX to play with pcsx2, but I'm running into problems. To rip PSX games, I've always done:

dd if=/dev/scd0 of=game.iso

But, when I tried to play the ISO for FFX, I just got a black screen. Playing from the CD works, and I tried to rip it twice, so I know that's the problem. An odd fact was that the DVD drive was VERY loud throughout this entire process.

I'm using the SVN version of pcsx2, and its ISO-reading plugin has a ripping feature. However, this lasted half of a day for just one game. This image turned out to be only 2GB and didn't work - when I ran it, pcsx2 just went to the PS2 menu screen. Additionally, this entire time ripping, messages like this were produced (at about a terminal-screen-full per second):

```

Error Reading 87:30: 814Kbytes/s, 0X)
Error Reading 87:30: 914Kbytes/s, 0X)
Error Reading 87:30:1014Kbytes/s, 0X)
Error Reading 87:30:1114Kbytes/s, 0X)
Error Reading 87:30:1214Kbytes/s, 0X)
Error Reading 87:30:1314Kbytes/s, 0X)
Error Reading 87:30:1414Kbytes/s, 0X)
Error Reading 87:30:1514Kbytes/s, 0X)
Error Reading 87:30:1614Kbytes/s, 0X)
Error Reading 87:30:1714Kbytes/s, 0X)
Error Reading 87:30:1814Kbytes/s, 0X)
Error Reading 87:30:1914Kbytes/s, 0X)
Error Reading 87:30:2014Kbytes/s, 0X)
Error Reading 87:30:2114Kbytes/s, 0X)
Error Reading 87:30:2214Kbytes/s, 0X)
Error Reading 87:30:2314Kbytes/s, 0X)
Error Reading 87:30:2414Kbytes/s, 0X)

```

How can I rip a PS2 game properly in Linux? Thanks.

---

### Post by FranMichaels on 2008-08-14
Here is how I've always backed up my psx games.

[http://pearsfyh.blogspot.com/2007/11/backing-up-non-pc-cd.html](http://pearsfyh.blogspot.com/2007/11/backing-up-non-pc-cd.html)

I should really try my hand at pcsx2, as I've got access to a 64-bit Ubuntu box now (shared with family.), and plenty of ps2 games to see if I can back up with this method...

Hope this helps.

---

### Post by cristo-father on 2008-08-14
[http://www.youtube.com/watch?v=zPEcCEDu_qI](http://www.youtube.com/watch?v=zPEcCEDu_qI), do not worry, because dvddecrypter works well with wine.
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=1558](http://appdb.winehq.org/objectManager.php?sClass=application&iId=1558)

---

### Post by DeathOnJuice on 2008-08-14
I tried all of those solutions, but nothing worked. Once I get an ISO, they all have the same problem. A black screen displays with about 150FPS, and the output is always like this (the last number is always the same too, on the isoReadBlock lines):

Complete output. These lines didn't go on forever.
```
_openfile /home/mark/Desktop/Emulation/ps2/ffx.iso 0
detected blocksize = 2048
isoOpen: /home/mark/Desktop/Emulation/ps2/ffx.iso ok
offset = 0
blockofs = 24
blocksize = 2048
blocks = 104128
type = 2
ZeroGS: creating
ZeroGS: Got Doublebuffered Visual!
ZeroGS: glX-Version 1.3
ZeroGS: Depth 24
ZeroGS: you have Direct Rendering!
ZeroGS: Disabling MRT depth writing
ZeroGS: Creating effects
ZeroGS: Creating extra effects
ZeroGS: using accurate shaders
ZeroGS: initialization successful
ZeroGS: Disabling MRT depth writing
isoReadBlock: 386206 > 104128
isoReadBlock: 327075 > 104128
isoReadBlock: 327076 > 104128
isoReadBlock: 327075 > 104128
isoReadBlock: 327076 > 104128
isoReadBlock: 327077 > 104128
isoReadBlock: 327078 > 104128
isoReadBlock: 327079 > 104128
isoReadBlock: 327080 > 104128
isoReadBlock: 327080 > 104128
isoReadBlock: 327081 > 104128
isoReadBlock: 327143 > 104128
isoReadBlock: 327144 > 104128
isoReadBlock: 327143 > 104128
isoReadBlock: 327144 > 104128
isoReadBlock: 327145 > 104128
isoReadBlock: 327146 > 104128
isoReadBlock: 327147 > 104128
isoReadBlock: 327148 > 104128
isoReadBlock: 327149 > 104128
isoReadBlock: 327150 > 104128
isoReadBlock: 327151 > 104128
isoReadBlock: 327152 > 104128
isoReadBlock: 327152 > 104128
isoReadBlock: 327153 > 104128
isoReadBlock: 327154 > 104128
isoReadBlock: 327155 > 104128
isoReadBlock: 327156 > 104128
isoReadBlock: 327157 > 104128
isoReadBlock: 327158 > 104128
isoReadBlock: 327159 > 104128
isoReadBlock: 327160 > 104128
isoReadBlock: 327161 > 104128
isoReadBlock: 327162 > 104128
isoReadBlock: 327163 > 104128
isoReadBlock: 327164 > 104128
isoReadBlock: 327165 > 104128
isoReadBlock: 327166 > 104128
isoReadBlock: 327167 > 104128
isoReadBlock: 327168 > 104128
isoReadBlock: 327168 > 104128
isoReadBlock: 327169 > 104128
isoReadBlock: 327170 > 104128
isoReadBlock: 327171 > 104128
isoReadBlock: 327172 > 104128
isoReadBlock: 327173 > 104128
isoReadBlock: 327174 > 104128
isoReadBlock: 327174 > 104128
isoReadBlock: 327111 > 104128
isoReadBlock: 327112 > 104128
isoReadBlock: 327111 > 104128
isoReadBlock: 327112 > 104128
isoReadBlock: 327113 > 104128
isoReadBlock: 327114 > 104128
isoReadBlock: 327115 > 104128
isoReadBlock: 327116 > 104128
isoReadBlock: 327117 > 104128
isoReadBlock: 327118 > 104128
isoReadBlock: 327119 > 104128
isoReadBlock: 327120 > 104128
isoReadBlock: 327120 > 104128
isoReadBlock: 327121 > 104128
isoReadBlock: 327122 > 104128
isoReadBlock: 327123 > 104128
isoReadBlock: 327124 > 104128
isoReadBlock: 327125 > 104128
isoReadBlock: 327126 > 104128
isoReadBlock: 327127 > 104128
isoReadBlock: 327128 > 104128
isoReadBlock: 327129 > 104128
isoReadBlock: 327130 > 104128
isoReadBlock: 327131 > 104128
isoReadBlock: 327132 > 104128
isoReadBlock: 327133 > 104128
isoReadBlock: 327134 > 104128
isoReadBlock: 327135 > 104128
isoReadBlock: 327136 > 104128
isoReadBlock: 327136 > 104128
isoReadBlock: 327137 > 104128
isoReadBlock: 327138 > 104128
isoReadBlock: 327139 > 104128
isoReadBlock: 327140 > 104128
isoReadBlock: 327141 > 104128
isoReadBlock: 327142 > 104128
isoReadBlock: 327142 > 104128
isoReadBlock: 327354 > 104128
isoReadBlock: 327355 > 104128
isoReadBlock: 327354 > 104128
isoReadBlock: 327355 > 104128
isoReadBlock: 327356 > 104128
isoReadBlock: 327357 > 104128
isoReadBlock: 327358 > 104128
isoReadBlock: 327359 > 104128
isoReadBlock: 327360 > 104128
isoReadBlock: 327361 > 104128
isoReadBlock: 327361 > 104128
isoReadBlock: 327186 > 104128
isoReadBlock: 327187 > 104128
isoReadBlock: 327188 > 104128
isoReadBlock: 327189 > 104128
isoReadBlock: 327190 > 104128
isoReadBlock: 327191 > 104128
isoReadBlock: 327192 > 104128
isoReadBlock: 327193 > 104128
isoReadBlock: 327194 > 104128
isoReadBlock: 327195 > 104128
isoReadBlock: 327194 > 104128
isoReadBlock: 327195 > 104128
isoReadBlock: 327196 > 104128
isoReadBlock: 327197 > 104128
isoReadBlock: 327198 > 104128
isoReadBlock: 327199 > 104128
isoReadBlock: 327200 > 104128
isoReadBlock: 327201 > 104128
isoReadBlock: 327202 > 104128
isoReadBlock: 327203 > 104128
isoReadBlock: 327204 > 104128
isoReadBlock: 327205 > 104128
isoReadBlock: 327206 > 104128
isoReadBlock: 327207 > 104128
isoReadBlock: 327208 > 104128
isoReadBlock: 327209 > 104128
isoReadBlock: 327209 > 104128
isoReadBlock: 327095 > 104128
isoReadBlock: 327096 > 104128
isoReadBlock: 327095 > 104128
isoReadBlock: 327096 > 104128
isoReadBlock: 327097 > 104128
isoReadBlock: 327098 > 104128
isoReadBlock: 327099 > 104128
isoReadBlock: 327100 > 104128
isoReadBlock: 327101 > 104128
isoReadBlock: 327102 > 104128
isoReadBlock: 327102 > 104128
isoReadBlock: 327362 > 104128
isoReadBlock: 327363 > 104128
isoReadBlock: 327364 > 104128
isoReadBlock: 327363 > 104128
isoReadBlock: 327364 > 104128
isoReadBlock: 327365 > 104128
isoReadBlock: 327366 > 104128
isoReadBlock: 327367 > 104128
isoReadBlock: 327368 > 104128
isoReadBlock: 327369 > 104128
isoReadBlock: 327370 > 104128
isoReadBlock: 327371 > 104128
isoReadBlock: 327371 > 104128
isoReadBlock: 327372 > 104128
isoReadBlock: 327373 > 104128
isoReadBlock: 327374 > 104128
isoReadBlock: 327373 > 104128
isoReadBlock: 327374 > 104128
isoReadBlock: 327375 > 104128
isoReadBlock: 327376 > 104128
isoReadBlock: 327376 > 104128
isoReadBlock: 327377 > 104128
isoReadBlock: 327378 > 104128
isoReadBlock: 327379 > 104128
isoReadBlock: 327380 > 104128
isoReadBlock: 327381 > 104128
isoReadBlock: 327382 > 104128
isoReadBlock: 327383 > 104128
isoReadBlock: 327384 > 104128
isoReadBlock: 327385 > 104128
isoReadBlock: 327386 > 104128
isoReadBlock: 327387 > 104128
isoReadBlock: 327388 > 104128
isoReadBlock: 327389 > 104128
isoReadBlock: 327389 > 104128
isoReadBlock: 327390 > 104128
isoReadBlock: 327082 > 104128
isoReadBlock: 327083 > 104128
isoReadBlock: 327082 > 104128
isoReadBlock: 327083 > 104128
isoReadBlock: 327084 > 104128
isoReadBlock: 327085 > 104128
isoReadBlock: 327086 > 104128
isoReadBlock: 327087 > 104128
isoReadBlock: 327088 > 104128
isoReadBlock: 327089 > 104128
isoReadBlock: 327090 > 104128
isoReadBlock: 327090 > 104128
isoReadBlock: 327091 > 104128
isoReadBlock: 327093 > 104128
isoReadBlock: 327092 > 104128
isoReadBlock: 327094 > 104128
isoReadBlock: 385595 > 104128
isoReadBlock: 385596 > 104128
isoReadBlock: 385597 > 104128
isoReadBlock: 385598 > 104128
isoReadBlock: 385599 > 104128
isoReadBlock: 385600 > 104128
isoReadBlock: 385601 > 104128
isoReadBlock: 385602 > 104128
isoReadBlock: 385603 > 104128
isoReadBlock: 385604 > 104128
isoReadBlock: 328364 > 104128
isoReadBlock: 328365 > 104128
isoReadBlock: 328366 > 104128
isoReadBlock: 328367 > 104128
isoReadBlock: 328368 > 104128
isoReadBlock: 328369 > 104128
isoReadBlock: 328370 > 104128
isoReadBlock: 328371 > 104128
isoReadBlock: 328372 > 104128
isoReadBlock: 328373 > 104128
isoReadBlock: 328374 > 104128
isoReadBlock: 328375 > 104128
isoReadBlock: 328376 > 104128
isoReadBlock: 328377 > 104128
isoReadBlock: 328378 > 104128
isoReadBlock: 328379 > 104128
isoReadBlock: 330976 > 104128
isoReadBlock: 330977 > 104128
isoReadBlock: 330978 > 104128
isoReadBlock: 330979 > 104128
isoReadBlock: 330980 > 104128
isoReadBlock: 330981 > 104128
isoReadBlock: 330982 > 104128
isoReadBlock: 330983 > 104128
isoReadBlock: 330984 > 104128
isoReadBlock: 330985 > 104128
isoReadBlock: 330986 > 104128
isoReadBlock: 330987 > 104128
isoReadBlock: 330988 > 104128
isoReadBlock: 330989 > 104128
isoReadBlock: 330990 > 104128
isoReadBlock: 330991 > 104128
isoReadBlock: 328364 > 104128
isoReadBlock: 328365 > 104128
isoReadBlock: 328366 > 104128
isoReadBlock: 328367 > 104128
isoReadBlock: 328368 > 104128
isoReadBlock: 328369 > 104128
isoReadBlock: 328370 > 104128
isoReadBlock: 328371 > 104128
isoReadBlock: 328372 > 104128
isoReadBlock: 328373 > 104128
isoReadBlock: 328374 > 104128
isoReadBlock: 328375 > 104128
isoReadBlock: 328376 > 104128
isoReadBlock: 328377 > 104128
isoReadBlock: 328378 > 104128
isoReadBlock: 328379 > 104128
isoReadBlock: 386189 > 104128
isoReadBlock: 386190 > 104128
isoReadBlock: 386191 > 104128
isoReadBlock: 386192 > 104128
isoReadBlock: 386193 > 104128
isoReadBlock: 386194 > 104128
isoReadBlock: 386195 > 104128
isoReadBlock: 386196 > 104128
isoReadBlock: 386197 > 104128
isoReadBlock: 386198 > 104128
PCSX2 Quitting

```

 FranMichaels, I use your command for pSX games as well; dd is for DVDs. However, it doesn't even start on PS2 games.

However, I had only been trying FFX. dd worked perfectly with Dragon Quest VIII (no isoReadBlock statements)! I don't know why FFX doesn't work, however; it's a brand new disk (much newer than DQVIII), and as I said, playing from the CD works. Does anyone have any ideas? Is it a bad rip, or a problem with pcsx2? I really want to have a good rip for when the game eventually dies.

---

### Post by cisforcojo on 2008-08-15
I may be way off here but I believe AcetoneISO2 works. You can get it from [www.getdeb.net](www.getdeb.net). I'm positive it works for PSX... little foggy on PS2 developments.

---

### Post by DeathOnJuice on 2008-08-17
The rip must be fine, as it ran in a Windows installation of pcsx2. Ergo, I have a working backup, and my OCD is cleared. Solved!

---

