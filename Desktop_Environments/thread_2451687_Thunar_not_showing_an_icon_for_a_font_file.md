---
title: "Thunar not showing an icon for a font file"
date: 2020-10-09
forum: Desktop Environments
---

### Post by geofftf on 2020-10-09
I downloaded a .ttf font file that shows its own icon in Thunar. I edited that file using FontForge and saved the result as another .ttf file. Thunar shows a title for that file, but no icon. All the other file icons are unaffected. Changing the icon theme does not help. The file has a generic font icon when I view it in Dolphin.

---

### Post by geofftf on 2020-10-14
I have got some clues. I typed in a terminal:

```
gvfs-info OrigAlpha.ttf

```
The custom icon is shown as:

```
thumbnail::path: /home/geoff/.cache/thumbnails/normal/ad484297f06a885bad48d54bd27a2839.png
```

the corresponding .png for the edited font file is blank space. I tried:

```
gvfs-set-attribute EditedAlpha.ttf metadata::thumbnail::path: /home/geoff/.cache/thumbnails/normal/ad484297f06a885bad48d54bd27a2839.png
```

but I got:

This tool has been deprecated, use 'gio set' instead.
See 'gio help set' for more info.

I now have some idea of what is causing the problem, and I expect that I can fix if I can find the time to do it.

---

