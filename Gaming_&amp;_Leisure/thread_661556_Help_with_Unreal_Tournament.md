---
title: "Help with Unreal Tournament"
date: 2008-01-08
forum: Gaming &amp; Leisure
---

### Post by Blueranger on 2008-01-08
Hi all, first post here.

I need some help with installing Unreal Tournament. I am very new to Linux and am now on my second version of Ubuntu 7.10. 
I have original version of UT V4.00 I think. Managed to install UT with the Loki installer but UT won't run, think it was to do with ownership, so i think I have set up the folder /UT for me to access it with the chmod -R command, but it still will not run.
So I thought maybe i need to update the game to 4.36, so downloaded 2 patches, utpatch436.run and ut-patch-436.run. Tried the sh utpatch436.run command in the terminal and comes up with an error "warning "+number" is deprecated please use "-n number" and some other stuff. Tried both patches and same thing happened. Kept coming up bash after running sh command, so because i am a total noob on the workings of linux i tried bash utpatch436.run and i thought it was gonna install ok then it came up with Error no delta for /home/alan/ut/system/Editor.u  the program returned an error code (3). 

I know this is an old game but I just want to get it to work on my laptop. I am very PC savvy but all on microsoft software from Dos onwards, and have good knowledge of computer hardware. I am willing to put the work i to learn linux as i believe it is a far superior operating sytem that windows. If you can help it wold be much appreciated, and if you have any good sites where i can learn more about using linux in the terminal and about file types and the file structure of linux that would be great too.Hope this isn't too long a speel for my first post.:)

---

### Post by Blueranger on 2008-01-13
I kinda sussed out the errors were to do with the package i was trying to install, i think.
Anyway what i done was installed UT through wine and it worked just fine, installed the 4.36 update and it's running perfect in OpenGL mode.
See I thought wine was just for programs, not games. But checking out these forums discovered that you can install some games in wine....cool.
I had tried to install it with cedega as i thought this was the games version of wine but didn't work.
Anyway if anyone else ever has this problem I hope this may help.

---

