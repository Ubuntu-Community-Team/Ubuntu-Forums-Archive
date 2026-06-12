---
title: "Counter-Strike: Source dedicated server woes"
date: 2007-07-12
forum: Gaming &amp; Leisure
---

### Post by Sturm on 2007-07-12
Searching around on the forums for my specific problem has yielded, unfortunately, no results.  Thus, I shall post it, hoping this is the correct section for it:

After following the [srcds.com guide]("http://www.srcds.com/db/engine.php?subaction=showfull&id=1098643920&archive=") and the [J_K9]("http://wolphination.com/linux/2006/03/29/how-to-setup-a-cssource-dedicated-server/") guide, I was able to finally get my Counter-Strike: Source dedicated server up and running just fine on my Ubuntu Feisty box. I’ve connected to it from three different PCs within the network–no problem. I then set my Buffalo WBR-G54 router to forward all the ports are needed for the dedicated server that linux box so that everyone on the internet can access it as well.

Unfortunately, it’s a no go. A friend of mine trying to connect from his house says he gets a “Server is not responding” message when he tries to connect to it. I’ve checked, rechecked, and triple-checked all the ports that are being forwarded in the router. They’re all correctly configured, so why can’t he connect?

(By the way, I also tried to do the same thing from another PC on the LAN. Instead of using the “Lan” tab when finding a server, I used the “Favorites” tab and manually entered my WAN address, just to see if it might work. It didn’t, which helps sustain my friend’s claim that he cannot connect.)

What am I overlooking here?

---

### Post by Brynster on 2007-07-13
you need to add the flag + ip xxx.xxx.xxx.xxx:xxxxx to the launcher comand

the xxx.xxx.xxx.xxx being your external ip find that by pointing your favourite web browser to [www.whatismyipaddress.com](www.whatismyipaddress.com)

you can then set the game port to whatever you require after the ip address :xxxx

so for example mine is currently set to + ip 88.216.197.44:27015

and providing you have your port forwarding set correctly or the server internal  ip (typically 192.168.x.x) in the DMZ part of the router then everybody should be able to connect.

Blasted emotes ,

---

### Post by Sturm on 2007-07-14
> **Brynster said:**
> you need to add the flag + ip xxx.xxx.xxx.xxx:xxxxx to the launcher comand

the xxx.xxx.xxx.xxx being your external ip find that by pointing your favourite web browser to [www.whatismyipaddress.com](www.whatismyipaddress.com)

you can then set the game port to whatever you require after the ip address :xxxx

so for example mine is currently set to + ip 88.216.197.44:27015

and providing you have your port forwarding set correctly or the server internal  ip (typically 192.168.x.x) in the DMZ part of the router then everybody should be able to connect.

Blasted emotes ,

Is there supposed to be a space between the "+" and "ip" in that argument?  I assumed there wasn't, so my server.sh file is:

```
#!/bin/sh
echo "Starting CS:Source server"
sleep 1
screen -A -m -d -S css-server ./srcds_run -console -game cstrike +map de_dust +ip 74.140.239.73:27015 +maxplayers 16 -autoupdate
```

However, at the end of the output, I receive:

```
Console initialized.
Game.dll loaded for "Counter-Strike: Source"
maxplayers set to 32
maxplayers set to 16
WARNING: NNET_OpenSocket: bind: Cannot assign requested address
Couldn't allocate dedicated server UDP port
Add "-debug" to the ./srcds_run command line to generate a debug.log to help with solving this problem
Sat Jul 14 12:56:39 EDT 2007: Server restart in 10 seconds
```

If I leave out the "+ip" argument, the server runs fine, but no one can connect from outside my router.

---

### Post by Sturm on 2007-07-17
Hmmm...  Is there a better place for me to post this question?  It seems as though it is going to end up stagnant here...

---

### Post by Brynster on 2007-07-18
sorry my bad there should not  be a space between the + and the ip (it should read +ip xxx.xxx.xxx.xxx:xxxx)

the issue appears that the router is open to UDF traffic according tot he error message you are recieving.

if that doesn't work can i reconmend [http://forums.srcds.com/](http://forums.srcds.com/) as a source (sorry about the pun) for more specific info.

---

### Post by frodon on 2007-07-18
BTW, do you have VAC on your server ?

---

### Post by Brynster on 2007-07-18
VAC is automatic to the best of my knowledge unless you "opt out" by adding another launcher command flag.

I may be wrong, I know when my server is fired up it has VAC sheild in the master server list.

---

### Post by frodon on 2007-07-18
Ok, don't know if it's your problem but me as well as some users have issued VAC connection issues after the late updates and we found out that VAC is now using port after 27015 UDP on contrary of what the documentation says, so to solve the issue we have to open port from 27000 to 27020 UDP.

No sure it will help you, but just in case ...

---

### Post by Brynster on 2007-07-18
> **frodon said:**
> Ok, don't know if it's your problem but me as well as some users have issued VAC connection issues after the late updates and we found out that VAC is now using port after 27015 UDP on contrary of what the documentation says, so to solve the issue we have to open port from 27000 to 27020 UDP.

No sure it will help you, but just in case ...

Great suggestion!!!!

I have not had that issue so i wasn't expecting it ! Mr/Mrs OP give that a try also!

---

