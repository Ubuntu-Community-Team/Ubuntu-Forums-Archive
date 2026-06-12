---
title: "After login, black screen with solid HDD light"
date: 2009-05-19
forum: General Help
---

### Post by parx86 on 2009-05-19
I have an issue where after I type my username and password, I get a black screen, with a solid HDD light.  If I Alt-F2 to another terminal window, I see some continuous scrolling about I/O errors or something similar (can't screenshot or I'd include it)

I suspected a HDD problem, but after running a full set of tests with PC-Check, everything passed 100%.

I've also tried disconnected my DVD drive to see if that might be causing a problem, but I still get the same results.

I have quite a bit of data on my home partition that I cannot access now, so I'd really like to find a solution to this, as I'd rather not go back to Windows.

Any help would be greatly appreciated!

---

### Post by maheshasolkar on 2009-05-19
What kind of video hardware do you have?

Can you go to another terminal (Alt-F3 may be) and try to examine the output of *dmesg*? Or the contents of */var/log/Xorg.0.log*? They might have some error messages that may be useful.

---

