---
title: "How can I check my graphics card has been installed properly?"
date: 2009-03-25
forum: General Help
---

### Post by aceplayer97 on 2009-03-25
Besides checking if it is installed using the Hardware Drivers section what else can I do to check if it is working properly? I always see people talking about some glrx rendering thing which helps determine if a graphic card is working. How does that work? And this is a completely random question but does enabling compiz effects for Ubuntu slow the performance of games?

---

### Post by evilaim on 2009-03-25
This is a good thread.  Generally if you can enable 3d effects and all that stuff, your card is installed.  But if you are getting choppy graphics then maybe your card doesn't have 3d rendering or something along those lines.

Yes, compiz uses quite a bit of resources and it might slow down your game play depending on how good your computer is.  If you're running a quad core with 8 gigs of ram or something insane like that, then I wouldn't worry too much about it.

---

### Post by Chemical Imbalance on 2009-03-25
```
glxgears
```

---

### Post by ajgreeny on 2009-03-25
```
glxinfo
``` will also give you lots of data that may help, particularly with the success or not of direct rendering, near the top of the output.

---

