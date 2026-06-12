---
title: "[SOLVED] Removing Windows XP After Xubuntu Wubi Install"
date: 2009-01-03
forum: General Help
---

### Post by jbeaunaux on 2009-01-03
I've just finished installing Xubuntu on an old laptop that I've got kicking around which was running extremely slowly on Windows XP. Since the machine's CD drive isn't working well I installed Xubuntu through Wubi (found on ubuntu.com). The installation went perfectly - but now I've got a dual boot machine. How do I completely remove Windows XP now that I've installed Xubuntu?

---

### Post by 2hot6ft2 on 2009-01-03
A screenshot of your partitions would help to answer the question.
System>Administration>Partition Editor
then
Applications>Accessories>Take Screenshot
grab current window
and attach it to your post

---

### Post by kokkus on 2009-01-03
Here's an easy way. In xubuntu, delete the windows folder and delete windows from grub.
Now run System > Administration > Partition Editor and delete the Windows partition.

---

### Post by kokkus on 2009-01-03
Delete windows from grub and run System > Administration > Partition Editor and delete the Windows partition.[/QUOTE]

---

### Post by cptr13 on 2009-01-03
woah....I'm not a super strong linux type but I'm under the impression that installing with wubi puts linux effectively "inside" windows and doesn't create a separate partition.  I may be wrong (though I'm fairly certain) that there's no way to remove windows if Ubuntu is installedd with Wubi.  I think you would have to do a full reinstall to get rid of windows.

Someone please correct me if I'm wrong.

---

### Post by zenmatrix on 2009-01-03
Thats what I though too. Its a disk image on the hdd which removing the windows directory will work since ntldr passes control to a bootloader that reads the disk img. A better idea if you don't have a cd drive is you can put an install on a flash drive or setup a pxe server

---

### Post by kokkus on 2009-01-03
Oh sorry I forgot that when I wrote the message. U r running ubuntu under windows. Ol. i wouldn't try to get rid of windows then. Just uninstall as much as possible in windows, and then remove it from grub.

---

### Post by eriqjaffe on 2009-01-04
Indeed, WUBI creates a file in your C:\ drive for the Ubuntu install.  If you wipe out the Windows install, you'll lose the Ubuntu install as well.

You can use LVPM to move the (X)Ubuntu install to a physcial partition.  Once you have that completed (and running), you can remove the Windows partition.

[http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)

---

### Post by iPodVision on 2009-01-04
> **eriqjaffe said:**
> Indeed, WUBI creates a file in your C:\ drive for the Ubuntu install.  If you wipe out the Windows install, you'll lose the Ubuntu install as well.

You can use LVPM to move the (X)Ubuntu install to a physcial partition.  Once you have that completed (and running), you can remove the Windows partition.

[http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)

I downloaded and ran the file but no new partition was made? It told me to restart so I did. And there was no new partition? I ran this in linux, installed and realized what am I doing I need to do this in vista, so ya no new partition is there.

---

### Post by jbeaunaux on 2009-01-04
Good to know about the whole Wubi/Windows relationship! Thanks for the heads up! I've created a new partition and will move Xubuntu there - and THEN remove Windows. Thanks for the help and info from everyone!

---

