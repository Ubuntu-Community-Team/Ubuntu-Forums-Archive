---
title: "Warcraft 3 problems"
date: 2007-08-05
forum: Gaming &amp; Leisure
---

### Post by xubu_caapn on 2007-08-05
Okay, I installed WINE yesterday to play Warcraft 3. At first it ran at very low fps, so I added "glx" and "dri"  as modules on xorg.conf. That fixed the problem, however it crashes often, and always when I'm on Battle.net, right when I join a game. There are also rendering problems with the units avatars and fog of war. I partially fixed this by setting "Particles" to medium, however it still flickers. Text is also choppy looking. I thought this might be because of a conflicting module on xorg.conf, so I uncommented everything except the aforementioned two and it still crashes. I tried Wine 0.9.42 and 0.9.39, same result with each. I'm calling it from my XP partition by the way, and this isn't on ubuntu but wolvix, not that it matters. There is very little documentation found on this so if anyone could help me, please do! I would post my wine config but it doesn't look like it's possible to easily, so if anyone wants to know anything from it I'll post.

---

### Post by vexorian on 2007-08-05
Do you use -opengl  on the command line?

like

```
wine ./war3.exe -opengl

```

That should deal with the rendering and performance issues

I have not experienced crashes in bnet so I am not sure how I could help. But if you are running from the windows partition it might need write access.

---

### Post by xubu_caapn on 2007-08-05
yes, i use the -opengl flag.. i guess i should've mentioned that. also, i have read and write permission to my xp partition.

---

### Post by xubu_caapn on 2007-08-06
can anyone help me? anyone else having this problem? for what it's worth, it crashes more often in windowed mode, especially if i focus another window.

---

### Post by vexorian on 2007-08-06
I think it is hard to solve this, since feedback on warcraft III in WINE is always good and can't find much reports on this, only thing I can say is that it could be issues with your graphic card's support on Linux.

So, what's left is experiment:
- try without -opengl
- try installing on Linux partition if possible (you'll need time and hard disk space)

It would be lame to have to dual boot a game that is supposed to work well on WINE, I am sorry I can't do more here.

---

### Post by Wiebelhaus on 2007-08-06
Try [Codeweavers]("http://www.codeweavers.com/")

---

