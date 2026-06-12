---
title: "After eject, DVD tray closes immedialely &amp; too fast"
date: 2008-11-03
forum: Desktop Environments
---

### Post by bedege on 2008-11-03
Hi

I've done a fresh new install of Xubuntu Intrepid Ibex. Since then, when I ask the system to eject my DVD drive, the tray opens and closes again immediately, leaving me no time to grab the disk... That happens whatever I do to eject the disk: eject command, right click on Desktop with thunar, k3b or brasero.

Any hint or similar behavior ?

---

### Post by Halow on 2008-11-03
I've been experiencing that intermittently (just about every other time). Also having issues with unmounting during those same occurrences.

[edit: I forgot to mention, using Ubuntu Intrepid Ibex.]

---

### Post by bedege on 2008-11-04
> **Halow said:**
> I've been experiencing that intermittently (just about every other time). Also having issues with unmounting during those same occurrences.

[edit: I forgot to mention, using Ubuntu Intrepid Ibex.]

Does it occur since you upgraded to Intrepid Ibex ? If you have it under Ubuntu, it rules out a Xubuntu specific bug.

---

### Post by exploder on 2008-11-04
The new udev 124-9 in the Intrepid backports repo fixes the eject problem.

---

### Post by Halow on 2008-11-04
This worked!

Only difference was in Ubuntu it was in Proposed, not Backports.

---

### Post by jenkinbr on 2008-11-04
I also have this problem in Ubuntu 8.10.  I will give this fix a try.

---

### Post by blue13130 on 2008-11-04
> **exploder said:**
> The new udev 124-9 in the Intrepid backports repo fixes the eject problem.

Thanks, I was having this problem in Ubuntu and your solution solved it.

---

### Post by bedege on 2008-11-04
Thanks, udev 124-9 solved the issue. Had to install it "by hand" after downloading the deb package, as synaptic could not find this recent version in backports or proposed.

Cheers

---

### Post by exploder on 2008-11-04
Glad I could be of help! I subscribed to the bug report, that is how I knew how to fix this.

---

### Post by Ecclesia on 2008-11-04
Thanks for figuring this out.  I couldn't believe it when I copied over my 7.10 install last night (after the live CD worked beautifully) and then couldn't use my dvd drive this morning.  I'm surprised this bug made it to the final release and that the udev in "proposed" isn't on the official updates yet.  It makes it hard to recommend Ubuntu to members of my family, because who knows what's going to happen when they install it.

Another question - there are 55 other proposed updates.  On the whole is it safe to install them?  How long do they take to make it to the recommended updates?

---

### Post by exploder on 2008-11-04
I have the other 55 updates installed with no problems, your results may vary. I read the description for each update and decided the risk was low for messing anything up.

---

### Post by rfurman24 on 2008-11-15
The udev update did not fix mine.

---

