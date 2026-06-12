---
title: "Java applet doesn't display properly when Visual Effects enabled"
date: 2007-12-06
forum: Desktop Effects &amp; Customization
---

### Post by lofftjm on 2007-12-06
I am using the Java Plugin for Firefox, both version 1.5.0_12 and 1.5.0_13 to display Oracle Forms on my desktop.  When I have the desktop Visual Effect set to "Normal" the applet window will appear but none of the contents will display.  When I set the the desktop Visual Effects to "none" the applet window functions properly.

My video card is a nVidia GeForce 6800.

Has anyone else encountered this?

---

### Post by schaumkeks on 2007-12-06
> **lofftjm said:**
> I am using the Java Plugin for Firefox, both version 1.5.0_12 and 1.5.0_13 to display Oracle Forms on my desktop.  When I have the desktop Visual Effect set to "Normal" the applet window will appear but none of the contents will display.  When I set the the desktop Visual Effects to "none" the applet window functions properly.

My video card is a nVidia GeForce 6800.

Has anyone else encountered this?

You may solve this with the comments for the Compiz Bug in Java:
[http://wiki.ubuntuusers.de/Compiz/Problembehebung#head-3de3c90266c70375fb5a8d5a6fcc1d98167524f9](http://wiki.ubuntuusers.de/Compiz/Problembehebung#head-3de3c90266c70375fb5a8d5a6fcc1d98167524f9)

Edit: Oops soory, that is german =)
Simply add the line
> AWT_TOOLKIT=MToolkit
to the file /etc/environment and restart.

Bye, schaumkeks

---

### Post by lofftjm on 2007-12-13
That solved the problem....thanks very much!

---

