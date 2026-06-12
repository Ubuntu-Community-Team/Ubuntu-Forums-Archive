---
title: "Terminal default size"
date: 2006-07-24
forum: Desktop Environments
---

### Post by LucidTaZ on 2006-07-24
Hey,

I don't know if this sounds like a stupid question, but I'm gonna ask it anyways.

I put a picture of my cute lil two kittens as a background of my gnome-terminal. But in order to view it properly I need to stretch the size of the window a bit. Could anyone tell me how to set new default sizes cause it resets each time I start the terminal?

Thanks.

---

### Post by ajgreeny on 2006-07-24
It's in sessions>profile in the kde konsole where you can set such things.  I have looked in the gnome terminal but can't find a similar way to set the size.  It must be possible somhow.

---

### Post by LucidTaZ on 2006-07-24
Yep that's what I thought. I looked around but couldn't find it.

Any more ideas?

---

### Post by 5-HT on 2006-07-24
There are a couple of options I can think of off the top of my head that may be of some help.

1) If you go into gnome-terminal's profile editor (right-click from the terminal) and change the font size, the window will resize as well. The settings will persist until you change them or use a different profile.

2) Call gnome-terminal with a specific geometry using the *--geometry=* flag (see 'man gnome-terminal'). If going this route, I would suggest making an shortcut/launcher/alias for gnome-terminal stipulating the desired geometry.

Hope that helps

---

### Post by LucidTaZ on 2006-07-24
The second step worked. Thanks! :)

For others who wanna do this:
```
$ gnome-terminal --geometry 100x24
```
Where 100x24 is my new window size.

---

