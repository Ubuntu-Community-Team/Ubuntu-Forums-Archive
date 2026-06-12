---
title: "[SOLVED] Annoying windows title bar issue"
date: 2008-12-23
forum: General Help
---

### Post by luca_linux on 2008-12-23
Every time I enable Visual Effects (even to "Normal" not "Extra") I get this annoying issue of windows title bars (both when the windows are maximized and when they are unmaximized).
First of all, I am running Gnome 2.24.1 on Ubuntu 8.10 (but I had this issue with the previous versions as well), my graphics card is a nVidia GeForce 7300 LE (I know it's kind of entry level and obsolete by now, but I don't play games nor do 3D authoring stuff) currently using the nVidia 177 driver.
Here is a screenshot pointing out the issue: [http://img244.imageshack.us/img244/8564/screenshotsm9.png](http://img244.imageshack.us/img244/8564/screenshotsm9.png)

Is there a way to fix this? Maybe some specific parameter to set up in xorg.conf?

Thank you in advance.

---

### Post by .arean on 2008-12-23
It's a bug with compiz and nvidia. To fix it you can turn off compiz, change the theme or install the beta nvidia drivers.

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/99508](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/99508)

---

### Post by luca_linux on 2008-12-23
Oh, thank you very much. I'm updating the nvidia driver right now. :)

---

### Post by Tomatz on 2008-12-23
Sheesh???

Just use emerald ;)

---

### Post by luca_linux on 2008-12-23
As a workaround, I eventually decided to change the theme to Clearlooks (customized a bit by me though) rather than updating the nvidia driver, because I have read it will be available in the intrepid-backports repository soon. So the manual update is just not worth it.

---

### Post by Usufruct on 2008-12-23
> **luca_linux said:**
> As a workaround, I eventually decided to change the theme to Clearlooks (customized a bit by me though) rather than updating the nvidia driver, because I have read it will be available in the intrepid-backports repository soon. So the manual update is just not worth it.

I would say "just not worth it" is pretty relative.  For me, it was well worth the five minutes it took to download and install it, and it solved both the title bar display bug, and a bug I was having with AWN.

---

### Post by luca_linux on 2008-12-23
> **Usufruct said:**
> I would say "just not worth it" is pretty relative. For me, it was well worth the five minutes it took to download and install it, and it solved both the title bar display bug, and a bug I was having with AWN.
Of course. I was talking about the title bar bug only. ;)

---

