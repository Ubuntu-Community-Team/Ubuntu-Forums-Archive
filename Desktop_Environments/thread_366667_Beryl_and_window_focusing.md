---
title: "Beryl and window focusing"
date: 2007-02-21
forum: Desktop Environments
---

### Post by Snaiper on 2007-02-21
Hello, sorry if my english is not perfect.

I am have ubuntu feisty with latest on this time program version.
My vcard is nvidia 5600, driver is official from nvidia site, 9746.
My beryl version is  0.1.9999.2.

I am solved problem with black/white screens using --use-copy.
And all works ok, but today i am got a big beryl trouble.

Program windows does not recognize any clicks on elements (buttons, text areas). I am can move windows, but if window is minimized, i cant restore him.

I am cleared all my beryl settings, reinstalled twice all components, but it does not help me.
Also i am tried 1.4 version. Same bug.

---

### Post by Snaiper on 2007-02-21
Hello again.
I am found solution for this problem. Today i am upgraded few libs (libdrm2 and libxrandr) from current feisty fawn repo. Downgrading this libs cured my system.

---

