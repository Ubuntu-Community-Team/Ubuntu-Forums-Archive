---
title: "How to add genres to Applications-&gt;Games"
date: 2013-02-24
forum: Gaming &amp; Leisure
---

### Post by cristo-father on 2013-02-24
This was curiously created, by installing some games, anyway can i customize this and add more/move some around etc ?
1 More question, can i add non-deb installed games to there, like with a shortcut to a .sh, executable, .jar etc for example ?

---

### Post by Perfect Storm on 2013-02-25
Yes, you can (to all of your questions).

```
sudo nano /usr/share/applications/give-it-a-name.desktop
```

then add/edit/paste this into it:

```
[Desktop Entry]
Version=
Name=
Comment=
Type=Application
Categories=Application;Games
Exec=
Terminal=false
Icon=
```

It will now show up in dash/search.

---

### Post by cristo-father on 2013-02-25
> **Artificial Intelligence said:**
> Yes, you can (to all of your questions).

```
sudo nano /usr/share/applications/give-it-a-name.desktop
```

then add/edit/paste this into it:

```
[Desktop Entry]
Version=
Name=
Comment=
Type=Application
Categories=Application;Games
Exec=
Terminal=false
Icon=
```

It will now show up in dash/search.

2 more somewhat related questions:

I am using gamelauncher and it already has created some gamename.desktop.gamelauncher files on that folder. Will there be conflicts ?
[http://ubuntuforums.org/showthread.php?t=2101504](http://ubuntuforums.org/showthread.php?t=2101504)

In the icons tab, can i link to a image ? Also, can i change the image of one of the genres( example: Applications->Games->SurvivalHorror with a zombie pic for example.)

---

### Post by Perfect Storm on 2013-02-25
As long you don't give the same .desktop name as the other one (overwrite), then it should be fine.

You can link to any images. And yes you can change the icon of other games/applications as well, you just need to find its .desktop file or create a new one, but then it will show up twice :P

---

### Post by Perfect Storm on 2013-02-25
You can also try: [http://www.addictivetips.com/ubuntu-linux-tips/edit-ubuntu-unity-launcher-quicklist-with-unity-launcher-editor/](http://www.addictivetips.com/ubuntu-linux-tips/edit-ubuntu-unity-launcher-quicklist-with-unity-launcher-editor/)

But it's still in development.

---

