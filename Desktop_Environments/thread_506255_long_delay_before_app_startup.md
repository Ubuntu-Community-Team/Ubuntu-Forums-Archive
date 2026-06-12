---
title: "long delay before app startup"
date: 2007-07-21
forum: Desktop Environments
---

### Post by xlinuks on 2007-07-21
At some point applications in Gnome or KDE start launching after a large delay (when the system isn't even under heavy load). I experienced this on different distros on both intel 32 and amd64. Now I have Ubuntu 7.04 and same thing. I wanna know if someone knows why this happens and how to solve it. (It's not the Ubuntu date bug).
I haven't ever experienced such weird delays on windows.
I think it has something to do with the X Server not managing locking/unlocking events in time (I might be wrong about events, but I'm pretty sure it's about the X Server because commands, applications and compilers like "ls", "javac", "gcc" launch immediately while those which require a GUI take a huge delay).

I found more posts like mine but none of them seems to have an answer, it's like a mystery. Here's one of them:
[http://ubuntuforums.org/showthread.php?t=355084](http://ubuntuforums.org/showthread.php?t=355084)

---

