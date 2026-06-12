---
title: "Baldur's Gate 2 and Wine"
date: 2005-12-26
forum: Gaming &amp; Leisure
---

### Post by Wermut on 2005-12-26
Hello everybody! I'm trying to get Baldur's Gate 2 working.
First I tried it with Cedega... actually everything worked, but it was so slow that it was unplayable. Then I tried Wine and installed BG2 with the Loki installer. Now the performance is good, but there are two problems:
- no sound in the actual game (solved - I oversaw an error message)
- Wine does not hide the X mouse cursor
Any help would be appreciated.

I have an idea how to solve the second problem. It may be a kludge, but does anybody know how to set the mouse cursor for a xinit session?
My kludge is almost finished. I have a script that is supposed to run wine on a different display and make the cursor invisible:
xinit bg2 -- :1
xsetroot -display :1 -cursor ec ec
But the script waits for the first command being terminated before executing the second... How should I handle that?

---

