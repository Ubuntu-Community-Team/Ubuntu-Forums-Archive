---
title: "Tuxguitar (with timidity) locks the sound."
date: 2008-12-15
forum: General Help
---

### Post by pPrdrm on 2008-12-15
I want to use Tuxguitar along with a media player playing but Tuxguitar seems to lock the sound for it self. If I run Tuxguitar first no other app can play sound (not VLC, Totem, Audacious etc.). If I start another app first then Tuxguitar don't have sound. I think it has to do something with timidity because if I run this command: **timidity -iA -Os** and configure Tuxguitar to use the new port that it suggests then I can have sound in all apps. But the thing that bothers me, besides the fact that I have to run this command every time I want to use Tuxguitar, is that by default timidity is set to run at startup with these options: **timidity -iAD -Os**. So running timidity again gives me two instances of timitidy. Why should I have two instance of timidity when I only need one. Any suggestions about how to solve these and make it run at startup?

---

