---
title: "unable to resize window in preferences screen resolution"
date: 2009-01-17
forum: General Help
---

### Post by Russell Burrows on 2009-01-17
I had Ubuntu 8.1 32 bit working on my toshiba laptop l305d-s5892

I decided to install Ubuntu 8.1 64 bit version.

When I try to resize windows in firefox it works....closing a window works fine

But when I open a window in system(or any window in System preferences they refuse to resize and refuse to close) preferences to try and change my screen resolution from 600 to 1200 then I am unable to change the window size to reach the apply button and the window refuses to close when pressing X
The only way to close this window is to right click on the minimized window and select close.

Thank you for reading this.

---

### Post by mikewhatever on 2009-01-17
You can't shrink that window, because apparently, it opens at its minimum size, but there seems to be no problem enlarging it. What's the resolution you should be using?

---

### Post by Russell Burrows on 2009-01-17
I am stuck at 640 x 480 (4:3)and when I select the 1280 X 800(16:10)resolution there is no way for me to scroll the window down to press apply and so I am stuck at 640 X 480 resolution.

Any other way to change my screen resolution?

Thank you.

---

### Post by mikewhatever on 2009-01-17
sudo xrandr -s 1280x800

---

### Post by Russell Burrows on 2009-01-17
> **mikewhatever said:**
> sudo xrandr -s 1280x800

Ahhhhhhh!

aplications acesories terminal!

It worked!

Thank you.

Thank you.

---

### Post by Russell Burrows on 2009-01-18
I want to press the thanks buttons and the thread solved in thread tools but they are gone?

Anywho thanks for solving my problem as it was driving me nuts trying to find a fix.

Once again thank you.

---

### Post by mikewhatever on 2009-01-18
Yes, those two functions were disabled because apparently, the crumbling server that hosts the forums couldn't cope with all the load.
I am mighty glad it worked, you are most welcome.

---

