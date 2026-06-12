---
title: "Launch application from bash script without window borders"
date: 2009-04-29
forum: Desktop Environments
---

### Post by jucas_lo on 2009-04-29
Hi all

I want to run a small vlc window to monitor a webcam, and I have a script to launch vlc with the proper parameters, but I would like to know how to hide the window borders from the window.


cvlc -d --quiet --extraintf dummy,rc --rc-host localhost:8094 v4l:///dev/video0

I'm able to hide the borders by right-clicking on the title then selecting Advanced->No borders, but I don't know how to do that from a script.

I was taking a look at kstart but I didn't find any option to hide the borders...although I didn't find that much of documentation for it. :-(

I really need to be able to launch vlc without borders, I hope you guys can help me.

Thanks in advance!

Any suggestions are welcome!

---

