---
title: "Minecraft Done Loading Fix"
date: 2011-12-17
forum: Gaming &amp; Leisure
---

### Post by didinium on 2011-12-17
Edit 2
Just changed the file to a .py, it works better.
-------------------------------------------------------------------------------------------------------------------------------------
Edit 1
I'm actually not sure if the below method works another method would be to save it, put it into your home file then go into terminal type in cd /home/*whatever your username is* then chmod +x /home/*whatever your username is*/mcdl.py then ./mcdl.py
--------------------------------------------------------------------------------------------------------------------------------------------------------------
Hello all. I'm kind of new to python but I decided to make a program that was actually useful! This is a fix to the done loading glitch in minecraft. All you do is save the file right click it, select properties then make it executable then double click it say run in terminal. Feel free to write any problems you have

---

### Post by Horbo on 2013-01-30
All this script does is delete ~/.minecraft/bin

That may have worked when it was posted, but it doesn't work now.

I haven't found a working solution yet, but hoping one of these two links has the answer:
[http://askubuntu.com/questions/181897/minecraft-for-ubuntu-12-04-does-not-pass-done-loading-screen](http://askubuntu.com/questions/181897/minecraft-for-ubuntu-12-04-does-not-pass-done-loading-screen)
[http://askubuntu.com/questions/175383/minecraft-done-loading-error-12-04-ubuntu-how-to-fix-it](http://askubuntu.com/questions/175383/minecraft-done-loading-error-12-04-ubuntu-how-to-fix-it)

---

### Post by Horbo on 2013-01-30
Yep, the first link I posted there had the answer:  Oracle Java 7 does not work with minecraft!!

Install Oracle Java 6 and use it to run minecraft.
See here for how to install Orcle Java 6: [http://www.liberiangeek.net/2012/11/install-oracle-java-jrejdk-6-in-ubuntu-12-10-quantal-quetzal/](http://www.liberiangeek.net/2012/11/install-oracle-java-jrejdk-6-in-ubuntu-12-10-quantal-quetzal/)

---

### Post by Xslymaster on 2013-01-30
If you want to fix the done loading or the black screen after minecraft you can either delete your bin folder and see if that works or go here [http://www.lwjgl.org/]("http://www.lwjgl.org/")

---

### Post by Horbo on 2013-02-02
> **Xslymaster said:**
> If you want to fix the done loading or the black screen after minecraft you can either delete your bin folder and see if that works or go here [http://www.lwjgl.org/](http://www.lwjgl.org/)

I promise you xsly that deleting bin so it is re-downloaded no longer works.  Tried that many, many times.

None of the lwjgl fixes that I found in the minecraft forums worked for me either.

The ONLY thing that worked was using Java 6 instead of Java 7. (Oracle - no idea about Open)

---

