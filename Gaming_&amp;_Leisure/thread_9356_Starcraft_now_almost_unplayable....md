---
title: "Starcraft now almost unplayable..."
date: 2004-12-27
forum: Gaming &amp; Leisure
---

### Post by Neo40 on 2004-12-27
Hi,

When I installed winex (or cedega) a few weeks ago, I was able to play starcraft just fine. Now, since 2-3 days, the game is very slow and not playable. I really don't know what I did wrong. I installed some packages here and there with apt-get but really dont know what could cause that problem. I really don't want to re-install Ubuntu just for a game! 

Anyone has an idea?

Thanks

---

### Post by kzetts on 2004-12-28
Did you pay for winex? or is there a repository i can find it at somewhere?

---

### Post by Neo40 on 2004-12-28
[QUOTE=Neo40]Hi,

When I installed winex (or cedega) a few weeks ago, I was able to play starcraft just fine. Now, since 2-3 days, the game is very slow and not playable. I really don't know what I did wrong. I installed some packages here and there with apt-get but really dont know what could cause that problem. I really don't want to re-install Ubuntu just for a game! 

Anyone has an idea?

Thanks[/QUOTE]


Well, I found the solution to the transgaming forum. Just add "nice -n 20" and the game runs perfectly! ;)
The complete command is:
nice -n 20 winex3 starcraft.exe

---

