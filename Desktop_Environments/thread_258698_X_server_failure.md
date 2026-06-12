---
title: "X server failure"
date: 2006-09-16
forum: Desktop Environments
---

### Post by brdmartin on 2006-09-16
OK, so I installed Ubuntu (never even seen a linux OS before this), and it was running fine for about 2 weeks, when I get a Failed to start X server error. I had been recently adding and removing programs to see which ones I liked, which I think may have caused the problem. 

When I choose to diagnose the problem, it says: fatal server error, no screen found. I have tried various screen settings using the sudo dpkg-reconfigure xserver-xorg command, with no results. the detailed information looks like this:

(**) screen "default screen" (0)
(**) Monitor "Acer 77e"
(**) Device "NVIDIA Corporation NV40? [unknown nVidia Card]
(ww) The directory "/usr/share/X11/fonts/cyrillic" does not exist. Entry Deleted from font path

any suggestions would be great, and remember I am completely new at this, thanks
Brian

---

### Post by statue on 2006-09-16
Did you perhaps install the update that crashes X on nvidia drivers?

---

### Post by brdmartin on 2006-09-16
> **statue said:**
> Did you perhaps install the update that crashes X on nvidia drivers?

I don't think so, unless it somehow did an automatic update of the nvidia driver. Is there a method of checking the nvidia driver version?

The error message said that the cyrillic font was missing, If I reinstalled the font, might that fix the problem?

---

### Post by Paul41 on 2006-09-18
I was having this problem and somehow my linux-restriced-modules got removed which caused the problem.  Try to install linux-restricted-modules-Your Kernel Version (mine was linux-restricted-modules-2.6.15-27-686).

---

