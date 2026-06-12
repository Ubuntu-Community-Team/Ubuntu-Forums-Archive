---
title: "problem with install/unistall themes"
date: 2009-08-01
forum: Desktop Environments
---

### Post by heyyy on 2009-08-01
i tried to reinstall(by drag and drop) a theme that i deleted recently(which appeared in the "controls" and the "windows border") and gave me the following message:
```
Installation for theme "theme" failed.
Can't move directory over directory
```
So..
how do reinstall it?
how do i delete permanently a theme from my system?(so if i want to reinstall it)

---

### Post by rainwalker on 2009-08-02
For some reason, I think it started in Ubuntu 9.04, if the theme you're trying to drag-and-drop to install is already there, it won't let you and will give you that "Can't move directory over directory" error. 
The only solution I've found is to go to your home directory, press Control + H to show hidden files, and find the folder called ".themes" and delete the folder for the theme you're trying to install. Once you've done that you should be able to drag-and-drop like normal to reinstall it.

---

### Post by heyyy on 2009-08-02
i tried it and it worked
but shouldnt themes be deleted from the directories as soon as you delete them from the appearence preferences?

---

### Post by rainwalker on 2009-08-02
That would make sense, and that used to be how it worked; I'm not sure what changed :?

---

