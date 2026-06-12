---
title: "i'm trying to reformat C."
date: 2009-02-21
forum: General Help
---

### Post by Trim0 on 2009-02-21
when i start up my laptop, grub loads and it gives me the options of choosing between vista and ubuntu.
now ubuntu is not installed on C, and i'm not sure where the root of grub is, which leads me to my question;
if i reformat my C partition, will grub still load and will ubuntu still work fine???

also, for some reason, ubuntu is selected first on loading stage, and 2 windows vista (longhorn) appear. i'm not sure why that is.

---

### Post by wolfen69 on 2009-02-21
if you reformat windows, you will probably have to reinstall grub after. there are many how to's on the subject.

---

### Post by vanadium on 2009-02-21
You probably will not. The first loading stage of grub is installed in the Master Boot record. That points to the next stages, which are normally located on your Ubuntu partition. Formatting a partition (the Windows partition in this case) will not affect grub. Obviously, you won't be able to load Windows anymore, although the choice is still there. You can remove the Windows entry from the grub startup menu afterwards.

Reinstalling Windows is a different matter: then your MBR will be overwritten. You need to reinstall grub to make dual boot work again.

---

