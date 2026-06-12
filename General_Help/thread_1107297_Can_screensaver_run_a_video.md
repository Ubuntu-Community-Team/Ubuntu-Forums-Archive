---
title: "Can screensaver run a video?"
date: 2009-03-26
forum: General Help
---

### Post by ArgentSilver on 2009-03-26
What I'm trying to do is have the gnome screensaver run a video when it goes into saver mode. It seems mplayer will run the video looped and fullscreen (mplayer ~/video.mp4 -loop 0 -fs). So I copied one of the .desktop files in /usr/share/applications/screensavers and tried to modify it to start mplayer. No luck! So I made a script for it, verified the script works, and tried plugging that into the .desktop file. Still no luck!

Anyone know if this is possible and, if so, how to do it?

---

### Post by ArgentSilver on 2009-03-27
...<sound of crickets chirping>...

*sigh* Something else that SHOULD be easy, but you can't get there from here...

---

### Post by binbash on 2009-03-27
It is possible , i was doing that.There was a thread about this on this forum.

---

### Post by aeon on 2009-03-27
I'm not shure if gnome-screensaver is able to do it, but xscreensaver should handle it without too much of a hassle.. have a look [[COLOR="Red"]here[/COLOR] [jwz.org]]("http://www.jwz.org/xscreensaver/faq.html#mpeg")

---

### Post by ArgentSilver on 2009-03-27
Looks like the answer is that gnome-screensaver can't do this. Seems I'd have to replace it with xscreensaver. Initially I didn't want to do that but after digging into info on both, it seems gnome-screensaver is a step in the wrong direction, being less capable than xscreensaver and offering few, if any, advantages. So I may try it and see...

Still seems like this is lots harder than it should be!

---

### Post by ArgentSilver on 2009-03-27
> **binbash said:**
> It is possible , i was doing that.There was a thread about this on this forum.

Well it didn't show up in my searches. And if you were doing it...how?

---

