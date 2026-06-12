---
title: "How to precisely resize windows in XFCE?"
date: 2014-03-31
forum: Desktop Environments
---

### Post by etsnyman on 2014-03-31
Hi!

Is there some way in XFCE (I have 4.10) to precisely resize windows by pixel numbers?

I want some exactly resized windows, e.g. 501x504 pixels, for some training videos that I want to capture.

I don't mind some command line wizardry, and I don't mind even getting hold of some patch that adds tooltip sizes if I resize with the mouse.

Thanks!

---

### Post by Toz on 2014-03-31
[xdotool]("http://manpages.ubuntu.com/manpages/saucy/man1/xdotool.1.html") will allow you to resize windows on the fly. For example, to resize an existing Mousepad window to 400x400 pixels:
```
xdotool windowsize $(xdotool search --name "Mousepad" | tail -1) 400 400
```

If you want to start a program with a specific size, you can use the **--geometry** or **-g** paramters if the application supports them, or use a tool like [devilspie]("https://help.ubuntu.com/community/Devilspie").

---

### Post by etsnyman on 2014-03-31
Thanks, Toz

Installing xdotool and running the command from a terminal worked perfectly. Now I can resize all the windows I need perfectly.

Thanks again

---

