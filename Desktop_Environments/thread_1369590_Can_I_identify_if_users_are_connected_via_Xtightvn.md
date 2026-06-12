---
title: "Can I identify if users are connected via Xtightvnc?"
date: 2010-01-01
forum: Desktop Environments
---

### Post by Silas (son of Silas) on 2010-01-01
I have installed xtightvnc on my server and xtightvncviewer on my client as its so much quicker than vinagre.

My question is, can I identify from a terminal on my server if users are connected?

I have a suspend script that runs every 5 minutes looking for locked files or to see if either of my media players are on the network. If the answer to all of the above is no then the server suspends to RAM. My media players are set to send WOL magic packets to thge server when they turn on, so the server only runs when its needed.

It all works perfectly, except my script doesn't take into account the fact that I may be on the desktop via xtightvnc doing something, so I would like a way of seeing if users are connected, then add that into my script.

the script bit I can work out, its just I seem stumped when it comes to getting info regarding the xtightvnc sessions open.

---

