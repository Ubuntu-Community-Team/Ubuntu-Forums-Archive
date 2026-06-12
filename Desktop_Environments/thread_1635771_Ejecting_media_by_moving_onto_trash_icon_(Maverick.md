---
title: "Ejecting media by moving onto trash icon (Maverick)"
date: 2010-12-02
forum: Desktop Environments
---

### Post by z5t on 2010-12-02
Hello,

I'm stuck with the following problem - maybe someone already has a solution? (I'm using Maverick.)

I'm trying to make my trashcan icon act like in MacOS when I move media icon on it. It means media gets unmounted and (if "mechanized") ejected. Ubuntu per default refuses to unmount the media, a modification in nautilus is necessary. I personally prefer the drag-and-drop solution over the right-click, but of course is a matter of taste.

I was following this thread:

[http://ubuntuforums.org/showthread.php?t=504002](http://ubuntuforums.org/showthread.php?t=504002)

I downloaded the sources for nautilus, opened the .c file to edit it and I realized that unfortunately the function has been redesigned. Instead of "volume" it uses "mount" variable. The "patch" for nautilus described in the quoted thread wouldn't work.

Does someone have a "patch" of this kind for the current version of nautilus?

Many thanks in advance

z5t

---

