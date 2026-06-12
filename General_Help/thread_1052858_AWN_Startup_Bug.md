---
title: "AWN Startup Bug"
date: 2009-01-28
forum: General Help
---

### Post by adredz on 2009-01-28
This bug ([https://bugs.launchpad.net/awn/+bug/243191](https://bugs.launchpad.net/awn/+bug/243191)) still hasn't been fixed yet and it is marked as low priority. I really hope the devs will allot time for it because it is very annoying every time I boot my computer and see that hideous bug. Or it's just me?

---

### Post by Sam Lars on 2009-01-28
I think I know what it's talking about, but I'm not sure.  A screenshot would be nice.
Since it's there and then gone, it doesn't really bother me.  I'm more annoyed by the fact that the Zoom animation doesn't resize the icons, so they just get blurry.  At least they know about it and plan to fix it eventually.
Oh, and you also have a workaround, which is better than nothing.

---

### Post by adredz on 2009-01-28
Workarounds don't work. I have tried them. Bout the zoom effect, yeah it's not really good. I would love to have the OS X zooming effect like what Cairo has...

---

### Post by detroit/zero on 2009-01-28
I think I know what OP is referring to. I was just about to make my own post about it:

[IMG]http://i150.photobucket.com/albums/s104/backup23/awn.png[/IMG]

I always have to kill/restart AWN manually to get rid of those black bars.

I've tried changing the command in Sessions that launches AWN to ```
sleep XX && avant-window-navigator
```(where XX is anything from 10 to 45 seconds) but AWN won't launch with a sleep command attached. Same goes for a startup script - sleep XX && avant-window-navigator just means I have to hit alt-f2 and start it on my own.

Funny thing is, I have Conky set to start on a delay of 20 or 25 seconds, and that comes up just fine (the black bars at the top right and bottom left). I tried adding AWN to my conky startup script, and it still doesn't work with a sleep command.

It's a batty bug, for sure, but I'll deal with it before I ever go back to that heinous POS Cairo Dock.

---

### Post by adredz on 2009-01-29
> **detroit/zero said:**
> I think I know what OP is referring to. I was just about to make my own post about it:

[IMG]http://i150.photobucket.com/albums/s104/backup23/awn.png[/IMG]

I always have to kill/restart AWN manually to get rid of those black bars.

I've tried changing the command in Sessions that launches AWN to ```
sleep XX && avant-window-navigator
```(where XX is anything from 10 to 45 seconds) but AWN won't launch with a sleep command attached. Same goes for a startup script - sleep XX && avant-window-navigator just means I have to hit alt-f2 and start it on my own.

Funny thing is, I have Conky set to start on a delay of 20 or 25 seconds, and that comes up just fine (the black bars at the top right and bottom left). I tried adding AWN to my conky startup script, and it still doesn't work with a sleep command.

It's a batty bug, for sure, but I'll deal with it before I ever go back to that heinous POS Cairo Dock.

Yup, that's it.. I tried to capture it but I couldn't. That is really the thing I always see on start up. But before that, there are two large white bars on the top left corner and on the bottom left beside the AWN dock that appear which gradually turn into what your screenshot looks like..

---

### Post by Sam Lars on 2009-01-29
I'm not sure you want the && after the sleep command... I think you want a semicolon.  I have awn in a startup script with sleeps that works fine.

---

### Post by detroit/zero on 2009-01-29
> **Sam Lars said:**
> I'm not sure you want the && after the sleep command... I think you want a semicolon.  I have awn in a startup script with sleeps that works fine.
I'll give that a shot then. Thanks!

---

