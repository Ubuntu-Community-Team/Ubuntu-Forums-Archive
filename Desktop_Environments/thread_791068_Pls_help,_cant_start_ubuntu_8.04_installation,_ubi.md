---
title: "Pls help, cant start ubuntu 8.04 installation, ubiquity failure"
date: 2008-05-11
forum: Desktop Environments
---

### Post by phrksho on 2008-05-11
I'm in dire need of help. Just spent the last couple hours trying to get ubuntu to install...

I get ubuntu to boot but when i hit install ubuntu or demo ubuntu I get a screen saying my video device or screen is not configured correctly and three options: Configure, Shut down, Continue. If i hit continue it crashes. When i try configuring, none of the drivers on the test work.

My pc is a Dell XPS Gen 3 with an ATI Radeon X800 SE and an HP w2207 monitor on DVI.

I tried erasing the splash screen from the command line by pressing F6 on the boot screen and replacing it with break=bottom. When it got to the command prompt i editted my xorg.conf adding Driver "radeon" and "vesa" but got a [fail] both times when it tried starting Ubiquity for the installation.

I'd really appreciate all the help i could get.
Thx

---

### Post by rogier.de.groot on 2008-05-12
Have you tried selecting safe mode when the liveCD starts?
Otherwise, I'd try installing using the alternate CD. That's what I did after the livecd failed to work properly on my laptop, which now works well enough to post messages on internet forums ;)

---

