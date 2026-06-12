---
title: "Kubuntu hosed through updating!"
date: 2005-04-29
forum: Desktop Environments
---

### Post by Arbiter on 2005-04-29
After using regular both Hoary and Warty versions of Ubuntu, I decided to give a try at an install of Kubuntu Hoary.  It was working fine until I started running updates.  Then somehow KDE lost all my desktop settings and all I'm left with is the default KDE 3.4 background and a taksbar only with the terminal button on it.

I tried running the kdelibs debug script found in another forum thread, but that did nothing.

So, what did I do wrong and how can I fix it?

---

### Post by govert on 2005-05-06
I had this problem as well.
*eagerly awaiting feedback from someone...*

---

### Post by Firetech on 2005-05-06
It's all because of some error in the kdelibs-data package, which was updated some weeks ago. (Couldn't overwrite some icon also in knetworkconf.) There are some threads in this forum about that package. I don't know the exact reason, but that package is to blame.

---

### Post by zupermanz on 2005-05-06
i have had the same problem.... + lost the taskbar!
anyway i sont know which update caused it but i ve had to fix the menus and taskbar manually

---

