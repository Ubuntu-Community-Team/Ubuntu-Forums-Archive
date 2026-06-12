---
title: "How do I get rid of this black bar on my Cairo Dock?"
date: 2008-09-27
forum: Desktop Environments
---

### Post by morbid_bean on 2008-09-27
Just wondering how I can get rid of this black bar behind my dock whenever I bring it up.

[IMG]http://i34.tinypic.com/j9bxjp.png[/IMG]

---

### Post by whymichael on 2009-05-31
Bump

---

### Post by Viva on 2009-05-31
Do you have a composite manager running?

---

### Post by Sarai the Geek on 2009-05-31
Enable compiz-fusion:
```
sudo apt-get install compizconfig-settings-manager
```
Note that you need a relatively new graphics card and, depending on the card and manufacturer, you may need proprietary drivers. 

If you don't want to, or can't, use compiz, try a theme for your cairo dock that doesn't use pseudo-transparency.

---

### Post by morbid_bean on 2009-05-31
lol im surprised someone dug up my old thread, anyhow, i solved this problem by making sure the Visual Effects were set on "Extra"  Go to system>preferences>appearance and go to the "Visual Effects Tab" Set this on "Extra"


\\:D/ \\:D/

---

### Post by TheNosh on 2009-05-31
visual effects are compiz. you can also enable compositing in metacity though

---

### Post by Sarai the Geek on 2009-06-01
> **morbid_bean said:**
> lol im surprised someone dug up my old thread, anyhow, i solved this problem by making sure the Visual Effects were set on "Extra"  Go to system>preferences>appearance and go to the "Visual Effects Tab" Set this on "Extra"


\\:D/ \\:D/

Wow, I didn't even notice it was an old thread, haha...

---

### Post by whymichael on 2009-06-03
Thanks for all of the replies, I will try them out. For now, I am using the command ```
cairo-dock -c
``` which forces Cairo to run without using OpenGL. It seems to work, but it requires more resources to run and it might limit what I can do with Cairo.

---

