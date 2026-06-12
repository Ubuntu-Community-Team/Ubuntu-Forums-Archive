---
title: "Clearlooks shades?"
date: 2005-03-05
forum: Desktop Environments
---

### Post by hashimoto on 2005-03-05
Dear forum,

I'm running Hoary with Clearlooks theme, but the theme doesn't look exactly the same as here: [http://www.gnome-look.org/content/preview.php?preview=1&id=19527&file1=19527-1.png&file2=19527-2.png&file3=&name=Clearlooks](http://www.gnome-look.org/content/preview.php?preview=1&id=19527&file1=19527-1.png&file2=19527-2.png&file3=&name=Clearlooks)

Specifically I'm missing the nice 3D shades around the windows. How do I enable them? I just can't seem to find anything in the system preferences so this must be something that I got to configure in CLI, probably in X settings. What, where and how are the questions.

Sure, this does not affect the usability a bit. It's just something nice I would like to have. Thanks in advance!

---

### Post by Remm on 2005-03-05
You need to enable the composite x.org extension, and use xcompmgr for that (assuming you have a nvidia card, otherwise it's likely going to be too slow).

The metacity theme portion of Clearlooks does not work for me, so I don't get the fancy rounded windows #-o

---

### Post by paul cooke on 2005-03-05
[QUOTE=hashimoto]Dear forum,

I'm running Hoary with Clearlooks theme, but the theme doesn't look exactly the same as here: [http://www.gnome-look.org/content/preview.php?preview=1&id=19527&file1=19527-1.png&file2=19527-2.png&file3=&name=Clearlooks](http://www.gnome-look.org/content/preview.php?preview=1&id=19527&file1=19527-1.png&file2=19527-2.png&file3=&name=Clearlooks)

Specifically I'm missing the nice 3D shades around the windows. How do I enable them? I just can't seem to find anything in the system preferences so this must be something that I got to configure in CLI, probably in X settings. What, where and how are the questions.

Sure, this does not affect the usability a bit. It's just something nice I would like to have. Thanks in advance![/QUOTE]

It's an Xorg thing, not a Gnome thing.

See here

[http://ubuntuforums.org/archive/index.php/t-5520.html](http://ubuntuforums.org/archive/index.php/t-5520.html)

you need xcompmgr installing and optionally transset

they're both in Hoary universe... I haven't installed them yet myself... just about to try them myself :)

ps, you also need to have 3D working as you need to enable xrender accel

---

### Post by rosslaird on 2005-03-05
And yes, xcompmgr looks very cool (using "xcompmgr -fc &" or something similar), but it's buggy as a mosquito nest. It's also slow. If you like the drop shadow effect, you can get it nice and stable in xfce, which has its own composite manager (use the graphical installers from os-works).

As for transparency, that seems to work better (using transset) than shadows and fade-in/out of windows. But it's really a steep price to pay for a bit of eye candy: your X session will be a lot less stable.

---

### Post by hashimoto on 2005-03-05
OK, got it working. And it really seems buggy. My panel didn't came up on some occasions and when it did, it got stuck. Too high a price to pay for eye candy, as you said. Will try xfce later.

Thanks all!

---

