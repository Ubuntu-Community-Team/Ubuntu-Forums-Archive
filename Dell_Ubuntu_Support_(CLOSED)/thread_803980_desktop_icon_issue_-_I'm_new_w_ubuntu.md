---
title: "desktop icon issue - I'm new w/ ubuntu"
date: 2008-05-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ameuse on 2008-05-22
Hi there!-
So far I am loving Ubuntu and Linux - 

I have a dual boot of Windows XP (not for long) and Ubuntu - I had a local computer tech do that for me to help avoid any issues for now -However- Now when I boot up Ubuntu I have three icons on my desktop that I can not seem to get rid of- they are Media Direct - Dell Restore - and one that reads 105.3 GB Media - I have these all listed as well under the PLACES tab but I would love to not have to see them on my desktop - Can anyone help me on this - it sort of seems like it should be a simple thing - I feel a little silly - Thanks -Aaron.

---

### Post by aidave on 2008-05-22
One thing that might help you get rid of those, is the configuration editor.

Try "gconf-editor" at the command line, or, enable it in your System Tools Menu.

In "apps->nautilus" you may find what you are looking for, but I am not running the Dell image, so I can't be sure.

---

### Post by diaa on 2008-05-23
> **aidave said:**
> One thing that might help you get rid of those, is the configuration editor.

Try "gconf-editor" at the command line, or, enable it in your System Tools Menu.

In "apps->nautilus" you may find what you are looking for, but I am not running the Dell image, so I can't be sure.
As aidave said, go to
```
apps > nautilus > desktop
```then remove the checkbox infront of *volumes_visible* in the right panel, it'll take effect immediately

---

