---
title: "WoW crashes (again)"
date: 2007-04-19
forum: Gaming &amp; Leisure
---

### Post by lakersforce on 2007-04-19
Lately I have been experiencing a awful lot of crashes when playing WoW. It began since the new patch. Basically the game freezes and the sound keeps playing. Have anyone else been having this problem?


Btw. do you love Ubuntu? If you do, go and show your love here: [http://ubuntuforums.org/showthread.php?t=413741](http://ubuntuforums.org/showthread.php?t=413741)

---

### Post by justin whitaker on 2007-04-19
> **lakersforce said:**
> Lately I have been experiencing a awful lot of crashes when playing WoW. It began since the new patch. Basically the game freezes and the sound keeps playing. Have anyone else been having this problem?


Btw. do you love Ubuntu? If you do, go and show your love here: [http://ubuntuforums.org/showthread.php?t=413741](http://ubuntuforums.org/showthread.php?t=413741)

What hardware? I'm guessing a video driver issue...the game is still running but isn't rendering. ATI? 

One thing you could try is try downloading a demo of Crossover office, and try running WoW.exe using that. I run WoW:TBC via Crossover, and not an issue yet....although I run an older Nvidia, and vanilla hardware.

---

### Post by lakersforce on 2007-04-19
No it is not a video-driver issue. Trust me, everything is setup fine. I have been playing on ubuntu only for +6 months. The problem is that WoW, after running fine for several months suddenly started crashing very often after the newest patch (at least after I got 2.0.10...I updated to it recently after not having logged in in about one month)

EDIT: It is patch 2.0.12, not 2.0.10

---

### Post by justin whitaker on 2007-04-19
> **lakersforce said:**
> No it is not a video-driver issue. Trust me, everything is setup fine. I have been playing on ubuntu only for +6 months. The problem is that WoW, after running fine for several months suddenly started crashing very often after the newest patch.

Seems you are not alone: [http://appdb.winehq.org/appview.php?iVersionId=6482](http://appdb.winehq.org/appview.php?iVersionId=6482)

Looks like there is an OpenGL bug. I can't get to it from work (blocked by Websense) but check the WoW wiki for a fix: [http://www.wowwiki.com/Linux/Wine](http://www.wowwiki.com/Linux/Wine)

---

### Post by lakersforce on 2007-04-19
I have seen people diagnosed the same problem as me on forums.wow-europe.com, but if it really is the same problem is hard to tell. But most users there post their problems from Windows. I would like to hear if Ubuntu users have experienced the same. Allow me to narrow the problem down:

After running WoW for a couple of minutes it randomly crashes.
The crash is kind of identical to what happens when you press the exit button. The sound keeps playing, so the game is not completely crashed. My desktop still works and I can kill the proces. When I run the game from Windows, almost excactly the same thing happens. The game runs for a couple of minutes then crashes. The only difference being that on Windows I return to the desktop and the sound stops automatically. No error messages are printed either in Windows nor Ubuntu.

---

### Post by justin whitaker on 2007-04-19
> **lakersforce said:**
> I have seen people diagnosed the same problem as me on forums.wow-europe.com, but if it really is the same problem is hard to tell. But most users there post their problems from Windows. I would like to hear if Ubuntu users have experienced the same. Allow me to narrow the problem down:

After running WoW for a couple of minutes it randomly crashes.
The crash is kind of identical to what happens when you press the exit button. The sound keeps playing, so the game is not completely crashed. My desktop still works and I can kill the proces. When I run the game from Windows, almost excactly the same thing happens. The game runs for a couple of minutes then crashes. The only difference being that on Windows I return to the desktop and the sound stops automatically. No error messages are printed either in Windows nor Ubuntu.

Yeah, I had that problem before, but I never actually fixed it: I moved over to Crossover, and it worked. I'm still thinking either something hardware related, since it's happening on Windows as well, or a bad patch. Did you run the repair on either Ubuntu or Windows?

---

### Post by lakersforce on 2007-04-19
> **justin whitaker said:**
> Did you run the repair on either Ubuntu or Windows?

OFC, appreciate the response :)

Are anyone else experiencing this?

---

### Post by Ferrat on 2007-04-19
Do you mean the PTR? the test is somewhat instable.

---

### Post by lakersforce on 2007-04-19
Not PTR. This patch:

```
WoW-2.0.10.6448-to-2.0.12.6546-enGB-patch.exe
```

---

### Post by donoman on 2007-04-22
Can crossover office trial be used for more then 30 days O_o?

---

