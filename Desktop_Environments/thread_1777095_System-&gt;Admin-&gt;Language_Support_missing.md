---
title: "System-&gt;Admin-&gt;Language Support missing"
date: 2011-06-07
forum: Desktop Environments
---

### Post by syrag on 2011-06-07
I have no menu entry for System->Admin->Language Support, and it is not present in the menu editor. Which package do I need to install to get this?

---

### Post by Tamlynmac on 2011-06-07
I'm not certain which version of Ubuntu your using. For example, if your using 10.04/10.10 then it's the "language-selector". It's a gnome app. and should have been installed in 10.04/10.10 by default unless you did a custom install.

Assuming your using 10.04 or 10.10, you can assure that it's in the filesystem under "usr/bin/gnome-language-selector". If it's there and not listed in the menu, just create a menu item that links it in the system administration menu.

If not, use the synaptic package manager to install the "language -selector" that's the actual name of the file as viewed in the synaptic package manager.

Good Luck & hope this helps.

---

### Post by syrag on 2011-06-08
Thanks! It was not present. I installed it via synaptic and everything's fine now.

I installed 10.04 from a CD. I don't know why it wasn't installed by default.

---

### Post by Tamlynmac on 2011-06-08
Odd, I'll assume everything else was installed and operational. 

Please mark this thread solved and Good Luck. :popcorn:

---

