---
title: "Can't select items in nautilus icon view, selection jumps to a different item"
date: 2019-04-08
forum: Desktop Environments
---

### Post by peter-a on 2019-04-08
Ubuntu 19.04, Gnome 3.32.0

When I have more items in a folder than will fit into one screen's size, selecting an item by clicking once with the mouse causes the selection to jump to another item which the cursor is nowhere near. This is true for any type of item, e.g. images, folders or documents. It means that double clicking on an item often results in the wrong item opening, and right clicking an item always applies the right click to the wrong item.

I've uploaded a screencast to youtube: [https://youtu.be/6oPqA3tulK4](https://youtu.be/6oPqA3tulK4)

Depending on where I'm clicking, the whole selection of files visible might jump, as if I am clicking in the scroll bar rather than on an icon.

Any ideas?

---

### Post by peter-a on 2019-05-09
Anyone?

---

### Post by Claus7 on 2019-05-09
Hello,

checking your video I was able to enable back the desktop folder from nautilus. I had disabled it while checking for a different issue than yours. It seems that the org.desktop.background option handles this.

Anyway, I tried to check your issue in my system and it is working fine. So it seems that there is something wrong with your configuration. You could create a new user and check if the same thing happens. If yes, then it is a global issue, if not then it is related to your user account. You could try also a reinstallation of nautilus if you haven't tried already.

Do you get the same behavior when switching views? Just some initial ideas.

Regards!

---

### Post by peter-a on 2019-05-09
Thank you - that was an outstanding suggestion. It worked in another user account. I don't know what the problem was but I reset all the nautilus settings in dconf-editor (I had already reinstalled, no effect) and it's working perfectly again. Thanks again.

---

