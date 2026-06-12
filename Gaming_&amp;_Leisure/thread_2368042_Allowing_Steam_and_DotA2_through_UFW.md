---
title: "Allowing Steam and DotA2 through UFW"
date: 2017-08-06
forum: Gaming &amp; Leisure
---

### Post by Tamrat_Assefa on 2017-08-06
Hello all, I'm kinda new to Ubuntu and I need help setting up UFW. I live in Ethiopia and internet is a luxury here. So I have to watch my data usage very carefully. I play 2 or 3 games of DotA with my limited data of 300MB per day. When I had just installed Ubuntu, nothing was using the internet unless I had it explicitly open. But after a lot of app installs and etc, I see a usage of around 50MB with in seconds of connecting.

Back when I was using Windows, I could just block everything in Windows Firewall then create a rule to allow steam.exe and dota2.exe. I tried to achieve the same thing with UFW in Ubuntu but I found out that I could only allow or deny connections based on ports. That was a bit alien to me. I mean if I allow port 80, sure I can make HTTP requests in Steam but that means other apps can also use this open port, right? 

My question is, is there anyway I can deny all incoming and outgoing connections, then add a rule that allows outgoing connections for Steam and DotA2? 

Thanks, 
Tamrat

P.S: I have installed gufw in hopes of achieving this, but I never got anything.

---

### Post by sccman on 2017-08-12
I've found what you're looking for:

[https://askubuntu.com/questions/409013/how-do-you-create-an-app-profile-for-ufw](https://askubuntu.com/questions/409013/how-do-you-create-an-app-profile-for-ufw)

Steam uses various ports:
[https://support.steampowered.com/kb_article.php?ref=8571-GLVN-8711](https://support.steampowered.com/kb_article.php?ref=8571-GLVN-8711)

Dota 2 uses UDP port 27005 for connecting to a game and UDP ports 27015-28999 for dedicated servers:
[http://dev.dota2.com/showthread.php?t=15261](http://dev.dota2.com/showthread.php?t=15261)

---

