---
title: "Minecraft"
date: 2010-11-02
forum: Gaming &amp; Leisure
---

### Post by Sexraider on 2010-11-02
I surely must not be the only one playing this amazing game!

[http://www.minecraft.net](http://www.minecraft.net)

very awesome sandbox game!

---

### Post by Refalm on 2010-11-02
I have a shortcut on my desktop for it:
```
java -Xmx1024M -Xms768M -cp /home/refalm/Downloads/Minecraft/Minecraft.jar net.minecraft.LauncherFrame
```

Works great this way.

---

### Post by korn101 on 2010-11-02
I have a shortcut to it.

IN MY DOCK :D

---

### Post by ThePhysician on 2010-11-02
I hate you all so much. I crave playing this game but sadly the browser version does nothing on my netbook, and I can't afford the download version. Ah, the life of being a poor poor person. Haha.

Looking forward to hopefully getting and playing this game for christmas. Fingers crossed. =)

---

### Post by zitch on 2010-11-02
I have a shortcut in... err... wait... I don't.  :o

What I do have is a script in the same directory as the .jar file to launch it with the right amount of memory available (similar to Refalm has), but I dare not have a shortcut to it in a quick-to-access area lest I wouldn't be able to resist the temptation to play it at work... ;)

---

### Post by shortrun on 2010-11-02
Could someone please explain how I get minecraft going.
I did the download but I need the simple detailed instructions.
thanks

---

### Post by Russss on 2010-11-02
> **shortrun said:**
> Could someone please explain how I get minecraft going.
I did the download but I need the simple detailed instructions.
thanks

Make Minecraft.jar executable (right click>properties>Permissions or use terminal)

then in the same directory as the download:
```
java -jar Minecraft.jar
```

Also from their site:
If you run into out of memory errors, try launching it with ```
java -Xmx1024M -Xms512M -cp Minecraft.jar net.minecraft.LauncherFrame
```

---

### Post by shortrun on 2010-11-02
Thanks Russs
I will give this a try tomorrow evening and let you know how it goes.

---

### Post by donkyhotay on 2010-11-03
> **Sexraider said:**
> I surely must not be the only one playing this amazing game!

[http://www.minecraft.net](http://www.minecraft.net)

very awesome sandbox game!

You're not, it is a pretty cool game. I'm looking forward to when multiplayer is fixed so I can play with friends.

---

### Post by shortrun on 2010-11-03
Ok

I have tried the above instructions.

Now I get
Could not find the main class: net.minecraft.LauncherFrame. Program will exit.

If I look  in net   minecraft   I do see LauncherFrame.class

Any help please.

---

### Post by Russss on 2010-11-03
> **shortrun said:**
> Ok

I have tried the above instructions.

Now I get
Could not find the main class: net.minecraft.LauncherFrame. Program will exit.

If I look  in net   minecraft   I do see LauncherFrame.class

Any help please.

I'm not sure. I downloaded the [[COLOR="Blue"]Minecraft.jar[/COLOR]]("http://www.minecraft.net/download/Minecraft.jar?v=1288838807271") file then placed it in a games folder I made in my home folder. To run it I use the command:
```
java -jar /home/rusty/games/Minecraft.jar 
```

replace 'rusty' with your user name. If that doesn't work I don't know how to fix it. Sorry.

Good Luck

---

### Post by rft183 on 2010-11-10
I just made the Minecraft.jar executable.  Then I right click and choose "Run With Sun JRE" or whatever the context menu calls it.

---

### Post by MaximB on 2010-11-10
Shame that minecraft only runs properly with sudo for me, if I don't use sudo, the mice won't work.

A great game indeed, I've already built 3 bases in which 1 is a huge mine, 1 is a middle base and 3rd is a castle on a very tall mounten and a garden.

But this game has no real purpose, you make the objective and you can't win this ;)

---

### Post by StaticIp on 2010-11-10
Love that game! Been playing for a while.

---

### Post by Whiteice on 2010-11-10
I love minecraft! I'm so addicted to it one of my daily website checks is world of notch. I am anxiously waiting for multiplayer to be debugged. I currently have a server running but nobody i know plays it which makes me :( sad. If anyone wants to come over it's stizzle.homelinux.net  currently tonight its down trying to fix it. thats why im on the forms haha.

---

### Post by drklunk on 2010-11-13
Been playing this for a while now, running into problems since Ive switched to 10.10 but single player works fine. If youre looking for a good multiplayer server check out 209.23.116.25, Ive been playing on it since Ive started really. Good community there.

---

### Post by StaticIp on 2010-11-13
Starting my own minecraft server, staticip-online.com
Anyone interested in helping me build a city?

---

### Post by lone_wolfII on 2010-11-13
I'm really happy about the latest update. 

Minecarts and liquids finally work properly in multiplayer! 

Now for me to make some epic rail networks :D

---

### Post by pumaft945 on 2010-12-14
I have tried using the sudo java -jar /home/matt/Games/Minecraft.jar command, and Minecraft opens, and being to run however once it finished installing the updates, it went to a black screen. In the terminal the following error occured:


Exception in thread "Minecraft main thread" java.lang.ExceptionInInitializerError
    at net.minecraft.client.Minecraft.a(SourceFile:149)
    at net.minecraft.client.Minecraft.run(SourceFile:559)
    at java.lang.Thread.run(Thread.java:662)
Caused by: java.lang.ArrayIndexOutOfBoundsException: 0
    at org.lwjgl.opengl.XRandR$Screen.<init>(XRandR.java:234)
    at org.lwjgl.opengl.XRandR$Screen.<init>(XRandR.java:196)
    at org.lwjgl.opengl.XRandR.populate(XRandR.java:87)
    at org.lwjgl.opengl.XRandR.access$100(XRandR.java:52)
    at org.lwjgl.opengl.XRandR$1.run(XRandR.java:110)
    at java.security.AccessController.doPrivileged(Native Method)
    at org.lwjgl.opengl.XRandR.getConfiguration(XRandR.java:108)
    at org.lwjgl.opengl.LinuxDisplay.init(LinuxDisplay.java:618)
    at org.lwjgl.opengl.Display.<clinit>(Display.java:135)
    ... 3 more

Any help?

---

### Post by austaph on 2010-12-14
> Make Minecraft.jar executable (right click>properties>Permissions or use terminal)

Russss, I love you!  I've been trying all sorts of suggestions to get Minecraft to work all day, all I had to do was a chmod.

Thanks so much!

---

