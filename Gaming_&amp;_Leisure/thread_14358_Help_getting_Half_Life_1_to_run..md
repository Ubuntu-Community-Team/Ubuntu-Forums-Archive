---
title: "Help getting Half Life 1 to run."
date: 2005-02-06
forum: Gaming &amp; Leisure
---

### Post by Ricapar on 2005-02-06
I'm using Wine to install HL: GOTY edition. The installation went well, so I went to run hl.exe. I got the message box asking for the CD key, but when I tried typing it in, nothing happend. I kept pressing keys, but nothing would show up in the box.

Help?

---

### Post by valadil on 2005-02-06
One of the things Cedega/Winex/Wine always struggled with in my experience was displaying fonts.  It could be that the numbers are being entered but not being written to screen correctly.  Try typing it in blindly and see if it'll accept.

Also, I doubt you're installing HL1 for its multiplayer greatness.  If all you do is singleplayer and lan games I think you're allowed to have a bad cd key.

Finally, I had the most luck with HL1 in plain old vanilla wine.  If cedega isn't happy you might want to try original wine, which is actually free.

---

### Post by jdodson on 2005-02-07
[QUOTE=Ricapar]I'm using Wine to install HL: GOTY edition. The installation went well, so I went to run hl.exe. I got the message box asking for the CD key, but when I tried typing it in, nothing happend. I kept pressing keys, but nothing would show up in the box.

Help?[/QUOTE]

did you click the mouse inside the box that makes you enter the key?  if you have then i would recommend cedega.

---

### Post by mrt on 2005-02-07
[QUOTE=Ricapar]I'm using Wine to install HL: GOTY edition. The installation went well, so I went to run hl.exe. I got the message box asking for the CD key, but when I tried typing it in, nothing happend. I kept pressing keys, but nothing would show up in the box.

Help?[/QUOTE]
I've found that I'm able to paste the key in.  Just type it out in gedit (or whatever), then copy and paste it in.

Let us know how it runs, though.  I could never get it to fully run.

---

### Post by Ricapar on 2005-02-07
YAY! It worked! I copied and pasted the CD Key from gedit.

It runs really good. I got a constant 72.1 frames per second through everything using this computer:
AMD Athlon @ 1.44GHz
600 something MB of PC100 RAM
GeForce FX 5200
(Not bad for a computer I found in the trash :D)


To get it to run I had to edit the xf86 config file to go to 16bit colors though, I couln't find an option anywhere else to change that.

To start it up in wine, I used
```

wine hl.exe -dev -console

```
It wouldn't start otherwise for some reason.

Thanks again.

EDIT: I also had to install the 1.1.1.0 update patch to remove the screen where it asks for the CD. CD was in the drive, but wasn't detecting it.

---

### Post by jdodson on 2005-02-07
[QUOTE=Ricapar]YAY! It worked! I copied and pasted the CD Key from gedit.

It runs really good. I got a constant 72.1 frames per second through everything using this computer:
AMD Athlon @ 1.44GHz
600 something MB of PC100 RAM
GeForce FX 5200
(Not bad for a computer I found in the trash :D)
[/QUOTE]

ill say.  thats a cool find.

---

