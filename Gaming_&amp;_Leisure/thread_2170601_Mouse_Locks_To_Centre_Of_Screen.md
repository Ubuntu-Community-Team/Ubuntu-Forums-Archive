---
title: "Mouse Locks To Centre Of Screen"
date: 2013-08-26
forum: Gaming &amp; Leisure
---

### Post by kschlichther on 2013-08-26
I just moved to Ubuntu last week (like I just scraped windows, the only OS on my drive is Ubuntu) and I like to multi-task alot. However when I'm in some full screen games, like zsnes I cannot move the mouse, even when minimized. The mouse remains locked to the centre of my screen no matter what. My only solution is to close out the program that is creating the issue. Is there another solution for this, like a setting I can disable a setting in Terminal or in the shell? Also, if anyone knows, I am also curious to understand why this happens. I would really prefer to avoid using a VM for applications that cause this issue as they are usually games, and games do not run well in a VM on an ATI/AMD video card

---

### Post by oldrocker99 on 2013-08-27
I've had that problem in Windows 7, but never with Ubuntu (or any of its derivitaves), and I can only suggest that you try a different mouse. I'll admit that trying a different mouse didn't work with Windows; I had to boot into Safe Mode and let it reinstall mysteriously disappeared drivers.

When all else fails, you can always CTRL-ALT-F1, log in to that screen, then do a sudo shutdown -r now to restart the system.

---

### Post by kschlichther on 2013-08-27
I found what may be the same issue here: [https://bugs.launchpad.net/ubuntu/+source/unclutter/+bug/61105](https://bugs.launchpad.net/ubuntu/+source/unclutter/+bug/61105)at the bottom someone mentions that the issue still exists in ubuntu 12.04. In addition it does appear to be "Jumping to the screen". A good tug on the mouse make it appear in a different place on the screen, but on the next screen refresh it is back in the centre. I tried rebooting from the shell, it had no effect. I also tried a different mouse

EDIT: Forgot to mention that I cannot kill un-clutter as it is not installed

---

### Post by DarkAmbient on 2013-08-28
Maybe you could try to launch zsnes with different configs?

[http://zsnes-docs.sourceforge.net/html/advanced.htm#config_files](http://zsnes-docs.sourceforge.net/html/advanced.htm#config_files)

It's documented for zsnes 1.5.1, you can check which version you got install with:

```
dpkg -s zsnes | grep Version
```

---

### Post by kschlichther on 2013-08-28
> **DarkAmbient said:**
> Maybe you could try to launch zsnes with different configs?

[http://zsnes-docs.sourceforge.net/html/advanced.htm#config_files](http://zsnes-docs.sourceforge.net/html/advanced.htm#config_files)

It's documented for zsnes 1.5.1, you can check which version you got install with:

```
dpkg -s zsnes | grep Version
```


I have the correct version, I tired fiddling about with some mouse related settings, no luck. In general it seems that any openGL application does this, similar to the bug I linked to above

---

