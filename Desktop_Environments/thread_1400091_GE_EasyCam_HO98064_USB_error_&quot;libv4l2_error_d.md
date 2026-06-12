---
title: "GE EasyCam HO98064 USB error &quot;libv4l2: error dequeuing buf: Input/output error&quot;"
date: 2010-02-06
forum: Desktop Environments
---

### Post by Staesys on 2010-02-06
This webcam "just works" when plugged into my 9.10 desktop, including the microphone. Using it in Skype or Camorama however requires the

```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so
```

command to work. Xawtv doesn't like it (picture starts out great, but then gets darker and darker until it's black) however and when using the webcam program from the terminal, the colors are inverted. This isn't a problem as I like Camorama much better anyway.

Camorama does work with it just fine, as I stated above. The problem I have is that a random amount of time (an hour, a day, etc) Camorama will crash with an error. In the terminal I find the line:

```
libv4l2: error dequeuing buf: Input/output error
```

If I unplug the webcam and then plug it back in, I can then reload Camorama and it will work until it crashes again.

Does anyone have any ideas?

---

