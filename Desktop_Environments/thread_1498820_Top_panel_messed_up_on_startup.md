---
title: "Top panel messed up on startup"
date: 2010-06-01
forum: Desktop Environments
---

### Post by RoyalPie717 on 2010-06-01
[http://img691.imageshack.us/img691/9281/screenshotth.png](http://img691.imageshack.us/img691/9281/screenshotth.png)
I just started up Ubuntu and I noticed my top panel is messed up, see the screen shot. I was downloading a handful of application before. Is there a way to fix this?

---

### Post by moongia on 2010-06-01
look like your missing your notification area,and you have 2 indicator applets..add the notification applet by right clicking on the top panel and add to panel..when added middle click and hold it to movie it were ever,,then lock it..try removing one of the indicator applets...may need to log out and back when done..hope this helps...

---

### Post by moongia on 2010-06-01
i think its an "indicator applet session" you have 2 of

---

### Post by petehild on 2010-09-29
I have the same problem with Ubuntu 10.04 (happens on both 32bit and 64bit) did you find a way to fix this?

It does not happen all the time maybe 1 out of 10 times when I boot up. When I logout and in again, it's fixed.

I hope someone has an idea. What outputs and logfiles would you guys need?

Thanks.

Pete

---

### Post by roggenschrotbrot on 2010-09-29
i had a messed up panel configuration before, best is to
[LIST=1]
[*]add a new panel
[*]move you applets
[*]delete old panel
[*]move new panel to wherever you want it
[/LIST]

---

### Post by petehild on 2010-09-29
Thanks for you input an the problem :)
By searching some more I found another solution:

If you run the following:
```
# gconftool --recursive-unset /apps/panel && killall gnome-panel
```
The panel gets set back to the ubuntu default (all your changes are gone) and restarted. Lets see if this fixes the problem once and for all :)

---

### Post by petehild on 2010-10-05
Well it didn't fix the problem all together, the messed up bar still shows up once in a while. For now I just restart the gnome-panel if it's messed up.

```
killall gnome-panel
```

No real fix, but it works...

Pete

---

### Post by glitch323 on 2010-10-05
I have seen this before on my computer too.  It only does this every once in a while, so I use the ctrl+alt+backspace to reset X and it seems to fix it.  That may be overkill, but it's a quick fix.

---

### Post by Firem4nJoe on 2011-03-11
killall works for me :)

---

### Post by tgrego on 2011-12-20
have the same problem....
every time I boot the system, the top panel is messed up.
I need to kill gnome-panel every time I boot to fix it...

Is there any fix someone found? or at least a quick way to restart the gnome-panel automatically right after boot so that i don't have to bother with it?

cheers

---

### Post by kodb on 2011-12-26
I am having the same issue intermittently (but frequently) on 2 of our office machines.
All the clients are the same: Athlon64 x2, 2GB Ram, all running 32bit 10.04.3 with all updates current.
 using ```
killall gnome-panel
``` works but I am also looking to see if there is a better idea of the root cause or better fix
Thanks
Bob

---

