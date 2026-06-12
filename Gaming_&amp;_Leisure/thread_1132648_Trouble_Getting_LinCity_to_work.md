---
title: "Trouble Getting LinCity to work"
date: 2009-04-22
forum: Gaming &amp; Leisure
---

### Post by ProfWilliamWang on 2009-04-22
Hello,

I downloaded LinCity from their download URL [http://lincity-ng.berlios.de/wiki/index.php/Download/Installation]("http://lincity-ng.berlios.de/wiki/index.php/Download/Installation")

I followed the instructions to install. During installation the addionatal packages did not install: physfs; sdl_gfx; sdl_image; sdl_ttf.

I managed to install the sdl-ttf, sdl_image and phsfs packages but now I'm getting the following error:
> 
lincity-ng: error while loading shared libraries: libSDL_gfx.so.13: cannot open shared object file: No such file or directory

I've tried to download it from the LinCity website

[http://download2.berlios.de/lincity-ng/sdl_gfx-2.0.13.x86.package]("http://download2.berlios.de/lincity-ng/sdl_gfx-2.0.13.x86.package")

but is appears that the link is broken.

How else can I get this package? It doesn't appear in apt-get as far as I can tell.

Thanks

---

### Post by Grishka on 2009-04-22
[apt://libsdl-gfx1.2-dev]("apt://libsdl-gfx1.2-dev"). oh, and there's no need to compile from source. lincity 2.0 is in the repos. [apt://lincity-ng]("apt://lincity-ng"). uh, but you're probably not on jaunty yet. so just wait three more days and upgrade, lincity 2.0 will be there.

---

### Post by ProfWilliamWang on 2009-04-22
Thank for the reply.

I saw libsdl-gfx1.2-dev but it seemed to have a lot more in it than just the required libSDL_gfx.so.13.

How would I know that libSDL_gfx.so.13 was in libsdl-gfx1.2-dev?

Yeap, not on Jaunty just now using 8.10. Waiting and looking forward to it.

For now I'll download libsdl-gfx1.2-dev and keep trying to get it to work for the experience of it. Fairly new to Linux but loving it all. Just need someone to show me what was possible (which my firend did a couple fo weeks ago) and I'm hooked :)

---

### Post by ProfWilliamWang on 2009-04-22
I apt-get install(ed) libsdl-gfx1.2-dev but am still getting the error.

lincity-ng: error while loading shared libraries: libSDL_gfx.so.13: cannot open shared object file: No such file or directory

It would seem that libSDL_gfx.so.13 is not a part of libsdl-gfx1.2-dev.

---

### Post by Grishka on 2009-04-22
> **ProfWilliamWang said:**
> <SNIP>

How would I know that libSDL_gfx.so.13 was in libsdl-gfx1.2-dev?

I would search for "sdl gfx" in synaptic, or look here: [https://launchpad.net/ubuntu/+search?text=libSDL_gfx.so.13](https://launchpad.net/ubuntu/+search?text=libSDL_gfx.so.13).

> **ProfWilliamWang said:**
> I apt-get install(ed) libsdl-gfx1.2-dev but am still getting the error.

lincity-ng: error while loading shared libraries: libSDL_gfx.so.13: cannot open shared object file: No such file or directory

It would seem that libSDL_gfx.so.13 is not a part of libsdl-gfx1.2-dev.

it should be. you sure you did ./configure before jam? again, it compiles well on jaunty.

---

### Post by ProfWilliamWang on 2009-04-23
OK. Sorry I'm not following.

I did ```
sudo apt-get install  libsdl-gfx1.2-dev
```

So libsdl-gfx1.2-dev is now installed. What is the next step I need to so to get libSDL_gfx.so.13 where it needs to be to get this working? A step-by-step would bea greatly appreciated.

Thanks for your help.

---

