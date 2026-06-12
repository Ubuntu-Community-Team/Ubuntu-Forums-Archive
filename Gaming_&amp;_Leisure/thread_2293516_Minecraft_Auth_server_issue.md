---
title: "Minecraft Auth server issue"
date: 2015-09-05
forum: Gaming &amp; Leisure
---

### Post by jailbreaker1220 on 2015-09-05
I have recently install Ubuntu Gnome. It did not have java pre-installed. So i have installed it with apt-get install default-jre

I run a technic server and use the client. My friend tried to connect to the server and was stopped when he couldn't authenticate. I tried to log in with the technic launcher and I couldn't because it couldn't connect to the authentication server. I have enabled and disabled the firewall with Gufw. It does not help. I have already added an exception both ways for port 25565 for the server. I am unsure what else to do. The server runs fine and i connect just fine when I am on windows. I had this same problem when I had the firewall with Kaspersky on windows, however I added the exception for java program and I never had this issue. The ports are forwarded correctly for the server. I am just having issues with reaching the authentication servers. Which by the way are up, as I checked from here. [https://help.mojang.com/](https://help.mojang.com/)

---

### Post by ethan27 on 2015-09-10
Make sure you have a fast and stable Internet. Is it's not fast enough it may time out and not be able to reach the authentication servers in time. Stable because a little drop out for like 1 second can cause the Authentication servers to think you disconnected. Just some advice though It may apply to some people don't know but this may be the cause.

---

### Post by tinynja98 on 2016-02-13
Hello, i have the exact same problem here. I am running a minecraft server on Ubuntu server 15.10, and i cannot connect to my server because it says "Authentication servers are down" while they are actually up. Would this problem be related to a firewall or something? I have close to 0 experience with ubuntu server so i have no idea what features are in it and how to configure this os.

Thanks in advance for your help :)

---

### Post by tinynja98 on 2016-02-13
Welp... I found a fix for my issue. I wrote a [thread in the minecraft forums]("http://www.minecraftforum.net/forums/support/server-support/2615148-fix-for-authentication-servers-are-down-issue-on").

---

