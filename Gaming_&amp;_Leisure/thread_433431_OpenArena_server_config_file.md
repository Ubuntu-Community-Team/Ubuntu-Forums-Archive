---
title: "OpenArena server config file"
date: 2007-05-05
forum: Gaming &amp; Leisure
---

### Post by anjilslaire on 2007-05-05
Hi everyone.

I'm looking to set up my own OA server for me and some friends. I've got the server package on my edgy server and it appears that I need to write up a config file for it. I'll be playing the client on my kubuntu feisty system.

Does anybody have a sample server config file I can look at to modify, or point me to a good tutorial for setting it up, including file placement, enabling bots, maps, etc? I've got plenty of bandwidth & upload/download speed, so I plan to leave it up pretty much all the time.

Any help is appreciated.

---

### Post by anjilslaire on 2007-05-10
bump. Any suggestions?
Thanks!

---

### Post by Gouki on 2007-12-24
I would like to know more information about running a server. I was thinking about running it on a VPS with 64MB of RAM :)

---

### Post by Matthewslf on 2008-01-05
There really is no need to touch the config file. If you have the openarena-server package, just go to multiplayer and create, and it has all of the options you mentioned. Openarena defaults to port 27960, so make sure you forward that to your computer in your router settings. Other than that, you should be set.

---

### Post by ubuntu_demon on 2008-01-09
If you want to have a dedicated server there is need for a server config file. 

You can base your config file on the linux example here :
[http://openarena.wikia.com/wiki/Servers](http://openarena.wikia.com/wiki/Servers)

This config file contains all map names :
[http://openarena.ws/board/index.php?topic=854.0](http://openarena.ws/board/index.php?topic=854.0)

```

sudo aptitude install openarena-server

```
Create your config file (for example server.cfg) and store in the folder ~/.openarena/baseoa
```

openarena-server +exec server.cfg

```

You can have multiple config files and multiple servers running. The first one is at 27960.

more information (q3a options work in openarena) :
[http://gameadmins.com/modules.php?name=Sections&op=listarticles&secid=1](http://gameadmins.com/modules.php?name=Sections&op=listarticles&secid=1)
[http://www.sp1r1t.org/networks/q3_install/q3_linux_server_howto.php](http://www.sp1r1t.org/networks/q3_install/q3_linux_server_howto.php)

---

### Post by vindimy on 2010-03-22
See [http://thedimi.net/wiki/openarena]("http://thedimi.net/wiki/openarena") and [http://oa.thedimi.net/configs/]("http://oa.thedimi.net/configs/") - all you need to get your OpenArena server started.

---

