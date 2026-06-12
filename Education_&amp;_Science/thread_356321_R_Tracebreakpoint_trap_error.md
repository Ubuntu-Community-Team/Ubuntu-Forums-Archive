---
title: "R Trace/breakpoint trap error"
date: 2007-02-08
forum: Education &amp; Science
---

### Post by samden on 2007-02-08
I was using R today in the terminal, and had just had it open for a few minutes when it exited without warning, going back to the usual Ubuntu terminal prompt. All it displayed as an error was:

```
Trace/breakpoint trap
```

Now whenever I try to use R in the terminal in either Gnome or XFCE4, the terminal prints all the R login messages (right down to 'Type 'q()' to quit R.'), then instantly prings "Trace/breakpoint trap" below that and exits R.

I can run R in a terminal screen (Cntrl-Alt-F2), but obviously cannot produce plots here without having a window manager.

Does anyone have any idea what could be happening here?

Edit:
Rkward will not run either - the Rkward window opens then suddenly closes again, with Trace/breakpoint trap showing in the terminal from which I was starting Rkward.

---

### Post by akniss on 2007-02-08
[http://en.wikipedia.org/wiki/SIGTRAP](http://en.wikipedia.org/wiki/SIGTRAP)

Have you installed all recommended packages?  ```
sudo aptitude install r-recommended
```
Have you tried reinstalling R?  Judging from the number of google hits for the error message, it is a very common problem, and certainly not specific to R.  Maybe a required library or package is not being loaded successfully.  Try a reinstall of R and see if the problem goes away.

---

