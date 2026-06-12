---
title: "Streaming NCAA hoops content"
date: 2009-01-26
forum: General Help
---

### Post by Radioman991 on 2009-01-26
Hello:

I stream the basketball games of our local university to my 42" TV.  CBS "Sports" uses that annoying Microsoft Silverlight nonsense to stream sports.  I have tried the Moonlight application on 8.10, but cannot seem to ever get it to work.

Anyone else have this issue, or know what I might be doing wrong?

Regards,

Radioman

---

### Post by Radioman991 on 2009-01-28
Bump

---

### Post by avtolle on 2009-01-28
[http://ubuntuforums.org/showthread.php?t=1045676](http://ubuntuforums.org/showthread.php?t=1045676) may explain your difficulties a bit (you may ignore the posts about statistics). Simply stated, Moonlight handles Silverlight 1.0; if CBS is using SL2, as I suspect is the case, Moonlight isn't going to be able to handle it.

---

### Post by madtownmike1 on 2009-03-20
I'm part way there.  first of all, you don't actually need  silverlight / moonlight installed- windows media player access is also available, once you get past the "silverlight required" screen.
I installed the "user agent" plugin for firefox and after switching my user agent to internet explorer I was able to get past the silverlight screen. The next screen says I don't have silverlight or microsoft media player installed. I know I can play microsoft media content, but I can't seem to convince CBS of that. Anyone have access to a windows machine? if we could get the URL that is streaming the games, maybe we could go directly to it?

---

### Post by dalhamir on 2009-03-20
okay, well, I was able to get two web addresses, but can't get either to work with ubuntu...

first, is the url of the webpage that the sd player is on for the ncaa site:
[http://mmod.ncaa.com/video/player?ts=1237594213&t=70f4ad034224b469c08a8c854eaf8df4&w=90](http://mmod.ncaa.com/video/player?ts=1237594213&t=70f4ad034224b469c08a8c854eaf8df4&w=90)

next is the url that you get when you right-click on the sd player and look at properties -> location :
[http://www.cbssports.com/video/playlist?prod=mmod%3Bfeat=live&qlevel=s&adtype=pre&dc=videos.spln.com&zone=mmod&&id=m](http://www.cbssports.com/video/playlist?prod=mmod%3Bfeat=live&qlevel=s&adtype=pre&dc=videos.spln.com&zone=mmod&&id=m)

but that doesn't really get you much. even entering either of those urls into wmp on my xp machine doesn't work. It almost seems like they are going out of their way to try and shut linux out. I'm sure their not, but it's anoying none the less.

---

### Post by dalhamir on 2009-03-20
OHHH! I was wrong!!! I just hadn't selected a game yet. There is going to be a different url for each game.

The Arizona/Utah game is:
[http://mfile.ncaasports.com/69193/live/reflector:60441.asx?auth=daEbRcWahbDdmcPdNbYdwbPbbagdycacldF-bjXdrW-c0-OM9vCyvebbj&aifp=v0001&ROUND=1&REGION=Miami%2C%20Fla.%20-%20Midwest%20Region&GAME=AZvsUT&](http://mfile.ncaasports.com/69193/live/reflector:60441.asx?auth=daEbRcWahbDdmcPdNbYdwbPbbagdycacldF-bjXdrW-c0-OM9vCyvebbj&aifp=v0001&ROUND=1&REGION=Miami%2C%20Fla.%20-%20Midwest%20Region&GAME=AZvsUT&)

it looks like that last variable is all that would need to be changed to get other games... I still can't get it working with totem, but we are very very close

---

### Post by Glucklich on 2009-03-21
> **dalhamir said:**
> OHHH! I was wrong!!! I just hadn't selected a game yet. There is going to be a different url for each game.

The Arizona/Utah game is:
[http://mfile.ncaasports.com/69193/live/reflector:60441.asx?auth=daEbRcWahbDdmcPdNbYdwbPbbagdycacldF-bjXdrW-c0-OM9vCyvebbj&aifp=v0001&ROUND=1&REGION=Miami%2C%20Fla.%20-%20Midwest%20Region&GAME=AZvsUT&](http://mfile.ncaasports.com/69193/live/reflector:60441.asx?auth=daEbRcWahbDdmcPdNbYdwbPbbagdycacldF-bjXdrW-c0-OM9vCyvebbj&aifp=v0001&ROUND=1&REGION=Miami%2C%20Fla.%20-%20Midwest%20Region&GAME=AZvsUT&)

it looks like that last variable is all that would need to be changed to get other games... I still can't get it working with totem, but we are very very close

How did you got the link of the game? Or better yet, how did you got past by the screen? There is a version 2 of Moonlight in the repositories.

---

