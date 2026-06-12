---
title: "probelms installing WoW with wine"
date: 2007-05-13
forum: Gaming &amp; Leisure
---

### Post by h3knix on 2007-05-13
sorry if this has been answered i am extremely new to this.  I am using [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft) as a reference.  I get the installer open, first thing it says is that my cpu cant handle WoW...which it can duo core 2ghz.  Next when i click install i get a message saying..

 Unrecognized key "options". (AttributeParser::Parse)

Agian sorry if this has been answered but i am confused/lost.  :confused:

---

### Post by z0phi3l on 2007-05-13
Don't know how to fix your error, but I might be able to help.

Do you have access to an installed copy of WoW? What I did was copy the whole WoW folder from another PC and placed it on my computer, then created a shortcut to it using the command wine /home/username/WorldofWarcraft/wow.exe

That actually works and saved me from having to try and get it installed the "normal" way.

---

### Post by Kal9001 on 2007-05-13
I have found that the wow.exe is runnable without install or any registry editing in windows or wine. Once the game is "installed" and its set up its data directories. the files and folders can then copied as a whole to any machine and used to run the game. 

WoW makes all the graphics detection and the like when the game is started. 

So if you wanna play it at your mates just image your wow directory and take it around on a DVD with you and run the EXE from the DVD and it should work XD

ofc this can be used to "copy" the game but as you need to login to play and that is how all the authentication is handled I guess blizzard didnt see the point in making mechene specific install peramiters.

---

### Post by h3knix on 2007-05-14
awesome got it to start up :)   BUT lol my mouse is showing my out of game mouse cursor and WoW mouse cursor is 1 problem.  2nd i have found is when i tryed changing my screen resolution it hung up on me right away.

Thanks agian guys:guitar:

---

### Post by AndrewRiedi on 2007-05-14
> **h3knix said:**
> awesome got it to start up :)   BUT lol my mouse is showing my out of game mouse cursor and WoW mouse cursor is 1 problem.  2nd i have found is when i tryed changing my screen resolution it hung up on me right away.

Thanks agian guys:guitar:

The cursor problem I am working on.  Hopefully I will have hardware cursors implemented by 0.9.38.  Basically, once my patch gets in, you will just have to check the hardware cursor box.  (Right now it is grayed out though)  :)

---

### Post by h3knix on 2007-05-14
heh, alright ill be looking for that then  :)  i also got resolution and everything else to work right...fps is abit low and all but i think with a few tweaks it will be gold  :)  thanks agian

---

### Post by AndrewRiedi on 2007-05-14
No problem.  Hope it all works well.

---

