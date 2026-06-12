---
title: "I need help with installing and running a game!"
date: 2006-05-30
forum: Gaming &amp; Leisure
---

### Post by novik420 on 2006-05-30
I just got ubuntu up today and i have wine etc... I am trying to installl Diablo 2 and Diablo 2 LOD I installed Diablo 2 with no trouble but i can not start it. And with Diablo 2 LOD when i go to install it tells me to insert LOD disc (which is already in drive) If anyone can help me at all i would love it~ By the way i am new

---

### Post by croak77 on 2006-05-30
I'm not much of a gamer but you can try these instructions:

[http://www.frankscorner.org/index.php?p=diablo2](http://www.frankscorner.org/index.php?p=diablo2)

---

### Post by novik420 on 2006-05-31
I need some help with installing a game, Diablo 2 and diablo 2 lor of destruction expansion pack. I am installing these with wine and i get diablo 2 to install but not run and can not install Diablo 2 LOD, So if anyone could help it would be much appreciated!


           -thanks

---

### Post by bruce89 on 2006-05-31
Isn't that a windows game?  It might work in some kind of WINE.

---

### Post by novik420 on 2006-05-31
Yes i have tried WINE and with the wine i am using i can install Diablo 2 but no Diablo 2 LOD and i need help with that~

---

### Post by mostwanted on 2006-05-31
There's a gaming forum which is more suited for your needs. Also, check the wine application database (find it via the mighty google), it might have some instructions.

---

### Post by novik420 on 2006-05-31
[QUOTE=mostwanted]There's a gaming forum which is more suited for your needs. Also, check the wine application database (find it via the mighty google), it might have some instructions.[/QUOTE]


I appreciated your help but that doesnt help me at alll so very sorry. (not to be rude) but i understand that all but my comp loads up files differently from what i understand or that i need a new version of wine

---

### Post by Kilz on 2006-05-31
[QUOTE=novik420]I just got ubuntu up today and i have wine etc... I am trying to installl Diablo 2 and Diablo 2 LOD I installed Diablo 2 with no trouble but i can not start it. And with Diablo 2 LOD when i go to install it tells me to insert LOD disc (which is already in drive) If anyone can help me at all i would love it~ By the way i am new[/QUOTE]

Well a fellow D2 LOD addict I see. My whole family is addicted to the game. I have never been able to play it under wine.[ But Cedega works flawlessly]("http://www.transgaming.com/"). The program costs money tho. $15 dollars for a 3 month subscription. During that time you can download the program, any updates, and get help running things. You can let the subscription run out and the program will still run, just make sure to save it someplace in case you have to reinstall in the future. Because once the subscription runs out you cant download the program, or any updates. Updates add newer games but only come out about every 6 months.

---

### Post by novik420 on 2006-05-31
Well i am broke and play d2 (addicted) and need to get it up XD lol il give you items for cedega XD haha Thanks much anyway

---

### Post by Sukarn on 2006-05-31
Did you try Cedega CVS? I've never managed to get it up and running, but WineCVS might help. That project automates the download and installation of a variety of wine projects. cedega is saved as cvscedega, wine as cvswine.

By the way, different parts of the forum are not different forums. You were posting the same thing in two threads on one forum, not two...

---

### Post by markr on 2006-05-31
I have Diablo II (Not LOD) up and running fine on both ubuntu and kubuntu (Dapper).

I hit a few problems initially, see below for suggestions:

1. You need to ensure that the xorg.conf file for your default screen depth allows a resolution of 800x600 and 640x480 (depending on the resolution you wish to play at) - not having this set will result in a window to play diablo in which caused real problems if you move the mouse out of the window.

2. Download the 'NoCD' crack from megagames.com, and replace your current Game.exe with teh one from the download (save the original first!), this should sort out the 'Insert Play CD' issue.

3. Configure Wine (issue winecfg from command line).  In the Applications tab I added the Game.exe application and set the windows version to 98.

4. When you run the video test, make sure you select the 2D option, running 3D caused no end of grief for me.

5. Make sure you have the latest Diablo patch (1.11b?) and install that using wine as well (Do this before applying the NoCD patch).

Enjoy DII, it may be old but it's still one of the best games around!!!!

Let me know how you get on.

Mark.

---

### Post by Kilz on 2006-05-31
> Well i am broke and play d2 (addicted) and need to get it up XD lol il give you items for cedega XD haha Thanks much anyway Sorry but the program is copyrighted, I cant distribute it. If you cant afford it there is a 100% free solution to running Windoz games. Its called installing Windowz as a duel boot setup with Ubuntu. That way you can boot into windoz until you can afford the whopping $15.

> Did you try Cedega CVS? I've never managed to get it up and running, but WineCVS might help. That project automates the download and installation of a variety of wine projects. cedega is saved as cvscedega, wine as cvswine.

By the way, different parts of the forum are not different forums. You were posting the same thing in two threads on one forum, not two... Cedega CVS is free , but it isn't the complete Cedega program. There are parts of Cedega that allow games that check if the CD is in the drive that isn't included because it is 3rd party software.

[QUOTE=markr]I have Diablo II (Not LOD) up and running fine on both ubuntu and kubuntu (Dapper).

I hit a few problems initially, see below for suggestions:

1. You need to ensure that the xorg.conf file for your default screen depth allows a resolution of 800x600 and 640x480 (depending on the resolution you wish to play at) - not having this set will result in a window to play diablo in which caused real problems if you move the mouse out of the window.

2. Download the 'NoCD' crack from megagames.com, and replace your current Game.exe with teh one from the download (save the original first!), this should sort out the 'Insert Play CD' issue.

3. Configure Wine (issue winecfg from command line).  In the Applications tab I added the Game.exe application and set the windows version to 98.

4. When you run the video test, make sure you select the 2D option, running 3D caused no end of grief for me.

5. Make sure you have the latest Diablo patch (1.11b?) and install that using wine as well (Do this before applying the NoCD patch).

Enjoy DII, it may be old but it's still one of the best games around!!!!

Let me know how you get on.

Mark.[/QUOTE]

No CD crack is a 3rd party hack in violation of the Blizzard Terms of Use. This wouldn't be a big thing , but Blizzard games have a thing called Warden that checks for hacks while you run it online. You risk having your game banned form online play, forever, if you use one.

---

### Post by Sukarn on 2006-06-05
Did you check the link - [http://www.ubuntuforums.org/showthread.php?t=45231&highlight=howto+diablo+ii+LOD](http://www.ubuntuforums.org/showthread.php?t=45231&highlight=howto+diablo+ii+LOD)
A quick search lead me to that thread.
Or maybe this thread - [http://www.ubuntuforums.org/showthread.php?t=67147&highlight=howto+diablo+ii+LOD](http://www.ubuntuforums.org/showthread.php?t=67147&highlight=howto+diablo+ii+LOD)

---

### Post by flapane on 2006-06-07
i have problems
[[IMG]http://img237.imageshack.us/img237/2750/sk155ag.th.jpg[/IMG]](http://img237.imageshack.us/img237/2750/sk155ag.jpg)

---

### Post by ghost_00 on 2007-04-11
You can download Cedega.
Try: [http://thepiratebay.org/search/cedega/0/0/0]("http://thepiratebay.org/search/cedega/0/0/0")
have fun...:)

---

