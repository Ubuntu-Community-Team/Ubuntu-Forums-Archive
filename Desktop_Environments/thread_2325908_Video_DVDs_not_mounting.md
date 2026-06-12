---
title: "Video DVDs not mounting"
date: 2016-05-26
forum: Desktop Environments
---

### Post by Poncho on 2016-05-26
Hello all - Having an issue with Xubuntu 16.04.

When I insert a Video DVD they will not auto-mount. I can force the system to mount the DVD by going to VLC and pointing the program to /dev/sr0 and then everything works.

What makes this strange is that Data DVDs and CDs both automount with no issues.

Any thoughts?

Thanks
Steve

---

### Post by SeijiSensei on 2016-05-26
Video DVDs cannot be mounted like data discs.  They don't contain a recognizable filesystem because of [CSS]("https://en.wikipedia.org/wiki/Content_Scramble_System") encryption.

---

### Post by kansasnoob on 2016-05-26
It's a bug:

[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/1577768](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/1577768)

[The fix]("https://git.kernel.org/cgit/utils/util-linux/util-linux.git/commit/?id=55ad13c26fe5d0e606be5a83937f31b8cf576588") will land in Yakkety very soon, then we'll have to do a [SRU]("https://wiki.ubuntu.com/StableReleaseUpdates") to get it fixed in Xenial.

---

