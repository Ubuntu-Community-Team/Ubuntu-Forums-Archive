---
title: "Minecraft Problems"
date: 2014-12-01
forum: Gaming &amp; Leisure
---

### Post by kris26 on 2014-12-01
hello all, new user here, with a bit of a problem. i recently used this writeup:
[http://doctor-not-magician.blogspot.com/2014/01/minecraft-on-acer-c720-chromebook.html#comment-form](http://doctor-not-magician.blogspot.com/2014/01/minecraft-on-acer-c720-chromebook.html#comment-form)
to install Minecraft on my Acer C720 Chromebook. i have all the steps done correctly(to my knowledge) but when i clikc on the game to play it, nothing happens. it shows it loading and says "OpenJDK Java 6 Runtime" on the toolbar, and then after a bit, it disapears. no game, no warning, nothing. has anybody done this? if so, where did i go wrong? and what can i do to fix this? thank you.

---

### Post by mastablasta on 2014-12-03
what OS version are you running?
I believe current java is version 7.

how are you running the minecraft? what is you command line when you run it? what does it say if you run it from terminal Window?

---

### Post by Dragonbite on 2014-12-03
Try using a terminal and type ```
java -jar Minecraft.jar
``` and see if you get more feedback from that.

I run it using the OpenJDK which when I installed ver. 8 (latest) I also got ver. 7.  I used to go through the whole Oracle Java but once I found out the other program I was using it for would not work fully for Linux anyway, I tried OpenJDK and it works fine for me (possibly even slightly better).  Since then, I have more-or-less dropped using Oracle Java for OpenJDK.

I recently created a .desktop file for Minecraft on my Ubuntu 14.10 (Unity), which runs great at starting it up and I was able to lock that to the activity/task/shortcut bar.

---

### Post by kris26 on 2014-12-04
> **mastablasta said:**
> what OS version are you running?
I believe current java is version 7.

how are you running the minecraft? what is you command line when you run it? what does it say if you run it from terminal Window?
I'm sorry. i am completely new to running this sort of thing. how would i find out OS i am running, i followed the writeup in the link i posted to install and run minecraft, i dont know how to see the command line when i run it, and i don't know how to run it from a terminal window. lol sorry for being a newb

---

### Post by mastablasta on 2014-12-04
Dragonbite provided instructions on how to run it from terminal.

if there are any errors copy and post them here.

as for where to find the info on os - depends
 what desktop you are using. but terminal command (all desktops have same terminal commands) for that would be for example

```
uname -a
```

again you can copy it and paste results here.

as for desktop the one on the write up is Kubuntu. is that what you are having? [http://www.kubuntu.org/](http://www.kubuntu.org/) it's Ubuntu with KDE desktop.

---

