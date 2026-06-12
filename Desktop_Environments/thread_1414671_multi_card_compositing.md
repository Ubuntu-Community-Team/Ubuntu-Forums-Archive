---
title: "multi card compositing"
date: 2010-02-23
forum: Desktop Environments
---

### Post by Sojurner on 2010-02-23
I am aware that you can not use compiz (because of compositing) with multiple video cards in Ubuntu. Does anyone know if this is an issue with just ubuntu. Can you use compositing for all those nice effects in other distros of linux, say fedora and such like that?

I have a system with 2 video cards and 4 monitors and want to sue compiz-fusion but am unable to because of the limitation of not being able to enable compositing on my desktop.

---

### Post by warp99 on 2010-02-23
> **Sojurner said:**
> I am aware that you can not use compiz (because of compositing) with multiple video cards in Ubuntu. Does anyone know if this is an issue with just ubuntu. Can you use compositing for all those nice effects in other distros of linux, say fedora and such like that?

I have a system with 2 video cards and 4 monitors and want to sue compiz-fusion but am unable to because of the limitation of not being able to enable compositing on my desktop.

You can use multiple video cards. This guy here is doing it with three nVidia 8800GTXs, but he's using XGL:

[http://www.youtube.com/watch?v=1DWzuIreDGA](http://www.youtube.com/watch?v=1DWzuIreDGA)

Normally you can't do this because of a limitation in X-server, not Ubuntu. So if you move to any other distro you'll have the same issue since they all use X-server.

---

### Post by Sojurner on 2010-02-23
I do have SLI on my 2 video cards but i dont believe that has anything to do it.

Yea i am aware of that guy. Ive spoken with him on several ocassions, however he is using a hack. He has been working on a way to do it without using XGL which is sorta how he got it to work. Since XGL is no longer supported it wont work without hacks.. but you have pretty much answered my question. Thanks

---

