---
title: "Minecraft LAN not working"
date: 2022-02-12
forum: Gaming &amp; Leisure
---

### Post by fatn00b on 2022-02-12
I've  opened a world to LAN (running minecraft on Ubuntu 20.04, using OpenJDK  runtime environment 17.0.1) and I'm trying to have a friend (macOS Big  Sur) join. It's not working.

  We are on the same network. We have each other's local IP addresses  and are able to ping each other, but when my friend tries to direct  connect to my [noparse]IP:Port[/noparse], they get the message "Cant connect to server.  Operation timed out" (nothing shows up on the "scanning for games on  your local network either).
  My friend has been able to connect to my game opened to LAN when we  were both on a different network, so it must be something with the  network, but I am very confused since we can still ping each other. Any  help is really appreciated!

---

### Post by mastablasta on 2022-02-14
> **fatn00b said:**
> 
  My friend has been able to connect to my game opened to LAN when we  were both on a different network,!

that doesn't really make any sense.


from version 15 or so onward it doesn't seem to work like it did before. at least it is not that easy to set it up. so i just downloaded and installed the server version. made it LAN only, changed a few other parameters and we were good to go.

---

### Post by linux-sysop on 2022-02-14
Hello, 

First LAN stands for Local Area Network and Local normally means just, 2 or more PCs on one network.  Games over a network can connect via the internet by sharing your IP address, this is not LAN. Unless you share the same router, you are broadcasting over the intern via [TCP and UDP]("https://byjus.com/gate/difference-between-tcp-and-udp/").   

Now that definitions are cleared up, you or your friend, are likely being blocked by a firewall, on your end, his end, or both.  You should be prepared to study a lot about port forwarding a program.  Network games are fun, but don't put your system security at risk.

Edit starts here:

I spoke to a good friend of mine who plays games often.  He told me the biggest issue with Minecraft connectivity was the mods.  He plays with other users across Europe and told me different OS isn't the biggest reason for not connecting.  Your packages must match, his friends would add mods without telling him and the matchmaking server will not connect you.  He said some mods are called "server mods" and the others are "local mods".  Make sure your friend hasn't got a server mod you don't have installed.

---

### Post by fatn00b on 2022-03-04
Right this was poorly worded. We were both on the same network, which was a different network from the one we are both currently on. Given that we connected over the LAN network, I don't think it has anything to do with a firewall, as nothing changed on our computers, just the router we were both connected to was different.

---

### Post by mastablasta on 2022-03-09
try typing in the IP address and port manually in Minecraft. sometimes it doesn't find the LAN games, but if you type the > IP:port it will find it and you can then connect to it.

use command
```
ifconfig
``` 

to see your ip address and network data.

if it still doesn't work can you share your server config file? 

ever since MS took over they really overcomplicated things for LAN players.

---

### Post by ahmedshah on 2022-03-21
Try updating the network drivers that could help you to fix [Minecraft LAN not working]("https://cyberxgaming.com/minecraft-lan-not-working/") issue or try to play without MODs.

---

