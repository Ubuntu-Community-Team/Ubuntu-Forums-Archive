---
title: "Kiba-Dock error message"
date: 2007-04-15
forum: Desktop Effects &amp; Customization
---

### Post by jazoon on 2007-04-15
I have spent the past couple hours trying to figure out why kiba-dock won't work and I am just about ready to give up. When I would run the kiba-dock command nothing would come up but when I tried to run it in the terminal i got an error message. Can anyone tell me how to fix kiba-dock from bringing up this error:

> (kiba-dock:15317): Gdk-CRITICAL **: gdk_pixmap_new: assertion `(width != 0) && (height != 0)' failed


I am pretty much a beginner at linux, as far as trying to install something without using the apt-get install feature so cut me a break please :)

---

### Post by octesian on 2007-04-17
> **jazoon said:**
> I have spent the past couple hours trying to figure out why kiba-dock won't work and I am just about ready to give up. When I would run the kiba-dock command nothing would come up but when I tried to run it in the terminal i got an error message. Can anyone tell me how to fix kiba-dock from bringing up this error:



I am pretty much a beginner at linux, as far as trying to install something without using the apt-get install feature so cut me a break please

I was having the same problem untill I installed 'checkinstall'

> sudo aptitude install checkinstall

then I redid the "sudo checkinstall" parts of the how-to and assigned version numbers.
Now I'm getting this error:

========================= Installation results ===========================
make: *** No rule to make target `install'.  Stop.

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.


If anyone knows how to fix this, both of our problems might be solved.

---

### Post by Bostonian on 2007-07-13
I'm having the same problem. did either of yu ever get it working?

---

