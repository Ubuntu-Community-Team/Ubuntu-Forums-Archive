---
title: "How can I play Zork?"
date: 2007-04-14
forum: Gaming &amp; Leisure
---

### Post by chrisrx on 2007-04-14
I've been reading up on zork recently and it sounds quite interesting,  I used to play a few text adventures.

But I haven't got a clue how to play it on linux,  has anyone got it to work?
What interpreter should I use etc.

---

### Post by dfreer on 2007-04-14
I had zork (or maybe minizork? is there a difference?) running using dosbox at one point in time... be careful though. It is dark out, you are likely to be eaten by a grue!

---

### Post by dfreer on 2007-04-14
[http://www.csd.uwo.ca/Infocom/](http://www.csd.uwo.ca/Infocom/)

You can download the DOS version of the game at the link above. Extract the game, and then install dosbox. start dosbox, and then type:
```
MOUNT C ~/zorkdownloadfolderhere
C:
zork1
```

Have fun!

---

### Post by chrisrx on 2007-04-14
Ah I found a much easier way,  Install frotz which is an interpreter
download zork from that link you posted
load DATA/ZORK1.DAT in frotz in the terminal

---

### Post by rolando2424 on 2007-04-14
You can play zork online I think.

I forgot the site though.

EDIT: I think it was in this site: [http://www.gameszoo.org/rezork/](http://www.gameszoo.org/rezork/)

---

### Post by fakie_flip on 2007-05-02
How do I install games using dosbox? I believe the game Shivers installs on Windows 95/3.1 and dos, but the SETUP.EXE is only for Win95, and the AUTOPLAY.EXE does not work either. Look at the picture I have attached.

---

### Post by davin on 2007-05-02
Play online man

---

### Post by Sonja on 2008-04-09
Frotz worked much better for me. 

The web-based one crashed sometimes, and saving and restoring is a bit annoying. (I wish it used cookies or something.)

Here's a song to put you in the mood: [http://ca.youtube.com/watch?v=4nigRT2KmCE](http://ca.youtube.com/watch?v=4nigRT2KmCE)

---

### Post by FranMichaels on 2008-04-09
Hmm, the last Sierra games I bought with Windows/DOS versions were Larry 7 and King's Quest 7. 

If memory serves, there should be an INSTALL.EXE (in addition to setup.exe) to use for DOS instead. Your screenshot didn't show the whole file listing...

Hope that works though.

EDIT: D'oh just realized I replied to a offtrack post in an old thread.
Back to zork, use frotz, don't bother emulating a full VM, and why play zork online if you can have it on your computer? (Unless you use different machines all the time, then I guess play it online...)

---

### Post by Ideastone on 2008-04-09
I miss King's Quest. Did anyone here ever play the original? I had it on my parent's Tandy 1000. It was great. Though, Oregon Trail is better than King's Quest and Zork.

---

### Post by FranMichaels on 2008-04-09
> **Ideastone said:**
> I miss King's Quest. Did anyone here ever play the original? I had it on my parent's Tandy 1000. It was great. Though, Oregon Trail is better than King's Quest and Zork.

I have played through King's Quest I-VII, never touched #8 though. Heard it had battling and was in 3D. Blah to that. Anyway, the above work perfectly in DOSBox, much better than running them on the old machines themselves.

---

### Post by Ideastone on 2008-04-10
> **FranMichaels said:**
> I have played through King's Quest I-VII, never touched #8 though. Heard it had battling and was in 3D. Blah to that. Anyway, the above work perfectly in DOSBox, much better than running them on the old machines themselves.

Awesome, now I need to track dow King's Quest I and relive my youth.

---

### Post by yaztromo on 2008-04-10
You are in a maze of corridors all alike, do you go North, East, South or West?
North
North
North
North

A stone wall blocks your path.
East
The forest closes in and blocks your path
West
West
West
You are eaten by a grue!

Bah :)

---

### Post by Ideastone on 2008-04-11
> **yaztromo said:**
> You are in a maze of corridors all alike, do you go North, East, South or West?
North
North
North
North

A stone wall blocks your path.
East
The forest closes in and blocks your path
West
West
West
You are eaten by a grue!

Bah :)

Eaten by a grue indeed. Back when I used to play with Gentoo I would have swore that some config files got ate by grues on occasion, but that could have just been user error on my part.

---

### Post by Totenglocke on 2008-04-29
I'm new to linux (just installed Ubuntu this past weekend) and I installed frotz, but frotz DATA/ZORK1.dat doesn't work.  I get an error saying that it cannot open the story file.  Any ideas?

---

### Post by linuxlizard on 2008-04-29
dosbox, wine, and vice (commodore 64 emulator).

If it's win95 try wine.

---

### Post by DirtDawg on 2008-04-29
Playing Zork is very easy.

Install frotz
```
sudo apt-get install frotz
```

Download Zork(s) from Infocom: [http://www.infocom-if.org/downloads/downloads.html](http://www.infocom-if.org/downloads/downloads.html)

Unzip Zork in desired location, then use frotz to run the DAT file located in the DATA directory inside the extracted Zork directory:
```
frotz ~/zork1/DATA/ZORK1.DAT
```

It works like a champ and there's no need to mess with Wine or Dosbox.

---

### Post by DirtDawg on 2008-04-29
> **Totenglocke said:**
> I'm new to linux (just installed Ubuntu this past weekend) and I installed frotz, but frotz DATA/ZORK1.dat doesn't work.  I get an error saying that it cannot open the story file.  Any ideas?

Frotz is case sensative. Try running DATA/ZORK1.DAT

---

### Post by Totenglocke on 2008-04-29
The case sensitive thing didn't work and the other told me "no such directory".  

Maybe I'm doing it wrong (again, new to Linux), but I made a folder named zGames inside my home folder.  I typed ~/zgames/zork1/data/zork1.dat and it said that the directory does not exist.  Now (I realized I forgot the frotz) I typed frotz ~/zgames/zork1/data/zork1.dat and it again said it cannot open the story file.

---

### Post by DirtDawg on 2008-04-29
> **Totenglocke said:**
> The case sensitive thing didn't work and the other told me "no such directory".  

Maybe I'm doing it wrong (again, new to Linux), but I made a folder named zGames inside my home folder.  I typed ~/zgames/zork1/data/zork1.dat and it said that the directory does not exist.  Now (I realized I forgot the frotz) I typed frotz ~/zgames/zork1/data/zork1.dat and it again said it cannot open the story file.

When I extracted zork, I did so into a folder called "zork1", but the files inside were all caps. So to run, I had to use:
```
frotz ~/zork1/DATA/ZORK1.DAT
```
Note that the "~" at the beginning is shorthand for your home folder (/home/dirtdawg/ in my case).

The first time you tried, it didn't work probably because there is no "~/zgames/zork1/data/" folder but a "~/zgames/zork1/DATA/" folder. When you use the frotz command, it will always tell you it can't open the story file no matter the error. If you try:
```
frotz /all/cows/eat/grass
```
you will get the same message (though most cows eat starchy corn nowadays).

If what you're saying is accurate, my guess is this command will work:
```
fortz ~/zgames/zork1/DATA/ZORK1.DAT
```

If that doesn't work, I would recommend double checking the files to make sure you have the caps and the path correct (zgames or zGames?). If you are certain that your path is correct and all the caps are correct, then maybe your download was corrupted and you should download again. If it still doesn't work, then "your frotz is broken" :)

---

### Post by Totenglocke on 2008-04-29
FINALLY!  I tried doing exactly what you just said, but I guess I was missing a cap somewhere.....it works now. I feel like an idiot.  Surprisingly, I got everything working after installing Ubuntu within 2 hours, yet I couldn't get a simple game to run.......

---

### Post by DirtDawg on 2008-04-29
> **Totenglocke said:**
> FINALLY!  I tried doing exactly what you just said, but I guess I was missing a cap somewhere.....it works now. I feel like an idiot.  Surprisingly, I got everything working after installing Ubuntu within 2 hours, yet I couldn't get a simple game to run.......

Hey, you're learning so cut yourself a little slack. We've all been there before. Glad you got it working. :KS

---

### Post by Totenglocke on 2008-04-29
Now what I want to know is, how do I write a script or make some kind of a shortcut so that I either 1) click on an icon to start the game or 2) type something like "zork1" and start it?

---

### Post by Totenglocke on 2008-04-29
Actually, scratch that, I found a site that showed me how to write a script.

---

### Post by Grishka on 2008-04-30
you don't need a script. get this: [http://ccxvii.net/gargoyle/](http://ccxvii.net/gargoyle/).

---

### Post by k33bz on 2008-05-02
great game btw.

I didnt install frotz, seemed better for me to use dosbox, since i have alot of old dos games i play.

and if you use dosbox, you dont install the games onto your system, just need to know where you put the system game files at. for instance mine are located in its own home folder, that my main account has access to. so i start up dosbox:
```
mount c /home/dos
cd c
```
and that is all i do.

---

### Post by Bilderbikkel on 2010-11-20
I have ported the Zork C++ source code to a Qt Creator project: [http://richelbilderbeek.nl/GameZork.htm](http://richelbilderbeek.nl/GameZork.htm) . Compile it to play in a terminal. Have fun, Bilderbikkel

---

### Post by Sslaxx on 2010-11-21
> **Bilderbikkel said:**
> I have ported the Zork C++ source code to a Qt Creator project: [http://richelbilderbeek.nl/GameZork.htm](http://richelbilderbeek.nl/GameZork.htm) . Compile it to play in a terminal. Have fun, Bilderbikkel
You should have the copyright disclaimers for *Activision*, not Infocom.

---

### Post by Bilderbikkel on 2010-11-21
> **Sslaxx said:**
> You should have the copyright disclaimers for *Activision*, not Infocom.

Dear Sslaxx,

Thanks for this notice, yet I still believe Infocom has created Zork, due to the Wikipedia page about Zork ([http://en.wikipedia.org/wiki/Zork](http://en.wikipedia.org/wiki/Zork)) and the Infocom page about Zork ([http://www.infocom-if.org/games/zork1/zork1.html](http://www.infocom-if.org/games/zork1/zork1.html)). Searching the Activision website for Zork does not yield its page. Why do you think Activision created it nevertheless?

Thanks in advance, Bilderbikkel

---

### Post by Sslaxx on 2010-11-21
Creation has nothing to do with it. Activision own the copyrights to the original Zork game as they own the assets of Infocom.

---

### Post by Bilderbikkel on 2010-11-22
> **Sslaxx said:**
> Creation has nothing to do with it. Activision own the copyrights to the original Zork game as they own the assets of Infocom.

Dear Sslaxx, I believe you and have changed the disclaimer. Thanks, Bilderbikkel

---

