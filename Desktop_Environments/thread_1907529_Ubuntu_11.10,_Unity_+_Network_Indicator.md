---
title: "Ubuntu 11.10, Unity + Network Indicator"
date: 2012-01-11
forum: Desktop Environments
---

### Post by creiss on 2012-01-11
Hey all,

Running 11.10 with Unity on my Notebook here.
For some reason I am now missing the network indicator icon.

Not sure what I did - any clues?

Thanks,
Cheers!
Chris

---

### Post by Krytarik on 2012-01-11
First, make sure "Network Manager" is there under "Startup Applications" and is enabled.

Also, you can run it manually to check if any error messages are popping out; via the Alt+F2 dialog, run:
```
nm-applet
```Hope it helps.

---

### Post by creiss on 2012-01-11
Huh,

Trying to launch nw-applet resulted in file not found.
(Re)installed it, and now it works again. I dont know why it dissapeared but what the heck, its working now!

Thank you so much for pushing me in the right direction!

<3

-Chris.

---

