---
title: "Quake 2/Quake4 SE DVD Edition Install"
date: 2006-09-04
forum: Gaming &amp; Leisure
---

### Post by thx_1138 on 2006-09-04
Hello,
I got Quake 4 up and running great, but now as Iam almost done it I was wondering if anyone has had any luck getting Quake 2 up and working off the bonus DVD?, It says I cant even acess the contents of the disc, that I dont have the premission to do so. Is this because of the copy protection on the disc? I would'nt mind firing it up since I havent played Quake 2 since the days of windows 95 (shudders!) and I long since lost that install cd I used to own back then so thats not an option. I have recently seen a Quake Trilogy release for dirt cheap, I would buy that to play Q2, and possibly Q1, but if there is a way I can use the DVD I already have (not to mention the two expansion packs with it as well) I would love to use that instead(besides I paid good money for this game already).

thanks for any assistance possible

---

### Post by pharcyde on 2006-09-04
In order to mount the second disc try the following.
```
sudo -s
mount /cdrom
```
You essentially have to be root to mount the disc because they messed up the disc when they were manufacturing it.

---

### Post by artinla on 2006-09-04
I am not sure that it will work.  I tried not long ago and never could get Q2 to work.  Q3, Q4, UT, UT2004, HL2, Doom3, All the Medal of Honor Series (with Cedega) etc. work fine for me but Q2 never worked right.

I own the same Q4 DVD as you have, but I have also tried to get the game to work by copying a working W32 Q2 installation and applying the installer to it.  Still didn't work very well.  I remember that sound was a huge issue as well as some other significant hitches with OpenGL (it kept bitching that I had no openGL and/or the wrong version.  I finally decided that it wasn't worth the effort.


Art

---

### Post by billyfoxtrot on 2006-09-29
Not sure if you figured this out yet, but here's what you have to do to get access to the files (I'm going to assume you know how to actually install the game, or you can google it).

Insert the Bonus DVD and open a terminal.  Type:
```
sudo -s
cd /media
cp -r cdrom0/ ~/Desktop/.

```

then chmod the entire directory.  Hope this helps!

---

### Post by dmn_clown on 2006-09-29
All I did was copy the contents of the Install directory to my hardrive, installed the quake2 deb, edited the security warning out of the startup script, and away I went (IIRC).

---

