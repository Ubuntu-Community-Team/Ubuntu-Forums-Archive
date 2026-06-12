---
title: "Remote Desktop with Dual Monitors(Black screen on viewer)"
date: 2010-11-08
forum: Desktop Environments
---

### Post by TheShadow124 on 2010-11-08
I recently did a clean install to upgrade to 10.10 and I also got a 2nd monitor recently after upgrading. I want to be able to connect remotely to my desktop like I used to from my phone, but when I connect I get a black screen the size of my full desktop(both monitors) and I can move the mouse/type... 


Any ideas? sorry I do not know what diagnostic info you guys might need.


Thanks in advance

---

### Post by TheShadow124 on 2010-11-09
Bump?

---

### Post by TheShadow124 on 2010-11-11
Turns out it was compiz causing my problems, typing the following fixed my problem:

```
metacity --replace
```

Source:  [http://ubuntuforums.org/showthread.php?t=1177707](http://ubuntuforums.org/showthread.php?t=1177707)
Post #7

For use without disabling conpiz:
[Http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1407458](Http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1407458)
Post #4

---

