---
title: "Nautilus taking 50% of cpu time"
date: 2008-05-19
forum: Desktop Environments
---

### Post by hughc1 on 2008-05-19
Folks,

This system is very slow.  My gnome-system-monitor shows a continous flux between 100% and 50% cpu usage.  The processes window of gnome-system-monitor shows Nautilus as a big user?  kern.log has several messages like this-
May 15 14:51:10 bunny kernel: [ 2632.097800] [fglrx] interrupt source 10000000 successfully disabled!

Attempt to fix the problem.
Uninstalling nautilus and reinstalling did not help.

Workaround with undesired consquences
If System>Preference>gTweakui-nautilus and unchecking 'Use Nautilus to draw background' frees up the cpu but doesn't display desktop icons.

System
The system is Hardy 8.04, kernel 2.6.24.-17 generic.  The hardware AMD Sempron 2200 with 1 gig of memory.  ATI graphics.

Any ideas?

---

### Post by Bd0g on 2008-05-19
I can confirm this

The issue is definetly located to the latest updates.. 
Did a reinstall and then downloaded them and the same problem came back.

Nautilus turned into a resource hog and swallowed 800mb of memory. Killing the process only ended with it launching a new nautilus window and repeating the process of filling the memory again.

When I avoided downloading them, the system was ok.

---

### Post by Bd0g on 2008-05-20
My issue might be somehow related to having a 1gb movie on my desktop (mkv format but dont know if that places any special significance on this)

In launchpad, a few issues sounded quite similar:

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/187547](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/187547)
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/228739](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/228739)
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/219878](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/219878)

---

### Post by hughc1 on 2008-06-05
I want to add that the desktop icons can be enabled if you go to System>Preferences>File Management> Preview and set
'Other Previewable Files' to 'Show Thumbnails' "Never".
After this step go to the  gTweakUI-Nautilus Preferences box and enable Always use browser mode and Use nautilus to draw desktop.
With these settings the cpu idles to a resonable level.

---

