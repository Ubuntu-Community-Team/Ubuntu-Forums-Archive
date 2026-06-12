---
title: "totem can't play videos although w32codecs is present"
date: 2006-07-27
forum: Desktop Environments
---

### Post by mrhonne on 2006-07-27
Right after I've installed Dapper, I used EasyUbuntu to play videos via totem-xine and w32codecs. Everything was fine and I was happy.

But a few days ago things changed: totem refuses to play videos and is making stupid comments that he doesn't support video-codecs like the popular "DivX 5" or "Microsoft MPEG-4 v3". Totem doesn't even play videos which it played earlier flawlessly!

As a consequence I installed vlc and that player has no problem playing my videos.

I don't know what caused the strange behaviour of totem, I can only guess that it is connected with an automatical update of w32codecs. A few days ago (I checked in the history of synaptic) w32codecs was updated from 20050412-1plf4 to 20060611-1plf1. It was just about in these days that totem started to refuse its work (but I'm not quite sure). Unfortunately I couldn't confirm this, because I wasn't able to find the older package of w32codecs.

Does anybody had the same experience? Or better: does anybody know a solution? (I know I can use vlc instead and maybe I'll have to, but I prefer totem - maybe because of its simpler gui)

---

### Post by mrhonne on 2006-07-28
I found a solution to this problem: It's not the fault of w32codecs, but libxine-main1!

After replacing the package libxine-main in the version 1.1.1+ubuntu2-7.2 (from the dapper security repository) with the older version 1.1.1+ubuntu2-7 (from the dapper repository), totem plays videos as it should.

UPDATE: Is not quite right, totem still refuses to play divx5. After updating to 1.1.1+ubuntu2-7.2 the behaviour of totem doesn't change to total refusal again. So I can still view movies except divx5. This problem is getting more and more mysterious :confused:

---

