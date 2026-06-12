---
title: "DOOM III - screen resolution"
date: 2008-07-12
forum: Gaming &amp; Leisure
---

### Post by cjnkns on 2008-07-12
I just installed doom 3 on hardy. 

It starts up just fine and seems to work ok, but when exiting the game my system screen resolution doesn't get set back. Everything is huge like 800x600 or something.

---

### Post by Jim! on 2008-07-12
This probably wont work but its worth a try. When quitting instead of going into the Doom 3 menu to quit just press "~" and then type "quit" and then press enter. Don't know if it will work just a suggestion:)

---

### Post by cjnkns on 2008-07-12
Thanks for the suggestion, i tried it but that didnt' work either.
Not sure why this happens but it is quit annoying. :)

---

### Post by kdorf on 2008-07-12
I don't know what your computer specs are, but if you have a little bit of extra memory you could try launching Doom 3 in another X server. I actually do this for all my games -- it keeps your window manager from getting in the way along with preventing the resolution problem you're having. To do this, you need to change /etc/X11/Xwrapper.config to say "allowed_users=anybody" (instead of just console) -- but note that this is less secure from what I understand (don't know why - console users can just start their own X server anyways.)

Then, run the following in the console (or make a launcher for it):

```
startx /path/to/doom3 -- :1
```

When you exit Doom 3, it should punt you back to your original desktop. Or you can manually switch back with ctrl+alt+F7

---

