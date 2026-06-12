---
title: "Windows freeze"
date: 2009-05-03
forum: General Help
---

### Post by uv2008 on 2009-05-03
Hello,

There is one minor problem that I have since I've replace my Ubuntu 8.10 32 bit with the new 9.04 64 bit. Whenever I am opening or resizing a window (either file or internet browser) there is about half a second of a delay/freeze where the graphics/fonts are blurry before it comes to normal. Any idea what that may be?

Thanks for any hint!

---

### Post by khelben1979 on 2009-05-03
One thing which comes to my mind is that maybe the upgrade destroyed your native graphics drivers?

One other thing that you can check is how it looks like in ```
cd /etc/init.d/
``` and then use [the man command]("http://en.wikipedia.org/wiki/Man_(Unix)") to check out these scripts to see if Ubuntu Jaunty have added something more to the system which wasn't there before the upgrade.

---

