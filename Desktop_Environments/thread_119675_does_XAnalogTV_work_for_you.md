---
title: "does XAnalogTV work for you?"
date: 2006-01-20
forum: Desktop Environments
---

### Post by Bou on 2006-01-20
Hi, looking for a good screensaver I found XAnalogTV, which I immediately loved. Unfortunately, after a few seconds on it just freezes seemingly without a cause. So, can anyone test if this happens to you, too?

I would really like to get XAnalogTV to work.

Cheers guys.

---

### Post by encompass on 2006-01-20
Works for me... are you using any accellaration... like opengl?

---

### Post by Bou on 2006-01-20
Hmmm I think so, but how can I check it for sure?

Thanks, BTW :)

EDIT:

I went to /usr/lib/xscreensaver and launched the program from there. The problem seems to be when dealing with some pictures, because this is how it works:

-It seems to load a certain number of images from your image folder.
-It cycles them with various effects.
-When you click, it changes image and effect.

Well, sometimes I click a lot of times without it crashing (guess that's because it can deal with all the loaded pictures), but others it crashes at the third, second... first image.

> david@frandavid100:/usr/lib/xscreensaver$ ./xanalogtv
Aborted
david@frandavid100:/usr/lib/xscreensaver$

---

### Post by encompass on 2006-01-23
Good testing.... have you tried just letting load your screenshot rather than all the images.  That would be a good check too.  Perhaps it has trouble with some of the file types and freaks.  screensaves are always tough to debug cause they are built to still save your screen when they don't work... if I am not mistaken... sometimes you can even set it so that is xscreen... has an error is will display it...

---

### Post by Bou on 2006-01-24
[QUOTE=encompass]have you tried just letting load your screenshot rather than all the images.[/QUOTE]

Yep, just tried that, with the same results. I think the problem is not with the images, but rather with one of the effects it applies.

Guess I should file a bug, but I don't know who to send it to. Does it really work for everyone but me? :confused:

---

### Post by PuNGS on 2006-01-24
Well, for me it works normally.

---

### Post by encompass on 2006-01-25
Actauly, no, at least I thought it did... but not anymore.
It is a pretty Hardware instence Screener.
YesFile a bug.  Personally I would go straight to the website of the screensaver if any and report it there... if not there then xscreensaver and up from there.  Be VERY descriptive.

---

