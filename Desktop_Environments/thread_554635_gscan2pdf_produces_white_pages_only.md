---
title: "gscan2pdf produces white pages only"
date: 2007-09-19
forum: Desktop Environments
---

### Post by fdimmling on 2007-09-19
gscan2pdf v 0.9.16 with all recommended packages installed scans pages properly, however the resulting pdf file has white pages only. It is a rather big file, e.g. 1mb for 3 pages b/w, but neither evince, kpdf nor acroread displays anything but 3 white pages.

Any ideas?

Friedrich

---

### Post by JeffreyRatcliffe on 2007-10-09
> **fdimmling said:**
> gscan2pdf v 0.9.16 with all recommended packages installed scans pages properly, however the resulting pdf file has white pages only. It is a rather big file, e.g. 1mb for 3 pages b/w, but neither evince, kpdf nor acroread displays anything but 3 white pages.

I've only just spotted this post - the best way to get help for gscan2pdf is the gscan2pdf-help mailing list on the website on sourceforge.

But now I'm here - I released 0.9.17 last week, so install that. If you are still only getting white pages, start gscan2pdf with ```
gscan2pdf --debug
``` and post the output from the command line.

---

### Post by rkh on 2007-10-13
As gscan2pdf has added features -most of which I use at least from time to time- the scan window has grown in size. Unfortunately, now I can't get to the scan button in this window unless I move my  top and bottom panels to the right and left of the screen. It does work but its awkward. I can shrink the window to make it narrower but not shorter. Maybe there is a trick I'm missing.

In any event, thanks once again for a great  program.

---

### Post by JeffreyRatcliffe on 2007-10-13
> **rkh said:**
> As gscan2pdf has added features -most of which I use at least from time to time- the scan window has grown in size. Unfortunately, now I can't get to the scan button in this window unless I move my  top and bottom panels to the right and left of the screen.

I don't have this problem, as the number of options in the scan dialog depends on the scanner. If you can post a screenshot illustrating the problem, then I'll see what I can do. You're not the only one to have reported this.

---

### Post by rkh on 2007-10-14
Here are a couple of screenshots illustrating the issue and my workaround.

---

### Post by JeffreyRatcliffe on 2007-10-15
> **rkh said:**
> Here are a couple of screenshots illustrating the issue and my workaround.

I'm going to fix this by putting the device-dependent options **next** to the others, rather than below them

---

