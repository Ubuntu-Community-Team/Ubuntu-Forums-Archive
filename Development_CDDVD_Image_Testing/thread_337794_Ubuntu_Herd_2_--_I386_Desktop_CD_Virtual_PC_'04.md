---
title: "Ubuntu Herd 2 -- I386 Desktop CD Virtual PC '04"
date: 2007-01-13
forum: Development CD/DVD Image Testing
---

### Post by spd106 on 2007-01-13
Test case type: Ubuntu Herd 2 -- I386 Desktop CD
Image ID: 20070111.1
Date of testing: 2007-01-13
md5sum confirmed: Yes
Pass/Fail: [COLOR="Red"]Fail[/COLOR]
Bugs: [#79117]("https://bugs.launchpad.net/ubuntu/+bug/79117") and I think this one [#59618]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/59618")

Basically the live won't boot with the default settings. You need to select a vga setting with either 16 or 32 bit colours, not the default 24. Because of #59618 after boot you need to restart the X server after changing the default bit to either 16 or 32 in the /etc/X11/xorg.conf. Next I've found that the mouse won't work, so all navigation has to be done through the keyboard. Going through ubiquity works fine until the locale selection, I tried to tab to proceed but it doesn't work. So I can't install to a .vhd.

---

