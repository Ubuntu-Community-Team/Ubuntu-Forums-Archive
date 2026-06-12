---
title: "Ventrilo Server Troubles"
date: 2006-04-25
forum: Desktop Environments
---

### Post by conedude13 on 2006-04-25
Hi all, I am new to ubuntu breezy badger and couldn't find any detailed info on my subject.  I have the vent server and can get it to start.  I am behind a lynksys router and have port forwarding set up the same way I did when I had xp on the system.  Even though I have everything set up correctly, IMO, no one is able to connect to the server.

I have the latest vent server, linux version, from the ventrilo website.  It starts up great and I can enter the status commands to see what is going on in the server.  I have everything set up for port forwarding on port 3784, which is the default port for the free version of the server.  I also have the windows version of the client running through wine.  Both are running from my computer from their own folders.

With this set up, I cannot connect from my client to the server on my own computer, nor can anyone else connect to my server from the outside world.  So I was just wondering if there was some port that I have to specify ubuntu to listen to in order to get people to connect from the ethernet card to the server?  Or should the port forwarding be enough to get things to work?

Also, before anyone says get the native version of teamspeak, I have tried teamspeak and me and my guild prefer the quality and interface of ventrilo.  We have tried teamspeak before and were more pleased with the results we got while using ventrilo.

Any help is greatly appreciated by me and my guild mates.  Thanks!

---

### Post by conedude13 on 2006-05-08
Never mind, I managed to fix it.  I installed firestarter, the firewall for linux, and now it is working fine.  After tinkering with it for a while, I found out that linux just blocks everything that comes to it.  With the firewall, you are able to pick and choose what you want to let through that gets port forwarded to you by your router.  It was a learning experience, but now that i have that installed people are connecting to my server!

---

