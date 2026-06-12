---
title: "[SOLVED] can you do tricks with dosbox.conf?"
date: 2008-01-30
forum: Gaming &amp; Leisure
---

### Post by PfromD on 2008-01-30
I currently have the **[autoexec]** section of dosbox.conf (for dosbox obviously) set up so that two mount statements are performed, but is it possible to 'program' it so I need only press a key, eg. "c" for *Colonization*, and then a mount of the drive/folder containing Colonization is performed, drive selected and runfile executed, with several options for keys/associated actions?
Or is **[autoexec]** entirely static.

---

### Post by lha on 2008-02-01
Why don't you use -c switch to give dosbox commands? For example,
```

dosbox ~/mydir/myexe.exe -c "mount B ~/mydir" -c "b:"

```
This method allows you to create custom launchers. (You can add your dos games to Applications->Games -menu.)

---

### Post by PfromD on 2008-02-01
Thanks for the launcher tip, but how do you actually place/arrange the launchers in the menu?

---

### Post by lha on 2008-02-02
Try Alacarte Menu Editor. Its package is called alacarte.

---

### Post by PfromD on 2008-02-03
Nice clean editor. Though I'd still say that editing the menu is still a lot more straightforward and easy in ... dare I say it? Windows. 'Couple of well placed right-clicks and some drag'n'drop and you're set. Perhaps Ubuntu will implement that at a later stage.

---

