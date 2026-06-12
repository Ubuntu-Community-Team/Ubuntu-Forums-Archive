---
title: "Urban Terror runs in wine, but not natively"
date: 2010-01-04
forum: Gaming &amp; Leisure
---

### Post by patchwork on 2010-01-04
Hi all,
I have an annoying, but not incapacitating problem.  I can get UT to run flawlessly through Wine, but if I instead run UT natively I have no video and must Alt-Tab to exit.  I would prefer to run the game natively, so any input would be appreciated.

---

### Post by patchwork on 2010-01-05
OK, not exactly sure why this was working in Wine but not natively, but I now have it running well in both.  I had to change my autoexec.cfg file to include :

seta r_customheight "1024"
seta r_customwidth "1280"    //The resolution of my monitor

Also, could run game before changing resolution if:

seta r_fullscreen "0"

...but now works fullscreen natively, so the last line is not necessary.

If anyone knows why this was working in Wine before these changes, I'm still curious.

---

### Post by Joon Lee on 2012-11-13
How on Earth did you get it to work in wine? can you tell me how? I keep getting an error that says "Urban Terror cannot be installed with Windows Installer earlier than Windows Installer 5.0"

Did you use the zip installation?

---

