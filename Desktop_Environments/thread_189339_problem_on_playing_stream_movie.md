---
title: "problem on playing stream movie"
date: 2006-06-05
forum: Desktop Environments
---

### Post by muzaki on 2006-06-05
after upgrading to dapper few days ago ,today i noticed some problems about playing streamed movie/video....
I want to be able to see yahoo's movie
and so i can hear the sound of the trailer playing but no pictures at all, i mean the screen blinks for second and nothing show up....
then i try to copy the url and try to play it in many media like vlc, totem, mplayer....but the result is the same , only the sound i could hear
(this was never happen in breezy)

if i'm not mistaken when the dapper upgrading process run,it ask me to rewrite some config files (including mplayer's).So i just wonder if anybody succes to play streamed movie ,please give me your config, or if you have other solution...

thanks in advance

---

### Post by localzuk on 2006-06-05
Hi,

Do you have the codecs required to view that type of video? Movies often use 2 different codecs for audio and video, so this would explain being able to hear but not see the content.

Take a look at [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats) for more information about installing the non-free codecs.

---

### Post by muzaki on 2006-06-05
thanks,
yes i have the codecs (all which is written on the how-to)
and never mind i can play it on **Gxine**, what i mean is how to play it embedded in firefox

ps. I have w32 codecs etc. and mplayerplug-in 0.2.1 but still cant embed playing on forefox

---

### Post by localzuk on 2006-06-05
Try installing one of the package gxineplugin. This is another plugin for firefox IIRC.

---

### Post by muzaki on 2006-06-05
installed but still no luck, i guess i have to configure it so that it will use gxine plugin, instead of mlpayer plugin which is not working for me..
Its ok, i still be able to watch , i just have to copy the url
thanks

---

