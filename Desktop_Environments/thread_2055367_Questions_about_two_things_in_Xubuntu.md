---
title: "Questions about two things in Xubuntu"
date: 2012-09-09
forum: Desktop Environments
---

### Post by lou002 on 2012-09-09
Hello all!

I have finally settled on a distro--xubuntu. I love the way it's designed and I love how lowkey it is. I even changed the panel so it's on the bottom like windows. 

Anyway, I had two quick questions:

1. Can I map the Windows/Super button (the one the logos on it) to the applications menu?

2. Is there away to enable the middle mouse button/scroll wheel to be able to drag and scroll? I can scroll with it but I mean hold down the middle button and then moving the mouse to scroll

I've tried googling and didn't find anything myself; I come here only as a very last resort. If I came here otherwise, I'd be clogging up the boards lol

Thank you in advance.

---

### Post by vasa1 on 2012-09-09
> **lou002 said:**
> ...
1. Can I map the Windows/Super button (the one the logos on it) to the applications menu?
...
I hope someone answers you! All I could find was this:
> My windows button does not work in the Keyboard Settings > Shortcuts.

The windows button (also known as the superkey) not working as a modifier is related to the toolkit, GTK+ in the case of Xfce. If you want to have the windows-key working we recommend you to upgrade GTK+ to at least version 2.10.0.

from: [http://wiki.xfce.org/faq](http://wiki.xfce.org/faq)

I don't know whether that is out-of-date or not.

---

### Post by LewisTM on 2012-09-09
In Xfce 4.10, the Super key alone can be mapped to command
```
xfce4-popup-applicationsmenu
``` 
[https://launchpad.net/~xubuntu-dev/+archive/xfce-4.10](https://launchpad.net/~xubuntu-dev/+archive/xfce-4.10)

I don't think you can set the middle button for drag and scroll in a general way. This must be set by the application, not the desktop environment. For instance it works in evince, the PDF viewer.

Cheers!

---

### Post by december0123 on 2012-09-09
> **lou002 said:**
> Hello all!
2. Is there away to enable the middle mouse button/scroll wheel to be able to drag and scroll? I can scroll with it but I mean hold down the middle button and then moving the mouse to scroll


In firefox settings go to advanced and search for "Use autoscrolling" or something like that.

---

### Post by cmcanulty on 2012-09-09
very cool can I get the same effect in gnome classic with a command to make super key open a menu like that?

---

