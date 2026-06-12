---
title: "Start Minecraft server.jar with terminal"
date: 2013-06-03
forum: Gaming &amp; Leisure
---

### Post by PureTryOut on 2013-06-03
I'm running a MC server on a Ubuntu server 10.04.
Whenever i'm going to change something on the server I first test it on my laptop, running Ubuntu 13.04.

At the moment when I run the minecraft server I have to start the terminal, navigate to the MC directory using "cd", and then run "java -Xmx2048M -Xms2048M -jar minecraft_server.jar nogui".
I run it this way so it shows the console.

What I want is to run a .sh file, which starts up the terminal, and then shows the console.
When just putting "java -Xmx2048M -Xms2048M -jar minecraft_server.jar nogui" in a .sh file, it starts up the server, but without terminal and I have to close it via system monitor or ingame using "/quit".

Is there anyway to do this?
Thanks in advance!

---

### Post by taowa4 on 2013-06-03
Try removing the nogui

---

### Post by PureTryOut on 2013-06-03
Yes but that starts up the default GUI, which is not what I want. In Windows you can just run a .bat file and it will start up a terminal (mostly used for Bukkit servers which don't have that GUI).

---

### Post by steeldriver on 2013-06-03
You could try starting a terminal in your script file and running your minecraft command inside that with the -e argument, e.g.

```
gnome-terminal -e "java -Xmx2048M -Xms2048M -jar minecraft_server.jar nogui"
```

or more generically (should choose the appropriate terminal emulator for your desktop)

```
x-terminal-emulator -e "java -Xmx2048M -Xms2048M -jar minecraft_server.jar nogui"
```

If you want the terminal to stay open after the command quits, you will probably need to open a regular terminal (Ctrl-Alt-t) and then go to the 'Edit' menu --> 'Profile Preferences' and then in the 'Title and command' tab, set it to 'Hold the terminal open' from the 'When command exits: ' drop-down box

---

### Post by misterbiskits on 2013-06-03
I use screen in a script:

screen -dmS minecraft java -Xmx2048M -Xms2048M -jar mincraft_server.jar nogui

then I manually open another terminal window and connect to the screen which displays the server console:

screen -r minecraft

I'd like it to automatically open the second terminal and connect to the screen but i haven't figured that out yet.

---

### Post by PureTryOut on 2013-06-04
I like that idea. I am familiar with screen because I run an Ubuntu server, so I think i'm going to use this!

Thanks everyone!

---

