---
title: "How do I change the color depth?"
date: 2005-08-03
forum: Desktop Environments
---

### Post by FNM on 2005-08-03
I just installed Ubuntu, but the screen is set at 32-bit (millions of colors, I think), and my monitor only supports 16-bit (thousands of colors). How do I change the color depth?

---

### Post by heimo on 2005-08-03
There may be a way to do it in GUI tool too, but this is (almost) the way I'd do it.

Edit /etc/X11/xorg.conf
change DefaultDepth to 16 (I think it's in screen section). Close programs, hit ctrl+alt+backspace. If everyhing was ok, you're now using 16 bit color depth.

To edit configuration file enter this in terminal (Applications->System Tools->Terminal):
sudo gedit /etc/X11/xorg.conf

---

### Post by FNM on 2005-08-03
[QUOTE=heimo]There may be a way to do it in GUI tool too, but this is (almost) the way I'd do it.

Edit /etc/X11/xorg.conf
change DefaultDepth to 16 (I think it's in screen section). Close programs, hit ctrl+alt+backspace. If everyhing was ok, you're now using 16 bit color depth.

To edit configuration file enter this in terminal (Applications->System Tools->Terminal):
sudo gedit /etc/X11/xorg.conf[/QUOTE]

Thanks.

---

