---
title: "Compiz &amp; window transparency"
date: 2011-11-17
forum: Desktop Environments
---

### Post by orrorin on 2011-11-17
Hello,

I've Unity (3D) and Compiz running on my Ubuntu 11.10 machine. I've enabled Transparency on 'Normal' windows from the "Opacity, Brightness, Saturation" feature.

However, these settings affect the entire window. How can get a transparency effect similar to Windows Aero, where only the Windows title bar is transparent but the window body is not? Also, is it possible to set transparency level on a per application level? e.g. I'd like my text editors to work at a different transparency level from say my music player.

Thanks.

---

### Post by orrorin on 2011-11-17
I dug around this and from what I understand, the emerald window decorator is now part of the compiz-decorator. (I tried to install emerald with sudo apt-get install emerald, but it complained that the package could not be found.) But, I can't find info about how to import emerald themes into compiz.

Is any one using emerald themes through compiz on a Unity 3D desktop (running 11.10)?

---

### Post by Copper Bezel on 2011-11-17
Yeah, Emerald is what you're looking for. Emerald definitely hasn't been rolled into the Compiz decorator - it's just essentially abandoned at this point. (The only rolling-in that happened was between the gtk-window-decorator and unity-window-decorator, which were temporarily separate in 11.04.) Try _[this]("http://ubuntuforums.org/showthread.php?t=1870792")_ to get it working under 11.10.

---

