---
title: "Problems with boot screen not appearing"
date: 2009-02-03
forum: General Help
---

### Post by darsiant on 2009-02-03
Hi, I just recently installed unbuntu through wubi on windows vista, and it has been working fine for about a week. Windows vista then had an error booting (This happens often, not sure why) I didn't reinstall, I just used the repair option. However, upon doing this, the dual boot screen which let me pick to boot ubuntu or vista, was gone, and I can't boot ubuntu. I don't think the installation was damaged, but I can't find it under startup options on Vista. The files are still in my C:\ dirctory i.e. ubuntu, wubi folders. Can anyone help?:(

---

### Post by shivansh on 2009-02-03
yeah, i am having the same problem.

---

### Post by shivansh on 2009-02-03
Perhaps this may help:

[http://ubuntuforums.org/showthread.php?t=1058641&highlight=boot+screen]("http://ubuntuforums.org/showthread.php?t=1058641&highlight=boot+screen")

---

### Post by shivansh on 2009-02-03
Or this:

[http://ubuntuforums.org/showthread.php?t=993805]("http://ubuntuforums.org/showthread.php?t=993805")

---

### Post by gradysghost on 2009-02-03
Are you using GRUB or NTLDR to boot?

You should check your bootloader options.  When doing a repair in Vista (or any Windows, for that matter), it overwrites the bootloader, so if you were using GRUB beforehand, you will now be using NTLDR.  If you want, there are ways to configure NTLDR to boot to something different.  There are also ways to recover GRUB without doing a full reinstall of the OS.  You can find guides to both on this forum somewhere.

---

