---
title: "Freeciv Client freezes"
date: 2007-05-24
forum: Gaming &amp; Leisure
---

### Post by mrfredman on 2007-05-24
I can't get freeciv to work. The client opens, but when I click on any of the options to start a game it just freezes up. Any ideas as to why this is going on? 

Note: The soundcard on this machine has no linux support so I have no functioning sound, and it gives me errors about that, but I didn't think it was related because other games run fine.

---

### Post by afderrick on 2007-11-13
I am having this same problem and haven't found any answers pertaining to this yet.  Has anyone found a fix action for this or what is causing the problem?

---

### Post by himasaram on 2007-11-18
There could be many reasons for this happening. You have to realize Freeciv is a client-server application. When you click "start new game" in the main menu, a server session is started in the background. If this session for some reason fails, it can freeze the client.

First please post Freeciv version numbers and where you got the game from, i.e. synaptic, 3rd party package, or complied from source.

Then you can try this: from the terminal type civserver and press enter. This will start a server session separate from the client. After that start Freeciv as usual, but instead of starting a new game, choose to connect to a network game and connect to your own locally hosted server. Report any output you get!

---

### Post by maljaros on 2008-03-26
Running Ubuntu 7.10 my Freeciv worked fine until I disabled "Roaming Mode" in Eth1 and set the config to Static IP address.  Since then, my Freeciv client can no longer find the server (even if I start it separately) so selecting any of the startup options except "Connect to Network Game" causes a freeze of about a minute during which the System Monitor shows heavy network activity and then the error messages "couldn't connect to server" followed by "we probably couldn't start from here" and then "you will have to start one manually".  Any ideas on what setting to change? or how to start manually?

---

### Post by Perfect Storm on 2008-03-26
> **maljaros said:**
> Running Ubuntu 7.10 my Freeciv worked fine until I disabled "Roaming Mode" in Eth1 and set the config to Static IP address.  Since then, my Freeciv client can no longer find the server (even if I start it separately) so selecting any of the startup options except "Connect to Network Game" causes a freeze of about a minute during which the System Monitor shows heavy network activity and then the error messages "couldn't connect to server" followed by "we probably couldn't start from here" and then "you will have to start one manually".  Any ideas on what setting to change? or how to start manually?

Tried deleting the .freeciv folder (which contains info/setup for your user.

---

### Post by maljaros on 2008-03-26
Thank you Artificial Intelligence.  I emptied and removed the directory /usr/games/freeciv and then used "Add/Remove Applications" to first Remove and then Add Freeciv. 
Opened civserver in terminal - it says "Now accepting new client connections".
Opened civclient in new terminal and clicked "Start New Game".  Same result - long wait with network activity then "Opening Server .." followed by "Couldn't connect to server .."
Tried "Connect to Network Host".  LAN tab has Host: localhost and Port 5555.  Press OK - get message "Connection refused".
Connected to a game on Internet Metaserver O.K. 
Localhost refuses connection, although I can ping it ok from a terminal.
Any suggestions ?

---

### Post by Perfect Storm on 2008-03-27
But did you delete .freeciv? It's hidden in your home directory.

---

### Post by maljaros on 2008-03-27
err.. well, no, actually I hadn't.
I didn't know about hidden directories.  
Thank you again for the further enlightenment.  
But, unfortunately, deleting .freeciv hasn't helped either.

---

### Post by Perfect Storm on 2008-03-27
Is the port open?

---

### Post by maljaros on 2008-03-27
I am embarrased to say that I don't know if the port is open or, worse still, how to find out.
Have now opened Firestarter for the first time and will embark on a short voyage of dicovery before reporting back, but that won't be for several hours as I now have to drudge through the day, it being 7:22am local time here.

---

### Post by maljaros on 2008-03-28
> **himasaram said:**
> There could be many reasons for this happening. You have to realize Freeciv is a client-server application. When you click "start new game" in the main menu, a server session is started in the background. If this session for some reason fails, it can freeze the client.

First please post Freeciv version numbers and where you got the game from, i.e. synaptic, 3rd party package, or complied from source.

Then you can try this: from the terminal type civserver and press enter. This will start a server session separate from the client. After that start Freeciv as usual, but instead of starting a new game, choose to connect to a network game and connect to your own locally hosted server. Report any output you get!

Checked status of Firestarter and found that, although all ports appeared to be open, the firewall was blocking access to 192.168.1.2 which is the address allocated to my desktop by the DSL router.  So, I enabledl connections to/from this address and the sequence suggested above by HIMASARAM now works.  Remaining problem is that the options "Start new game", "Start scenario game" and "Load saved game" still don't work.  Of these the only one I really need is a way to restart a saved game.

---

### Post by maljaros on 2008-03-29
OK guys, I know we have moved on from gaming to network issues, and maybe I should start another thread, but you have taught me plenty in the last couple of days so lets give it another go.
The firewall issue is sorted - port 5555 is open and so is localhost and turning the firewall off completely makes no difference. 
To recap - I downloaded freeciv 2.0.9 using Synaptic on gutsy 7.10 and it all worked fine until I changed Eth0 from Roaming Mode to Automatic (DHCP).  Since then my Freeciv client cannot find or start a server to "Start New Game" or "Load Saved Game", but "Connect to Network Game" still works fine and allows connection to a bunch of Network Metaservers or any civserver that I have started from Terminal on Localhost.  
I have found similar posts across the forums, none of them has an answer except "Your network is broken - fix it". But my network is not broken.  Through the ADSL router I can surf the net and link to my notebook.  So the question is, if the Client can find a Server through "Connect to Network Game", why can it not start (or connect to) a server in the "normal" way?

---

### Post by Perfect Storm on 2008-03-29
I don't have an answer to that, other than it could be a bug. What was the reason to change it to roaming? (I'm a cable user guy, where it works when just plugged in).

---

### Post by maljaros on 2008-03-29
From the general air of puzzlement on this and other forums it does look like a bug.
The change from roaming mode was not a clever move, and the bad effect was irreversible.  Putting it back into roaming mode doesn't solve anything.
The reason?  Well, I was setting up FreeBSD on an external drive (the problem may be something FreeBSD did) and playing with the settings to get a feel for what does what.  A classic case of "if it ain't broke don't fix it".  But so far there don't seem to be any other consequences outside of this freeciv thing.
Thanks for your help, and I reckon the learning experience has already made it worthwhile.  At least I know how the firewall works and learned a little bit, with maybe more to come, about setting up a network.

---

