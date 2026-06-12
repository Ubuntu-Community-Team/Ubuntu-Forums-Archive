---
title: "How do I add a panel, when there are no panels left on my desktop?"
date: 2009-08-17
forum: Desktop Environments
---

### Post by tmadsen on 2009-08-17
Hi, I just restarted jaunty, and now my top panel is gone. It was the only one I had. How do I add it again? I have tried looking in gconf-editor to see if there was some entry that might relate to panels, but found none.

Please help me :)

---

### Post by mcduck on 2009-08-17
try running "gnome-panel" to see if it will start.

As long as gnome-panel is running you will always have at least one panel, it's not possible to remove last panel in any other way than by stopping "gnome-panel".

---

### Post by tmadsen on 2009-08-17
Thanks. It turned out that gnome-panel was not installed - weird, since I certainly didn't remove it. When I did apt-get install gnome-panel, it was installed fine. When trying to run it, it told me something was wrong with the gnome-globalmenu applet.

Anyways, thank you for helping, I now have my panel back :)

---

