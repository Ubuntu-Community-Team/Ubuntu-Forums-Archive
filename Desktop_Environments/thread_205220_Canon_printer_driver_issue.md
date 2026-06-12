---
title: "Canon printer driver issue"
date: 2006-06-28
forum: Desktop Environments
---

### Post by Misterleebee on 2006-06-28
I have a canon mp360 printer scanner and have installed the compatible driver but when I print it only prints the page on a scale of 1/4 of the a4 sheet.  I have checked all the setting and need to know how to make it fill the page.

Has any one got any ideas to how this can be achieved?

---

### Post by bohboh on 2006-06-28
I had this problem with my ip4000 printer. After lots of playing around i ended up having to install [turboprint]("http://www.turboprint.de/english.html") drivers with the latest version of cups (1.2.1).

This may not apply to you since yours is a different model, but the problems are the same.

You can get a trial version of the drivers.

---

### Post by patrickfromspain on 2006-06-28
I had also problems with my IP3000 and did the same as bohboh: installed cups 1.2.1 (very easy: just configure make and make install, no problems) and turboprint. Now it works perfect

Bohboh: does the check ink work for you???

---

### Post by bohboh on 2006-06-28
I dont even have a check ink option.

Where is it? Had a look at printer preferences and nothing.

---

### Post by patrickfromspain on 2006-06-28
If you go into xtpconfig -> Toolbox there's a check ink options.. although mine is grayed out, even when opening as sudo.

---

### Post by bohboh on 2006-06-28
In the help file it says

> This is because TurboPrint has to access the parallel port directly.

Could be parr port only. Is yours usb? Mine is. What dya think?

---

### Post by patrickfromspain on 2006-06-28
mine too. So I suppose no ink check :(

---

### Post by bohboh on 2006-06-28
For what its worth. I have sent turborprint an email asking for clarification on this, and if not possible then if there are any other tools which can inform us on ink levels.

I'll let you know.

---

### Post by bohboh on 2006-07-04
Got a reply from turboprint.

I managed to get the printer button working. But the printer would no longer print. So its one or the other, they apparently are looking into it.

The thing to do is run xtpsetup and change the device path to /dev/usblp0 . Then run xtpconfig and you should have the check ink button enabled, Then change the device back to get the printer working again.

Good luck. :)

---

