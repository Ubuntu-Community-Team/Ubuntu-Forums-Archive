---
title: "battle.net"
date: 2006-07-15
forum: Gaming &amp; Leisure
---

### Post by Cure777 on 2006-07-15
Okay, sorry if this has been posted many times before, but I am new to Ubuntu Linux and to these forums so... I can run Starcraft in Wine fine, but how do I get battle.net to work? When I try to connect, it just minimizes/crashes starcraft.

---

### Post by Sandlst on 2006-07-15
EDIT: Post changed to make installing wine a lot less complicated..........thanks for pointing it out krazyd.

I used to play starcraft under wine. When I did the battle.net graphics were horribly screwed up; the background was simply not there, and the text would overlap-you would see the chat lobby names, then you could click join game, at which point your game list would have all the chat lobby stuff overlapping it, making things very difficult.  I seem to remember having to get into the join games area by hotkey at first, only afterward would my mouse work (its ctrl or shift j I believe), but anyway back to your problem: have you installed the latest version of wine? if not, go [here]("http://www.winehq.org/site/download-deb") and follow the instructions on how to add the wine repo to synaptic, then install from synaptic.  Another thing to check would be....do you have the latest patch installed?  If not, download it from  a third party site, then run the .exe file with wine.  After checking these two things, the terminal can be forced to stay open after an app exits, displaying valuable errors, by opening a terminal, clicking edit, current profile, going to the Title and Command tab, then at the bottom set the field 'When command exits:' to Hold the terminal open.  After you do this, the command```
wine '~/.wine/drive_c/Program Files/Starcraft/Game.exe'
```should run the game.  You might need to replace the ending 'Game.exe' with something else, my memory is rusted, just use whatever .exe launches the game.  Be sure to include the quotes as well. After the game crashes you should get some sort of error as the last few lines, copy and paste it in here and we shall see what we can do from there.  Post back if you have any problems.

---

### Post by krazyd on 2006-07-15
why from source if this version of wine is pre-built already on wine-hq?

---

### Post by vem0m on 2006-07-16
yes u can add thier repos to ur list do a sudo apt-get update and then update it i dunno if Bnet works with even the newest wine but i know it does in 5.2 Cedega

---

### Post by Polygon on 2006-07-16
battle.net works, but the menus are kinda screwed up

you basically get only text, and the text stacks up on top of eachother and doesnt dissapear correctly so its really hard to navigate through the menus and stuff

but if you do get in a game, it is reported to work just like normal. this is a reported wine bug and hopefully it will be fixed.

---

### Post by vem0m on 2006-07-16
yea last time i tried to use wine for it i couldn't see anything E.G no menus or anything showed but that was wine 0.9.9, old. so yea i dunno tho might be better i used cedega but it was slow running it so i played Single player thu wine. Now the fact remains tho multi player starcraft thu bnet sucks these days with all the noobs wanting to play on the fastest setting, no old school hard core ppl play anymore such as myself. i was a backstabber hunter AHHHHH the good ole days

---

### Post by Cure777 on 2006-07-17
Does CVSCedega have support with battle.net? I still cant get it to work with Wine...](*,) ](*,)

---

### Post by vem0m on 2006-07-17
not sure i use Cedega PAid version 5.2.1

---

