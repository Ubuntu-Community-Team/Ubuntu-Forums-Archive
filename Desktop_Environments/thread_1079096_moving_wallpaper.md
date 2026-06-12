---
title: "moving wallpaper"
date: 2009-02-24
forum: Desktop Environments
---

### Post by snowman12 on 2009-02-24
is it possible to set a movie/video file as your desktop wallpaper?
and if so what do you need to do?

thanks in advance.

---

### Post by MedianMajik on 2009-02-24
You'll need Compiz in order to do this.  A quick google search shows other have done it.  I'm not the best person to help you with this question, but there are many who can.

---

### Post by snowman12 on 2009-02-24
ok so googled for a bit found this:[http://www.ubuntu-unleashed.com/2008/04/howto-loop-movie-or-video-as-desktop.html](http://www.ubuntu-unleashed.com/2008/04/howto-loop-movie-or-video-as-desktop.html) 
works fine......but when i tried to change the screensaver with this:
```
nice -n 15 ./xwinwrap -ni -o 0.20 -fs -s -sp -st -b -nf -- /usr/lib/xscreensaver/glmatrix -root -window-id WID
```
I got this:
```
nice: ./xwinwrap: Permission denied
```

---

### Post by waltons_pacman on 2009-02-24
you need to execute the command with the "sudo" preference.

the line should read:
```
sudo nice -n 15 ./xwinwrap -ni -o 0.20 -fs -s -sp -st -b -nf -- /usr/lib/xscreensaver/glmatrix -root -window-id WID
```

---

### Post by snowman12 on 2009-02-24
same error still comes up

---

