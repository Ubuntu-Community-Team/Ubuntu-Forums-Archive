---
title: "Run script at startup in terminal and put it in system tray."
date: 2008-09-02
forum: Desktop Environments
---

### Post by woolysheep on 2008-09-02
Hello I have several questions

I have the following script for example:

```
#!/bin/bash
cd /home/username/bin/SoB
/home/username/bin/SoB/./sob.sh
```

This executes the program sb and runs it in the background without a terminal, now I would like to run this program in the gnome-terminal to see the progress of the calculations it is doing. 

I tried something with gnome terminal -x options etc but it doesn't seem to run. Or the terminal closes immediately. 

**So which commands do I need to execute this script in a terminal automatically and that the terminal stays open?**

Then secondly with sessions I added this script to my start-up procedure (so it is starting when gnome is starting) this is working fine but I would like that when it start (with the terminal) it will immediately minimize to the system tray. I found the program AllTray already and it works perfectly but I would like to automatize it.

**So is it possible to create a script that automatically minimize to tray when started.**

I hope its a bit clear what I want, I am completely new to linux/ubuntu and used this way of starting programs in windows. (Create a bat, execute it at startup, and put it directly in the system tray) So I am hoping it is possible with linux.

Thanks

---

### Post by kosmiciatakuja on 2008-09-02
I can't help much but I'll try at least some.
First of all - if the terminal closes immediately (with the -x option) maybe try adding '&' (ampersand) in the end of the command, e.g. ```
gnome-terminal -x myscript.sh &
```
I don't have gnome-terminal to check if this will work but I think it might help. 
& basically tells the system to fork the command in a separate process and don't kill it when the parent process dies (or something like that;) )

As far as minimizing on startup - that's a tough one for me. I'd try digging around 'devilspie' application, but I'm not sure if it's compatible with compiz. And I'm not sure it can minimize on startup, but check it out.

---

### Post by yjwong on 2008-09-02
To cause the window not to close at startup, add a new line to your shell script:

read -p ""

This will cause bash to wait for an input before continuing.

As for your second query, I am not sure how to do that.

---

### Post by kpkeerthi on 2008-09-02
[http://www.ubuntugeek.com/alltray-dock-any-program-into-the-system-tray.html](http://www.ubuntugeek.com/alltray-dock-any-program-into-the-system-tray.html)

---

### Post by woolysheep on 2008-09-02
First of all thank for helping me, now my scipts runs without closing the terminal.

edit: played a bit more with this and still it didn't seem to work with the session manager (scripts didn't start) so i am using now this:

```
#!/bin/bash
cd /homeuser/bin/SoB/
xterm -e 'bash -c "/home/user/bin/SoB/./sb /home/user/bin/SoB/sclient.conf; read -n1"'
```

changed from gnome-terminal to xterm and it worked. Is this because the gnome-terminal starts later than xterm? (so the gnome-terminal is not available when session manager starts my startup session?)

About AllTray at the moment i am already using the program but do you know how to automate it, so when a specific script/programs starts it automatically minimize this to the system tray (every time).
Putting alltray before xterm doesn't seem to work, it randomly does what it want (to tray or not to tray)

---

### Post by Bobly on 2009-11-06
Old thread, I know, but I just figured I'd add this solution as this might help others who search and fall on this page:



Why not start the script in a screen session? A screen session is basically a terminal window which when closed, will keep running in the background, and can be resumed later.



The command to start it would be:
```
screen -dmS [name] [command or path to script]

Example: screen -dmS NetworkStability ping 192.168.1.1
```


This will start screen in daemon mode (detached) and can be later resumed to see how the process is doing.

To resume the screen session and see how it's doing:

```
screen -r [name]

Example: screen -r NetworkStability
```


To detach (minimise if you wish) a screen session and return to a normal terminal, Ctrl+A followed by D (or just close the terminal window, it'll keep running in the background :P)


To exit/kill a screen session, resume it, stop the script (ctrl+c?) and then just type "exit".

---

