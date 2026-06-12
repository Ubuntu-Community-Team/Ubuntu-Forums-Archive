---
title: "WoW help with wine?"
date: 2007-04-20
forum: Gaming &amp; Leisure
---

### Post by addysonclark on 2007-04-20
Ok so i have wine installed and it runs fine (atleast i assume it runs fine...i can access the winecfg and there is no error messages) So how do i make it load my exe's i tryed doing "wine wowclient-blahblah.exe" but it said

"wine: could not load L"c:\\windows\\system32\\wowclient-downloader.exe": Module not found"

now im assuming that means i have to get the client downloader into the system 32 folder? but how do i do that....or how do i make it be able to load things off of the desktop or where ever i choose?


sorry if it seems like a noob question..i just started ubuntu today:lolflag:

---

### Post by hikaricore on 2007-04-20
(before doing anything with wine after a fresh install it's always a good idea to run **winecfg**)

```
winecfg
```

Aside from that.

It's best to be IN the directory of the file.  For example if the wow client downloader is on your desktop open a terminal and type:

```
cd ~/Desltop
```

This changes to the Desktop folder in your home folder which is refered to as ~ while logged in.

Then type:

```
wine wowclient-downloader.exe
```

You can also run it as:

```
wine ~/Desktop/wowclient-downloader.exe
```

If you experience problems running a windows based application this way, try it from the directory it's in.  :)

---

