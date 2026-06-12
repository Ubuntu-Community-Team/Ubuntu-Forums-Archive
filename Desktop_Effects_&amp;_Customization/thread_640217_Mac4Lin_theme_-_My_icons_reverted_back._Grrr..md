---
title: "Mac4Lin theme - My icons reverted back. Grrr."
date: 2007-12-13
forum: Desktop Effects &amp; Customization
---

### Post by Roasted on 2007-12-13
I had the Mac4Lin theme installed as well as the icon package. Everything looked identical to  Mac. In fact, I have a laptop running the exact same Ubuntu Gutsy 7.10 OS and the exact same Mac4Lin theme. Both systems appeared to be identical. The laptop still has the theme running fine, whereas the desktop I am posting from had some changes reverted.

I have no idea how it happened. But now instead of the red/yellow/green circles in the top/right of windows, I have the _ square X. Also, my window border is a bright maroonish color... I didn't change this, I don't know how it changed.

Anybody an expert on this matter?

---

### Post by FuturePilot on 2007-12-13
Sounds like you installed Emerald. There's two ways to not use Emerald. The first way is to just uninstall Emerald. However if you want to use Emerald at some later point and don't want to uninstall it do this
```
gedit .config/compiz/compiz-manager
```
Put this in there.
```
USE_EMERALD="no"
```
Then the next time you restart Compiz you will be using the gtk-window-decorator.
If you ever want to use Emerald just change "no" to "yes" in that file.

---

### Post by Roasted on 2007-12-14
Is it supposed to show up as a blank document?

---

### Post by FuturePilot on 2007-12-17
> **Roasted said:**
> Is it supposed to show up as a blank document?

Yes. It actually doesn't even exist by default.

---

### Post by infra_red_dude on 2007-12-19
A simpler method is to install Emerald (rather than uninstalling it) and use the bundled Emerald theme. Mac4Lin ver.0.4 has been released now. Check it out.

---

### Post by CCBalla10 on 2007-12-19
> **infra_red_dude said:**
> A simpler method is to install Emerald (rather than uninstalling it) and use the bundled Emerald theme. Mac4Lin ver.0.4 has been released now. Check it out.

i have and thank you for making this pack...i really can't thank you enough

---

