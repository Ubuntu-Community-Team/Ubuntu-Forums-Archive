---
title: "Compiz-Fusion, Yakuake, ALSA (possibly) Bug"
date: 2008-04-19
forum: Desktop Environments
---

### Post by Patriot1776 on 2008-04-19
Okay, I've found an issue where X will crash with Compiz-Fusion, Yakuake, and ALSA.

Here's what causes it:

Open Yakuake shell, enter mp3blaster to listen to music.

Start playing a song, and then open another Yakuake shell while the music is playing.

Close yakuake from NEW shell instance while music still going, X crashes and I'm back to the login screen.

THIS DOES NOT HAPPEN WHEN DESKTOP-EFFECTS/COMPIZ-FUSION IS NOT TURNED ON.

Any ideas?

---

### Post by erolosty on 2008-05-05
Its not a bug in alsa. I get the same issue when i use yakuake in compiz. Seems to happen on yakuake focus change (which I set to hide yakuake) when the command being run in yakuake is running. Def a bug but at least i can eliminate 1 of those 3 as a cause. Sorry I cant be of more help - drives me mad as well but i cant figure out whats going on. Hopefully someone else will read this (maybe edit the title to Yakuake+Compiz=X crash).

Edit:

Anyone else reading this with yakuake and compiz please take a sec to check if this is a bug.

-Open yakuake
-Run anything (anything!) that will continue to run (sudo apt-get update for example)
-before this process finishes open a new shell in yakuake then press F12 or click on something outside yakuake
-X will die

Edit:

Im using kde 3.5. I think I remember the author of yakuake switching to kde4 maybe we need some backports in our yakuake

---

### Post by Patriot1776 on 2008-05-05
I've now gotten my confirmation of it being a yakuake bug too as it's not happening anymore to me at all as of late.

---

### Post by erolosty on 2008-05-05
I have used yakuake for years and cant imagine kde without it. Im really glad I have found this thread as i never realised why X would die when I run compiz (yakuake gets used a lot). Did you switch to kuake or konsole or what did you do? I think Ill miss yakuake lots but I cant get by without my compiz-expose(scale) feature now. Hope the devs fix this. Can you change the title in hopes more people will read this. Ill file a big report in the morning and you could add to it

Edit:

[http://www.kde-apps.org/content/show.php?content=29153](http://www.kde-apps.org/content/show.php?content=29153)

I made a little hack that stops the crash from happening, the trade off is the animation when (un)focusing yakuake

---

