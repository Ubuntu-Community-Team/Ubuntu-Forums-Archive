---
title: "Diablo 2  insert play disc problem"
date: 2006-09-06
forum: Gaming &amp; Leisure
---

### Post by heretic9 on 2006-09-06
I'm on kubuntu dapper,I've installed diablo 2 using wine from the official wine repo. Install went through fine as did the update to the latest version but when attempting to launch diablo I get a message asking for the play disc. Figured it was a copy protection error so downloaded a nocd crack from megagames and replaced the game.exe. Same issue. This is what happens when attempting to launch diablo

```

wine game.exe
fixme:advapi:SetSecurityInfo stub

```

Then a dialog box asking for the play disc pops up.

I've installed it using the windows 2000 profile for wine and have made sure that my cd drives are listed in winecfg.

Not sure what i'm doing wrong. Anyone else have this problem?

---

### Post by Niko38752 on 2006-09-08
I had this same problem. It can be fixed by copying a file called d2music.mpq from the play disc to the directory you installed it into.

---

### Post by Kilz on 2006-09-08
> **heretic9 said:**
> I'm on kubuntu dapper,I've installed diablo 2 using wine from the official wine repo. Install went through fine as did the update to the latest version but when attempting to launch diablo I get a message asking for the play disc. Figured it was a copy protection error so downloaded a nocd crack from megagames and replaced the game.exe. Same issue. This is what happens when attempting to launch diablo

```

wine game.exe
fixme:advapi:SetSecurityInfo stub

```

Then a dialog box asking for the play disc pops up.

I've installed it using the windows 2000 profile for wine and have made sure that my cd drives are listed in winecfg.

Not sure what i'm doing wrong. Anyone else have this problem?

Playing on Battelnet with a nocd crack can lead to your keys being banned. You may want to stop trying if you play a lot. I have been a Diablo 2 player since the 1.09 patch. I could never get the game to play with Wine. The $15 bucks I payed to get Cedega were money well spent. Its click, click , install, play for a lot of games. Diablo 2 is one of them.

---

### Post by nielz on 2006-11-01
This may sound a bit silly, but I have to mount the disc (no automounter, didn't come with xubuntu I guess) or else I'll get the same message. 

D2 worked out of the box for me though (besides having to tell wine to go fullscreen using XRandr and the mounting issue, which wasn't apparent until I moved to xubuntu).  

(All thanks to Kilz his nice little wine on amd64 script <3)

---

