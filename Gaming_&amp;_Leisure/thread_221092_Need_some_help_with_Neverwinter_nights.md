---
title: "Need some help with Neverwinter nights"
date: 2006-07-22
forum: Gaming &amp; Leisure
---

### Post by vem0m on 2006-07-22
ok heres the deal it installed fine but...... i have a 14" monitor(yea its small) and a max resolution of 1024x768 but when i run the game i hear it running but i cannot see it due to the resolution it runs in being to high. i tried changing it in an ini file that had something to do with resolution but it did not work. can someone help me with this? how can i get it to load in a lower resolution?

---

### Post by mlind on 2006-07-22
Try modifying nwn.ini like this
```

[Display Options]
RefreshRate=0
BitsPerPixels=32
[B]Height=600
Width=800
[/B]TexturePack=3
#FullScreen=1
**FullScreen=0**

```

---

### Post by vem0m on 2006-07-22
still loads full screen and wrong resolution :(

---

### Post by mlind on 2006-07-22
> **vem0m said:**
> still loads full screen and wrong resolution :(

I dunno. I just tried modifying nwn.ini myself and it works, even runs on windowed mode. Are you launching game using nwn script ?

---

### Post by vem0m on 2006-07-22
yep as if i try to do a straight nwmain bin file it don't work

---

### Post by mlind on 2006-07-22
Does 3D acceleration work fine? **glxgears** works?

---

### Post by vem0m on 2006-07-22
yep as i said i have a small monitor and i think its just trying to load up to big

---

### Post by vem0m on 2006-07-22
ok so i loaded it up with another monitor and entered my cd keys changed it to a 1024x768 resolution thu the ingame options then i edited the ini file to read

RefreshRate=60
as it was a =0 which was flickering and the such so its all better now thx to all those who tried :D

---

