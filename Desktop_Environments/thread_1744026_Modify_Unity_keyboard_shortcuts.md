---
title: "Modify Unity keyboard shortcuts"
date: 2011-04-30
forum: Desktop Environments
---

### Post by alexjohnc3 on 2011-04-30
Previously, I set the keyboard shortcuts so "Mod4+L" (which is just one key) would lock my screen. However, after upgrading to 11.04, that key now acts like a "Super" key, even though the shortcuts haven't changed. I tried modifying the keyboard shortcuts, but that doesn't seem to do anything for me. I can't figure out a solution. Any help would be greatly appreciated!

---

### Post by kalos on 2011-05-01
For my keyboard, Super and Mod4 are both the Windows key.

You can change the shortcut to invoke the dash:

```
gconftool --set /apps/compiz-1/plugins/unityshell/screen0/options/show_launcher --type=string "F6"

```

More info on askubuntu:
[http://askubuntu.com/questions/21934/how-to-change-the-binding-of-windows-key-which-runs-unitys-dash/38843#38843](http://askubuntu.com/questions/21934/how-to-change-the-binding-of-windows-key-which-runs-unitys-dash/38843#38843)

---

### Post by alexjohnc3 on 2011-05-01
> **kalos said:**
> For my keyboard, Super and Mod4 are both the Windows key.

You can change the shortcut to invoke the dash:

```
gconftool --set /apps/compiz-1/plugins/unityshell/screen0/options/show_launcher --type=string "F6"

```

More info on askubuntu:
[http://askubuntu.com/questions/21934/how-to-change-the-binding-of-windows-key-which-runs-unitys-dash/38843#38843](http://askubuntu.com/questions/21934/how-to-change-the-binding-of-windows-key-which-runs-unitys-dash/38843#38843)
I used the compizconfig-settings-manager, and it worked like a charm. It took a few minutes before it started working though. Thanks! :)

---

