---
title: "Multimedia keyboard half works XPS M1330"
date: 2009-03-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by geoffm on 2009-03-18
[I]Multimedia keys stopped working after I upgraded to 8.10 and KDE 4.2

I know a lot of people have these problems. I tried solutions from a couple of posts and they didn't work for me. Only the volumeUP and volumeDOWN work, not mute, not controls with Amarok...
is there an official fix?[/I]

------

I finally managed to get them to work!!
Here's how I did it.

Went to **System Settings** / **Keyboard & Mouse** / **Global Shortcuts** and I disabled all the multimedia controls there (both **kmix** and **amarok**).
I also turned off **kayboard layout **in **regional settings**, not sure if that's important...
Then in **Amarok**, **Configure Global Shortcuts**, I set my multimedia controls there. Now they work fine.
Then in **kmix**, what was wrong there is that PCM was set as the Master channel! This settings isn't present in the kmix window. To change this you have to **right click the kmix tray icon**, **select master channel**, and select Master.

Now all my multimedia keys work perfectly at last! Hope this helps some people.

---

### Post by TobyReynolds on 2009-03-19
> **geoffm said:**
> Also, how can I set numlock to be off on startup?

I think I can answer that one for you: I believe it's a setting in the BIOS. No idea about the media keys though, mine work fine, sorry.

---

### Post by geoffm on 2009-03-19
no, X server turns numlock on when it starts.

---

