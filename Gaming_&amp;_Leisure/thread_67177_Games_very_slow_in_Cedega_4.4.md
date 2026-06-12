---
title: "Games very slow in Cedega 4.4"
date: 2005-09-19
forum: Gaming &amp; Leisure
---

### Post by jeffreyvergara.NET on 2005-09-19
hello, you might be asking why I post here instead in transgaming forum, the answer is, I don't like their forum, it's not organize and there's a little support in Ubuntu.

I have a fresh installation of Breezy but I havnt updated it yet, (200++ files to be updated?) then I installed Cedega 4.4 it was successful, then I tried installing both WarCraft3 and Frozen throne, it worked, but it's not playable, is very very slow, i tried to put --opengl after War3.exe (clueless) and still very slow. 
Is there something else I need to install, download or configure?

---

### Post by jeffreyvergara.NET on 2005-09-19
never mind I figured it out. I have another question, how to make a shortcut for exe files to ubuntu desktop? it's really a hassle to always for to a certain folder to open the exe file.

---

### Post by oneybm on 2005-09-19
I'm not on my Ubuntu box at the moment; however, if memory serves you can just right click the desktop and there should be an option to create a new link.  Simply use that to direct it to the file you want and there you go.  \\:D/

---

### Post by e^e on 2005-09-19
what oneybm said, and make sure you put cedega before of the .exe like this

 cedega '/whatever/game.exe'

 that works for me.

---

### Post by rwabel on 2005-09-20
[QUOTE=jeffreyvergara.NET]never mind I figured it out. I have another question, how to make a shortcut for exe files to ubuntu desktop? it's really a hassle to always for to a certain folder to open the exe file.[/QUOTE]
 would be great if you post how you fixed your problem. If another one has the same problem, he will have a fix :-)

---

### Post by jeffreyvergara.NET on 2005-09-20
I just installed my video card driver (Nvidia) and some openGL files, I suggest full system update.

---

### Post by rwabel on 2005-09-20
[QUOTE=jeffreyvergara.NET]I just installed my video card driver (Nvidia) and some openGL files, I suggest full system update.[/QUOTE]
 did you install the driver from the nvidia homepage or the one from the ubuntu repository?

---

### Post by jeffreyvergara.NET on 2005-09-20
I used ubuntu repository, its easier than manually downloading and installing files.. ehehe

---

### Post by Ibuntu_52 on 2005-09-20
>  I have another question, how to make a shortcut for exe files to ubuntu desktop? it's really a hassle to always for to a certain folder to open the exe file.
 

I know of to ways to do this.The first would be with a shell script.
Just create an empty file open it with a text editor and write "wine <program>" then close and rename the file with a .sh on the end.

the other way (the one I use) is make an icon with gdesklets.Just get gdesklets and download a plugin, I use justanicon.

---

### Post by Dolphin on 2005-09-21
[QUOTE=jeffreyvergara.NET]I have another question, how to make a shortcut for exe files to ubuntu desktop? it's really a hassle to always for to a certain folder to open the exe file.[/QUOTE]

You could just use Point2Play.  It's a graphical front end for Cedega.  Makes life alot more simple.

---

