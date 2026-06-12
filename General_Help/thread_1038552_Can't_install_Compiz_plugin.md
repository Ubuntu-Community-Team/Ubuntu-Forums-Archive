---
title: "Can't install Compiz plugin"
date: 2009-01-12
forum: General Help
---

### Post by R2D2! on 2009-01-12
I'm try&#305;ng to &#305;nstall the Headtrack&#305;ng plug&#305;n (the one that uses the webcam v&#305;a OpenCV). When I 'make' &#305;t, the follow&#305;ng error message appears:
```
ilhuitemoc@ilhuitemoc-laptop:~/headtracking$ make
convert   : headtracking.xml.in -> build/headtracking.xml
bcop'ing  : build/headtracking.xml -> build/headtracking_options.h
bcop'ing  : build/headtracking.xml -> build/headtracking_options.c
schema    : build/headtracking.xml -> build/compiz-headtracking.schema
make: *** No hay ninguna regla para construir el objetivo `build/headtracking.lo', necesario para `c-build-objs'.  Alto.
ilhuitemoc@ilhuitemoc-laptop:~/headtracking$
```
It's &#305;n Span&#305;sh, but essent&#305;ally &#305;t doesn't know how to bu&#305;ld the .lo f&#305;le.

I've googled, and I found other people w&#305;th the same error for d&#305;fferent plug&#305;ns, but I couldn't f&#305;nd a solut&#305;on. What can &#305;t be?

—Ilhu&#305;temoc &#948;

---

### Post by R2D2! on 2009-01-13
*bump*

I forgot to ment&#305;on that I've &#305;nstalled Comp&#305;z from GIT, v0.7.9. I've &#305;nstalled everyth&#305;ng but compiz-gnome, because &#305;t says &#305;t's un&#305;nstallable.

—Ilhu&#305;temoc &#948;

---

### Post by R2D2! on 2009-01-25
*bump*

---

