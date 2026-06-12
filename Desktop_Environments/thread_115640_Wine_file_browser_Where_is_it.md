---
title: "Wine file browser?? Where is it"
date: 2006-01-11
forum: Desktop Environments
---

### Post by shade11 on 2006-01-11
I remember at one time when I used an .exe installer, after i installed there was a window that was a file browser that showed everything in the virtual C:\ drive. How do I get to that?

---

### Post by eddiewalker on 2006-01-11
Just navigate to your fake windows root.  Try ~/.wine/fake_windows/

---

### Post by leech on 2006-01-11
Download Sidenet, and it'll install some cool stuff (like IE and the explorer style browser)

[http://sidenet.ddo.jp/winetips/config.html](http://sidenet.ddo.jp/winetips/config.html)

Leech

---

### Post by shade11 on 2006-01-11
[QUOTE=eddiewalker]Just navigate to your fake windows root.  Try ~/.wine/fake_windows/[/QUOTE]
Tried it, doesn't work.

It showed this:
```

ian@Jevelxelwen:~$ ~/.wine/fake_windows/
bash: /home/ian/.wine/fake_windows/: No such file or directory
```

---

### Post by zoiks on 2006-01-11
I think what eddie meant was to browse there with nautilus or some such.

You might be thinking of "winefile".  I don't know which package it comes from (it may just come standard with wine) but when I type "winefile" at the command prompt I get a windows-explorer like window.

---

### Post by arnieboy on 2006-01-11
[QUOTE=shade11]Tried it, doesn't work.

It showed this:
```

ian@Jevelxelwen:~$ ~/.wine/fake_windows/
bash: /home/ian/.wine/fake_windows/: No such file or directory
```[/QUOTE]
open **nautilus**
press **ctrl+H**
double click **.wine**
from thereon it shd be obvious.

---

### Post by shade11 on 2006-01-14
[QUOTE=arnieboy]open **nautilus**
press **ctrl+H**
double click **.wine**
from thereon it shd be obvious.[/QUOTE]

Thanks arnieboy :D

---

