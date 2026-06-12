---
title: "How to get ePSXe to run ISOs mounted to a virtual drive?"
date: 2009-08-18
forum: Gaming &amp; Leisure
---

### Post by Doval on 2009-08-18
I'm having problems with Mega Man Legends 2. With ePSXe, it froze right after the Capcom screen; with pSX, it froze shortly after the final boss. A bit of Google searching suggested that, at least in the case of ePSXe, the game gives problems when the ISO is run directly but works fine when the ISO is mounted to a virtual drive.

So I found this nifty little program called acetoneISO that lets me mount image files of various formats (iso, mdf, bin, etc) to any directory I want. Problem is, as far as I can tell, ePSXe's CDROM config asks for the /dev/ file, not the mount point. Normally one would fill in /dev/cdrom to run a game from a real disc, but I have no idea what to put in for a mounted ISO. I tried using /dev/cdrom as the device and mounting the ISO to /media/cdrom but that didn't work.

Is what I'm asking to do even possible? Thank you in advance.

---

### Post by HoKaze on 2009-08-21
As far as I know (although I may be wrong), you can't play mounted ISOs. Well you can load the ISO of course but not the directory in /mnt or /media.
(edit: after re-reading your post I assume this advice found via Google applies to the windows version, right?)

---

