---
title: "how do i configure video output to gl2 in mplayer?"
date: 2006-06-04
forum: Desktop Environments
---

### Post by copey02 on 2006-06-04
mplayer plays my videos extremely slow while running xgl, and i read in the forums that switching to gl2 could help but i cant figure out how to do that. i'm a complete linux/ubuntu noob. been running it only for about 4 days now. thanks alot.

---

### Post by mattkenn4545 on 2006-06-05
Gfx wise what are you running and what method did you use to setup xgl/compiz?

---

### Post by copey02 on 2006-06-05
i have GeForce MX 420 and i used the xgl HOWTO on these forums.

---

### Post by mattkenn4545 on 2006-06-05
is that the thefuture method or are you using quinn repository to get the newest version

---

### Post by angkor on 2006-06-05
[QUOTE=copey02]mplayer plays my videos extremely slow while running xgl, and i read in the forums that switching to gl2 could help but i cant figure out how to do that. i'm a complete linux/ubuntu noob. been running it only for about 4 days now. thanks alot.[/QUOTE]

you can try a video with:

```
mplayer -vo gl2 (name-of-video)
```

If this improves your playback you can add it to the mplayer config file:

```
gedit .mplayer/config
```

just put vo=gl2 in the file and save it. Mplayer will now use this video output by default.

I don't think it is really going to improve playing videos full screen since you need a very powerful graphics card to run videos full screen on xgl.

---

