---
title: "SSH streaming"
date: 2006-01-09
forum: Desktop Environments
---

### Post by shawnzyoo on 2006-01-09
i just set-up a server to use ssh/scp
is there a way that i can stream my media while using ssh?
i think i use x11 forwarding...but i am not sure
thank you

---

### Post by Suger on 2006-01-09
Either use ssh -Y (remote X through ssh)and launch a media app on the local box, but that's not really streaming, either use a streaming client and ssh -L (ssh port forwarding) the port your streamer is using from your local box(es)

VLC has a streaming facility, you might want to read that

[http://www.videolan.org/doc/streaming-howto/en/ch04.html](http://www.videolan.org/doc/streaming-howto/en/ch04.html)

You might also want to read this

[http://www.linuxquestions.org/questions/showthread.php?t=391205](http://www.linuxquestions.org/questions/showthread.php?t=391205)

One of the three solutions should suit you.

---

