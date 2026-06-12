---
title: "Sound works in Desktop but not GAMES."
date: 2006-04-03
forum: Desktop Environments
---

### Post by LateNighter on 2006-04-03
My sound works while I'm in Desktop, And on the Games you have to set the Sound for in Sound and Multimedia.

 But it doesn't work at all in Games downloaded from Synaptic, Like Tuxkart, Slune etc.

 Does anyone have any ideas on how to fix it.

 I've got a PCI Slot Sound Card installed instead of Using the one that's built into my Mainboard.
 But the one thats built into my MainBoard, I've disabled in Cmos, Could this have anything to do with it?

 Any Ideas and I'll give it/them a Shot....](*,)

---

### Post by blackbeastofaarrgh on 2006-04-03
Before starting a game, close any audio apps you might have open (XMMS, Rythmbox, etc), open a terminal, and type "killall esd" without the quotes. Start your game and everything should be fine.
Well, it works for me.

---

### Post by LateNighter on 2006-04-03
[QUOTE=blackbeastofaarrgh]Before starting a game, close any audio apps you might have open (XMMS, Rythmbox, etc), open a terminal, and type "killall esd" without the quotes. Start your game and everything should be fine.
Well, it works for me.[/QUOTE]

 Thanks Sounds like a Plan.

 I've tried others and they don't work, SOOOOOOOOOOOOO it's worth a Shot.

 Stranger Things have worked for me....

 If this works??? I'll let ya know, and I'll add it to my "Strange Workings Files"8)

---

### Post by LateNighter on 2006-04-04
[QUOTE=blackbeastofaarrgh]Before starting a game, close any audio apps you might have open (XMMS, Rythmbox, etc), open a terminal, and type "killall esd" without the quotes. Start your game and everything should be fine.
Well, it works for me.[/QUOTE]

 Well as I said it was worth a shot....](*,) 

 But it didn't Work.:-# 

 Anyone Else have any Ideas I'm desperate here....

 Thanks Again for any and all Suggestions and Advice....:confused:

---

### Post by T*&amp;1p87)v# on 2006-04-04
Hi there,

I also have this kind of problem with some games,
I serached for this in some forums and here is what works for me

quake4-demo +set s_driver oss

to start the quake4-demo, but of course before that I have to turn off any music or video players, I have also disabled all kde-sound-notifications because they bug me :)

I think the command I used above can be also set with paramters "esd" and "alsa",
so give it a try and let me know if that worked for you.

---

### Post by LateNighter on 2006-04-04
[QUOTE=ayarov]Hi there,

I also have this kind of problem with some games,
I serached for this in some forums and here is what works for me

quake4-demo +set s_driver oss

to start the quake4-demo, but of course before that I have to turn off any music or video players, I have also disabled all kde-sound-notifications because they bug me :)

I think the command I used above can be also set with paramters "esd" and "alsa",
so give it a try and let me know if that worked for you.[/QUOTE]

 In a Simple Word.... NOPE!!!!:twisted: ](*,)

---

### Post by T*&amp;1p87)v# on 2006-04-05
Hmm,

normally when I start some game from the console I have a lot of dump information that can help in fixing problems. Do you think you can post some of it if you have it? May be we can see  what is missing.

---

### Post by LateNighter on 2006-04-05
[QUOTE=ayarov]Hmm,

normally when I start some game from the console I have a lot of dump information that can help in fixing problems. Do you think you can post some of it if you have it? May be we can see  what is missing.[/QUOTE]

 If this HELPS any.
 
 if I Goto Open my Game in the Console or Terminal.

 for Example: planetpenguin-racer +set s_driver alsa
 or oss or esd.

 All it comes up with is planetpenguin-racer "Command Not Found":mad: 

 I tried all the sound drivers oss alsa and esd No Soap.  Samething???

 But if I click on the Stupid Icon it will run but No Sound???

 The same goes for many others like tuxkart and the like.

 I won't Give Up though...](*,)

---

