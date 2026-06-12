---
title: "Record Fullscreen OpenGL games?"
date: 2013-05-01
forum: Gaming &amp; Leisure
---

### Post by iTech278 on 2013-05-01
Hello!

I am on Ubuntu 13.04 and I was just wondering if there was anyway to record fullscreen OpenGL games? I tried installing GLC, but I get an error stating that the package could not be found, even after adding the repo and updating Aptitude. Maybe something changed in 13.04 that is stopping me from installing it... Any suggestions?

---

### Post by myromance123 on 2013-05-01
Besides GLC, have you tried anything else?

Off the top of my head, you should try Kazam (it's available in the Ubuntu Software Center). If that doesn't work (it can be unstable or have leaking issues), there's also Vokoscreen.

Lastly, you could just simply use the Terminal with FFMPEG. I'm not too familiar with the commands though.

---

### Post by iTech278 on 2013-05-01
> **myromance123 said:**
> Besides GLC, have you tried anything else?
Off the top of my head, you should try Kazam (it's available in the Ubuntu Software Center). If that doesn't work (it can be unstable or have leaking issues), there's also Vokoscreen.
Lastly, you could just simply use the Terminal with FFMPEG. I'm not too familiar with the commands though.

Yes, I have Kazam, but unfortunately neither that nor Vokoscreen will record the games in fullscreen (at least for me). I believe they work in windowed mode (I can't test it atm) though. I might look into FFMPEG if nothing else.

Thanks for the reply! If anyone else has any other suggestions, please let me know! :D

---

### Post by dak0 on 2013-05-02
Hi, I use RecordMyDesktop not sure if it records full screen OpenGL games.

---

### Post by mentorious on 2013-05-03
Gamecaster :)

---

### Post by Arthur_D on 2013-05-04
FFMPEG is the only thing I've found which works well, is near bug-free and has decent performance. But it's a bit of a drag learning it.

---

### Post by Ranko Kohime on 2013-05-07
> **dak0 said:**
> Hi, I use RecordMyDesktop not sure if it records full screen OpenGL games.
It does not record OpenGL, therefore it will not record the games that rely on it.  It's framerate is not sufficient for that, either, as in my testing it's 15 fps or lower, regardless of settings.

---

