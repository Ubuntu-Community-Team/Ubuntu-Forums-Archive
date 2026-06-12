---
title: "noob help with BF2 server"
date: 2006-10-01
forum: Gaming &amp; Leisure
---

### Post by repairthat on 2006-10-01
Hi all,
I'm a complete noob with linux, and an avid gamer, tho never on the server hosting side. I'm now trying to set up a server to play LAN games on with friends.

I plan on starting with BF2, and then adding other games once I can get comfortable with this process.

I dled the bf2 linux server files onto my windows machine, and burnt the file onto a cd. Also burnt the iso for dapper server, and was able to install that easily from the menu.

Using the command line interface of the server, I was able to mount the data cd, copy the server file to a new directory in my home directory, and unzip and install to the point where bf2 and punkbuster ask you to accept the eula and choose an install directory. I now have a directory ~/bf2/bf2 which has the important files, but I'm not sure how to launch, and get the config going. I can't seem to find a good set of instructions online or at this forum.  
I can see quite a number of files &directories. I've tried sh start.sh and got the following error - "error while loading shared libraries: lib stdc++.so.5: cannot open shared object file:no such file or directory"

I'm not even sure that's the correct command (guessing from a similar install guide for Quake 4 linux) and can't tell how to open up the .txt readme files.

I apologize for the basic questions here. If needed, please move this to appropriate forum. Please advise : if you have installed bf2 v1.4 server, or have a good link to instructions on how to do the server admin/linux admin, and other good beginner references.

Thanks!

PS- just found this wiki link on linux servers, I will give it a shot!
[http://www.serverwiki.org/index.php/Battlefield_2_Linux_Server_Setup](http://www.serverwiki.org/index.php/Battlefield_2_Linux_Server_Setup)

---

### Post by repairthat on 2006-10-05
Just an update for any interested parties. 
I've got it up and running on Ubuntu as a local Lan server for the basic BF2. I can play coop games, and apply bots and use the Rcon. :KS (Yay for me!)

I need some help though, from more experienced people. I have a number of issues, here numbered for your answering ease:
1) I can't figure out how get weapons unlocked. I don't have to have all unlocked, just the ones the players have earned. Do you know of any way to do that? It appears to be unable to be changed in the latest 1.4 version. 
2) Remote control of bf2 server- anyone done this? What do you use? Bf2cc? rcon? What makes bf2cc better (apparently)?
3)I'd like to add a few maps to my rotation (Special Forces, Armored Fury Pak)
4) I have to manually start either my ethernet connection or dhclient to connect to any sort of Lan or Internet. (using sudo ifup eth0 && sudo ifdown eth0 && sudo dhclient eth0) I think this is because the eth0 wasn't connected during install of Ubuntu. How can I automate this to startup?
5) I have more research to do about securing the server. Any one have a perfect guide/resource they'd like to point me to? 
6)I'm curious about others experiences with some of the mods that have been done. I've never played one, and would like to see about getting some of my friend into it by offering it during the LAN. Any recommendations?

Thanks for you patience with my lazyness and piggybacking! :-D

---

