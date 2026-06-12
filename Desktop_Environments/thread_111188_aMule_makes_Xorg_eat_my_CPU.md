---
title: "aMule makes Xorg eat my CPU"
date: 2006-01-01
forum: Desktop Environments
---

### Post by gobfrey on 2006-01-01
When I'm running aMule, after running it for half an hour or so, the processor load shoots up to 100%.  Checking in system monitor, it's Xorg that's running at 100%.  Everything else runs slowly.

  If I close aMule, everything's fine.

Why is that?

Adam

---

### Post by pyronicte on 2006-04-12
I have this behaviour too, any clues?

---

### Post by gobfrey on 2006-04-17
I did a fresh install and everything's fine.  I believe it was the 3d graphics card driver.

--
Adam

---

### Post by john_markh on 2006-10-16
Fresh install of what?
aMule or Ubuntu?

---

### Post by Hoshimaru on 2007-06-01
Well... I always had that 100% issue with aMule and therefore only used eMule on a windows box.
With Feisty I also installed amule to see if it improved. Not at all... 100% as soon as it starts downloading.

Well... I've been searching around and someone suggested installing wxgtk2.8 and it's i18n support...
This seemed to have solved to problem for me. It's happily downloading and my CPU remains at 600Mhz, 6% load instead of 1.6Ghz with 100% load.

---

### Post by DrSlump on 2007-11-17
> **Hoshimaru said:**
> Well... I always had that 100% issue with aMule and therefore only used eMule on a windows box.
With Feisty I also installed amule to see if it improved. Not at all... 100% as soon as it starts downloading.

Well... I've been searching around and someone suggested installing wxgtk2.8 and it's i18n support...
This seemed to have solved to problem for me. It's happily downloading and my CPU remains at 600Mhz, 6% load instead of 1.6Ghz with 100% load.

Hi,
i compiled amule cvs (date of yestwerday) on ubuntu 7.10 32bit using wxwidgets 2.8 and i have the same issue with amule: it keeps the cpu to 100% load :(

---

