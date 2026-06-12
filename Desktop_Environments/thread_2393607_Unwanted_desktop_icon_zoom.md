---
title: "Unwanted desktop icon zoom"
date: 2018-06-05
forum: Desktop Environments
---

### Post by rconway on 2018-06-05
Using ubuntu 18.04 (gnome).

Have found that if I zoom the file manager view in 'icon' view mode, then it has the side-effect of also zooming the desktop icons.

This is really annoying. E.g. use zoom to view some photo thumbnails in a directory - discover that all my desktop icons are massive.

Please tell me there's a setting to 'fix' this behaviour.

Thanks in advance.

Richard

---

### Post by PaulW2U on 2018-06-05
Sorry, there's no setting available until we get nautilus 3.28. Ubuntu 18.04 is still on version 3.26.

I can't remember the reason why we're stuck on that version but it might be something to do with users upgrading from Ubuntu 16.04 and keeping their Unity desktops.

The developers are aware of this issue. See the following bug reports:

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1537606](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1537606)
[https://bugzilla.gnome.org/show_bug.cgi?id=761610](https://bugzilla.gnome.org/show_bug.cgi?id=761610)

---

### Post by vanadium on 2018-06-05
With nautilus 3.28 the problem would readily go away as you would no more have any desktop icons that could become massive! Desktop icon support was removed from nautilus 3.28, which is why Ubuntu sticked with 3.26 for now.

---

### Post by rconway on 2018-06-06
Thanks for info.
Have installed nemo as a workaround.

---

### Post by rconway on 2018-06-06
You mean that desktop icons will be no more?
Not much of a 'desktop' if you can't put anything on it!

---

### Post by vanadium on 2018-06-07
Gnome has fully gotten rid of desktop ion support on the desktop. Since the beginning, the ability to put icons there was turned off by default. Now they axed it completely.
You still will be putting your active windows on the desktop. Just not launchers or documents. Launchers are conveniently placed in default Gnome on the Dask, or on a dock, or which are very quickly summoned after pressing the Windows key and typing a few letters. Also no documents any more. Documents will need to live in their proper folder - or in one scratch folder similar on how it was when you placed them on the desktop, and can be put on the desktop within a Files window if needed (e.g. have the command "nautilus ~/Desktop" autostart when you login).
Desktop support will likely return to Gnome, but then via third party extensions.

---

