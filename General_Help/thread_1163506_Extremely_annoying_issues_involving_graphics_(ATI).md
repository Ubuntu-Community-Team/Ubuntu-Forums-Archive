---
title: "Extremely annoying issues involving graphics (ATI)"
date: 2009-05-18
forum: General Help
---

### Post by OV3RDRIV3 on 2009-05-18
I know, ATI sucks with linux, everybody has problems, blah blah.

most of the problems I see with people have with ATI is when using compiz.
I, however, cannot enable effects in plain ol' linux either
when I go to system>preferences>appearance>effects
and click either normal or extra, my screen does a bunch of switching around
it says "searching for drivers: 0%" with a little bar that goes back and forth, then eventually just says "desktop effects could not be enabled"

when I try envy, the installation goes completely fine
when I try installing ATI restricted drivers, the installation goes completely fine
as we all know, the last step to any of these is to reboot, when I reboot, I get this screen
[http://www.youtube.com/watch?v=sFzRUkQS7_U&feature=email](http://www.youtube.com/watch?v=sFzRUkQS7_U&feature=email)

unfortunately, there's no way around that.
the only thing I can do at that point is go to recovery mode, go to netroot (one of two shell options in that menu)
and put this in:

sudo apt-get remove xorg-driver-fglrx

after I put that in, all of what I just installed is just...gone and it was all worthless.

my graphics card is ATI Radeon HD 3100 
I am running Ubuntu 9.04 (Jaunty)

btw, I also installed the driver straight from ATI/AMD's site, no help either.

any help would be greatly appreciated.
I would love to get the effects working, as well as compiz after this.

---

### Post by OV3RDRIV3 on 2009-05-19
bump

---

