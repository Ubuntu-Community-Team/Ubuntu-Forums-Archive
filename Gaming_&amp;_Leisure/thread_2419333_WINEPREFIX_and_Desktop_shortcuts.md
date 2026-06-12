---
title: "WINEPREFIX and Desktop shortcuts"
date: 2019-05-20
forum: Gaming &amp; Leisure
---

### Post by ubh on 2019-05-20
Can anyone please clarify me about shortcuts created by Wine (**with custom WINEPREFIX**) when installing SOFTWARE?

I mean, I create a custom profile in which I installed SOFTWARE:
```

WINEARCH=win32 WINEPREFIX=~/my_custom_bottle_of_wine/SOFTWARE wine /media/myusername/SOFTWARE/Install.exe

```

Wine created shortcuts on GNOME Desktop, fine.

How can I be 100% sure that double-clicking the icon, then Wine will work and load files from the correct profile (that is: *WINEARCH=win32 WINEPREFIX=~/my_custom_bottle_of_wine/SOFTWARE*)?


Because if I use:
```

WINEARCH=win32 WINEPREFIX=~/my_custom_bottle_of_wine/SOFTWARE wine /home/myusername/my_custom_bottle_of_wine/SOFTWARE/drive_c/Program%20Files/path/SOFTWARE.exe

``` SOFTWARE won't start. It'll start when double-clicking on its Desktop icon.

Thanks!

---

### Post by CatKiller on 2019-05-20
You can drag-and-drop the launcher onto a text editor to see all the details about the command that gets run, and edit it if you need to.

For your manual command that fails to work, you should probably be using an escaped space (\ ) rather than %20.

---

### Post by ubh on 2019-05-21
> **CatKiller said:**
> For your manual command that fails to work, you should probably be using an escaped space (\ ) rather than %20.
No, there is no %20 on the actual command (just copied from address bar). In fact I use escape: \

Not the manual command is failing, I explained wrong. SOFTWARE starts with manual command, but it complains about lack of some files: it seems to be not aware where to look for its installation folder and files.


> **CatKiller said:**
> You can drag-and-drop the launcher onto a text editor to see all the  details about the command that gets run, and edit it if you need to.
Shame on me! Thanks to you!! ):P
This is what I was looking for: **Exec=_env WINEPREFIX=_"/home/myusername/my_custom_bottle_of_wine/SOFTWARE"**
And it's right!

```
Exec=env WINEPREFIX="/home/myusername/my_custom_bottle_of_wine/SOFTWARE" wine-stable C:\\\\windows\\\\command\\\\start.exe /Unix /home/myusername/my_custom_bottle_of_wine/SOFTWARE/dosdevices/c:/users/Public/Desktop/icon_name_of_SOFTWARE.lnk
```

---

