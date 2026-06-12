---
title: "Not able to customise where &quot;accessories&quot; are in the menu"
date: 2012-04-29
forum: Desktop Environments
---

### Post by Dameentsia on 2012-04-29
As you can see in this picture:
[IMG]http://i.imgur.com/bEjGH.png[/IMG]
I cannot change where "Accessories" are in the XFCE menu.  It does not show up in the config menu.  It just always stays at the top of the list and I would like to move it. :L  Btw, I am using Xubuntu 12.04, just incase that matters.

---

### Post by Toz on 2012-04-29
Do you have a ~/.config/menus/xfce-applications.menu file? If so, can you post its contents? We might be able to fix it manually.

---

### Post by Dameentsia on 2012-04-29
> **Toz said:**
> Do you have a ~/.config/menus/xfce-applications.menu file? If so, can you post its contents? We might be able to fix it manually.

Here are the contents of the file you specified:
[http://pastebin.com/raw.php?i=aKa1aPgU](http://pastebin.com/raw.php?i=aKa1aPgU)

I could probably fix this if I screwed around with it enough, but I would rather know exactly what to do the first time, just incase I have a similar issue.  Thanks again!

**EDIT:** I fixed it. xP  All I had to do was remove the "<Deleted/>" tag under the Accessories name.  Thanks for helpming me discover that config file. :P

---

### Post by Toz on 2012-04-29
Glad to hear you got it all worked out. Can you mark this thread as "Solved" using the "Thread Tools" link above?

---

