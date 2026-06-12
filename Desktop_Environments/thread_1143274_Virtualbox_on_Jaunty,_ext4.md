---
title: "Virtualbox on Jaunty, ext4"
date: 2009-04-29
forum: Desktop Environments
---

### Post by maxwellcom on 2009-04-29
Hello,

I recently upgraded from Ibex to Jaunty with a fresh install.  I also decided to give ext4 a try.  Everything seems to be working great (and fast) with one exception.

I have a Virtualbox (OSE) image of Windows XP that I was using in 8.10.  In 9.04, I get a BSOD.

Has anyone else experienced problems with VBox images moving from 8.10 to 9.04 or from ext3 to ext4?  Suggestions?

Thanks for your help!

---

### Post by cariboo on 2009-04-30
I've been using VirtualBox on ext4 for the last three months and haven't had any problems through 3 or 4 complete installations. I also have it running in Karnic with no problem. I've been using the same images through all the changes.

---

### Post by HavocXphere on 2009-04-30
Have you tried removing all the checkboxes in the advanced section of settings...like VT-X etc.

---

### Post by maxwellcom on 2009-05-01
Thanks, HavocXphere, for your reply.  I did manage to locate the setting that was causing the issue under the Advanced tab:

Virtualbox > Settings > General > Advanced > changed "IDE Controller Type" from "PIIX4" to "PIIX3"

Now it works.

Thanks!

---

