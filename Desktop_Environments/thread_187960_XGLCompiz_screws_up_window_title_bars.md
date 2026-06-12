---
title: "XGL/Compiz screws up window title bars?"
date: 2006-06-03
forum: Desktop Environments
---

### Post by jamyskis on 2006-06-03
Hi all,

First of all, Dapper rocks. It's still a little unstable in places, but I don't doubt that patches will be here for these issues soon.

Now, I have a question: I've managed to get an XGL session up and running, and I've managed to start Compiz just the way I want it (just the fade effects) but the problem is that whenever I start Compiz, the title bar of many programs in GNOME gets screwed up. Does anyone know if there's a way around this or if this is supposed to be a "feature"?

Cheers!

---

### Post by MetalMusicAddict on 2006-06-03
Can you be more specific than "screwed up"? Maybe a screenshot?

---

### Post by jamyskis on 2006-06-03
[QUOTE=MetalMusicAddict]Can you be more specific than "screwed up"? Maybe a screenshot?[/QUOTE]
Well, I think I've sorted it - sort of.

I found the very useful gset-compiz in the same repo as I found the newer version of Xgl and it's helped me to tweak Compiz in just the way I need it.

The problem is that some windows get opened without title bars when there should be title bars and this means that some windows can only be closed with ALT+F4. Still, as sod's law would have it, I can't reproduce the problem now.

If it comes up again, I'll post a shot of it here. 

Thanks again!

---

### Post by christhemonkey on 2006-06-03
Sounds like you didnt have a window decorater running.

If it occurs again, type into a terminal:
```
gnome-window-decorater & 
```

---

### Post by jamyskis on 2006-06-03
Well, it looks like it's running fine, albeit for games it's useless at the present. SDL games don't run very well under XGL at all, and OpenGL based games usually have missing textures thanks to XGL stealing all the graphics memory.

Still, a promising start for what looks to be a good future for Linux desktops.

---

