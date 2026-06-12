---
title: "Enemy territory and monitor resolution"
date: 2011-11-22
forum: Gaming &amp; Leisure
---

### Post by badnack on 2011-11-22
Hi at all, i hope this is the right section to post my question, i was reading the others but there isn't any section for videogames:)
I've an annoying issue with enemy territory and ubuntu 11.10; whatever resolution i set the game has showed in a normal window (no fullscreen) or if i want to use fullscreen the game is in 4:3 (only using resolution 1024x768)  with two big  black bands on the sides.
If i try to increase the resolution or by setting mine in the config file; the game still returns in a common window.
I've tried to do: glxinfo | grep rendering and the result is rendering: Yes
So, where can be the issue, how can i fix this?

---

### Post by digithal on 2011-11-22
Open console in-game and type
```
r_customwidth "1366"
r_customheight "768"
r_mode "-1"
```
Just change the width and height values with the resolution you want to set. :)

---

### Post by lisati on 2011-11-22
*Thread moved to **Gaming & Leisure**.*

---

### Post by badnack on 2011-11-23
Thank you:) I've already tried to set my resolution in the config file, but i didn't know that was needed set the value -1.
Now all work well:)

---

