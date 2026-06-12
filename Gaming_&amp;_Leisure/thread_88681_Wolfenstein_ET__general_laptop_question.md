---
title: "Wolfenstein ET / general laptop question"
date: 2005-11-10
forum: Gaming &amp; Leisure
---

### Post by Copter on 2005-11-10
hi!

i could not decide where to put this post - gaming or laptop section. ive installed ET on LG GS50 laptop. when setting video to fastest (640x480) it runs flawlessly (Intel 852GM/855GM video inside :(). bad thing is that it runs in semi-full-screen mode. resolution is 1024x768 (black background) with the game in 640x480 _box_ in the lower left corner of the screen. how to fix it?

i had similar problem with mplayer - it did not rescale movies to the full screen. but when i changed video driver (in mplayer config) from x11 to xv the movie was resized.

how to do the same thing in ET?

thnx 4 help!

btw. my 100th post :D

copter :]

---

### Post by daller on 2005-12-02
Do this:

Goto a console, and execute:

```
xrandr
```

This will show you a list a screen-resolutions, something like this:

```

daniel@ubuntu:~$ xrandr
 SZ:    Pixels          Physical       Refresh
*0   1680 x 1050   ( 331mm x 212mm )  *60
 1   1400 x 1050   ( 331mm x 212mm )   60
 2   1280 x 1024   ( 331mm x 212mm )   60
 3   1440 x 900    ( 331mm x 212mm )   60
 4   1280 x 960    ( 331mm x 212mm )   60
 5   1280 x 800    ( 331mm x 212mm )   60
 6   1280 x 768    ( 331mm x 212mm )   60
 7   1024 x 768    ( 331mm x 212mm )   60
 8    800 x 600    ( 331mm x 212mm )   60   56
 9    840 x 525    ( 331mm x 212mm )   60
 10   700 x 525    ( 331mm x 212mm )   60
 11   640 x 512    ( 331mm x 212mm )   60
 12   720 x 450    ( 331mm x 212mm )   60
 13   640 x 480    ( 331mm x 212mm )   60
 14   640 x 400    ( 331mm x 212mm )   60
 15   640 x 384    ( 331mm x 212mm )   60
 16   512 x 384    ( 331mm x 212mm )   60
 17   400 x 300    ( 331mm x 212mm )   60   56
 18   320 x 240    ( 331mm x 212mm )   60

```

What you should do now is this:

Find the shortcut to ET, and edit it to fit this:

```
xrandr -s 11;THE_ET_LINK;xrandr -s 0
``` 

(Where "11" and "0" are the resolutions "before" and "after")

The thing it does, is to put your display into the desired resolution, it executes the games, and the rest of the command is not executed before the games times out (is closed)

Good luck!

---

### Post by Copter on 2005-12-15
thnx for reply! although my computer is a laptop so...
```

copter@xidge:/etc/ivman$ xrandr
 SZ:    Pixels          Physical       Refresh
*0   1024 x 768    ( 347mm x 260mm )  *60
Current rotation - normal
Current reflection - none
Rotations possible - normal
Reflections possible - none
```not good after all. i knew that i cant change resolution but i thought that i can rescale the screen just like xv driver in mplayer does.

thnx anyway :)

copter :]

---

### Post by knubbe on 2006-01-08
[QUOTE=Copter]i knew that i cant change resolution but i thought that i can rescale the screen just like xv driver in mplayer does.
[/QUOTE]

I have exactly the same problem. If anyone else knows a solution id be a very happy man :-)

Sincerely

---

### Post by knubbe on 2006-01-08
[QUOTE=Copter]
how to do the same thing in ET?
[/QUOTE]

OK. I solved this by:

1) Upgrading the kernel to 686 optimized from 386.
2) Installing new drivers.

Easy step-by-step guide: [Instructions]("http://www.ubuntuforums.org/showthread.php?t=75393")

(change the savage driver to the new intel driver)
Where you download the driver: [http://dri.freedesktop.org/snapshots/]("http://dri.freedesktop.org/snapshots/")

I use 20060107. ET in fullscreen is nice :-)

---

### Post by TheHighChild on 2006-01-25
Sorry to bump old threads and it may be a shot in the dark for these folks but try pressing 

alt + enter

Should bring you to a full screen ET display.  I use it as a screen minimizer. WHen the screen is in windowed mode, press the tilde(~) and you can navigate to other windows. Just remember, when a new map loads, the console in ET closes up and you won't be able to move your mouse or alt + tab through other windows. Just press your tilde(~) again and despite the window not having focus, it will bring down the console.

/ETaholic, playing on an IBM T42 from work.

---

