---
title: "Beryl causes videos to play back as empty black space."
date: 2007-06-15
forum: Desktop Effects &amp; Customization
---

### Post by diablo75 on 2007-06-15
I'm using a HP dv1000 laptop.  Beryl runs fine, but when I attempt to play a video, it shows up as black space.  So, I tried to change it's rendering path from automatic to copy.  And that fixed the problem with the video.  But later causes a ton of messy artifacts to wipe out menu items and task bars.  That would clear up after I changed to rendering path back to automatic, but then the videos go back to black.

Any suggestions?

---

### Post by Dread Knight on 2007-06-15
Something like that happened to me when I've installed Ubuntu Feisty on my dad's laptop.
I've just disabled the special effects in order to play videos :(

---

### Post by Alex Spencer on 2007-06-16
Are you sure it's Beryl? I have this same problem with videos and Beryl isn't installed (yet).

---

### Post by Alex Spencer on 2007-06-16
Cancel that, I restarted and it's all fine...hesitant to install Beryl now...unless you came up with a fix?

---

### Post by Soybean on 2007-06-16
Beryl doesn't get along with the default video driver for most video players. The way to fix it depends on your video player... for example, in VLC, you need to set the "video output module" to something else (I believe X11 is best), in Mplayer I think it's called the "driver" or something, again, change to x11... or just try different ones until it works.

Note that these methods are slower (which is why they're not the default), so if your computer isn't up to it, Dread Knight's solution of turning off Beryl to play videos may be your best bet.

---

### Post by Alex Spencer on 2007-06-16
Thanks for your quick reply, I'll give that a try

---

### Post by walkerk on 2007-06-16
> **Soybean said:**
> Beryl doesn't get along with the default video driver for most video players. The way to fix it depends on your video player... for example, in VLC, you need to set the "video output module" to something else (I believe X11 is best), in Mplayer I think it's called the "driver" or something, again, change to x11... or just try different ones until it works.

Note that these methods are slower (which is why they're not the default), so if your computer isn't up to it, Dread Knight's solution of turning off Beryl to play videos may be your best bet.

exactly.. you need to change the output mode.. most media players have the option to change to x11, gl, etc..

---

### Post by pingpongboss on 2007-06-16
i used to have this problem when playing through totem-gstreamer. Try installing totem-xine. that basically solved the problem for me.

---

### Post by Dread Knight on 2007-06-16
> **pingpongboss said:**
> i used to have this problem when playing through totem-gstreamer. Try installing totem-xine. that basically solved the problem for me.
Aham, that's the case, thanks. I'll try that tomorow.

---

### Post by LMP900 on 2007-06-16
For Totem (gstreamer):

1. Alt-F2
2. Type: gstreamer-properties
3. Go to the "video" tab and choose "X Window System (No Xv)"

---

### Post by parry_mathur on 2007-07-06
I was having the same problem, too. Now I got the videos working on totem. Can anybody give me detailed, step-by-step instructions on how to fix my videos on VLC media player?
Thanks

---

### Post by LMP900 on 2007-07-09
> **parry_mathur said:**
> I was having the same problem, too. Now I got the videos working on totem. Can anybody give me detailed, step-by-step instructions on how to fix my videos on VLC media player?
Thanks

Here's an earlier post of mine: [http://ubuntuforums.org/showpost.php?p=2382846&postcount=2](http://ubuntuforums.org/showpost.php?p=2382846&postcount=2)

I hope that solves your issue. :)

---

