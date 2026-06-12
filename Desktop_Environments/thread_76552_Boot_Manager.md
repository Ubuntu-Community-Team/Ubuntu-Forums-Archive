---
title: "Boot Manager"
date: 2005-10-15
forum: Desktop Environments
---

### Post by Storm Rider on 2005-10-15
Somewhere, not to long ago I saw and used a gui for Grub. Not sure if it was under utilities or system tools, anyway , can't find it now.
1) Where is it?
2) Can I remove reference to an older linux kernel without causing myself a bunch of grief.

---

### Post by HermanAB on 2005-10-15
With grub, it is easy to edit the menu by hand and remove useless entries.  Simply edit the file '/boot/grub/menu' (I think, not sure about the name, since I don't use grub at the moment, but just look around in /boot/grub), no need to reboot after.

Cheers,

Herman
[http://www.aerospacesoftware.com/linuxhowtos.html](http://www.aerospacesoftware.com/linuxhowtos.html)

---

### Post by hiperactive on 2005-10-15
[QUOTE=Storm Rider]Somewhere, not to long ago I saw and used a gui for Grub. Not sure if it was under utilities or system tools, anyway , can't find it now.
1) Where is it?
2) Can I remove reference to an older linux kernel without causing myself a bunch of grief.[/QUOTE]


Yes, I want the grub gui-based conf back too!!!

---

### Post by burningbed on 2005-10-16
[QUOTE=Storm Rider]
2) Can I remove reference to an older linux kernel without causing myself a bunch of grief.[/QUOTE]

If you just run sudo apt-get remove linux-image-XXX [insert the version of the old kernel you want to remove here], it will get removed and the grub list will get updated to reflect that that version is no longer available. It's just as simple as removing any other program, as long as you're not trying to remove the kernel you're currently running (i.e. make sure you boot up in the new kernel and remove the old one).

---

