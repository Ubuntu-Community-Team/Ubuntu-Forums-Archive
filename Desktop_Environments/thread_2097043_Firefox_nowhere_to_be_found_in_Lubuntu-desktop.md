---
title: "Firefox nowhere to be found in Lubuntu-desktop"
date: 2012-12-21
forum: Desktop Environments
---

### Post by marsgorski on 2012-12-21
[LEFT][COLOR=#333333][FONT=Ubuntu Beta]I have just installed lubuntu-desktop on top of ubuntu 12.04. I understand that chromium is the default browser in lubuntu but I was expecting Firefox to show up under the Internet menu. It is installed in my computer, and it shows in the Lubuntu Software Center under installed applications but I cannot find it anywhere. How do I have it show up on the Internet menu?[/FONT][/COLOR][/LEFT]

---

### Post by 2F4U on 2012-12-21
Can you check if there is a .desktop file for it and, if yes, if it contains menu categories?

[https://help.ubuntu.com/community/Lubuntu/Windows](https://help.ubuntu.com/community/Lubuntu/Windows)

---

### Post by vasa1 on 2012-12-22
[Cannot find firefox in Lubuntu desktop]("http://askubuntu.com/q/231448/25656")
And my comment there:
> What do you see when you run **locate firefox.desktop**? Do you have such a file? It should normally be in **/usr/share/applications** and you should see the regular Firefox icon. If you do, right-click on it and view it with a plain text editor. Then edit your question here to include the relevant lines. (There'll be a lot of lines in other languages.) It's possible that there's some line such as TargetEnvironment=Unity that may prevent display in a "Lubuntu" session. But, as the answer below suggests, a purge/install may do the trick.

---

### Post by vasa1 on 2012-12-22
> **2F4U said:**
> Can you check if there is a .desktop file for it ...
The .desktop file had this: **OnlyShowIn=Unity;** but it's unclear whether that is in a specific subpart of the .desktop file or in the main section.

Even though I have a pure Lubuntu installation I do see this **OnlyShowIn=Unity;** business in some .desktop files.

For example, Transmission has this in the main section:
```
Exec=transmission-gtk %U
```
but farther down has
```

[Desktop Action Pause]
Name=Start Transmission with All Torrents Paused
Exec=transmission-gtk --paused
OnlyShowIn=Unity

[Desktop Action Minimize]
Name=Start Transmission Minimized
Exec=transmission-gtk --minimized
OnlyShowIn=Unity;
```

---

