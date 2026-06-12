---
title: "How to right-click with right-click disabled"
date: 2020-02-28
forum: Desktop Environments
---

### Post by dbee on 2020-02-28
I disabled right click on my hp pavillion on ubuntu 19.10 because middle/right click kept shutting my browser tabs.

But i find it hard to save pics and use the 'inspect element' that usually comes up when you right click on something.

But today out of the blue, i click something and the right click box appeared. I have no idea what key combination i clicked ...

And i was unable to reproduce it. But it must be possible ...

Can anyone help ? how do i right click with right click disabled ?

Thanks,

---

### Post by vanadium on 2020-02-28
If on a laptop, could have been a combination of the "Fn" key and the "Menu" key, which for me coincides with the right "Ctrl" key. In many applications, "Shift+F10" does the same. Beware that that right-click menu relates to where your text cursor is, not where your mouse pointer is.

You could create a shortcut key and attach the command "xdotool click 3" to it to allow yourself issuing a right-click from the keyboard. You may need to install xdotool first, as it is not installed by default.

---

