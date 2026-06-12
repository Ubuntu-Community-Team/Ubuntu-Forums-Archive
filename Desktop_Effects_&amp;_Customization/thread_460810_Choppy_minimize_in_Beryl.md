---
title: "Choppy minimize in Beryl"
date: 2007-06-01
forum: Desktop Effects &amp; Customization
---

### Post by phoenixankit on 2007-06-01
My minimizing process is very choppy in Beryl. Everything else is uber smooth. It's just minimizing.Why?

---

### Post by phoenixankit on 2007-06-01
?

---

### Post by luciferin on 2007-06-01
I've had the same problem, it should be alleviated (mostly) by turning off the Sync to VBlank option in the Beryl Settings Manager, you'll just get more page tearing.  

You may also want have to change your settings in your Xorg.conf/videocard configuration utility depending on your drivers and settings, but try the Beryl Settings to start with.

---

### Post by reclusivemonkey on 2007-06-01
[LIST=1]
[*]You might want to wait more than an hour before bumping your post, you can give the impression of being impatient.

[*]Are you using any animations for window closing in beryl?
[/LIST]

---

### Post by phoenixankit on 2007-06-01
1. Sorry...
2.Yes, Magic Lamp 1, but I have the same one for Maximize, but thats as smooth as butter

---

### Post by phoenixankit on 2007-06-02
> **luciferin said:**
> I've had the same problem, it should be alleviated (mostly) by turning off the ** Sync to VBlank option**  in the Beryl Settings Manager, you'll just get more page tearing.  

You may also want have to change your settings in your Xorg.conf/videocard configuration utility depending on your drivers and settings, but try the Beryl Settings to start with.

Umm...I'm sorry, but where can I find those?

---

### Post by screaminj3sus on 2007-06-02
Yeah same thing here, maximize is smooth as hell for me but minimize is unsatisfactorily choppy. You can really notice it when you set minimize to zoom (like compiz default) it will be smooth occasionally but alot of the times very choppy. I already have sync to vblank off and changed the refresh rate to 75 (it incorrectly detected it as 60 making everything choppy)

@Phoenix, right click the beryl icon and go to beryl settings manager, scroll down under general settings.

---

### Post by astoltz on 2007-06-02
> **screaminj3sus said:**
>  I already have sync to vblank off and changed the refresh rate to 75 (it incorrectly detected it as 60 making everything choppy.That refresh rate is NOT related to the monitor's refresh rate in Xorg - maybe they should give it a different name.  There's a few tips out there that suggest bumping it all the way to 200.  That's where I have mine set and it seems to make a small difference.

---

### Post by screaminj3sus on 2007-06-02
Just changed it to 200, seems to mainly make a difference with the smoothness of wobbly windows and things seem a bit smoother overall, but it does cause more screen tearing.

---

### Post by konungursvia on 2007-06-02
Considering that maximizing is a constructive process, which ends up displaying a clear window, whereas minimizing is a destructive one, losing more and more of the window until it is gone, they probably put a lot more into the former than the latter. Why not use a different animation for minimize? I find the one that rotates the thing off like a thrown playing card doesn't look too bad.

---

### Post by phoenixankit on 2007-06-03
I've tried many...Even fade...but everyone of them is choppy...

---

### Post by screaminj3sus on 2007-06-04
I actually find fade and zoom seem the choppiest.

---

