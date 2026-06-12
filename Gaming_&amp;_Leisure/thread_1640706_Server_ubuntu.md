---
title: "Server ubuntu"
date: 2010-12-08
forum: Gaming &amp; Leisure
---

### Post by Seth-666 on 2010-12-08
I have 3 PCs at home, 2 Desktop (wn7) and an ubuntu server (cs 1.6 server) to connect all PCs use a physical router.
I've  tried to do port forwarding on the router but nothing and I thought to  turn the routeru  into a swich disable NAT on the router. Ubuntu server to make it router and do port forwarding on ubuntu server, it is possible to swich tarnsform physical router?

---

### Post by Wtower on 2010-12-08
I believe the router shouldn't need port forwarding for the local area, only to forward incoming from outside to a certain pc. Anyway, you can try with [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo) and with [https://help.ubuntu.com/community/Squid](https://help.ubuntu.com/community/Squid) . If you need dhcp server, try [https://help.ubuntu.com/community/dhcp3-server](https://help.ubuntu.com/community/dhcp3-server) and if you need dns try [http://ubuntuforums.org/showthread.php?t=236093](http://ubuntuforums.org/showthread.php?t=236093) .

Good luck

---

### Post by Seth-666 on 2010-12-08
> **Wtower said:**
> I believe the router shouldn't need port forwarding for the local area, only to forward incoming from outside to a certain pc. Anyway, you can try with [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo) and with [https://help.ubuntu.com/community/Squid](https://help.ubuntu.com/community/Squid) . If you need dhcp server, try [https://help.ubuntu.com/community/dhcp3-server](https://help.ubuntu.com/community/dhcp3-server) and if you need dns try [http://ubuntuforums.org/showthread.php?t=236093](http://ubuntuforums.org/showthread.php?t=236093) .

Good luck
no, i want the players to connect to my server ubutu (cs 1.6) from amywhere

[http://www.2shared.com/photo/DS8OYIzS/Normal.html](http://www.2shared.com/photo/DS8OYIzS/Normal.html)
[http://www.2shared.com/photo/6W5QdcQG/2_online.html](http://www.2shared.com/photo/6W5QdcQG/2_online.html)

---

### Post by Seth-666 on 2010-12-09
sorry for double post, bust i see that nobody is ansewering

---

### Post by thatguruguy on 2010-12-09
> **Seth-666 said:**
> I have 3 PCs at home, 2 Desktop (wn7) and an ubuntu server (cs 1.6 server) to connect all PCs use a physical router.
I've  tried to do port forwarding on the router but nothing and I thought to  turn the routeru  into a swich disable NAT on the router. Ubuntu server to make it router and do port forwarding on ubuntu server, it is possible to swich tarnsform physical router?

I don't want to be insulting, because I realize that English probably isn't your first language, but I am having a hard time figuring out what you're asking.  Could you elaborate a bit more?

---

### Post by Seth-666 on 2010-12-09
> **thatguruguy said:**
> I don't want to be insulting, because I realize that English probably isn't your first language, but I am having a hard time figuring out what you're asking.  Could you elaborate a bit more?
can you contact me on <email address removed>? so i can give you more info pls

---

### Post by thatguruguy on 2010-12-09
> **Seth-666 said:**
> can you contact me on <email address removed>? so i can give you more info pls

No.

Here are some links which may be helpful:
[http://www.cstrike-planet.com/tutorial/1](http://www.cstrike-planet.com/tutorial/1)
[http://server.counter-strike.net/server.php?cmd=howto](http://server.counter-strike.net/server.php?cmd=howto)
[http://www.youtube.com/watch?v=hVg7nwfSIcU](http://www.youtube.com/watch?v=hVg7nwfSIcU)

---

### Post by Seth-666 on 2010-12-09
> **thatguruguy said:**
> No.

Here are some links which may be helpful:
[http://www.cstrike-planet.com/tutorial/1](http://www.cstrike-planet.com/tutorial/1)
[http://server.counter-strike.net/server.php?cmd=howto](http://server.counter-strike.net/server.php?cmd=howto)
[http://www.youtube.com/watch?v=hVg7nwfSIcU](http://www.youtube.com/watch?v=hVg7nwfSIcU)

i want to make a cs 1.6 server. I know how, i want to make port forwarding But i can't do it on my router, so i want to make the ubuntu server Router to make from the ubuntu server port forwarding...

---

### Post by thatguruguy on 2010-12-09
At least one of us has no idea what you're talking about.  What do you mean by, "i want to make port forwarding But i can't do it on my router."

I'd think that any port forwarding HAS to be done on your router; if nothing is being forwarded to your server from your router, it doesn't matter what the settings on your server are.

---

### Post by e79 on 2010-12-09
> **Seth-666 said:**
> I've  tried to do port forwarding on the router but nothing and I thought to  turn the routeru  into a swich disable NAT on the router. Ubuntu server to make it router and do port forwarding on ubuntu server, it is possible to swich tarnsform physical router?

Is there a specefic reason why your router won't forward ports ? What is your router model/brand ? On another hand, do I understand that you would like to have your Ubuntu server (that is already servicing CS if I understand well) to act as a router on top of it ? Do you have 2 Network Cards ? Any knowledge of IPtables or such ?

---

### Post by Seth-666 on 2010-12-09
> **thatguruguy said:**
> At least one of us has no idea what you're talking about.  What do you mean by, "i want to make port forwarding But i can't do it on my router."

I'd think that any port forwarding HAS to be done on your router; if nothing is being forwarded to your server from your router, it doesn't matter what the settings on your server are.

...  what can you understand? no player can connect to my server, and i made port forwarding ...

---

### Post by thatguruguy on 2010-12-09
> **Seth-666 said:**
> ...  what can you understand? no player can connect to my server, and i made port forwarding ...

Apparently, you didn't make port forwarding.

What router are you using?  Are you sure your settings are correct?

---

### Post by Seth-666 on 2010-12-09
> **thatguruguy said:**
> Apparently, you didn't make port forwarding.

What router are you using?  Are you sure your settings are correct?
YES i DID !

---

### Post by thatguruguy on 2010-12-09
> **Seth-666 said:**
> YES i DID !

Well, in that case, everything must be working.  Have fun!

In the meantime, you haven't answered my question.

What router are you using?

---

### Post by thatguruguy on 2010-12-09
By the way, did you read the documentation available at the following link?
[http://www.ubunite.com/documents/cssserver.pdf](http://www.ubunite.com/documents/cssserver.pdf)

It was referred to in the youtube link I gave you.  Have you looked at the links I gave you?

---

### Post by Seth-666 on 2010-12-09
Omg :neutral: i don't know to explain myself? or u can't understand english ? The sv in ON !! i can connect. no erros .. PERFECT !! 

> root@xxx:/sv1# ./hlds_run -game cstrike +ip 192.168.0.6 +sv_lan 1  -nomaster                                              +maxplayers 24  +map de_dust2
Auto detecting CPU
Using AMD Optimised binary.
Auto-restarting the server on crash

Console initialized.
scandir failed:/sv1/./valve/SAVE
scandir failed:/sv1/./platform/SAVE
Protocol version 47
Exe version 1.1.2.6/Stdio (cstrike)
Exe build: 02:38:45 Jul  7 2004 (273:cool:
STEAM Auth Server
Server IP address xxx:27015

   Metamod version 1.17.2  Copyright (c) 2001-2004 Will Day  <willday@metamod.org                                             >
   Metamod comes with ABSOLUTELY NO WARRANTY; for details type `meta gpl'.
   This is free software, and you are welcome to redistribute it
   under certain conditions; type `meta gpl' for details.

scandir failed:/sv1/./valve/SAVE
scandir failed:/sv1/./platform/SAVE

Server logging data to file logs/L1209002.log
L 12/09/2010 - 20:10:28: Log file started (file "logs/L1209002.log") (game "cstrike") (version "47/1.1.2.6/Stdio/2738")
couldn't exec listip.cfg
couldn't exec banned.cfg
Executing Admin Mod config file
L 12/09/2010 - 20:10:28: Server cvar "default_access" = "1"
Master server communication disabled.
L 12/09/2010 - 20:10:36: World triggered "Round_Start"


SEE ? but nobody can connect, because the router blocks... and it won't work the port forweding i made on the router, SO i want to MAKE the ubuntu server Router with 2 etho and the real router to transform into a swich so i can make port fordweing from the ubuntu server ... did u understand ?:|

---

### Post by thatguruguy on 2010-12-09
I'll let someone else help you, because I find your tone unpleasant.

In the meanwhile, you may want to tell what router you're using. That would be a good place to start.

EDIT: You also may want to post your ip, so people can try to ping it.

---

### Post by drdos2006 on 2010-12-09
It sounds like you need some help.
Here is a HOWTO which I found comprehensive and invaluable.
> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
Setting up a Linux Server, Start to Finish, using Webmin. By Kevin Elwood


regards

---

### Post by Wtower on 2010-12-09
I know of routers that have got limited port forwarding capabilities like a Thomson that came across lately. If you are lucky enough that your router has got the feature to at least forward all incoming to a specific internal IP (sometimes they call this feature DMZ which name is debatable), then you can set iptables in that machine and do the job.

So I believe this is what our friend is trying to get to, but I am afraid he or she didn't  spend some time reading about ip tables at the links provided.

Regards

---

### Post by lisati on 2010-12-09
> **Seth-666 said:**
> can you contact me on <email address removed>? so i can give you more info pls

It's not a good idea to post your email address on these forums, unless you are happy to receive a truck load of Spam. It's also usually better to discuss your support request through the discussions on the forum (as you have been doing), so more people with similar problems can benefit.

---

### Post by thatguruguy on 2010-12-09
> **Wtower said:**
> I know of routers that have got limited port forwarding capabilities like a Thomson that came across lately. If you are lucky enough that your router has got the feature to at least forward all incoming to a specific internal IP (sometimes they call this feature DMZ which name is debatable), then you can set iptables in that machine and do the job.

So I believe this is what our friend is trying to get to, but I am afraid he or she didn't  spend some time reading about ip tables at the links provided.

Regards

Of course, there's no way to know if his router has that problem, because he has refused to tell us what kind of router he has. Despite the fact that he's been asked repeatedly.  Apparently, he expects people to help him without having the most basic information.

---

### Post by Seth-666 on 2010-12-09
sorrt for my tone...

[http://www.2shared.com/photo/iu070x-8/2_online.html](http://www.2shared.com/photo/iu070x-8/2_online.html)

---

### Post by e79 on 2010-12-10
> Console initialized.
scandir failed:/sv1/./valve/SAVE
scandir failed:/sv1/./platform/SAVE
Protocol version 47
Exe version 1.1.2.6/Stdio (cstrike)
Exe build: 02:38:45 Jul  7 2004 (273:cool:
STEAM Auth Server[U][B]
Server IP address xxx:27015[/B][/U]
Looking at your server log, did you forwarded incoming connexions from the WAN on port **27015 **to your server using the same port (**192.168.0.6:27015**) ?

On another hand, as a simple test, can you plug your server straight to the internet (for couples of minutes only) bypassing your router and see if people can connect ? Does that work ?

P.S : your screen shot is not of much help...we don't need to see your web admin interface but we do need to know the router model number... I can only assume this is the company who made your router....[http://www.zioncom.net/](http://www.zioncom.net/)

---

