---
title: "failed to create a url link on the desktop"
date: 2020-12-23
forum: Desktop Environments
---

### Post by vincentberenz on 2020-12-23
I am trying to create on the desktop a shortcut to an internet site.

I did the following:

- created a file ~/Desktop/ubuntu.desktop
- added to the file this content:

```

[Desktop Entry]
Version=1.0
Type=Link
Name=Ubuntu Forums
Comment=
Icon=gnome-fs-bookmark
URL=https://ubuntuforums.org
```

- made the file executable

```
chmod +x ubuntu.desktop
```

I only get to see the file "ubuntu.desktop" on the desktop, and double clicking the link open the file for edit (as it would for any text file).

I am on ubuntu 20.04.

Anything am I missing ?

---

### Post by T6&amp;sfpER35% on 2020-12-23
what browser ? I'm using Brave and it's as simple as **more tools - create shortcut...**and voila,there's the shortcut to the site on desktop and it works.
ps. i'm using xubuntu,don't know if that matters

---

### Post by CatKiller on 2020-12-23
I'm pretty sure Gnome removed the ability to launch things from the desktop. You might be able to get the functionality back with an extension.

---

### Post by Morbius1 on 2020-12-23
Change this:
> [Desktop Entry]
Version=1.0
Type=Link
Name=Ubuntu Forums
Comment=
Icon=gnome-fs-bookmark
URL=https://ubuntuforums.org
To this:
> [Desktop Entry]
Version=1.0
[COLOR=#ff0000]**Type=Application**[/COLOR]
Name=Ubuntu Forums
Comment=
Icon=gnome-fs-bookmark
[COLOR=#ff0000][B]Exec=firefox [https://ubuntuforums.org](https://ubuntuforums.org)
[/B][/COLOR]


Change firefox to your default browser.

Save the file then right click the icon on the desktop and select **Allow Launching**:
[ATTACH=CONFIG]287612[/ATTACH]

---

