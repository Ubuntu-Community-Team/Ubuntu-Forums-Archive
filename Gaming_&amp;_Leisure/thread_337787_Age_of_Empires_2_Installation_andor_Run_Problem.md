---
title: "Age of Empires 2 Installation and/or Run Problem"
date: 2007-01-13
forum: Gaming &amp; Leisure
---

### Post by FFfanatic on 2007-01-13
Just tried to install AOE2 using the latest wine and there are a couple of problems I'm getting. Firstly, when I install, it says that I don't have directplay 6.1a, I choose to continue anyways, then it says it installs dp6.1a and installs the program completely. Then when I try to run it, it doesn't give me a no cd error, it just starts up wine, then closes. I'm running edgy, fyi, so maybe it's a problem related to that?

---

### Post by kristjans on 2007-01-13
Whatever you do, it's probably not worth it - Age of Empires II is quite buggy on Wine anyways. I know quite a few people who stopped using Ubuntu for this very reason, and I'd like to get it working (multiplayer in Hamachi) smoothly also.

---

### Post by FFfanatic on 2007-01-13
> **kristjans said:**
> Whatever you do, it's probably not worth it - Age of Empires II is quite buggy on Wine anyways. I know quite a few people who stopped using Ubuntu for this very reason, and I'd like to get it working (multiplayer in Hamachi) smoothly also.

But on winehq it says that AOE2 has a gold rating, though I don't see how I'm doing anything different than normal. I insert the cd, run aoesetup.exe with wine, tells me I don't have directplay 6.1a so it installs it, finishes installing. Click play, wine/aoe quits. :-k

---

### Post by Enverex on 2007-01-13
You do need a NoCD patch despite it not complaining about missing the CD. Multiplayer currently does not work by default but will if you follow the instructions on this page - [http://wiki.winehq.org/DirectPlayGames?highlight=%28play%29](http://wiki.winehq.org/DirectPlayGames?highlight=%28play%29) . The menu is also slow to respond but does work. The actual "in-game" part of it is fine though.

So in short: Needs NoCD Patch, slow responding menu, needs dlls for multiplayer.

I have to add though, stopping using Ubuntu because AOE2 doesn't work seems very, very silly.

---

### Post by patrick295767 on 2007-01-14
> **kristjans said:**
> Whatever you do, it's probably not worth it - Age of Empires II is quite buggy on Wine anyways. I know quite a few people who stopped using Ubuntu for this very reason, and I'd like to get it working (multiplayer in Hamachi) smoothly also.

aoe2 : I used it both with cedega and cvscedega, and got it running better than with wine.
But it always depends on your config
  
try maybe this: [http://www.ubuntuforums.org/showthread.php?t=193814&highlight=cvscedega+automatic](http://www.ubuntuforums.org/showthread.php?t=193814&highlight=cvscedega+automatic)
i dont know if it works still ...

---

### Post by kristjans on 2007-01-14
> **Enverex said:**
> You do need a NoCD patch despite it not complaining about missing the CD. Multiplayer currently does not work by default but will if you follow the instructions on this page - [http://wiki.winehq.org/DirectPlayGames?highlight=%28play%29](http://wiki.winehq.org/DirectPlayGames?highlight=%28play%29) . The menu is also slow to respond but does work. The actual "in-game" part of it is fine though.

So in short: Needs NoCD Patch, slow responding menu, needs dlls for multiplayer.

I have to add though, stopping using Ubuntu because AOE2 doesn't work seems very, very silly.

I know that, but the Hamachi servers won't show up anyways. And it's not silly at all for people who play that game most of their free time. ;)

---

### Post by FFfanatic on 2007-01-14
I'm still a newbie to Ubuntu (how could you tell?) so I have one question. Where do I go to find the fake C: drive that wine makes, since that's where I need to patch the .exe?

---

### Post by christhemonkey on 2007-01-14
In:
```
cd ~/.wine/drive_c/ 
```

---

### Post by FFfanatic on 2007-01-14
What I should have said was, how do I get to it through using the mouse, since how am I going to replace the .exe with the patched one?

---

### Post by christhemonkey on 2007-01-14
You'll have to show hidden files in nautilus by typing Ctrl+H and then go to .wine 
there you will have drive_c etc.

---

### Post by FFfanatic on 2007-01-14
Yay!!!! Finding a terminal commands page and then copying to the files to ~/.wine/drive_c....... worked!!!!1 AOE2 is alive!!!!!!

---

### Post by linex on 2007-02-10
i'm having a similar problem, how'd u fix it?

i installed it and applied the patch, i get an error that reads "Could not initialize graphics system. Make sure that your video card and driver are compatible with DirectDraw."

---

### Post by Breepee on 2007-02-11
I also get that, with Star Wars Galactic Battlegrounds too (an AoE2 clone with a Star Wars jacket on).

---

### Post by linex on 2007-02-11
microsft has posted a solution to this problem at [http://support.microsoft.com/kb/242902](http://support.microsoft.com/kb/242902)
it has to do with altering the shortcut target but i don't know how to do that in linux. anyone have any idea?

---

### Post by Enverex on 2007-02-11
> **linex said:**
> i'm having a similar problem, how'd u fix it?

i installed it and applied the patch, i get an error that reads "Could not initialize graphics system. Make sure that your video card and driver are compatible with DirectDraw."

Just as it says, but you stick Wine on the front, i.e.

wine  "C:\Program Files\Microsoft Games\Age of Empires II\empires2.exe" nostartup

Obviously replacing the location with your location (but still using the Windows folder format). Second way of doing it is chdir'ing into the AOE2 folder then just "wine empires2.exe nostartup" which should work too.

---

