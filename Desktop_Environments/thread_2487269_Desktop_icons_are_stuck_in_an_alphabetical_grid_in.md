---
title: "Desktop icons are stuck in an alphabetical grid in 22.04 LTS"
date: 2023-05-29
forum: Desktop Environments
---

### Post by robertcull1 on 2023-05-29
I just upgraded from 18.04 LTS to 22.04 LTS. Now my desktop icons are stuck in an alphabetical grid and I can't move them around like I am accustomed to on 18.04 LTS.

I am using the Unity Desktop on a Lenovo ThinkPad T430.

---

### Post by ActionParsnip on 2023-05-30
[https://askubuntu.com/questions/1406236/desktop-icons-gone-in-22-04](https://askubuntu.com/questions/1406236/desktop-icons-gone-in-22-04)
May help

---

### Post by robertcull1 on 2023-05-30
Thanks Parsnip,

I tried everything in that link. Now I have an entirely different looking desktop, except everything is on a grid in alphabetical order just as before. Actually, I don't mind the change, if I could only rearrange the icons as I would like, the change would be fine.

I didn't know how to implement what was in the suggestions here:

```
[COLOR=#232629][FONT=-apple-system]The new Ubuntu 22.04.1 does not support the Type=Link in desktop icons. So make it an Application like this:[/FONT][/COLOR]
[Desktop Entry]
Encoding=UTF-8
Type=Application
Exec=firefox https://en.wikipedia.org/wiki/Main_Page
Icon=/home/chiel/Pictures/Icons/Wikipediaglobe.png
Name[en_US]=Wiki_en
[COLOR=#232629][FONT=-apple-system]Make sure the extension is .desktop[/FONT][/COLOR]

```

I don't know if that would have made any difference.

---

