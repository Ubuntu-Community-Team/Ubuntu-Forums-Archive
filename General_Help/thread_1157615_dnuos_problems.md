---
title: "dnuos problems"
date: 2009-05-12
forum: General Help
---

### Post by functionofxy on 2009-05-12
Hi. I tried to install dnuos ([http://bitheap.org/dnuos/](http://bitheap.org/dnuos/)) as indicated by the project's website.

Here's what I got when running it:
```
$ dnuos
Traceback (most recent call last):
  File "/usr/local/bin/dnuos", line 3, in <module>
    import dnuos
ImportError: No module named dnuos

```

any thoughts?
seems like a python problem...

maybe I'm missing a prereq.

---

### Post by functionofxy on 2009-05-13
bump?

Sorry for the trouble. Can't figure out how to fix this.

---

### Post by phovey on 2009-05-18
I too am having this problem and can't figure out how to solve it...any help would be great, thanks!

---

### Post by RobRum on 2009-05-18
I'm also having this problem. Interestingly, I installed this app on Ubuntu 8.10 and had no problems running the program, it only broke when I upgraded to 9.04

Perhaps a change in python has caused it to stop working? Any ideas much appreciated :)

---

### Post by functionofxy on 2009-05-18
I posted in the dnuos trac

[http://bitheap.org/dnuos/trac/ticket/30](http://bitheap.org/dnuos/trac/ticket/30)

---

### Post by RobRum on 2009-05-18
Hey guys,

I managed to fix this problem! :)

Turns out that for some reason, Python 2.6 on Ubuntu 9.04 no longer uses /site-packages/ for user installed scripts, instead using /dist-packages/

So to fix the problem and get DNUOS working again, I simply moved everything from

/usr/local/lib/python2.6/site-packages/

to

/usr/local/lib/python2.6/dist-packages/

using a sudo session of nautilus ("sudo nautilus" in terminal)

Hope this helps, and if any more experienced Linux users know a more correct/elegant way of achieving this, please post :)

---

### Post by functionofxy on 2009-05-18
works perfectly for me!

nice catch.

---

### Post by dwalker109 on 2009-07-04
Thanks very much, I symlinked dnuos/ from site-packages to dist-packages, which worked a treat.

---

