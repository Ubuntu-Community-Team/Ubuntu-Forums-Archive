---
title: "MPlayer -zoom"
date: 2006-03-19
forum: Desktop Environments
---

### Post by goober99 on 2006-03-19
I use mplayer to play videos. By default, full screen just surrounds the video with black bars. To actually get the video to scale, I have to launch mplayer from the terminal:

```
gmplayer -zoom
```

As you can imagine, this is tedious, and it does not allow me to just double-click a video file to play it. Is there a way to make -zoom permanent?

---

### Post by cilynx on 2006-03-19
look at your mplayer.conf either in your ~/.mplayer/ or in /etc/mplayer

To fix fullscreen on my systems, I just use

vo=xv

You can put it just about anywhere in the conf file.

Good Luck

---

### Post by goober99 on 2006-03-19
I have a savage video card and anytime I use xv it always messes up the picture, so I have to use x11. It plays fine in fullscreen mode even with x11. I'm just looking for a way to have -zoom enabled by default when using x11 also.

---

### Post by cilynx on 2006-03-19
add "zoom=1" to your config.

---

### Post by goober99 on 2006-03-20
Possibly I'm editing the config file wrong, but your suggestion did not work. Here's what I tried:

```
sudo gedit ./mplayer/gui.conf
```

In gedit, I added zoom=1 on the top line and saved. Then I ran mplayer. No scaling. I repeated my first step to open the config file in gedit. The line I had added was not even in the file anymore.

---

### Post by cilynx on 2006-03-20
Sorry to take so long on response...

Put the line in your ~/.mplayer/config

---

### Post by taurus on 2006-03-20
I believe it's "zoom=yes"...
```

echo "zoom=yes" >> ~/.mplayer/config

```

---

### Post by goober99 on 2006-03-20
Thank you so much. Actually either "zoom=1" or "zoom=yes" works!

---

