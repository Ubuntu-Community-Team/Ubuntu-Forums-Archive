---
title: "Some questions about Minecraft on Ubuntu 10.10."
date: 2011-02-28
forum: Gaming &amp; Leisure
---

### Post by MattDrumz on 2011-02-28
Hey guys, I'm new to the forum, and new to Ubuntu, so sorry if I've posted this in the wrong section, or if I don't understand some things correctly. I am pretty experienced with some Android stuff, so I do have some knowledge of Linux.

First of all, I just installed Ubuntu on my computer about a week ago, and I'm loving it. It is definitely way better than Vista.

Alright, so here's my questions. I've posted these on the official Minecraft forums, but nobody replied, which is what I guessed would happen.

1) Whenever I click the right or left mouse button to do something in the game, my actual mouse pointer appears on the screen for a split second. I think this may be causing a little bit of lag on the game. Is there any way to fix this? I've searched, but I couldn't find anything.

2) Are there any general tweaks/hacks that make games such as Minecraft run faster? I'm already using this command in terminal to start the game:
```
java -Xmx1024M -Xms512M -cp minecraft.jar net.minecraft.LauncherFrame
```

3) Sometimes when I'm moving my character around with the WASD keys, my character will keep moving forward without me pressing any keys. I have to turn my character around and mess with the keys to get it working right again. Any ideas?

I'm pretty sure these issues (except #2, since it ran worse on Vista) all have something to do with Ubuntu, since I don't experience these problems on Vista.

Thanks in advance!

---

### Post by klak1212 on 2011-03-02
Taken from a recent post on the Minecraft forums, and im guessing you are the topic OP there too :D, but this is for anyone else that has these issues with Minecraft... Turns out that both Questions 1 and 3 can be fixed by updating the lwjgl files in the .minecraft/bin folder.

> 1) Doesn't bother me enough to investigate!

3) Can be resolved by updating the lwjgl libraries:
_[http://sourceforge.net/projects/java-game-lib/files/Official%20Releases/LWJGL%202.7.1/lwjgl-2.7.1.zip/download]("http://sourceforge.net/projects/java-game-lib/files/Official%20Releases/LWJGL%202.7.1/lwjgl-2.7.1.zip/download")_
Overwrite  the Mojang supplied files in .minecraft/bin with those in  lwjgl-2.7.1/jar & .minecraft/bin/natives with those in  lwjgl-2.7.1/native/linux.
Worked prior to 1.3, not actually tested since.

---

### Post by tastygrue on 2011-03-02
For your second question, I found this thread:
[http://www.minecraftforum.net/viewtopic.php?f=25&t=132717](http://www.minecraftforum.net/viewtopic.php?f=25&t=132717)
It links to a FPS booster mod called Optimine, but I haven't tried it out yet.

---

### Post by Southernlights on 2011-10-16
Awesome thanks for this :)

---

### Post by Cabria on 2011-10-29
Where can one find the .minecraft/bin files? I can't seem to find them...

---

### Post by sirvinniei on 2011-10-29
> **Cabria said:**
> Where can one find the .minecraft/bin files? I can't seem to find them...
go  to your personalk  folder and press control+H then some folders should appear.
click .minecraft folder and there is the bin

---

### Post by Cabria on 2011-10-30
They don't appear. I'm running straight the downloaded .jar like MattDrumz. Or at least that's what I assume he's doing.

---

### Post by Manhi40 on 2012-01-16
for .minecraft folder, ctrl+h in home folder

---

