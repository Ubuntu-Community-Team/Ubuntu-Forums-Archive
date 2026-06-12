---
title: "Play vide on startup."
date: 2007-07-28
forum: Dell  Ubuntu Support
---

### Post by conorkirk on 2007-07-28
I have a dell, but this could go for any ubuntu :D

I was wondering how I could have a video play when my computer starts up... (Not in the Bios, but after X is started)


I tried this in /etc/X11/Xsession:

```

mplayer /home/conor/Desktop/video.mpg -fs -zoom -framedrop

```

and that command plays the video just fine from a terminal, but not when starting up...


Any ideas?

---

### Post by stinger30au on 2007-07-29
save it as a script and it to the the startup.
Add it to startup by going to system>preferences>sessions
click on new and point it to the script.
hope this helps

---

