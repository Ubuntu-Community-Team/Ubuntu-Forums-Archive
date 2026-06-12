---
title: "Terminal script"
date: 2014-11-27
forum: Desktop Environments
---

### Post by dennis40 on 2014-11-27
Hi everyone,

Since my old pc which i used as a Minecraft server with Windows 7 crashed i recovered my world data and installed ubuntu 10.04 with desktop to get started with ubuntu.
So now i got my Minecraft server running with this .sh file which I execute with the startup programs.
> [INDENT]cd Bureaublad/[/INDENT]
[INDENT]cd Server\ 1.7.10/[/INDENT]
[INDENT]#!/bin/sh[/INDENT]
[INDENT]java -Xms5G -Xmx6G -XX:PermSize=256m -XX:MaxPermSize=512m -jar ./FTBServer.jar nogui[/INDENT]

Now the server starts as normal and I can join and play, but on the ubuntu desktop the Terminal is missing, so i can't execute commands like save-all, stop, kick, ban...
But when i run the script I get a terminal window in which I can use the commands. But i want to press the button to power my pc and make it auto boot the server with the Terminal so if necessary i can use the commands
Who can help me with this? Cause I have 0 experience with Ubuntu

Regards Dennis

---

### Post by Impavidus on 2014-11-27
Goeienavond,

Any particular reason for using 10.04? Desktop version is unsupported, server version still is (just). This means the upgrades to the server version are not checked against the desktop packages, which may lead to all kinds of problems. Either use a pure server (no desktop; 10.04 is still supported until April) or install a supported desktop release. I suggest 14.04. If your hardware has trouble running that, don't run a heavy desktop environment.

---

### Post by dennis40 on 2014-11-27
I have an i5 with 16gb, it 'll run but i wanna use a desktop just so i can use it as Pc when needed for work.
But any idea how i can get the Terminal window to show up? It is running in the background.
But i ll take a look into updating to 14.04

---

### Post by dennis40 on 2014-11-27
I am stupid XD, i am running 14.04 on the desktop

---

### Post by etescartz on 2014-11-28
It seems to me that you are looking for a way to autorun the minecraft server at system boot? I have never installed/used/played Minecraft but if you want to run any software being a graphical interface ( GUI ) or a command line (CLI ) in Ubuntu desktop , you should look through the application menu for a "startup/ startup applications" keyword , and add/edit a new entry there. 
  Also , for the part about issuing  further commands to the Minecraft server after startup , you should lookup the official documentation for that.

---

### Post by dennis40 on 2014-11-28
But i know how to issue the other commands but i don't have the server terminal. But when i manually start it i do have the terminal. When using the startup applications it doesn't show that terminal, but in the background it is running.

---

### Post by mcduck on 2014-11-28
You don't actually have a terminal window running in the background, just a shell & the script you made.

Easy fix, anyway, instead of adding the script itself to your startup applications, add a command to launch a terminal, and then the script as a parameter in the command.

For example, instead of this: 
```
sh  /path/to/startminecraftserver.sh
```
...you'd use something like this:
```
gnome-terminal -e /path/to/startminecraftserver.sh
```

---

### Post by dennis40 on 2014-11-29
> **mcduck said:**
> You don't actually have a terminal window running in the background, just a shell & the script you made.

Easy fix, anyway, instead of adding the script itself to your startup applications, add a command to launch a terminal, and then the script as a parameter in the command.

For example, instead of this: 
```
sh  /path/to/startminecraftserver.sh
```
...you'd use something like this:
```
gnome-terminal -e /path/to/startminecraftserver.sh
```

Thanks! It now shows the terminal window i was looking for :D
I used these .sh scripts

```
gnome-terminal -e /home/dennis/Bureaublad/ServerStart.sh
```
And
```
cd Bureaublad/
cd Server\ 1.7.10/
#!/bin/sh
java -Xms5G -Xmx6G -XX:PermSize=256m -XX:MaxPermSize=512m -jar ./FTBServer.jar nogui
```

---

