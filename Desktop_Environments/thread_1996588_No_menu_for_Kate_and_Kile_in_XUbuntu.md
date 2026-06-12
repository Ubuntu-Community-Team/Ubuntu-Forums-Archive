---
title: "No menu for Kate and Kile in XUbuntu"
date: 2012-06-04
forum: Desktop Environments
---

### Post by etienoo on 2012-06-04
Dear all,

I just installed XUbuntu 12.04 on my laptop.

I also installed Kate and Kile (which, I know, are for KDE environments), and I have no menus available for both applications. By menu, I mean the "file", "edit", "tools", etc.

This might come from the fact that both applications are now compatible with Unity, which shows the menus on the topmost part of the screen. This is not the case of KUbuntu, which gives menus for each application in its dedicated window.

Did you encounter this problem? If yes, could you help me on finding a solution?

Many thanks,

---

### Post by anaconda on 2012-06-04
I have xubuntu 12.04 and kate installed.
Works without problems. And menus work too.

I have not installed kile.

Sorry cant help you more...

EDIT: Did you install from xubuntu CD? or did you just install xubuntu-desktop to an already installed ubuntu?

---

### Post by etienoo on 2012-06-05
I installed from a live USB. I already got a previously installed version of Ubuntu 11.10 (with Kile and Kate, working well).
I formatted and reinstalled the "/" partition, but I kept the "/home/me" partition, which means that previous settings from Kile and Kate might have been kept.
Actually, when I reinstalled Firefox, all my previous modules, history, etc., were there.

---

### Post by etienoo on 2012-06-05
OK, I got it: I precisely had to remove the previous settings from my Ubuntu 11.10.

I just deleted the .kde directory (well, I kept a copy, just in case).
And it now works fine!

Thanks for the (indirect!) help.

---

