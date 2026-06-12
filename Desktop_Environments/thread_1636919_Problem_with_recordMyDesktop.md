---
title: "Problem with recordMyDesktop"
date: 2010-12-03
forum: Desktop Environments
---

### Post by throese on 2010-12-03
So, when I type this: ```
ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 30 -s 1024x768 -i :0.0 -acodec pcm_s16le -vcodec libx264 -vpre lossless_ultrafast -threads 0 output.mkv
``` into my terminal, I this message:

"capture with some ALSA plugins, especially dsnoop, may hang."

What does that mean? It starts up shortly after that, but before it didn't start up.

---

