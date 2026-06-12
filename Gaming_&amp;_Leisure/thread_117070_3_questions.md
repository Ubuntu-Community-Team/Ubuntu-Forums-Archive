---
title: "3 questions"
date: 2006-01-14
forum: Gaming &amp; Leisure
---

### Post by Ubuntuud on 2006-01-14
Hi, I've got three noobish questions
1:
Does anyone know how to install the original tuxracer?
2:
I have unpacked all Glest files, which one should I open?
3:
The Tribal Trouble Demo file doesn't want to open, what should I do?

Thanks

---

### Post by ardchoille on 2006-01-14
[QUOTE=Ubuntuud]Hi, I've got three noobish questions
1:
Does anyone know how to install the original tuxracer?
2:
I have unpacked all Glest files, which one should I open?
3:
The Tribal Trouble Demo file doesn't want to open, what should I do?

Thanks[/QUOTE]
1. The game TuxRacer isn't developed anymore, but a fork called PlanetPenguin
Racer exists.

2. 

3. What kind of file is the Tribal Trouble Demo?

---

### Post by Perfect Storm on 2006-01-14
2. which format did you get? [.deb] [Loki] [Source] [.rpm]

3. The Demo is a .sh file so you need to **sudo sh /bla/bla/blah/<name of the file>**

---

### Post by Ubuntuud on 2006-01-14
1: I know about PlanetPinguinracer but I liked the original more, simple... Is it really impossible to get the original?
2: I downloaded .deb
3: Artificial Intelligence, it isn't working... The first directory, should that be "bestandsbeheer" (it's Dutch, I think it is file management in English) or "Persoonlijk" (something like Personal in English). And should I put .sh behind the <name of the file>?

---

### Post by Ubuntuud on 2006-01-14
And I have a fourth question: Scorched3D crashes after loading. Is this my computer or should I type a certain comandline?

---

### Post by Perfect Storm on 2006-01-14
2.

```
sudo dpkg -i /where/the/package/is/XXXXXXXXX.deb
```

3.

Yes if the file name end with .sh
so it would look like:

```

sudo sh /where/the/package/is/XXXXXXXXXXX.sh
```

---

### Post by Perfect Storm on 2006-01-14
[QUOTE=Ubuntuud]And I have a fourth question: Scorched3D crashes after loading. Is this my computer or should I type a certain comandline?[/QUOTE]

Did you installed it through apt-get?

---

### Post by Ubuntuud on 2006-01-14
I installed it throught apt-get yes. And thanks for all the help, how do you know all this????

---

### Post by Ubuntuud on 2006-01-14
And another thing, what should be on the place of "/where/"? home? (it is in home, but I don't know on what level (with level I mean the map-level, like /level1/level2/level3 etc.))

---

### Post by Perfect Storm on 2006-01-14
Start the game in terminal and post the (error) output.

> how do you know all this????

Mind reading ;)

---

### Post by Ubuntuud on 2006-01-14
No need for that, allready solved it, thanks anyway.

---

### Post by Rasymas on 2006-01-14
Sorry for posting here, but does anyone know what to type in order to start a game, I have MAFIA already isntalled on my machine, but I don't knwo what to type now :)

---

### Post by Ubuntuud on 2006-01-14
Try typing MAFIA...
But to make an overview from what I still need to know. Here are updated questions and problems

1:
Scorched3D keeps on crashing. (I installed it with apt-get)
2:
Glest... I did what artificial intelligence said (sudo dpkg -1 ////file) There is an icon now, but it doesn't work. I think that's because the second package (glest_1.0.10-7_i386.deb) caused an error.
3:
Is it possible to get the original Tuxracer? And no, not PlanetPenguinRacer!

---

### Post by Ubuntuud on 2006-01-19
Some extra information about the Scorched3D crashing: it crashes when I double-click on the "icon" of my tank. It zooms in, and then my entire screen turns black (even when in windowed mode), and I have to restart my PC.

---

### Post by r4ik on 2006-01-19
[QUOTE=Ubuntuud]1: I know about PlanetPinguinracer but I liked the original more, simple... Is it really impossible to get the original?
2: I downloaded .deb
3: Artificial Intelligence, it isn't working... The first directory, should that be "bestandsbeheer" (it's Dutch, I think it is file management in English) or "Persoonlijk" (something like Personal in English). And should I put .sh behind the <name of the file>?[/QUOTE]

Some advice for you.
If you want you can switch language  systeem>administratie>taalkeuze
Uncheck the Dutch language and it will be all English (after restart)
Once you get used to it things seems to be more easy :)
It stopped me from "thinking" Dutch so i didnt have to make the translation over and over again.

---

### Post by Ubuntuud on 2006-02-05
Are you using Hoary? There isn't an "administratie" in my Breezy...

---

