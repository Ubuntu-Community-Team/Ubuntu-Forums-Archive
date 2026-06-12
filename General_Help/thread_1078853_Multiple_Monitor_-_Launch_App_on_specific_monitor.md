---
title: "Multiple Monitor - Launch App on specific monitor ?"
date: 2009-02-23
forum: General Help
---

### Post by Tom_T on 2009-02-23
Hi

Nvidia graphics card running 177 drivers and 2 x 17" TFT's.

In XP I could tell an application to open on a specific monitor.
Is this possible in Ubuntu 8.10 ?

Thanks :)

---

### Post by SteveDee on 2009-02-24
> **Tom_T said:**
> Hi

Nvidia graphics card running 177 drivers and 2 x 17" TFT's.

In XP I could tell an application to open on a specific monitor.
Is this possible in Ubuntu 8.10 ?

Thanks :)

Yes, take a look at my post for MPlayer: [http://ubuntuforums.org/showthread.php?t=1073242](http://ubuntuforums.org/showthread.php?t=1073242)

What applications are you hoping to launch this way?

---

### Post by Tom_T on 2009-02-24
Thanks.
Ideally I'd like firefox to always open on my second screen..

BUT..Looking at this I don't think I'm actually configured for '2' screens just one large screen across 2 monitors.

If that makes sense. !

I tried you PlayMovie.sh script and I could hear the movie, but it never appeared on either screen.

????

---

### Post by SteveDee on 2009-02-24
> **Tom_T said:**
> Thanks.
Ideally I'd like firefox to always open on my second screen..

BUT..Looking at this I don't think I'm actually configured for '2' screens just one large screen across 2 monitors.

If that makes sense. !

I tried you PlayMovie.sh script and I could hear the movie, but it never appeared on either screen.

????

If you only have 1 desktop spread across 2 monitors then the movie was sent to a screen that does not exist. I guess you just want to run the movie on a specific part of your screen (like right of centre) so it appears on the other monitor.
If you are using mplayer, setting the "Save Windows Position" option should ensure it always re-starts in the same place as last time.

---

### Post by Tom_T on 2009-02-24
If you are using mplayer, setting the "Save Windows Position" option should ensure it always re-starts in the same place as last time.

Thanks 
Where do I find that option ??

---

### Post by SteveDee on 2009-02-24
> **Tom_T said:**
> If you are using mplayer, setting the "Save Windows Position" option should ensure it always re-starts in the same place as last time.

Thanks 
Where do I find that option ??

Right click on the mplayer screen/window to display its pop-up menu and select Preferences > Misc then enable "Save windows position"

---

