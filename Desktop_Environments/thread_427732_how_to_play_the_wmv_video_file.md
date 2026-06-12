---
title: "how to play the wmv video file?"
date: 2007-04-29
forum: Desktop Environments
---

### Post by chinese_ys on 2007-04-29
how to play the wmv video file? I have installed win32codec, but when I tried to play my wmv file the player prompted me error. I use totem-xine as my movie player. I am under feisty.
[IMG]http://myweb.dal.ca/sh746773/error.png[/IMG]
how to deal with this?
thanks!

---

### Post by Ozeuss on 2007-04-29
is the ubuntu codec installer not working with totem-xine? when i installed feisty (totem still with gstreamer) it installed the codecs with no problem... have you installed "ubuntu restricted extras"? available from "Add/Remove programs'?

---

### Post by FuturePilot on 2007-04-29
Try this ```
sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui
```

---

### Post by chinese_ys on 2007-04-29
thanks dudes, I have tried your ways actually, but it does not work.

---

### Post by ronacc on 2007-04-29
try automatix and install the codecs from there.

---

### Post by FuturePilot on 2007-04-29
Try installing MPlayer. That's what I use and it plays wmv fine.

---

