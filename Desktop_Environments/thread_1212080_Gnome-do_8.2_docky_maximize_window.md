---
title: "Gnome-do 8.2 docky maximize window"
date: 2009-07-13
forum: Desktop Environments
---

### Post by Bultot on 2009-07-13
Since the new Gnome-Do 8.2 (Docky) I can not maximize my windows to the full screen size. The windows stay above the Gnome-do Dock.
How can I set the dock in front and maximize my windows to my full screensize?

---

### Post by airtonix on 2009-07-13
[LIST=1]
[*]First you need to open gconf-editor :
```
$ gconf-editor
```
[*]Then in the left hand pane, follow this branch pattern: apps > gnome-do > preferences > Docky > Utilities > DockPreferences
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=120961&stc=1&d=1247499908[/IMG]
[*]Make sure ***AllowWindowOverlap*** is ticked.
[*]Then for a window to be allowed to overlap the docky panel, it needs to have its "Always OnTop" Propertie set. This is done by right clicking on the window frame and selecting it.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=120960&stc=1&d=1247499908[/IMG]
[/LIST]

---

### Post by Bultot on 2009-07-14
Thanks for you reply, But I'd like to have the dock always on top and maximized windows behind it.

---

### Post by Tibuda on 2009-07-14
It's not what you want, but I think the best option is the new Intellihide option.

---

### Post by jabryl on 2009-07-25
Anyone know when or if they're going to fix this?

---

### Post by jabryl on 2009-07-27
It seems that that feature was removed in version 8.2.

Here's the bug report page on launchpad.

[https://bugs.launchpad.net/do/+bug/379747](https://bugs.launchpad.net/do/+bug/379747)

Go leave a note if you want them to restore it in the next version. In the meantime there is a link to a patched version on that page as well.

---

### Post by KGyST on 2009-12-21
For me, IntelliHide worked @ Do 8.2, Karmic Koala
Thanks

---

### Post by jabryl on 2010-02-08
> **KGyST said:**
> For me, IntelliHide worked @ Do 8.2, Karmic Koala
Thanks

Thanks for the reply, but intellihide has nothing to do with this problem.

---

