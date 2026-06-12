---
title: "Problem with mouse settings"
date: 2007-09-14
forum: Desktop Environments
---

### Post by Kenchu on 2007-09-14
If you press left and right mouse button at the same time, this simulates a middle mouse click. I dont want to have this feature. Is it possible to turn off?

Also, ive got a fourth mousebutton near the thumb. This one seems to to do the same thing as the middle mouse button. Is there some way to  make it do something else (like going to previous page in windows)?

Thanks

---

### Post by geraldm on 2007-09-14
create a backup file for /etc/X11/xorg.conf
Edit that file: in Section "Input Device"
  Identifier "Configured Mouse"

change line that says:
  Option    "Emulate3Buttons" "true"
to read
  Option    "Emulate3Buttons" "false"

logout; then login again.

As for the other button, there is a HOWTO for the mouse, which does explain how to
use additional buttons, but these features may vary with different types of mice.
A forth button, with a third button only emulated is a bit odd, so you may have to
customize based on trials.  
Try under [https://help.ubuntu.com/community/ManyButtonsMouseHowto](https://help.ubuntu.com/community/ManyButtonsMouseHowto)

Gerald

---

### Post by Kenchu on 2007-09-14
Thanks, the middle mouse simulation thing fixed. Maybe ill try fixing the thumb button some other time.

**EDIT**

I read the page you linked to and now the buttons work as desired Thanks!

---

