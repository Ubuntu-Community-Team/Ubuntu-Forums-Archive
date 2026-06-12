---
title: "Counter Strike 1.6 on Lenovo T61"
date: 2015-09-09
forum: Gaming &amp; Leisure
---

### Post by Rumbl3 on 2015-09-09
Just curious if anyone has a pointers for me. Been away for a while from linux and computers in general lol. Got the itch and picked up a old laptop Lenovo T61 tossed a SSD in it. Anyway gaming on Counter Strike 1.6 works decent but performance wise I seem to only be able to get about 30fps. Just seems like for such a old game I should be able to pull more fps out of it? Or maybe I'm putting to much faith in Intel gma 965 lol. 

Just curious if there is any new drivers (that are not showing up) or things I can try to increase my performance? I tried lowering resolution and stuff but didnt seem to have any effect at all. 

Thanks good to be back.

---

### Post by mörgæs on 2015-09-09
Let's see a hardware description. Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by tgalati4 on 2015-09-09
Those old Thinkpads are business machines and generally have crappy graphics cards.  The exception are the "p" models like the T43p and T61p.  They have an upgraded graphics card such as a ATI FireGL.  Don't get too excited.

Install glxgears and post your framerate.

```
sudo apt-get install glxgears
glxgears
```

Control-C to quit.

---

