---
title: "JWM : How to pass ALT key presses to applications?"
date: 2010-09-04
forum: Desktop Environments
---

### Post by keithpeter on 2010-09-04
Hello

JWM is small and fast and enough of a window manager for my needs. I'm using it with XDM and Thunar on top of an Ubuntu minimal install.

I've noticed that the ALT-F and ALT-O-V short cuts in applications such as OpenOffice don't work with JWM, but they do with openbox on the same set up.

Anyone got their .jwmrc set up so it passes the ALT key presses? I've googled but have not found anything specific apart from one mention of JWM grabbing the alt key.

Solved: OK I googled harder and found

[http://manpages.ubuntu.com/manpages/gutsy/man1/jwm.1.html](http://manpages.ubuntu.com/manpages/gutsy/man1/jwm.1.html)

Scroll down for the bit about key bindings. None of the key bindings must use A as mask, else ALL the alt key presses are captured by JWM. I'm just using the Windows key now for JWM stuff and the ALT keys work in all my applications.

---

### Post by v_2e on 2011-06-02
Hello!
Could you please post your .jwmrc contents here?
and note your JWM version please.

Thanks!

---

