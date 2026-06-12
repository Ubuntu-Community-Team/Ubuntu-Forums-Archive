---
title: "Adding icons to docky"
date: 2016-12-24
forum: Desktop Environments
---

### Post by geovino on 2016-12-24
I'm running Xubuntu 16.10

Added Docky, but have noticed that certain apps can't launch from Docky. Terminal, Thunar Files both show as a grey generic icon and when clicking on it, it doesn't open. Are certain files not allowed to be pinned on Docky?

---

### Post by #&amp;thj^% on 2016-12-24
You can try to drop some applications' shortcut from /usr/share/applications to your dock. (If some applications are not in this folder you just need to create a new .desktop file).
IE: "xfce4-terminal.desktop" if it is not there already.
IE: "Thunar.desktop" and so on.
Hope this helps

---

### Post by geovino on 2016-12-24
I'll give that I try. Thanks

---

### Post by SantaFe on 2016-12-24
I've found in docky, if you make a launcher on the desktop & drag it into Docky, it'll work, but if you delete the desktop icon, it'll quit working.  In my case, I opened Thunar & created a folder and called it Docky Shortcuts.  Then I'd create a launcher on the desktop, dragged it into the folder I made, delete the desktop icon & drag the icon from my Docky Shortcuts folder onto the Docky dock.

I think if you drag it from the desktop to Docky, it makes a shortcut to the desktop icon on the Dockbar, while if you drag it from the desktop to a folder, it copies it to the folder.  So as long as you don't delete the folder, your launchers will still work.

---

### Post by geovino on 2016-12-26
Thanks, but what I would like to know is why many apps once opened and pinned to the Docky with their proper logo/icon, they open the programs. And others don't open! Its inconsistent. Why is that?

---

