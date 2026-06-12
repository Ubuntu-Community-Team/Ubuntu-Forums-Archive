---
title: "HLDS assign Admin CS:S"
date: 2010-03-30
forum: Gaming &amp; Leisure
---

### Post by wesg on 2010-03-30
I've set up a CS:S server running on Ubuntu 9.04 and I want to make sure I can admin it when I play. What do I do to actually reach the console and add bots, change players, etc.?

---

### Post by dfreer on 2010-03-30
First off just to clarify: SRCDS is the Counter-Strike: Source Dedicated Server, along with all other Source based engines (Half Life 2, Left 4 Dead, etc). HLDS is the **original** counter-strike dedicated server. The following will assume you are indeed using SRCDS for a CS:S server.

Your question is a bit vague, but here's some general info: When you launch the server on host machine, you will be greeted with a scrolling text summary of events transpiring in your server (players being killed, talking, map restarts, etc). At any time in this "server console" you can input commands, such as mp_restartgame or kickid.

Now from your client machine that connects to the server, you can access your clients console by going to Options -> Keyboard -> Advanced... -> Enable Developer Console (~). Once that's enabled, press the tilda (~) key to bring up the console anytime you are in the menu system (in game or not). 

To send commands to the CS:S as you are playing it, you will first need to make sure you have RCON enabled and a RCON password set in your server's config file. Then, in your clients console, type:
```
rcon_password **REPLACE_WITH_PASSWORD**
rcon mp_restartgame
rcon kick fatality
```

You can also do this without actually joining the server by using rcon address to specify which IP to connect to, then login in as normal.

If you would like to **not** use the console everytime you want to use admin in your server, I'd recommend mani's mod or something similiar.

---

