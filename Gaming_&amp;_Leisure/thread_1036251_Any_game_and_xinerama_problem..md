---
title: "Any game and xinerama problem."
date: 2009-01-10
forum: Gaming &amp; Leisure
---

### Post by Blazr on 2009-01-10
Hi,

I have dual monitors and I use xinerama. With xinerama disabled neither of my monitors will function properly.

I have a problem with any game (for example nexuiz).
I load the game and it goes into fullscreen, but I can't move my mouse.

I read somewhere this was a problem with xinerama, is there a fix for this anywhere?

I am unable to play games and I cannot disable xinerama and its starting to annoy me :)

Thanks!

---

### Post by detrate on 2009-01-14
I had the same problem and switched to twinview to solve it.  I had to sacrifice using separate cards per monitor but twinview has been a more pleasurable experience (overall) for me.

You can change to it / use it by installing nvidia-settings.

```
sudo apt-get install nvidia-settings
gksudo nvidia-settings
```

if you haven't already (it can configure for xinerama as well).

---

### Post by Blazr on 2009-01-19
I don't see the option for twinview in nvidia-settings anywhere.

I attached a screenshot,anybody help me out?

and thanks for your help!

---

### Post by detrate on 2009-01-19
click the configure button in your screenshot.

---

