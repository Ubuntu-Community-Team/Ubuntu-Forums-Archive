---
title: "True Combat Elite install error: Not supported by C lib"
date: 2009-08-26
forum: Gaming &amp; Leisure
---

### Post by ngrieb on 2009-08-26
Hi everyone,
I installed ET because I wanted to try out True Combat Elite, as I thought it looked like a good Linux alternative to Counter Strike. Anyway, ET installed without any errors, I have sound and everything. I immediately tried installing True Combat (with the update 0.49b I think), but it would not install. I gave up and forgot about it until recently.

I keep getting the error: Not supported by C libs...
What C libs does it need? Can I get them somehow? Seems like this should be an easy fix, but I don't know where to start.

Thanks in advance to anyone that can help.

---

### Post by ngrieb on 2009-08-27
Ok, I got it to work, but now it wont download any files from the servers. Is there a auto download button somewhere in the menus that I missed?

---

### Post by ngrieb on 2009-08-29
Tried an uninstall and reinstall, and when trying to install True Combat I get a C lib error, although it seems like it will attempt to proceed with the install. The install script itself says 0.48 not 0.49 curious? mislabeled perhaps? Help please ... anyone?

---

### Post by ngrieb on 2009-08-29
Ok, what happened was that TC:E created a profile under ~/.wolfet/ or something to that effect, and the profile was set to read only, which made it impossible to save my settings. [SOLVED]

---

