---
title: "Adding program icons to desktop?"
date: 2011-10-20
forum: Desktop Environments
---

### Post by googleye on 2011-10-20
Just wondering how the hell I do that in Gnome 3? I don't wan't to have them below activities but on the actual desktop area. 

Appreciate any help, getting tired of this...

---

### Post by googleye on 2011-10-22
Anyone?

---

### Post by crdlb on 2011-10-22
GNOME Shell isn't designed with desktop icons in mind. The best option I can come up with is to drag icons from /usr/share/applications in a nautilus window. You need to hold Alt since nautilus seems unwilling to copy .desktop files, even with Ctrl.

---

### Post by googleye on 2011-10-22
Thanks for your reply, it's nice to get rid of unity but without a way to start applications fast it's useless anyway. Will that mess up anything or will I just be dragging copies with possibly ugly icons to the desktop?

---

### Post by crdlb on 2011-10-22
It's perfectly safe, and the icons should be full-quality. It's the .desktop file describing the application that you are copying. The only problem is that GNOME Shell will automatically go to the overview when the last window in a workspace is closed, which is a little inconvenient when you want to get to icons on your desktop.

---

