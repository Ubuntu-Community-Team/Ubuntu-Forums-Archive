---
title: "Unable to use mouse right-click on Desktop - Ubuntu 11.10"
date: 2011-10-25
forum: Desktop Environments
---

### Post by silviutp on 2011-10-25
Hi,

I cannot use the mouse right-click button on the Desktop in Ubuntu 11.10. This happens in Unity and also in Gnome Shell. Another problem is that there are no icons on desktop...

Also, I cannot use right click on the top bar or side bar, is this behavior normal ?

Distribution:          Ubuntu 11.10
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation G72 [GeForce 7300 SE/7200 GS] (rev a1)
 Driver in use:         nouveau
 Rendering method:      Nvidia

Please help...

---

### Post by GCoffee on 2011-10-25
Hi,

I do believe (someone correct me if I'm wrong) that, if I've interpreted what you're saying correctly, this is standard behaviour for GNOME3 and Unity. 

In GNOME3 the 'desktop' area no longer serves as a desktop in the windows sense. You cannot create shortcuts on it or the like, and by default your right-click options are limited. I've only used Unity for a short amount of time but I'm pretty sure it's the same idea.

Again, Right-clicking the top and side bar has been taken out of GNOME3 (and Unity, I think). You can no longer add applets to the top bar.

To replace the desktop, GNOME3 and Unity now have a sort-of dashboard interface. This can be accessed in Unity by pressing the windows (or equivalent) key on your keyboard (and possibly by clicking the ubuntu logo in the top left hand corner of the screen) and in GNOME3 either press the Windows (or equivalent key) or mouse-over activities in the top left hand corner. 

To add shortcuts to the sidebar (e.g: different applications) drag the applications from the previously mentioned 'dashboard' interface, to the sidebar. To delete shortcuts from the side bar hold down on them, and a bin should appear at the bottom of the sidebar. Just drag the icon into the bin.

Hope this helps,
GC.

---

### Post by silviutp on 2011-10-25
> **GCoffee said:**
> 
I do believe (someone correct me if I'm wrong) that, if I've interpreted what you're saying correctly, this is standard behaviour for GNOME3 and Unity. 

In GNOME3 the 'desktop' area no longer serves as a desktop in the windows sense. You cannot create shortcuts on it or the like, and by default your right-click options are limited. I've only used Unity for a short amount of time but I'm pretty sure it's the same idea.
GC.

I thought of that too, but I saw at my colleague (he has also just installed Ubuntu 11.10) that he can create files/folders and has right click access on Desktop...so.. i'm confused :).

---

### Post by silviutp on 2011-11-15
So I still didn't solve this problem. I have installed Ubuntu on several computers and only on one of them I have this problem....

I would really appreciate some help.

---

### Post by silviutp on 2011-11-16
Finally I've made it, with help from other forum.
The solution was to use dconf-editor. And in org->gnome->desktop->background check the 'show desktop icons' checkbox.

---

### Post by markbl on 2011-11-16
> **silviutp said:**
> 
The solution was to use dconf-editor. And in org->gnome->desktop->background check the 'show desktop icons' checkbox.

Or, at least in gnome-shell, just install gnome-tweak-tool and it is one of the options presented there.

---

### Post by leekyuh on 2012-02-16
Thanks a lot for your solution!
I don't know how it got changed all of sudden, though.

---

### Post by silviutp on 2012-02-16
For me it didn't got changed like this. I think it was like this after a fresh install...
Anyway, I'm glad this was helpful.

---

