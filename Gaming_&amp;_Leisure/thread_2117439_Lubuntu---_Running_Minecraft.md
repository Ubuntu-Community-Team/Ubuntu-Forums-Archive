---
title: "Lubuntu--- Running Minecraft"
date: 2013-02-18
forum: Gaming &amp; Leisure
---

### Post by Sarger001 on 2013-02-18
I'm posting from Lubuntu right now, so yes, i do have it open.

I recently DL'd MC And am trying to run (duh.)
It can run on windows but after hearing how much better it runs on Linux, i decided to give it a try on Lubuntu. I followed through with the instructions and it is now on my desktop. A usr folder to be exact. Inside is bin and share, in which a file named minecraft is in bin.In share is 3 folders, applications, minecraft, and pixmaps. Applications has a file named minecraft that just doesn't work (I'ts a desktop configuration file). Minecraft has a jar that i don't know how to run (though it's probably what i need to run in the first place). In pixmaps is just the minecraft logo. Yay. Ok, so i opened the file in bin. No success. Tried opening the jar with no success (opens it as a archive). After no success with anything i decided to make my first executable file and put it on desktop.

exec java -Xmx1024M -Xms512M /home/sarger001/desktop/usr/share/minecraft/MinecraftSP.jar net.minecraft.LauncherFrame


When double clicked, it takes me to the text editor. I Want to know what i'm doing wrong.

Don't ask about graphics cards. I can run this stuff in windows, and yes, everything's updated.

YES I GOT THE LINUX VERSION.

---

### Post by efflandt on 2013-02-18
Where is MinecraftSP.jar from? You should only download it from [http://www.minecraft.net/]("http://www.minecraft.net") and it should consist of only a **minecraft.jar** which is a launcher file (OS should not matter, it is java). It should work fine with openjdk-6-jre (or 7).

But I don't quite understand where you are putting that command. If you are trying to write a shell script the first line should be **#!/bin/sh** (or #!/bin/bash) and you would not need the "exec".  You would also need to give it execute permission (chmod +x scriptname). Then when you double click it, it should ask if you want to run it or open it in a text editor.

cd to the directory it is in and from a terminal run (or whatever preferences for memory use):
```
java -Xmx1024M -Xms512M -cp minecraft.jar net.minecraft.LauncherFrame
```That should create the ~/.minecraft directory where it keeps all its files.  But you still always launch it from the minecraft.jar launcher, NOT the one in ~/.minecraft/bin/

If you want to run it from a desktop launcher (like ~/Desktop/minecraft.desktop), it still needs to launch from a terminal. This is an example o what I use (minecraft.png is favicon.png that I extracted from /net/minecraft in the minecraft.jar launcher):
```
[Desktop Entry]
Version=1.0
Type=Application
Terminal=true
Icon=/home/efflandt/Pictures/Icons/minecraft.png
Name=Minecraft-direct
Exec=sh -c 'java -Xmx2G -Xms1G -cp ~/MC-client/minecraft.jar net.minecraft.LauncherFrame'
```

---

