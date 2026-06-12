---
title: "Cairo-Clock + Beryl + Automatic Startup = :("
date: 2007-05-29
forum: Desktop Effects &amp; Customization
---

### Post by Hexydes on 2007-05-29
Ok, I am trying to get Cairo-Clock to load automatically on login. I added it into the startup list. It starts up. The problem is, Beryl loads after it, which for some reason makes Cairo-Clock disappear, and I can't get it to show back up again (Avant Window Navigator does something similar, but I just click on it and it fixes it).

Now, I tried changing the startup order (assigned Beryl-Manager priority 40 and Cairo-Clock priority 80), but they loaded in the same order. I went and looked, and the settings didn't keep (some searching on the web shows this was a problem in Edgy, and might again be a problem in Feisty, which is what I'm on).

Thoughts on how to get this working? I like Cairo-Clock, but I don't fancy the idea of having to manually load it every time I login. :(

---

### Post by NikoC on 2007-05-29
Perhaps you can write a small script for cairo-clock which delays the startup of the clock let's say with 5 seconds...

Perhaps [this]("http://ubuntuforums.org/showthread.php?t=369961") thread can help you... it worked for me, though it is intented for gdesklets use!

---

### Post by Hexydes on 2007-05-29
Cool, I will look into this, thanks!

This seems like a really simple fix. Ubuntu devs need to get on this. :(

---

### Post by Hexydes on 2007-05-30
Any other, more "official" ideas here...?

---

