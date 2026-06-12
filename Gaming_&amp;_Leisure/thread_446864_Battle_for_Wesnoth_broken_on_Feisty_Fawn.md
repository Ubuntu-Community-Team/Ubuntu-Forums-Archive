---
title: "Battle for Wesnoth broken on Feisty Fawn"
date: 2007-05-17
forum: Gaming &amp; Leisure
---

### Post by concord on 2007-05-17
I've installed two machines brand-new with Ubuntu 7.04.  After doing `sudo apt-get install wesnoth-all` on both machines I verified that hosting a game had the machine(s) listening on port 15000.  No matter which machine I hosted the game on the other one cannot connect (doesn't show a game being hosted by the other machine).  No personal firewalls whatsoever.

After downloading 1.2.4 (Ubuntu packages 1.2.3) and compiling from source one machine can host a game and the other can connect fine.  (hosting machine is running the newer version).

Can anyone verify this issue?

FYI

- Frank

---

### Post by markthecarp on 2007-05-19
It worked here but I used a different method.

Box 1 (desktop) I started the server daemon with "sudo /etc/init.d/wesnoth-server start". I found this better than "wesnothd -d" as the statistics didn't dump to stdout, my terminal window. That is not a typo; "wesnothd -d" without sudo will start the server.

On desktop I did Multiplayer > Join Game > "localhost:15000" and setup a game.
Box 2 (laptop) almost same thing Multiplayer > Join Game > IPofDesktop:15000" and joined the game.

The method you described worked here. I killed the server process before attempting the method you describe.

I do have a problem with "/query admin <password>" to access admin commands from the lobby. It doesn't work regardless of which command I use to start the server. Do you have that problem?

One thought on your first attempt, do you have the same user name on both machines? That, having the same user name on both machines, prevented me from joining a game until I'd changed my name in the game.

-mark

---

### Post by concord on 2007-05-19
I did not use any command line arguments - or even launch from the command line.  I simply start the game by clicking the icon called "Battle for Wesnoth" on the Applications/Games... menu. 

On the first machine (doesn't matter which one) I select "Multiplayer" and then "Host Network Game".  After selecting the appropriate options I wait for the other network player to connect.  They start the game, select to join a game, put in the ip address of the hosted game and port 15000.  They do not see any games available to join.

Like I said, after compiling from source I can do the exact same thing only now the game appears to the other machine attempting to join the game. 

Can anyone else confirm that it's simply not possible to have two computers running Fiesty Fawn and the packaged version of Wesnoth (meta package "wesnoth-all") connect and share a game over the network?

- Frank

---

### Post by markthecarp on 2007-05-20
Hi Frank,

About 95% sure if you install the wesnoth-all meta package the server part is loaded _and starts. Take a look at /etc/init.d on the machine you compiled on and compare that with one that still has the stock Ubuntu 7.04 binaries. 

I've just learned this in last couple of hours. As a test do "ps aux | grep wesnothd" on the machine that still has default Ubuntu binaries. I was shocked to find the server part running on my laptop when I never started it.

I put the wesnoth-all meta package on two machines belonging to a friend who is new to Linux last Friday. He's off sailing on Lake Norman this weekend so I won't be able to check his setup until sometime Monday. We didn't  have time Friday for testing/playing. We're planning on getting together anyway as his desktop machine still needs tweaking on some non-free stuff. (plus some strange to me HP printer that CUPS detects as two machines)

I will say that it worked on my LAN "out of the box" despite both machines running the server daemon, or maybe because? Another possible difference is that my desktop has a static IP and laptop a dhcpd assigned IP. Note: just a possible difference in our setups; makes no sense to me that static or dynamic IP should matter.

-mark

---

### Post by Cappy on 2007-05-20
ack! ur right! it's running a server in the background! =(

---

### Post by markthecarp on 2007-05-21
> **Cappy said:**
> ack! ur right! it's running a server in the background! =(

I'm wondering if you have had the problems concord describes? 

> On the first machine (doesn't matter which one) I select "Multiplayer" and then "Host Network Game". After selecting the appropriate options I wait for the other network player to connect. They start the game, select to join a game, put in the ip address of the hosted game and port 15000. They do not see any games available to join.

concord: on box 1 "Multiplayer > Join Game > localhost:15000" then try from box 2.

The _server is listening on port 15000 but the game is listening on some other port. I tried the game menu path; Multiplayer > Host Network Game, on my desktop. I cannot connect to that game from my laptop over port 15000. I tried "netstat -rl --inet" to find the port the game was listining on to no avail.

I kill the server process on desktop, leave it running on laptop, start game on desktop, follow the game menu on desktop to host a game. Inject that netstat line in after each step. Now the _game is listening on port 15000 so I can connect from laptop. Whose server process is still running and can be connected to from another instance of the game on desktop. 

Missing parts of my testing:
-does the server start on installation of the "wesnoth-all" package?
--can't confirm because I started the server with a command line perhaps starting a process not started by installation.
--can't confirm from laptop because of a reboot between installation and starting the game 

The #wesnoth channel is helpful.

-mark

---

