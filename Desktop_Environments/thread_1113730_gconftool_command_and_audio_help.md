---
title: "gconftool command and audio help"
date: 2009-04-01
forum: Desktop Environments
---

### Post by das867 on 2009-04-01
I was wondering if anybody could help me. I need the command for gconftool to switch audio to the default device, auto-detect, or alsa. i know that the command to change output to bluetooth is (gconftool -t string -s /system/gstreamer/0.10/default/musicaudiosink "sbcenc !a2dpsink device=00:0D:3C:BC:44:53") but i cant figure out what to change the last part to. any help appreciated!

---

### Post by das867 on 2009-04-02
Bump.

---

### Post by das867 on 2009-04-02
bump

---

### Post by glotz on 2009-04-02
```
gconftool -t string -s /system/gstreamer/0.10/default/musicaudiosink "alsasink"
``` You can also use *autoaudiosink* instead of *alsasink*. (Or even *osssink* and *esdsink* if you happen to use them.)

---

### Post by das867 on 2009-04-02
> **glotz said:**
> ```
gconftool -t string -s /system/gstreamer/0.10/default/musicaudiosink "alsasink"
``` You can also use *autoaudiosink* instead of *alsasink*. (Or even *osssink* and *esdsink* if you happen to use them.)

You sir, are awesome in the extreme.

---

### Post by glotz on 2009-04-02
Yes, sometimes! :lol:

The info was gathered by firing up```
gconf-editor /system/gstreamer/0.10/default/musicaudiosink &
```and checking out the explanation and the value I had there. Glad to be of any use.

---

