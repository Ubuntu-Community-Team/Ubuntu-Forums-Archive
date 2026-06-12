---
title: "X.org: no screens found - problem"
date: 2005-07-04
forum: Desktop Environments
---

### Post by southy on 2005-07-04
Sorry if my posting's a little out of style, it's because I'm writing in elinks (text mode browser) here.
Why? Because my X doesn't work (I guess you figured that out ;-) )  
I've got something new to play around with here: a netfinity 5500. It's got an S3 card 86C775/86C785 with 1024KB.  
When I start X.org, it tries all the different graphic modes and the log states for any of them:
e.g.: 800x600: Insufficient memory. 
This repeats with all aviable modes and results in the end - of course - in: "no valid modes found" and the X-Server won't start. In xorg.conf all looks well, the Graphic card (S3) and Monitor are detected correct. 
Also at least some of the modes definitely correct and really should work (e.g. 1024x768 in various versions) 
I added "VideoRam  1024" - no effect. I created my own xorg.conf - no effect. What else can I do? Any ideas?
Thanks very much in advance, southy

---

### Post by southy on 2005-07-05
I tried with a warthy live CD (XFree86 instead of X.org):
This time, right after starting the boot process (must be more less the first thing that happens after GRUB) a message comes up that my graphics adapter can not be detected and I have to choose how many lines/colums to display (for text mode).
Then it boots up and XFree86 starts without a problem, but only in 640x480.

So perhaps it could be a solution to switch from X.org to XFree86? Is this possible in hoary? How could I do that? Then I would only need to define the line/colums for text mode somehow and set XFree to 1024x768 manually somehow and it should be going.

Thanks for all you help in advance,
southy

---

