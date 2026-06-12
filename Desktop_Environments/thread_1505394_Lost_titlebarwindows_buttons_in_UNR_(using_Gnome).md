---
title: "Lost titlebar/windows buttons in UNR (using Gnome)"
date: 2010-06-09
forum: Desktop Environments
---

### Post by bilekbp on 2010-06-09
Hi, I recently installed Ubuntu Netbook Remix on my netbook, but couldn't stand the interface "improvements." I switched back to Gnome through System->Administration->Login Screen, and this was working great for me for a while.

However, just a little bit ago my windows lost their title bars and maximize/minimize/close buttons. They show up maximized, and I can't manipulate them other than through closing them in the application menu itself, or tabbing to another window.

I have created a second user, when I log into that second user this problem does not exist.

Can someone help me figure out how to get my title bars and window buttons back?

Thanks!

---

### Post by nilarimogard on 2010-06-09
That's because of maximus:

sudo apt-get remove maximus

---

