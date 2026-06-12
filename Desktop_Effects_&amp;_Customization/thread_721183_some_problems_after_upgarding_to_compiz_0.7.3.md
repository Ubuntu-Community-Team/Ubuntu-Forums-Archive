---
title: "some problems after upgarding to compiz 0.7.3"
date: 2008-03-11
forum: Desktop Effects &amp; Customization
---

### Post by chunchengch on 2008-03-11
I added Quattro's Eyecandy Repository to the sources.list and then installed Compiz 0.7.1 from Synaptic, this morning, the Compiz was upgraded to 0.7.3, but after reboot, I find some problems and hope there is solution to solve.

1. can not use mouse in nautilus, although this problem can be solved by reloading window manager, it is really annoying that I have to do this every time I open nautilus.

2. every time, after turning the cube with middle button of mouse, the window border will disappear, I have to reload window manager again

3. freewins plugin does not work any more


any solution or reply is appreciated.
Reply With Quote

---

### Post by Zorael on 2008-03-11
Installing compiz from foreign repositories is unsupported! Bad boy/girl! :>

Before software is added to the official sources, they're thoroughly tested because Canonical/the community end up being somehow "responsible" to make it work for everyone. Random developer/compiler/packager X (no offense intended) doesn't need to aim that high. There are certainly exceptions to this rule, but it's enough of a trend to give one pause.

That said, my general advice whenever things just stop working would be to completely remove it and then reinstall. There should be a **complete removal** option in Synaptic. Or just enter this in a terminal:
```
$ sudo apt-get remove --purge compiz* libcompiz* libdeco* emerald* libemerald*
```

Just 'apt-get purge' may work too, I'm used to using aptitude and it doesn't accept wildmarks.

Then reinstall from your repository of choice.

---

