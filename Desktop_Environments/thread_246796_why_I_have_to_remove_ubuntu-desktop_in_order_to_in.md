---
title: "why I have to remove ubuntu-desktop in order to install tpd?"
date: 2006-08-29
forum: Desktop Environments
---

### Post by baosheng on 2006-08-29
I wanna install a program called tpd that will enable me to use speical keys of IBM thinkpad.

But the synaptic said, in order to install tpd, ubuntu-desktop will be removed. How could this happen? 

What can I do? I think ubuntu-desktop is not desired to be removed.

---

### Post by lagagnon on 2006-08-29
That all sounds a bit fishy to me. There are at LEAST three other bits of software that can enable you to use ANY keys on any keyboard any way you want and they will not affect ubuntu-desktop. I suggest you check out:

[http://hocwp.free.fr/xbindkeys/xbindkeys.html](http://hocwp.free.fr/xbindkeys/xbindkeys.html)
[http://keytouch.sourceforge.net/](http://keytouch.sourceforge.net/)
[http://lineak.sourceforge.net/](http://lineak.sourceforge.net/)

---

### Post by skymt on 2006-08-29
ubuntu-desktop is safe to remove. It's... well... complicated. It's called a metapackage, and rest assured, your system will work fine without it.

However, Synaptic wouldn't remove it unless it also needs to remove something else. What else is Synaptic threatening to remove?

---

