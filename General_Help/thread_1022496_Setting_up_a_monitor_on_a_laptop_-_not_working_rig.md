---
title: "Setting up a monitor on a laptop - not working right"
date: 2008-12-26
forum: General Help
---

### Post by weirddan455 on 2008-12-26
Just got an HDTV/Monitor... a samsung SyncMaster T240HD.  Anyway, I'm trying to set it up on my laptop and weird things are happening.  I'm using the GUI "screen resolution" tool to set it up.  Here's a screen shot of the way I have it now.

[IMG]http://bellsouthpwp.net/w/e/weirddan455/resolution.jpg[/IMG]

The monitor's optimum resolution according to the manual is 1920 x 1200 @ 60 Hz but it's not listed.  Also, desktop effects don't work anymore even when I disconnect the monitor, reboot, mess with the screen resolutions again.  The display also seems "laggy".  When I move a window it's like the refresh rate off.  This is also consistent with and without the monitor and was never an issue before this tool messed my stuff up.

I think it may be because, when I first set it, a diologe box told me it needed to enable "virtual desktop" in my configuration file.  I clicked ok, the monitor turned on, and the problems started.

The laptop is a Satellite A135-S4666 using an integrated intel video card.  I used to be a slackware user before Ubuntu came around so I'm not afraid of editing files... it's just been a while and I thought Ubuntu was supposed to do everything for you with the GUI tools.

---

### Post by weirddan455 on 2008-12-26
Should have just googled lol... I fixed it.

```
sudo dpkg-reconfigure xserver-xorg
```

That command reconfigures your xorg.conf in case anyone has the same problem.

GUI tools suck... messed up my configuration file with no option to reconfigure and that's supposed to be "easier to use"... whatever.

---

### Post by 2hot6ft2 on 2008-12-26
Great post on dual monitors here. [http://forumubuntusoftware.info/viewtopic.php?f=46&t=2446#p24910](http://forumubuntusoftware.info/viewtopic.php?f=46&t=2446#p24910)

---

