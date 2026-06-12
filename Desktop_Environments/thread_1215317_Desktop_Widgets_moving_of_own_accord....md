---
title: "Desktop Widgets moving of own accord..."
date: 2009-07-17
forum: Desktop Environments
---

### Post by denbeigh2000 on 2009-07-17
Whenever I move my desktop widgets around, they always move somewhere else.

That is to say, they stay for about a second, then they try to relocate to the top left corner.

Thanks in advance for your help, d2000

---

### Post by ~sHyLoCk~ on 2009-07-17
> **denbeigh2000 said:**
> Whenever I move my desktop widgets around, they always move somewhere else.

That is to say, they stay for about a second, then they try to relocate to the top left corner.

Thanks in advance for your help, d2000

Isn't there a lock position option? =/

---

### Post by Zorael on 2009-07-18
Weird.

I'd try resetting the plasma settings (to get them automatically recreated to defaults). Perhaps they've borked up someplace.

The files to rename/delete are **~/.kde/share/config/plasma***. You may need to exit plasma first, as it just might save its settings when you logout. You should be able to terminate the process (named **plasma-desktop**) via the System Activity window (ctrl+esc) or by running '**kquitapp plasma-desktop**', in a run box or in a terminal. Once you've removed those settings files, just restart it by running **plasma-desktop** again. ('**plasma-desktop _&_**' if in a terminal.)

---

### Post by mister_p_1998 on 2009-07-22
My Gdesklets do this in gnome..
Steve

---

