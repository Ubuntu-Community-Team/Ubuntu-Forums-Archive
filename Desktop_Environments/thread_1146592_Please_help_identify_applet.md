---
title: "Please help identify applet"
date: 2009-05-02
forum: Desktop Environments
---

### Post by kenpotf on 2009-05-02
Can anyone identify that applet that used on the left hand side in the link? I'm "assuming" it's gdesklets, but I can't find any widget that matches this. It looks like it's an open applications tray of some sort, but it shows screenshots instead of icons.

[http://www.lynucs.org/index.php?screen_id=140407135640c8970070189&p=screen](http://www.lynucs.org/index.php?screen_id=140407135640c8970070189&p=screen)

Thanks!
John

---

### Post by PurposeOfReason on 2009-05-02
The open windows are a feature of fvwm.

---

### Post by kenpotf on 2009-05-02
Thanks for the quick reply!

Is there a way to run just that piece under Gnome?

---

### Post by PurposeOfReason on 2009-05-02
> **kenpotf said:**
> Thanks for the quick reply!

Is there a way to run just that piece under Gnome?
You could use fvwm instead of metacity or compiz. I do believe compiz has a shrink tool that can kind of minic it, that is about it.

---

### Post by jpkotta on 2009-05-10
It isn't really something that's a package you can install.  It's more like a bunch of scripts cobbled together to use screenshots instead of the usual application icons.  The main things that enable it are the ability of Fvwm to ask an external script for Fvwm code, and the ability of Fvwm to run commands on various events, like switching focus or resizing.  You can learn how it's done from the [Fvwm forums]("http://fvwm.lair.be/"); I can help if you get stuck.

---

