---
title: "[SOLVED] stuck workspaces"
date: 2008-01-31
forum: Desktop Effects &amp; Customization
---

### Post by da3shot on 2008-01-31
for some reason, no matter what i set the workspace numbers to be, its always on two columns, one row. i want to make it four columns and one row, any ideas on how to fix it?

---

### Post by Fraktyl on 2008-01-31
Right click on the desktop switcher window in the lower right.  Click preferences.

Change Rows to 1.

If that doesn't work, it may be compiz-fusion not picking up your changes if you are using Extra Visual Effects.  If that's the case, you'll want to download the compizconfig-settings-manager.

In a terminal window type:
```

sudo apt-get install compizconfig-settings-manager

```

You'll have to have the universe repositories enabled to get these.  Let me know if you need help getting those added.

Then click: System->Preferences->Advanced Desktop Effects Settings

Click General Options (first icon at the top) -> Desktop Size (3rd tab)
Change Vertical Virtual size to 1.

Click Back (lower left), Then Close (lower left)

---

### Post by da3shot on 2008-01-31
omg, thank you so much. it works now :)

---

