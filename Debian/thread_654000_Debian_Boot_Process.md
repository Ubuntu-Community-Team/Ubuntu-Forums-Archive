---
title: "Debian Boot Process"
date: 2007-12-30
forum: Debian
---

### Post by amrclutch1 on 2007-12-30
The boot process output for debian is quite messy, what files can I alter to change the formatting? I want it to show like

```

Mounting root filesystem       [Done]

```

with the [Done] in green or [FAILED] if it... failed. How could I do this, PCLinuxOS shows an example of this, I think.

This is what I am talking about
[http://www.bootsplash.org/Image:Verbose-mode.jpg](http://www.bootsplash.org/Image:Verbose-mode.jpg)

---

### Post by maybeway36 on 2007-12-30
Try adding quiet to the end of the kernel line in menu.lst like:
```
kernel		/boot/vmlinuz-2.6.22-3-686 root=/dev/hda1 ro quiet
```
It works in Ubuntu, not sure if Debian does or not (I've never really cared what my computer said when booting.)

---

### Post by amrclutch1 on 2007-12-31
That helps, but how can I change it to how I want, there has to be a way, after all, it's linux.

---

### Post by kellemes on 2008-01-01
> **amrclutch1 said:**
> That helps, but how can I change it to how I want, there has to be a way, after all, it's linux.


Well, it is GNU/Linux so it should be possible indeed.
Have you asked at the [Debian forums]("http://forums.debian.net/")?

Personally I like the "not so slick" output of Debian, it sort of belongs to Debian, boring but functional. :)

---

### Post by kellemes on 2008-01-01
[Splashy]("http://splashy.alioth.debian.org/wiki/start")

---

