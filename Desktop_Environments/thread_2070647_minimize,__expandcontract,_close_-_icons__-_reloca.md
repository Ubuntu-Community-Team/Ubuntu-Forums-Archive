---
title: "minimize,  expand/contract, close - icons  - relocate?"
date: 2012-10-13
forum: Desktop Environments
---

### Post by gertcher on 2012-10-13
I have been using MS since Win 3 and 3 little icons have become grained in to how I toggle the window.

The 3 icons in Windows are at the top right corner - minimize,  expand/contract, close. In Ubuntu the same three icons are at the top left corner.

Is there an app that will move the icons to the right in Ubuntu?

Thanks    Greg

---

### Post by wojox on 2012-10-13
I know of a command:
```
gconftool -s /apps/metacity/general/button_layout -t string menu:minimize,maximize,close
```

---

### Post by gertcher on 2012-10-13
> **wojox said:**
> I know of a command:
```
gconftool -s /apps/metacity/general/button_layout -t string menu:minimize,maximize,close
```Thanks for that.  B4 I enter that command, do u have one to undo it?  I have enough trouble finding the command line let alone entering anything

---

### Post by wojox on 2012-10-13
And back to the left:
```
gconftool-2 --set "/apps/metacity/general/button_layout" --type string "close,minimize,maximize:"
```

---

