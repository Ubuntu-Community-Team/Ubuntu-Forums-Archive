---
title: "totem-xine blue screen with compiz fusion"
date: 2007-09-02
forum: Desktop Effects &amp; Customization
---

### Post by coolen on 2007-09-02
My brother-in-law recently installed Ubuntu on his laptop. He got through it fine, but he's new to Linux, and doesn't know where to go from here, so he asked me to get him all the extra bits. I agreed, and got under way.
I'm having a problem, though. I installed Compiz Fusion, and totem-xine, since being unable to use DVD menus would probably put him off.
Then, I got this wierd blue screen. Whenever any compositing effect is laid over the video (transparency, for example), it goes blue.
Now, this is a known issue, and I installed gxine in order to get to the options to fix it (using a different video driver). Having done that, gxine worked beautifully...but totem did not.
So, I logged out, logged back in, reset, tried xine-ui, purged totem and all components, reinstalled, and it's still not using my xine configuration. There's nothing I can see in his home folder, /etc, or gconf.
Does anyone know how to fix this? Anything I can try?

---

### Post by Inxsible on 2007-09-02
Compiz Fusion is not known to play nice with other software requiring high cpu cycles like videos and games. Most times, you just have to shut down Compiz Fusion to get a quality experience in DVD/ video/ movies

---

### Post by coolen on 2007-09-02
No, I experienced the same problem when I installed gxine, and fixed it as described. My problem is applying this to totem using the xine backend. The thread I used ([http://ubuntuforums.org/showthread.php?t=507332](http://ubuntuforums.org/showthread.php?t=507332)) implied that the xine fix would carry over, but it didn't.
Besides, Compiz runs fine with me when playing video. Always has.

---

### Post by NiceGuy on 2007-09-11
> **kevinmedina said:**
> 
+ The same process enables Totem that has the totem-xine backend configured.

Not quite true... The version of totem-xine which ships with gutsy (I haven't tried other versions) has it's own config file, xine_config, which you need to edit. This can be found in the .gnome2/Totem/ in your home folder.

Just find where it says:
```

# video driver to use
# string, default: auto
#video.driver:auto

```

and change it to:
```

# video driver to use
# string, default: auto
video.driver:xshm

```

---

### Post by coolen on 2007-09-11
Ahh, thank you! I'll fix it up next time he's down.
Thank you!!!

---

