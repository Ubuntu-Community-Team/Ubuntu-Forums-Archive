---
title: "redo restore my kde to default"
date: 2012-06-19
forum: Desktop Environments
---

### Post by forsubhi on 2012-06-19
I restore my kde to default setting so I lose my gadget notes , can I restore my notes now ?

---

### Post by SeijiSensei on 2012-06-19
If you want to create a new desktop with the default settings, use:

```

cd ~
mv .kde .kde.old

```

or, in Dolphin, choose View > Hidden Files, then hit F5.  Find the .kde directory and rename it like I did above.
After you rename the directory, log out and log back in.  Your entire desktop should be recreated just the way it was originally.  If everything is okay, you can delete ~/.kde.old.

---

