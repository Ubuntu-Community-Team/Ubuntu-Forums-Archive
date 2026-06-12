---
title: "Compiz doesn't retain settings..."
date: 2006-12-19
forum: Desktop Environments
---

### Post by Nevermore on 2006-12-19
I installed the latest gandalfn compiz on my edgy, as well as compiz settings manager, however compiz doesn't retain the setting i make, if i activate animation, close the settings window, then open again, is deactivated again..what should i do?
Thanks

---

### Post by EnderTheThird on 2006-12-19
I think it's because you don't have permissions to write to .compiz (or .beryl), which is the folder that stores all of your settings for compiz.  See if this helps...

If you're using compiz, try this in a terminal:

```
sudo chmod -R 666 .compiz
```

If you're using beryl, try this in a terminal:

```
sudo chmod -R 666 .beryl
```

I'm not at my Ubuntu machine at home, so I could be a little off with the formatting there because I can't check it while I'm at a WinXP workstation.  ](*,)   Hope it helps though!

---

### Post by zootreeves on 2006-12-19
Nevermore if your talking about compiz-settings it's in very early development. Make sure your using the latest version from [http://forum.go-compiz.org/viewtopic.php?t=153](http://forum.go-compiz.org/viewtopic.php?t=153) or try and use gnome-compiz-manager instead.

If that doesn't It's probably because the animation plugin is failing to load (incorrect schema's etc), try reinstalling it and make sure you are using the same versions of compiz that animation was built for. I highly recommend using 0.34 from gandalfn's repo

---

### Post by Nevermore on 2006-12-27
well i simply fixed by deleting the whole gconf file related to compiz and rebooting
now i can change everything

---

