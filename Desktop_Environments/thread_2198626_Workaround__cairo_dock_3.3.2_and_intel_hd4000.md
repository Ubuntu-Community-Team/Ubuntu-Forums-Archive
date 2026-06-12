---
title: "Workaround : cairo dock 3.3.2 and intel hd4000"
date: 2014-01-09
forum: Desktop Environments
---

### Post by miousername on 2014-01-09
Hi at all,

for this christmas I bought a fantastic Acer S3-391, So I decided to install Debian Wheezy 7.3 and an old customized project of cairo dock (2.2-4)
but I found that it doesn't work , for some reason icons disappear when you hover the dock with the mouse.

I searched with google a solution but only opengl software rendering and cairo backend I found.

So I decided to found a workaround ( no a solution ) but something that let me to use this dock in my beautiful PC.

This patch is for cairo dock 3.3.2, to apply the patch follow this step:

$cp /path/to/patch /path/to/cairo-dock-3.3.2/
$patch -p1 <  cairo_dock_patch_intel_hd4000.patch

now compile with the same procedure.

Launch with:

$cairo-dock -O

I hope that this information could be usefull. ;-)

Bye!

---

### Post by ratamovic2 on 2014-01-12
Hi. Sadly I've got the same problem on my Dell computer...
But recompiling cairo-dock completely requires lots of space and work...

Do you think you could provide a binary for that please?
Many thanks.

---

### Post by matttbe2 on 2014-01-15
**@miousername**: glad to see you again! :-) I'm matttbe from Cairo-Dock team.

As you know I guess, we only have this bug with Intel HD4000 video card. It seems it's due to the video drivers but do you have any idea why?
Currently, if the dock detects it, it disables the OpenGL (except if we force it with -o or -O option). We decided to do that due to the high number of bug reports about this problem (and also due to the lack of answer from Intel devs in [this bug report]("https://bugs.freedesktop.org/show_bug.cgi?id=55036")).

Thank you for this patch! Is it maybe possible to give us a bit more informations about it? It seems that you decide to draw the reflects twice but for the first time (in your new function), you use a fully transparent colour, why? :-)
If you just use fully transparent reflects or with a size of 0 (config panel / Icons / reflects), does it fix this bug too?

---

