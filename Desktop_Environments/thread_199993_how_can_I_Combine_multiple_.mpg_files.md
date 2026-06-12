---
title: "how can I Combine multiple .mpg files"
date: 2006-06-19
forum: Desktop Environments
---

### Post by theSlyph on 2006-06-19
(Hopefully with a gui!) I might even have the program and dont realize it, but i have not figured out how to combine mgp.001,mpg.002++ with any of the tools i have installed. i have mplayer and full media playback, would just like to know how.

Thanks.

---

### Post by kb3hkg on 2006-06-19
all else fails you can use a video editor like cinelerra or kino and combine them that way.

---

### Post by aysiu on 2006-06-19
There may be a GUI for this--I don't know--but there's definitely a command-line tool. Assuming that all the mpgs you want to combine are on your desktop and in the right order (name-wise), and that [you have the Universe repository enabled](http://www.psychocats.net/ubuntu/sources): ```
sudo aptitude update
sudo aptitude install mpgtx
cd ~/Desktop
mpgjoin *.mpg
```

---

