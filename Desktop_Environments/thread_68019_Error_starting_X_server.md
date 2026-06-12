---
title: "Error starting X server"
date: 2005-09-21
forum: Desktop Environments
---

### Post by Chris Williamson on 2005-09-21
I took the leap last week and switched from Windows to Linux/Ubuntu. All was pretty much fine until today. After doing the daily update of packages, there was a little light bulb icon up at the top, and after clicking it there was a notice to restart my machine so that one of the new things could take effect. I got to the Ubuntu logo screen with all the status messages scrolling up underneath it, then a black screen alternating with text a couple of times before getting this message:

Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?

Then here's what seemed to me to be the relevant part of the information that followed:

xf860OpenSerial: Cannot open device /dev/input/mice
No such file or directory.
Configured mouse: cannot open input device
PreInit failed for input device "Configured Mouse"
No core pointer

Fatal server error:
failed to initialize core devices

Please consult the The X.Org Foundation support at [http://wiki.X.org](http://wiki.X.org)

Anyone have any ideas? I've done some Googling and found one promising suggestion, modprobe psmouse followed by startx, and modprobe mousedev too, but the problem persists. I have only a beginner's knowledge of Linux, but I'm pretty quick on the uptake with this kind of stuff, so I should be able to fix this if someone can just give me an idea what it could be.

Thanks.

Chris Williamson

---

### Post by Chris Williamson on 2005-09-21
Oops. This should be in the Breezy Badger forum. I'll repost there.

---

