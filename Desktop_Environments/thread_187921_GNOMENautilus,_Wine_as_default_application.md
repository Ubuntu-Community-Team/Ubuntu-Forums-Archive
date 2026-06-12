---
title: "GNOME/Nautilus, Wine as default application"
date: 2006-06-03
forum: Desktop Environments
---

### Post by meng on 2006-06-03
I had posted elsewhere that I had solved this problem, but I was mistaken, it is not solved yet.

I am trying to get .exe files automatically opened with Wine, when browsing with Nautilus. Unfortunately, it doesn't seem to work, whether I double-click, or right-click to bring up an Open menu (it always offers to open with the Text Editor).

Here's what I've tried:
- uninstalling cedega
- uninstalling and reinstalling wine (both 0.9.9 from universe and 0.9.14 from alternative repositories)
- right-click > Properties > Open With. Wine Windows Emulator is already selected as the default application according to this. It just doesn't actually work!
- manually examining and editing /usr/share/application-registry/gnome-vfs.applications, /usr/share/mime-info/gnome-vfs.mime, /usr/share/mime-info/gnome-vfs.keys (as well as the ~/.gnome/ versions of these files)
- renaming the .exe files to .EXE. I thought this was the solution, but the effect only sticks to that individual file, and only temporarily.

Anyone else experiencing this problem. Any fixes?

---

### Post by temcat on 2006-06-03
Works for me on double-click. I set it up through Open With.

---

### Post by meng on 2006-06-03
Thanks for the feedback. At least I know it's not an inherent GNOME problem, but something to do with my particular setup.

---

