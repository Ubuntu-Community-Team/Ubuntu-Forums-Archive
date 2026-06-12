---
title: "Maximising windows kills Compiz"
date: 2010-11-15
forum: Desktop Environments
---

### Post by bs00065 on 2010-11-15
Hey,
So I've been searching around for quite a while now but haven't found anything that really helps. I'm running an Intel 945GM, which means my max_texture_size is 2048x2048, my display is 2048x1152. This means I can run Compiz, but it dies easily.

If I maximise a window, the window decoration falls outside of my 2048 width and Compiz dies with a "Warn: Exceeded max texture size"

This only happens on windows which Compiz controls the decoration of. Chrome works fine, because (I think) it's decoration is handled by itself, and so it maximises to the correct size.
I think the issue may be with window shadows in the 'Window Decoration' options, because if I set "Decoration Windows = none", I can maximise windows no problem, Compiz stays working (though obviously it's kinda useless...)

Has anyone else seen this issue/aware of a fix? There must be other people that run Compiz on a resolution equal to the max_texture_size of their card right?

Thanks for any help :)

---

### Post by stinkeye on 2010-11-16
Possibly one place to look.

---

### Post by bs00065 on 2010-11-16
Hi Stinkeye,

Yeah that is set correctly, though changing it didn't seem to make any difference. I also disabled auto display detection, hoping if I manually forced it to stick to 2048 it might work. No luck :(

I probably should've mentioned I'm on a clean install of Maverick

---

