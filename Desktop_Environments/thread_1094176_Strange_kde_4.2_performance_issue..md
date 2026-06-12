---
title: "Strange kde 4.2 performance issue."
date: 2009-03-12
forum: Desktop Environments
---

### Post by opensourcederry on 2009-03-12
Hi all,

I have noticed something strange with Kubuntu 8.10 running KDE 4.2

Say I click on the firefox icon to open the program.  While the window is opening the initial window appears and for a split second the area within the window is full of what appears to be 'chopped up graphics'

The best way to describe it is almost like a bad tv picture with interference.

It's not a world ending problem but annoying.   I have a Dual Core Intel e2180 machine with 2gb ram and an nvidia 8500 graphics card with 512mb ram so I don't think the machine is an issue.

Any ideas?

cheers

osd

---

### Post by agim on 2009-03-12
Sometimes I get that too. I assume that it is the firefox window not being drawn correctly as it starts up. I don't have this problem with kde apps. I generally just ignore it, and hope the devs clean it up in an upcoming update.

---

### Post by Zorael on 2009-03-12
Sort of like [this](http://bugs.kde.org/attachment.cgi?id=28151)?

[https://bugs.kde.org/show_bug.cgi?id=170462](https://bugs.kde.org/show_bug.cgi?id=170462)
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/254468](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/254468)

---

### Post by opensourcederry on 2009-03-13
> **Zorael said:**
> Sort of like [this](http://bugs.kde.org/attachment.cgi?id=28151)?

[https://bugs.kde.org/show_bug.cgi?id=170462](https://bugs.kde.org/show_bug.cgi?id=170462)
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/254468](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/254468)

That's it.  Upgraded my nvidia drive from 177 to 180 and it's now fixed.

cheers,

osd

---

