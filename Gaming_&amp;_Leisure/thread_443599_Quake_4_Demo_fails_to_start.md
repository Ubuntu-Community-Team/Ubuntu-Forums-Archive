---
title: "Quake 4 Demo fails to start"
date: 2007-05-14
forum: Gaming &amp; Leisure
---

### Post by klange on 2007-05-14
I'm pretty sure my PC meets the requirements, but when I try to run the Quake 4 demo (quake4-demo), my screen switches to a lower res (feels like 640x480...) and nothing else happens. I've tried looking around to see if someone else was having this problem, but as the demo/game is fairly old (ok, not *that*, but sure as heck isn't brand new), I've had no luck in getting help.

Any ideas?
```
X..GL_ARB_texture_non_power_of_two not found
...using GL_NV_blend_square
...using GL_ARB_texture_compression
X..GL_EXT_texture_compression_s3tc not found
signal caught: Segmentation fault
si_code 1
Trying to exit gracefully..

```

---

### Post by B. Gates on 2007-05-14
Brand new commercial games don't exist in Linux; Quake 4's about the newest commerical game for Linux there is, so it's not old by those standards.

As for your problem - have you got the latest drivers for your video card installed? What is your video card? Froom the looks of things the card doesn't support the necessary GL extensions, so it might be too old.

---

