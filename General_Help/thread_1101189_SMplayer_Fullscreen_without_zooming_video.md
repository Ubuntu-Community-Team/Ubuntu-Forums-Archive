---
title: "SMplayer Fullscreen without zooming video"
date: 2009-03-20
forum: General Help
---

### Post by oinkl on 2009-03-20
Im currently using SMPlayer as my current media player.

Simple question:
How do I maximise the the window without the video scaling to fit the window as well? I want the video in the centre, surrounded by a black background.

I tried editing /etc/mplayer/mplayer.conf and setting zoom=no, and playing with other options, but nothing seems to work.

---

### Post by rvm4000 on 2009-03-20
You can pass -nozoom to mplayer, but that option works only with x11 as video driver.

---

### Post by DiegoBretti on 2009-04-14
Hi, i have a easy problem but i cant found the solution...

I start the SMPlayer with a video.. that's is OK.
But, when i Fullscreen the video, the video start again from the begin. And from Fullscreen to a window again, from the begin too.

That's the problem, i cant find in config/settings to resume the position of the video.

Thanks!

---

### Post by 3Miro on 2009-04-14
I don't know the solutions to your problems, I myself have had bad experience with SMPlayer. I switched to Gnome Mplayer and KMplayer. You might consider that.

---

### Post by DiegoBretti on 2009-04-14
> **3Miro said:**
> I don't know the solutions to your problems, I myself have had bad experience with SMPlayer. I switched to Gnome Mplayer and KMplayer. You might consider that.

Yes, i know MPlayer but i prefer S-MPlayer.
It's not a really problem.. but is annoying.

Thanks

---

### Post by rvm4000 on 2009-04-14
> **DiegoBretti said:**
> Hi, i have a easy problem but i cant found the solution...

I start the SMPlayer with a video.. that's is OK.
But, when i Fullscreen the video, the video start again from the begin. And from Fullscreen to a window again, from the begin too.

That's the problem, i cant find in config/settings to resume the position of the video.

Thanks!

I guess you have the option "Add black borders on fullscreen" (preferences -> general -> video) enabled. That option restarts mplayer every time you switch fullscreen. The video should resume at the same position, but maybe that video doesn't support seeking.

Just turn off that option.

---

### Post by DiegoBretti on 2009-04-21
> **rvm4000 said:**
> I guess you have the option "Add black borders on fullscreen" (preferences -> general -> video) enabled. That option restarts mplayer every time you switch fullscreen. The video should resume at the same position, but maybe that video doesn't support seeking.

Just turn off that option.

rvm4000 = The best! ;)

---

