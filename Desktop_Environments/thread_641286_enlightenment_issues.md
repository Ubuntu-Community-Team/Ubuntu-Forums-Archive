---
title: "enlightenment issues"
date: 2007-12-15
forum: Desktop Environments
---

### Post by TechnoJunky on 2007-12-15
I'm trying to install enlightenment via [http://ubuntuforums.org/showthread.php?t=97199&highlight=E17+cvs](http://ubuntuforums.org/showthread.php?t=97199&highlight=E17+cvs) instructions.  I've found solutions to all the problems I've encountered except for this one.  If anyone has any tips I'd appreciate it greatly.  Below is the error(s) I'm getting.

src/theora.c:161: error: ‘EnthrallTheora’ has no member named ‘yuv’
src/theora.c:162: error: ‘EnthrallTheora’ has no member named ‘yuv’
src/theora.c:163: error: ‘EnthrallTheora’ has no member named ‘yuv’
src/theora.c:163: error: ‘EnthrallTheora’ has no member named ‘yuv’
src/theora.c:165: error: ‘EnthrallTheora’ has no member named ‘yuv’
src/theora.c:166: error: ‘EnthrallTheora’ has no member named ‘yuv’
src/theora.c:167: error: ‘EnthrallTheora’ has no member named ‘yuv’
src/theora.c:167: error: ‘EnthrallTheora’ has no member named ‘yuv’
src/theora.c:174: error: ‘EnthrallTheora’ has no member named ‘td’
src/theora.c:174: error: ‘op’ undeclared (first use in this function)
src/theora.c:175: error: ‘EnthrallTheora’ has no member named ‘to’
src/theora.c:177: error: ‘EnthrallTheora’ has no member named ‘to’
src/theora.c:177: error: ‘og’ undeclared (first use in this function)
src/theora.c:187: error: ‘tc’ undeclared (first use in this function)
src/theora.c:189: error: ‘EnthrallTheora’ has no member named ‘to’
src/theora.c:191: error: ‘EnthrallTheora’ has no member named ‘td’
src/theora.c:192: error: ‘EnthrallTheora’ has no member named ‘to’
src/theora.c:199: error: ‘EnthrallTheora’ has no member named ‘to’
src/theora.c: In function ‘enthrall_theora_finish’:
src/theora.c:221: error: ‘EnthrallTheora’ has no member named ‘to’
src/theora.c:222: error: ‘EnthrallTheora’ has no member named ‘td’
src/theora.c:226: error: ‘EnthrallTheora’ has no member named ‘yuv’
src/theora.c:227: error: ‘EnthrallTheora’ has no member named ‘yuv’
src/theora.c:228: error: ‘EnthrallTheora’ has no member named ‘yuv’
make: *** [src/theora.o] Error 1

---

### Post by Half Step on 2007-12-15
Unless you're developing E17, try the [Ubuntu packages installation]("http://e17blog.tuxfamily.org/e17blog_en.php/post/2007/08/22/HowTo-Install-Enlightenment-on-Ubuntu-Gutsy-Gibbon") instead. If you're using a flavor other than Gutsy, follow the links. . . .  It was fairly straightforward---worked first time out of the box for me.  E17 still has issues, but it recovers from it's own hiccups very well.  YMMV, of course.

Best,
    HS

---

### Post by worldwithoutgurus on 2007-12-16
E17 binary packages are old and/or buggy - and for beginners only.

TechnoJunky, did you install libtheora-dev ? It is required for enthrall.

Enthrall builds fine on my system.

---

### Post by TechnoJunky on 2007-12-16
I used HalfStep's suggestion and it installed fine.  Now I just have to learn my way around. :)  Thanks for the help!

---

### Post by smartboyathome on 2007-12-17
By the way, that tutorial has been outdated. Try [this tutorial]("http://ubuntuforums.org/showthread.php?t=546746") instead.

---

