---
title: "Garry's Mod (aka Gmod) fails to start after PC reinstall"
date: 2015-03-10
forum: Gaming &amp; Leisure
---

### Post by CaptainMikeRak on 2015-03-10
I recently re-installed Ubuntu (also encrypted my HDD if that makes any change to this problem) to my PC (also completely wiping MS Windows), and now Gmod (using Steam for Linux [not virtualized or run via Wine]) isn't able to start at all. Prior to re-installing Ubuntu, my PC was dual booted with Windows 7 Professional and was not encrypted and Gmod worked fine. Now I cannot start the game all the way up.

Most of the time, after hitting play, nothing happens at all. Sometimes it will start up and show a totally blue screen with the text "Loading..." in the bottom right then immediately fails. I've re-installed Gmod several times to no avail. I also have other Steam games (Portal 2, Portal, & FEZ) and there appears to be no issues there.

I've tried to do research on this but came up with almost nothing. The most I found was that it might be something to do with 64-bit systems and to try this command in the terminal:
```
sudo apt-get install ia32-libs-multiarch
```
I've tried that and it displayed that it couldn't find that.

Any help would be appreciated since me and my friends tend to play this together a lot and now I'm down for the count.

---

### Post by stan16 on 2015-03-10
Hey, My wee nephew also had this problem today. This appears to be a Game Developer issue and not an issue with you're PC or installation. The root almost certainly seems to be the update to Garry's Mod received last night(9/3/2015) (or 3/9/2015 if State side).

[http://steamcommunity.com/app/4000/discussions/1/617329920708368669/](http://steamcommunity.com/app/4000/discussions/1/617329920708368669/)

But if there is a work around am all ears :) Hope this is a bit of help(If not great help!)

---

### Post by CaptainMikeRak on 2015-03-10
Thank you for finding that stan16! It appears that you are correct that it *is *related to to an update that occurred at the time I re-installed. This is both good and bad news in the sense that it proves my PC is fine, but it's bad since that means not just me, but tons of Linux users cannot use Gmod ATM because of this. So now the questions are: Does anyone know a way to circumvent this issue, and/or does anyone know when Valve will fix this?

---

### Post by CaptainMikeRak on 2015-03-11
Does anyone have an idea what the source of the problem might be so we can at least attempt a solution?

---

### Post by lampface on 2015-03-12
i would say Garry will fix it soon like maybe next month;)

---

### Post by CaptainMikeRak on 2015-03-13
I guess it's probably true that Garry pays next to no attention to the Linux users isn't it? Guess it's back to mindlessly replaying Portal 2 over and over again. lol

---

### Post by lampface on 2015-03-15
so true yet so sad

---

