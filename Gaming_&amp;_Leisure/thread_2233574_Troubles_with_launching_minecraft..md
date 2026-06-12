---
title: "Troubles with launching minecraft."
date: 2014-07-09
forum: Gaming &amp; Leisure
---

### Post by Overoker on 2014-07-09
Hello everyone.
I'm new in Linux OS (just a second day on Ubuntu 14.04 LTS), and I've a problem. I've been tried to run minecraft through java, but terminal said:

java.awt.IllegalComponentStateException: The frame is decorated
    at java.awt.Frame.setBackground(Frame.java:986)
    at java.awt.Window$1.setOpaque(Window.java:4045)
    at com.sun.awt.AWTUtilities.setWindowOpaque(AWTUtilities.java:360)
    at net.launcher.components.Frame.<init>(Frame.java:92)
    at net.launcher.components.Frame.start(Frame.java:306)
    at net.launcher.run.Mainclass.main(Mainclass.java:9)
Exception in thread "main" java.lang.NullPointerException
    at net.launcher.utils.BaseUtils.throwException(BaseUtils.java:303)
    at net.launcher.components.Frame.start(Frame.java:318)
    at net.launcher.run.Mainclass.main(Mainclass.java:9)


I just put minecraft.jar to the terminal window (it should be enough according to a video on YouTube).

If somebody knows what can I do to fix it, please help me =)

---

### Post by mastablasta on 2014-07-09
[FONT=Arial]how about:

```
java -jar  '/home/*user*/.minecraft/minecraft launcher/MinecraftLauncher.jar'
```

replace user with your username[/FONT]

---

### Post by Overoker on 2014-07-09
Error: Unable to access jarfile /home/overoker/.minecraft/minecraft launcher/MinecraftLauncher.jar

 That's an answer for your variant from terminal.

---

### Post by mastablasta on 2014-07-09
ehm well try

> java -jar and then click drag and drop the launcher file into terminal. i hope you took the whole path into acocunt.

are you using latest verison of minecraft? i am asking because previous versions needed some extra libraries.

---

### Post by Overoker on 2014-07-09
I don't know the version of Minecraft:
I tried to drag and drop the launcher file into terminal. it answered:
java.awt.IllegalComponentStateException: The frame is decorated
    at java.awt.Frame.setBackground(Frame.java:986)
    at java.awt.Window$1.setOpaque(Window.java:4021)
    at com.sun.awt.AWTUtilities.setWindowOpaque(AWTUtilities.java:360)
    at net.launcher.components.Frame.<init>(Frame.java:92)
    at net.launcher.components.Frame.start(Frame.java:306)
    at net.launcher.run.Mainclass.main(Mainclass.java:9)
Exception in thread "main" java.lang.NullPointerException
    at net.launcher.utils.BaseUtils.throwException(BaseUtils.java:303)
    at net.launcher.components.Frame.start(Frame.java:318)
    at net.launcher.run.Mainclass.main(Mainclass.java:9)

P.S.: I'm not using license minecraft (it's another pirate server =) )

---

### Post by mastablasta on 2014-07-10
> **Overoker said:**
> 
P.S.: I'm not using license minecraft (it's another pirat server =) )

this will get the thread closed.


also:

> In most case, it means that you are either executing the wrong minecraft.jar file (It should be the minecraft launcher which is less than 100kb in size and is named minecraft.jar and not the minecraft executable which is 5MB, is inside the .minecraft/bin folder and also happens to have the same minecraft.jar name) or you have not updated the libraries as I mentioned above with the newer LWJGL. Verify that you are in fact executing the correct minecraft.jar file and have overwritten and updated the correct library files.

from: [http://askubuntu.com/questions/225432/how-to-correctly-install-and-troubleshoot-minecraft-client](http://askubuntu.com/questions/225432/how-to-correctly-install-and-troubleshoot-minecraft-client)


and minecarft is in ./minecraft in my case. not sure if it matterrs...

use orginal game. it just might work.

---

### Post by Overoker on 2014-07-10
Well, I tried original minecraft today. And it works.
Thx for your answers.
Will still try to run pirate vesion :D (cuz other's could use is (I mean other players from those  server)).

---

### Post by mastablasta on 2014-07-10
clearly something is missing in the pirate version.

---

### Post by Overoker on 2014-07-10
Yes.
The 1st is that pirate's minecraft.jar have the size 1.2 MB (instead of "less than 100 Kb").

---

### Post by mastablasta on 2014-07-11
it means you need a launcher. you can actualyl use the launcher from another version. even Windows launcher will do if you rename it to .jar

---

### Post by Overoker on 2014-07-11
Ok, will try now...
-------------------
em... any launcher on that sever is >1 Mb... Idk what to do...

---

### Post by Overoker on 2014-07-11
Well, I didn't find any file on the server's site <100 kb (even for Windows - all of them are >1 MB)

---

### Post by Peter_Solver on 2014-07-13
It's still better to use the licensed Minecraft game. Ubuntu won't always work with the pirated ones.

---

