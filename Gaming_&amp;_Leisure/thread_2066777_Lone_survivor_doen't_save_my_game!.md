---
title: "Lone survivor doen't save my game?!"
date: 2012-10-05
forum: Gaming &amp; Leisure
---

### Post by Sarys on 2012-10-05
I was playing lone survivor (Great game BTW) and I went to save and quit game. When I came back to play it after few week there was only one option "New game". The game saves to RAM??? so I need to keep my PC on if I want to keep playing? Gee...
Another problem I'm having is that I can't play it on fullscreen or the controls won't work.
Any ideas how to fix these problems.

Thanks In advance.

EDIT: Sorry for bad English.

---

### Post by Toz on 2012-10-05
How did you install and how do you run the game? 

The game saves whenever you lie down in your bed. On restart, you can use the arrow keys to cycle between "Continue" and "New Game". Are you not getting this option?

---

### Post by Sarys on 2012-10-05
> **Toz said:**
> How did you install and how do you run the game? 

The game saves whenever you lie down in your bed. On restart, you can use the arrow keys to cycle between "Continue" and "New Game". Are you not getting this option?

I installed this game from Ubuntu softwate centre. And I run the game from ubuntu side bar. I only get"Continue" if I don't shut down my computer.

---

### Post by Sarys on 2012-10-08
No ideas how to fix this???

---

### Post by Majlo on 2012-10-08
Hello,

Make sure to not remove flash cookies .I suspect that you removed them from browser ? They are stored in your home folder in hidden directory .macromedia .In my case full path is :

[I]mario@ubuntu:/home$ find -name LoneSurvivor
./mario/.macromedia/Flash_Player/#SharedObjects/969LL7E4/localhost/opt/lonesurvivor/LoneSurvivor
mario@ubuntu:/home$ ll ./mario/.macromedia/Flash_Player/#SharedObjects/969LL7E4/localhost/opt/lonesurvivor/LoneSurvivor
total 52
drwx------ 2 mario mario  4096 Sep 28 23:41 ./
drwx------ 3 mario mario  4096 Sep 25 11:55 ../
-rw-rw-r-- 1 mario mario    63 Sep 28 21:46 flixel.sol
-rw-rw-r-- 1 mario mario 38385 Sep 28 23:41 LoneSurvivorSavedGame.sol
[/I]

---

### Post by Sarys on 2012-10-09
> **Majlo said:**
> Hello,

Make sure to not remove flash cookies .I suspect that you removed them from browser ? They are stored in your home folder in hidden directory .macromedia .In my case full path is :

[I]mario@ubuntu:/home$ find -name LoneSurvivor
./mario/.macromedia/Flash_Player/#SharedObjects/969LL7E4/localhost/opt/lonesurvivor/LoneSurvivor
mario@ubuntu:/home$ ll ./mario/.macromedia/Flash_Player/#SharedObjects/969LL7E4/localhost/opt/lonesurvivor/LoneSurvivor
total 52
drwx------ 2 mario mario  4096 Sep 28 23:41 ./
drwx------ 3 mario mario  4096 Sep 25 11:55 ../
-rw-rw-r-- 1 mario mario    63 Sep 28 21:46 flixel.sol
-rw-rw-r-- 1 mario mario 38385 Sep 28 23:41 LoneSurvivorSavedGame.sol
[/I]

Of course I delete all of my cookies every time the browser is closed.
Do you know anything about the full screen problem?

---

### Post by Majlo on 2012-10-09
I think you can use this workaround .Maximize window and use zoom in .I tried it once but playing in window was better for me .Flash is big mess on linux :(

---

### Post by Sarys on 2012-10-09
> **Majlo said:**
> I think you can use this workaround .Maximize window and use zoom in .I tried it once but playing in window was better for me .Flash is big mess on linux :(

Darn. I hope this gets fixed in the future.

---

