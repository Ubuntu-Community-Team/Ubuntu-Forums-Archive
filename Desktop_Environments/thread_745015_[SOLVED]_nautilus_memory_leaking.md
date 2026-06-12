---
title: "[SOLVED] nautilus memory leaking"
date: 2008-04-04
forum: Desktop Environments
---

### Post by natirips on 2008-04-04
I have no Nautilus windows open, but system monitor says that** nautilus takes over 500MB **(530,1MB right now)** of memory**. **Is there a way to flush or clear this?** It's ubuntu 7.10, Nautilus 2.20.0 . I mean, I do have 2GB of RAM, but still, 500MB for zero opened windows is way too much...

---

### Post by detgar on 2008-04-04
You can restart Nautilus by pressing ALT+F2 and typing: killall nautilus
It's not graceful, but it's not that terrible either.
If the problem persists between shutdowns, you should investigate further and file a bug report.

---

### Post by natirips on 2008-04-04
Thanks, it returned to normal (it takes only 12MB now which seems more normal).

---

### Post by joebert on 2008-04-17
I'd like to add a few things about my situation if I may, since "kllall nautilus" seems to have got me going again without needing to reboot.

I've been working with several thousand images, some folders have as many as 2K images in them.
I have thumbnails being generated from the images, in icon view.
I have two file browsers open, I'm looking through A-Z subfolders on one side, selecting like-groups, and moving them to categories on the other side. The other side just has a bunch of folders visible.
Occasionally I open a few of the images using eyeofgnome, the application that seems to be the default when I double-click a thumbnail.

After something like 8 straight hours of doing almost nothing but this, the only exception being using the terminal and Opera web browser, I start having an issue where eyeofgnome just ignores me. It will not open anything. GIMP wouldn't do anything with the image either.

I placed the monitors in my panel so I could watch resource usage, mem usage was up around 80%/20% and swap usage was at 100%.

Before finding this thread I had two instances where this situation happened and both times my system became unresponsive forcing me to cut the power after about 30 minutes of disk reading. I started looking and found this thread immediately after eyeofgnome quit working this morning because rebooting is no fun.

Once I used  ALT+F2 -> "killall nautilus" my swap usage dropped down to about 48% and eyeofgnome started working again immediately after.

---

