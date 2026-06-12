---
title: "Minecraft for Ubuntu"
date: 2015-03-22
forum: Gaming &amp; Leisure
---

### Post by schankame on 2015-03-22
Sorry if I missed it, I'm new at this. Does anyone have know of a link to set up a minecraft server on Ubuntu? Or how to access one on a windows computer from an ubuntu computer?

Thank you!

---

### Post by efflandt on 2015-03-23
A web search for "minecraft server wiki" should explain it in Windows, Mac, or Linux. Example: [http://minecraft.gamepedia.com/Tutorials/Setting_up_a_server](http://minecraft.gamepedia.com/Tutorials/Setting_up_a_server)

 However, you don't really need Oracle Java, a vanilla minecraft client or server runs fine with openjdk-6-jre, although, it would be better to install openjdk-7-jre which might be required by some mods (like if you are going to run tekkit). And depending upon how many players will be on it you may want to give it more than 1G. And if you have plenty of RAM on a fast enough computer (preferably 64-bit Linux) you can actually run minecraft client and server on same computer. You have to run the server once to get all the files set up. Then if you want to you can copy a single player world over from ~/.minecraft/saves/ to your minecraft server directory and use that world for your server by setting level-name=dir_of_that_world in server.properties file.

It is best to leave server-ip= blank in server.properties, so it binds to any IP on the server. That way if you do run the client on the same computer you can simply connect it to the server on localhost or 127.0.0.1, from another PC on your LAN you can connect to server's LAN IP, and if you properly port forward on your router, others on the internet should be able to access it using your public IP address. If you have a dynamic public IP it helps to have some sort of dynamic DNS, so others could connect to it using a fixed name.

As an experiment I have run a minecraft server on as little as a 1 GHz 2 core tablet PC with 2 GB RAM (64-bit Ubuntu 12.04 booted from SD card) and that worked fine. So it does not really take a high end PC to run just a server. However, if you try to run a regular minecraft "server" on a Raspberry Pi, you would get extreme lag trying to break blocks (been there, done that).

---

