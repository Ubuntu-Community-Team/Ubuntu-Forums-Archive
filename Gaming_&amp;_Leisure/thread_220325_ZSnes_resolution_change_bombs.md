---
title: "ZSnes resolution change bombs"
date: 2006-07-21
forum: Gaming &amp; Leisure
---

### Post by becominglumberg on 2006-07-21
So, when I start ZSnes, it puts up a splash and tells me to press the spacebar. That works, and ZSnes recognizes key input. Then I go to change the resolution to something not so itty-bitty. After that, it prompts me to hit the elusive 'any' key, but my keyboard goes totally unresponsive, nor do mouse clicks do anything. All I can do is kill the program. When I start the program back up, it requires me to see that splash screen again where i press the spacebar.

Any Ideas?

---

### Post by XVampireX on 2006-07-21
Yup... Need to get the new WIP.

Or I can try to upload the binary that totally works...

There you go: [http://rapidshare.de/files/26534667/zsnes.7z.html](http://rapidshare.de/files/26534667/zsnes.7z.html)

---

### Post by DoktorSeven on 2006-07-22
I've had random issues with zsnes with that exact same issue -- maybe the version pointed to by XVampireX will help, but if not...

open up ~/.zsnes/zsnesl.cfg and find **VideoModeLin = xx** (xx will be some number), there will be a table of possible values above it (commented) -- change the value to whichever mode you want to use.  Everything else about zsnes seems to run fine except the resolution change, and this edit fixes that.

---

### Post by XVampireX on 2006-07-22
The version I pointed out should work very well, as well as it uses OSS for sound rendering, if you ever have any sound problems, too.

I've personally talked to the developer on IRC about this, the video resolution problem is well known, it's related to the keyboard, actually.

---

