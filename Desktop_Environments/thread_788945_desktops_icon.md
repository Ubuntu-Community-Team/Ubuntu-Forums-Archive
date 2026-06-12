---
title: "desktops icon"
date: 2008-05-10
forum: Desktop Environments
---

### Post by ehsun7b on 2008-05-10
I've just installed Ubuntu 8.04. There is no icons on my desktop!!! Is it usual? there is no default icon on the desktop?


when I open any windows partitions of mine, this partition (drive) icon appears on the desktop! I don't want them there! I should unmount the volume in order to be disappeared. but again it will appear there!!!
what is the solution?

---

### Post by angry_johnnie on 2008-05-10
Hit Alt+F2 and type:

```
gconf-editor
```

then, find

**Apps > Nautilus > Desktop**

and uncheck the boxes of the things you don't want to see on the desktop.  You'll still be able to find them in the *Places* menu.

---

### Post by ehsun7b on 2008-05-11
Thanks buddy
Is there anyway to add Terminal to desktop too but making a luncher?

---

### Post by larryni on 2008-05-11
> **ehsun7b said:**
> Thanks buddy
Is there anyway to add Terminal to desktop too but making a luncher?
The easiest way to do that is to open Applications > Accessories, then right-click on Terminal and select 'Add this launcher to desktop'.

---

### Post by ehsun7b on 2008-05-11
Thanks

---

