---
title: "Grub menu.lst file gets reset after every update"
date: 2005-09-05
forum: Desktop Environments
---

### Post by chrisv on 2005-09-05
Hello, everyone

Ok I have been running Ubuntu more or less succesfully for now, but I have hit something that is a bit of a pain. 

I am dual booting with WinXP, and did the necessary modifications of the Grub menu.lst file, so I can load XP. However, whenever I do a major Ubuntu update the menu.lst file gets reset and the Windows XP option disappears. Therefore, I must again modify it to run Windows. 

Is there a way to prevent Ubuntu from deleting the Windows Xp option on updates? It is quite a pain to change the config file every time I load an Ubuntu update.

---

### Post by plb on 2005-09-05
hrm weird problem, never experienced it myself, you could just keep up a backup of it and then copy it over although this is an ugly solution as grub shouldn't be doing this. I don't have to time to google it right now but you may want to see if you can't find anything out about this

---

### Post by Curlydave on 2005-09-05
[QUOTE=chrisv]Hello, everyone

Ok I have been running Ubuntu more or less succesfully for now, but I have hit something that is a bit of a pain. 

I am dual booting with WinXP, and did the necessary modifications of the Grub menu.lst file, so I can load XP. However, whenever I do a major Ubuntu update the menu.lst file gets reset and the Windows XP option disappears. Therefore, I must again modify it to run Windows. 

Is there a way to prevent Ubuntu from deleting the Windows Xp option on updates? It is quite a pain to change the config file every time I load an Ubuntu update.[/QUOTE]

I get this too, and it gets on my nerves. People here seem to like to dismiss this issue though blaming it on lack of knowledge of some command that I can't recall. Bottom line: this is a significant issue that needs to be fixed.

---

### Post by plb on 2005-09-05
Is there any particular update that brings about this behavior? Seems to me the only updates that should edit grub settings would be kernel and the grub package itself, check out section 8.2 in the following link.....

[http://newbiedoc.sourceforge.net/system/kernel-pkg.html#GRUB-KERNEL-PKG](http://newbiedoc.sourceforge.net/system/kernel-pkg.html#GRUB-KERNEL-PKG)

---

### Post by Curlydave on 2005-09-05
[QUOTE=plb]Is there any particular update that brings about this behavior? Seems to me the only updates that should edit grub settings would be kernel and the grub package itself, check out section 8.2 in the following link.....

[http://newbiedoc.sourceforge.net/system/kernel-pkg.html#GRUB-KERNEL-PKG](http://newbiedoc.sourceforge.net/system/kernel-pkg.html#GRUB-KERNEL-PKG)[/QUOTE]

I know for a fact that any kernel update will do it, such as changing from the default kernel to your appropriate one, which is somewhat important.

---

### Post by rdwtux on 2005-09-05
I've noticed this also, although not with Winxp settings. 

I set the kopt option to include i8042.nomux for my synaptics touchpad.. I also set it on the kernel line. 

if I do a " sudo dpkg-reconfigure linux-image-`uname -r`" or usually even a kernel update and the kopt option gets cleared. 

I could be mistaken, but I thought the kopt= option in menu.lst was exactly for this - for Ubuntu to know what to add to each of the linux boot options when a new kernel is installed.

---

### Post by skoal on 2005-09-05
Well, you could do this:

1. Open up /etc/kernel-img.conf (as sudo) with your fav editor.
2. Remove the kernel-img hook script calls by deleting these two lines:

postinst_hook = /sbin/update-grub
postrm_hook   = /sbin/update-grub

note: I don't know that you can just comment (#) out these lines instead of removing them, but you can try that instead.  If you _do_ remove them, it might be a good idea to 'sudo cp /etc/kernel-img.conf /etc/kernel-img.conf~' first.

* Of course, after you do the above, you're left to remember to update your '/boot/grub/menu.lst' after a new kernel image install (or you'll never see that option on subsequent reboots).

\\//_

---

