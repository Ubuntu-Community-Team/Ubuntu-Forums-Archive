---
title: "ZSNES problem with save file - Ubuntu 64 bit"
date: 2010-01-26
forum: Gaming &amp; Leisure
---

### Post by Danielrj on 2010-01-26
Hello everyone and welcome to my first problematic post at this really great forum, which has helped me plenty of times! :p I have searched a lot, but couldn't find anything so, here goes! 

I have ZSNES installed on my laptop with ubuntu 9.10 64 bit, with much help from this thread [http://ubuntuforums.org/showthread.php?t=1321226](http://ubuntuforums.org/showthread.php?t=1321226) <- THANKS :D. It all worked great and I've played "The Legend of Zelda - Parallel Worlds" a lot in the in last 2 days. But this morning the ZSNES emulator "restarted" or something, because i got the "first time in use" intruduction yet again, and the video config was returened to default. "Oh", I thought, that's easy to reconfigure, and it was, but it was like I have never played before, because both the saved states and the "hard" safe in the game was gone - exactly like it was the first time I loaded the game rom. At the location /home/####/.zsnes I can still see, I think, is the save files. But I can't seem to make ZSNES load them in anyway. :confused:

Oh, and ZSNES crashes every time I try to quit it, and I can't even "kill" it either, so i have to restart my session if I want to get rid of it, but it has been like this the whole time,.. I can live with live with this,.. but I would be happy if anyone had a solution ;)

I hope I've given enough information so we can solve the problem :p.. and thanks in advance :D

(Yes, I know I could just start from the beginning once again, but I think that this would most likely happen again if I did ;))

---

### Post by Grishka on 2010-01-26
might be a corrupted configuration file. copy your savegames (.srm and .zst) somewhere safe, delete the .zsnes directory, then run zsnes and try configuring it normally. if everything works, simply put the savegames back there. hope it helps.

---

### Post by Danielrj on 2010-01-26
> **Grishka said:**
> might be a corrupted configuration file. copy your savegames (.srm and .zst) somewhere safe, delete the .zsnes directory, then run zsnes and try configuring it normally. if everything works, simply put the savegames back there. hope it helps.
It didn't work :(.. it can safe a new game file and every thing works as it should, but it dosn't read my "old" one.. when i try to open my "old" state it tells me that my 20 hours is "state too old".. can it have something to do with the crash every time I try to quit the program? ~~~ I just don't understand why it wont show me the "old" safe.. :S
 
- but thanks for the help anyway! :D

---

### Post by Grishka on 2010-01-26
tough luck. maybe there's something wrong with your version of zsnes. remove it, and try installing [mine](https://launchpad.net/~thir/+archive/ppa/+files/zsnes_1.510-2.2ubuntu2~ppa1_amd64.deb), it has served me, and others, well for some time now. remove the config files, install it, and see if it helps. be sure to run it for the first time with ```
zsnes -ad sdl
``` if your problems persist even with this version, then there's obviously something wrong with your system. if this is the case, maybe try running zsnes from the terminal, and see if it complains about anything.

---

### Post by Danielrj on 2010-01-26
Okay, i'll try that in 20 min. :)

 - how do i run it the first time with "zsnes -ad sdl" ? :P

and how do i run zsnes through the terminal? :)

---

### Post by Grishka on 2010-01-26
> **Danielrj said:**
> Okay, i'll try that in 20 min. :)

 - how do i run it the first time with "zsnes -ad sdl" ? :P

and how do i run zsnes through the terminal? :)

either press alt+F2 and type it there, or enter the command into the terminal. look for it in your applications.

---

### Post by Danielrj on 2010-03-09
I couldn't make it work...  and i didn't fell like starting all over.. buut :D.. thanks for the help anyway !.. you guys were awesome.. :)..

---

### Post by wolkenkaiser on 2011-02-10
All I did was extract my ROMs and **eliminate all spaces and special characters** (except dashes, if those count as special characters) from the ROM name.

Then I deleted the zsnesl.cgf file and reloaded ZSNES to set the configuration of it from within the GUI, without touching the paths.

After I brought everything back to the Land of Hunkydory I loaded a ROM, played it, and it saved both SRAM and states and loaded states just fine.

---

