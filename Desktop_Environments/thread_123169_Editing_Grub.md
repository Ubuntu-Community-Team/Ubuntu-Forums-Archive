---
title: "Editing Grub"
date: 2006-01-29
forum: Desktop Environments
---

### Post by zea on 2006-01-29
Hey. I went to install Ubuntu (cd version) but my cd was corrupt. It went through the whole process (after grub) and crashed during "Installing additional resources..." So I booted back into windows, downloaded the dvd version, burned, and installed. Everything works fine, but when It boots into grub it has two ubuntu entries, and my win xp at the last. Is there a way to delete one of these entries? They both successfully boot into the same ubuntu install. I've looked in grub.conf..i believe..and couldn't figure it out, thanks.

Z

---

### Post by gatorbrit on 2006-01-29
[QUOTE=zea]Hey. I went to install Ubuntu (cd version) but my cd was corrupt. It went through the whole process (after grub) and crashed during "Installing additional resources..." So I booted back into windows, downloaded the dvd version, burned, and installed. Everything works fine, but when It boots into grub it has two ubuntu entries, and my win xp at the last. Is there a way to delete one of these entries? They both successfully boot into the same ubuntu install. I've looked in grub.conf..i believe..and couldn't figure it out, thanks.

Z[/QUOTE]


You need to edit the menu.lst file in the grub folder.  That file lists the boot options at start up

---

### Post by zea on 2006-01-29
When I look at it, it doenst seem like it lists everything. I will post it in here in a sec.

---

