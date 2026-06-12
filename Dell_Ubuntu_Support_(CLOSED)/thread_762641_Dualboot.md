---
title: "Dualboot"
date: 2008-04-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by nitrokid759 on 2008-04-22
Hello, I do not like the Grub loader, is there a way to get the XP and ubuntu loaders to show up like this:

[[IMG]http://img225.imageshack.us/img225/1708/dualbootec2.th.png[/IMG]](http://img225.imageshack.us/my.php?image=dualbootec2.png)

I photoshopped it so the text up top and bottom would be different.

If anyone could help that'd be great.

---

### Post by StefAndrew on 2008-04-23
I'm not sure exactly how the boot table would look, but you would want to install the boot loader for Ubuntu on the same partition you install Ubuntu to, instead of the MBR, so that Windows XP boot loader is the default.  Then from Windows XP, the boot loader info is stored in the boot.ini file.  I'll have to see if I can find out what the line to boot Ubuntu would look like.  Also, IIRC, you can install Ubuntu first, even using the MBR, and then XP second, and it should automatically see the Ubuntu partition and add it to the boot.ini automatically for you.

---

### Post by uidb4056 on 2008-04-23
You can test to use Wubi, on the new hardy heron live CD you can install Wubi in windows if you put the live CD in windows, then you can install ubuntu using free space on windows and having a dual boot managed by windows bootloader without modifing your MBR on the boot disk.

---

