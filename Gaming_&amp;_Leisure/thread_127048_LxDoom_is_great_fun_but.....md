---
title: "LxDoom is great fun but...."
date: 2006-02-08
forum: Gaming &amp; Leisure
---

### Post by qwazert on 2006-02-08
Don't know if this is the right place for this thread...the moderator can move it if s/he desires...

I managed to get LxDoom installed and running...but how on earth do I change the screen size??
It's the size of a postage-stamp now and although I **could** play it, I don't think I could for too long!

Any suggestions? The usual SETUP program doesn't do much...

---

### Post by hentaidan on 2006-02-09
Try calling lxdoom with width and height specified:

lxdoom -width 800 -height 600

Dan

---

### Post by barisurum on 2006-07-11
The best way to use that type of "console run" programs is to create a runnable text file (like the Batch files in the good old dos days :)
  Here is how to create one for lxdoom:

  first create a text file in the directory you want to use it ex: home/yourhome/ or usr/bin

  [COLOR="Blue"]in the file write:

  ```
lxdoom -width 800 -height 600 -iwad /usr/share/games/doom/doom2.wad
```

  save the file as "doom" or whatever you like[/COLOR]

  [COLOR="Red"]On the same directory as the textfile run:

  ```
chmod +x doom
```[/COLOR]

  And run the file as:

  [COLOR="Red"]./doom[/COLOR] (on the same directory of if you copy it to "usr/bin" you can run wherever you want but you must be root to do that)

---

