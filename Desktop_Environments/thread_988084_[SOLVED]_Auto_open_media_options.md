---
title: "[SOLVED] Auto open media options?"
date: 2008-11-20
forum: Desktop Environments
---

### Post by ezekiel000 on 2008-11-20
Why can't I select any actions for most of the types of media (see attached image), I have Sound Juicer installed that I would like to open automatically when I insert an audio cd. Does anyone know how to fix this?

---

### Post by sillyxone on 2008-11-20
I think you can set that manually by running gconf-editor, go into desktop > gnome >volume_manager, and fill in the xxx-command options with paths to your programs.

---

### Post by ezekiel000 on 2008-11-20
> **sillyxone said:**
> I think you can set that manually by running gconf-editor, go into desktop > gnome >volume_manager, and fill in the xxx-command options with paths to your programs.
I tried that, it had no effect. Thanks anyway, any other ideas?

---

### Post by ezekiel000 on 2008-11-28
I solved this by installing the default Gnome applications for the various option (rhythm box, gthumb etc) then I was able to change the auto open options. So I selected my prefered options and removed the default Gnome applications I didn't want.

---

