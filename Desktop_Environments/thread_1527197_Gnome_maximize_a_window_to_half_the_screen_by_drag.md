---
title: "Gnome: maximize a window to half the screen by dragging it to the left/right edge?"
date: 2010-07-09
forum: Desktop Environments
---

### Post by Kurtosis on 2010-07-09
KDE and Windows7 both have a nice feature/setting that lets you maximize a window to half the screen by dragging it to the left or right edge of the screen.

Does Gnome have anything similar?

Thanks!

Edit: Use Compiz Grid:

```
sudo apt-get install compiz-fusion-plugins-extra
```

---

### Post by bobcollard on 2010-07-10
Yes, set at Maximum, hold down Alt and drag the body of the application screen until you can adjust it accordingly.

---

### Post by chiliman on 2010-07-10
it didn't work perfectly for me because i might have conflicting compiz plug ins on or something.  but follow the instructions on this page and let me know if they work for you.

[http://www.omgubuntu.co.uk/2009/11/aero-snap-ubuntu-linux.html](http://www.omgubuntu.co.uk/2009/11/aero-snap-ubuntu-linux.html)

---

### Post by chiliman on 2010-07-10
after resetting compiz settings to default i got better results, but i think since i have GLX-dock running its conflicting with the compiz settings for the snap.

edit: ok after playing with it some more its works for me if edge trigger delay is set to 0 and increasing the delay breaks it sooo i would just give a try i think im gonna hang on to these settings now.

Edit: ok after playing wiht it some more it messed something up now i only have half a wallpaper... hmmmmm.. i guess its pretty glitchy

---

### Post by Kurtosis on 2010-07-10
> **bobcollard said:**
> Yes, set at Maximum, hold down Alt and drag the body of the application screen until you can adjust it accordingly.
Thanks, but not quite what I'm looking for.  That just changes the maximized window to whatever shape it was prior to being maximized and lets you drag it around.  

I want something that resizes the window to exactly one half of of a widescreen monitor, and places it on one side or the other.

---

### Post by Kurtosis on 2010-07-10
> **chiliman said:**
> it didn't work perfectly for me because i might have conflicting compiz plug ins on or something.  but follow the instructions on this page and let me know if they work for you.

[http://www.omgubuntu.co.uk/2009/11/aero-snap-ubuntu-linux.html](http://www.omgubuntu.co.uk/2009/11/aero-snap-ubuntu-linux.html)
Ah, Aero Snap is the term, thanks, that helps hugely!  I got those instructions working on 10.04, the only thing is that system changes the windows around even when you're not dragging them and are just moving the mouse alone.  But still the right track, thanks!

---

### Post by Kurtosis on 2010-07-10
Update:  Best solution so far is Compiz Grid:

```
sudo apt-get install compiz-fusion-plugins-extra
```

It uses mod key + numpad to position windows around the screen, instead of the mouse as Aero Snap does, but is easy to install and works as well or better (more placement options).

---

### Post by stinkeye on 2010-07-10
You can also use the commands in the tutorial chillman posted, and set them
to mouse gestures with easystroke.

---

### Post by demosthenese on 2010-07-10
> **stinkeye said:**
> You can also use the commands in the tutorial chillman posted, and set them
to mouse gestures with easystroke.

Or to corner actions using brightside

```
sudo apt-get install brightside
```

and set up with alt-f2 and brightside-properties

---

### Post by Kurtosis on 2010-07-12
I tried that, but the main problem is that that hack actually causes windows to change position when you move the mouse pointer to the edge of the screen, regardless whether you're dragging a window with it or not.  

That behavior was a little weird, prefer Compiz Grid instead, especially since Grid doesn't require the mouse in the first place.  That's even better than Aero Snap, imho, and comes close to tiling window managers in efficiency.

---

