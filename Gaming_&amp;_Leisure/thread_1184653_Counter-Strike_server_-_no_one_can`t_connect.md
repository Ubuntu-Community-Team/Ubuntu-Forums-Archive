---
title: "Counter-Strike server - no one can`t connect?"
date: 2009-06-11
forum: Gaming &amp; Leisure
---

### Post by Blagomir on 2009-06-11
Hello

I have very strange problem. I have searched the forum and google'd the problem but nothing came out... So if you can help me please.

I have successful installed Counter-Strike server on my laptop (Ubuntu 9.04)

On my second laptop i have Counter Strike installed and tested -> playing with no problems on other server.

The problem is that when i try to connect from laptop2 to my CS server ot laptop1 inside my network (192.168.1.x) i get only "Reconnecting to the server" and after 2-3 tries it says that "Failed to contact game server"

Anyone have any idea how to debug this ?

---

### Post by v3xtra on 2009-06-12
What is the IP address that you are giving the server?  You should have set one up somewhere in the configuration settings.  You maaay or may not need to set up port forwarding on the router for the actual ports, or somewhere there is most likely a firewall blocking the port, either on the client machine or the server machine.

Also, I think there is a command that you MAY want to set, sv_lan 1, to make it a LAN game instead of an internet game, although I don't think that will make a difference.

Have you tried pinging the server computer from the client computer?  Can they even "see" each other?  If not, there is your problem and you should fix that first.  Second, if they can see each other, then somewhere the port is getting blocked and you need to unblock it somewhere.  Third, another way that you could try and do this is to port forward the ports from your router to the server computer, and then use the OUTSIDE IP address on your client computer to connect to it.  Unfortunately that will make it accessible to others on the internet, but if that works then you can pretty much figure out that it is something blocking ports on one of the computers.

I hope that that helps you a little bit, it's been a while since I have run my own server and I haven't ever done it yet in Ubuntu!  Hoping to be able to do that soon though!

---

### Post by AnkurOn on 2010-11-24
Dude First of All Did u Forward The ports !! .. Go to portforward.com and search for ur modem . Then see procedure for opening port And open Port number 27015 which mainly specified for Counter strike .
after opening port run the server And keep udp port as 27015 .
Then try to connect The Server frm any PC / laptop in ur network .
Even if u go in lan option it must Show u the Server Name.

I need some help frm u
How did u install Counter strike server .
please Reply me .
I Knw Eveything abt server config / Hosting .
 But when i downloaded Ubuntu Server edition 10.10 I am unable to make use of it .
So please Sal that do u have all files ??
Hope My Quote Helps u In solving the reconnect option !!! 
Ur faithfull friend  ANKUR

---

### Post by RabidWeezle on 2010-11-24
Well, for one he said he was trying to connect from inside the lan, not from another machine on the internet. Soo port forwarding isn't really nessasary for a lan connection. Some things you might want to check:

Check the version of the server that it is the same as the clients connecting to it. Basically you need to tear into the config files and make sure everything is kosher in there. Port setup, public or passworded, etc. Check the port in the config, then go into the console on the client on the lan and...

```

connect <server ip>:<port>

```

so for me that would be...

```

connect 192.168.1.101:27960

```

If it still isn't loading, make sure you have a maplist setup and the server actually loads a map.

Then once you want to share outside to the internet, open the ports on your router and firewall to the server machine.

Hope this helps.

---

