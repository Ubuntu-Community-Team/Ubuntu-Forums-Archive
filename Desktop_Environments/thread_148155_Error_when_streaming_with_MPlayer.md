---
title: "Error when streaming with MPlayer"
date: 2006-03-21
forum: Desktop Environments
---

### Post by andy101 on 2006-03-21
When I try and listen to an internet stream in MPlayer I get the following error message:

```
Couldn't resolve name for AF_INET6:rmv8.bbc.net.uk
```

Obviously the end bit changes depending on what server I am streaming from.

After clicking ok it seems to work.

I fired up mplayer from the command line to get a better view of debugging details:

```

Playing rtsp://rmv8.bbc.net.uk/radio1/jules.ra.
STREAM_RTSP, URL: rtsp://rmv8.bbc.net.uk/radio1/jules.ra
Resolving rmv8.bbc.net.uk for AF_INET6...
Couldn't resolve name for AF_INET6: rmv8.bbc.net.uk
Resolving rmv8.bbc.net.uk for AF_INET...
Connecting to server rmv8.bbc.net.uk[212.58.224.140]:554 ...

```

It seems to try and resolve the domain name by passing the AF_INET6 to the function it uses (i forget what the function normally used is, I forgot the small amount of stuff I knew about sockets), that fails and then it tries AF_INET and it works.

It is kind of disconcerting to see an error message every time I try to stream audio.

Anyone know why its doing this, how I can stop it doing that or how I can suppress the error message?

Thanks.

(I hope this is the right place to post, got kind of confused by the new forum layout)

Couldn't seem to find anything on the wiki.

---

### Post by jrib on 2006-03-21
add ```
prefer-ipv4 = yes
``` to your ~/.mplayer/config

---

