---
title: "MacSlow's cairo-clock does not look right on startup"
date: 2009-11-29
forum: Desktop Environments
---

### Post by Vertumnus on 2009-11-29
I put cairo-clock in the startup applications list. However, in the startup version of the clock, the shadow is cut off and the hands are off center. No one else seems to have posted about this problem. It only occurs at startup and does not happen when I start the clock manually. Any Ideas?  -V

---

### Post by evoka0 on 2010-07-15
Happens the same to me :(  in 32 bits

---

### Post by bobcollard on 2010-07-16
Instead of putting it in Startup Applications use the Cairo-Dock Congfig to "Launch Cairo Dock at Startup"  It's in Gmenu.

---

### Post by Vertumnus on 2010-08-30
Thanks, bobcollard. I am now using Cairo-Dock too and it works much better. For those who use MacSlow's cairo-clock without Cairo-Dock, I found that delaying the launch of cairo-clock at startup helps.

---

### Post by calande on 2011-03-08
Hi guys, same problem here. I don't use Cairo-Dock, just Cairo-Clock. Delaying didn't help:
> sleep 5s && cairo-clock
I doesn't even launch on startup... Any idea?
This is how my clock looks like if launched on startup with the regular command:
> cairo-clock
[http://i51.tinypic.com/dh91k3.png](http://i51.tinypic.com/dh91k3.png)
Thanks,

---

### Post by stinkeye on 2011-03-08
Try as the startup command
```
bash -c "sleep 5; cairo-clock"
```

---

### Post by calande on 2011-03-08
Thanks. Here's whan happens with the above command. The Gnome desktop remains empty for 5 seconds, then all icons, bars and applications show up, and the cairo clock shows up in the upper-left corner, cut by half. I doesn't remember the position I had set. Any idea? Thanks.

---

### Post by stinkeye on 2011-03-08
I've had this problem with cairo-clock.
To fix move it to the position you want and resize to your liking.
Then right click on cairo-clock and quit.
You may have to try numerous times before the quit dialogue comes up.

Quitting in this way seems to save the new preferences while other ways
keep the old preferences.

---

### Post by calande on 2011-03-08
Ok, thank you. I tried but with no success... I had a look at the man page and the following code works for me, with no delay launching the clock, simply running at startup:
```
cairo-clock --xposition 1125 --yposition 50 --width 127 --height 127
```

---

### Post by stinkeye on 2011-03-08
Ah ok, no probs.... got it working anyway. :D

FYI the preferences are @ **~/.cairo-clockrc **

---

### Post by calande on 2011-05-07
Hey guys, I upgraded to natty, and there's another problem :)
There is a white corner now:

[IMG]http://i53.tinypic.com/316av0k.png[/IMG]

Any idea?
Thanks,

---

### Post by stinkeye on 2011-05-07
Open your **~/.gtkrc-2.0** file.
```
gedit ~/.gtkrc-2.0
```

...add this and save.
```
style "default-style"
{
  GtkWindow::resize-grip-height = 0
  GtkWindow::resize-grip-width = 0
}

class "GtkWidget" style "default-style"
```

---

### Post by calande on 2011-05-07
Thanks! Problem solved :)

---

### Post by calande on 2011-05-08
I spoke too fast, now, the clock is *weird*:

[IMG]http://i51.tinypic.com/xgdag.png[/IMG]

Any idea?

---

### Post by stinkeye on 2011-05-08
Try quitting cairo-clock, delete your **~/.cairo-clockrc**
config file and restart cairo-clock.

---

### Post by calande on 2011-05-08
That was it :)
Thanks again!

---

