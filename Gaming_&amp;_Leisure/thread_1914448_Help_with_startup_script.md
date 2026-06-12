---
title: "Help with startup script"
date: 2012-01-24
forum: Gaming &amp; Leisure
---

### Post by Pazau on 2012-01-24
Hello all.
I have started making a startup script to my Minecraft server, running Ubuntu Server 10.04 LTS.

My idea is that the script in my account (username nicolas), should start screen, do a change directory, and run the minecraft file with the Java command. My problem is that I can not get the script to work.


"#!/bin/bash
sudo -u nicolas screen -dmS minecraft java -Xms1024M -Xmx1024M -jar /home/nicolas/STUMCS/minecraft_server.jar nogui"

- I have put the script in etc/init.d and run update-rc.d command.


What have I done wrong?

- Nicolas.

---

### Post by btindie on 2012-01-24
For a start that script isn't formatted or written correctly for an init script, have you taken a look at the files in /etc/init.d ?

---

### Post by ubudog on 2012-01-24
*Thread moved to Gaming & Leisure*

Since it seems you have it in the right place, restart your system and run:
```
screen -r
```

Does it show your server console?
(note: to detach, press CTL+A+D)

---

### Post by Pazau on 2012-01-24
btindie:
Yes I have, but they cut the all-out, which I do not need. All I want the system to do, is to start the minecraft file as I do - but without that I have to do it every time. It should not require so insane a script.

ubudog: Tried several times, but Screen says that there is no session to continue. My Minecraft client can not find the server (fearing that the minecraft file is started as root).

---

### Post by ubudog on 2012-01-24
When I run:
```
sudo -u ubudog ls
```
as root, I get permission denied.  Could you try running a similar command and see what happens?

---

### Post by Pazau on 2012-01-24
Found out why the script failed to start. Had forgotten chmod+x on it...

The script now starts the minecraft file in a detached Screen session, but the minecraft file just freeze in the progress.

Here is the output after a clean reboot of the server:

[http://ragelse.com/i/8EbsvPe](http://ragelse.com/i/8EbsvPe)

(Can't for some reason copy the content from my SSH session)

---

