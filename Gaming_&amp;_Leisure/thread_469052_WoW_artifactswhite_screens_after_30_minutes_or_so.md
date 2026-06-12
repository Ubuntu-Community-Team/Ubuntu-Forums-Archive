---
title: "WoW artifacts/white screens after 30 minutes or so"
date: 2007-06-09
forum: Gaming &amp; Leisure
---

### Post by eqisow on 2007-06-09
Playing WoW in Wine runs at pretty much full speed. It's been very nice,. However, when I play after 30-45 minutes the screen goes mostly white with some artifacting. I can't even restart X with ctrl + alt + backspace. I have to do a hard shutdown.

I'm pretty sure the cards not overheating, though I'm working on eliminating that possibility. Does anybody have any other ideas? Does wine save it's errors to a text file anywhere?

---

### Post by Enverex on 2007-06-09
Wine doesn't create a log by default (it outputs everything to stdout/err) but you can make one yourself. Run the app like:

wine WoW.exe &> ~/Desktop/wow.log

Which will output everything from Wine into a file called wow.log on your desktop.

---

