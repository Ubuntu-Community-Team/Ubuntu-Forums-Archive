---
title: "Problems with uninstalling Ubuntu"
date: 2009-02-07
forum: General Help
---

### Post by your_brain on 2009-02-07
I have both Ubuntu and Windows XP and I wanted unintall Ubuntu. I followed instructions from this thread: [http://ubuntuforums.org/showthread.php?t=113630](http://ubuntuforums.org/showthread.php?t=113630) but when I tried to resize a partition I received a message "Error 62 found on file system. Use a tool such as scandisk or chldsk /f to correct this error". I rebooted computer to run chkdsk, but I got a message "GRUB loading, please wait... Error 22". So I tried undeleting Linux partition - it worked with normal one, but not with swap partition and now I get "Error 17"

---

### Post by 73ckn797 on 2009-02-07
Can you get system to boot into Windows? If not then boot the Windows CD and enter recovery mode. Once there enter "fixmbr" and let it re-write the MBR. You should be able to load Windows then. You can still use the Live CD to boot from and delete all Linux partitions and resize the Windows partition to what ever size you like. I recommend defragmenting Windows prior to resizing.

---

### Post by your_brain on 2009-02-07
I deleted Linux partitions, added free space to one non-system partition that I wanted to resize, but I still get error 22, even when trying to boot from windows cd

---

### Post by your_brain on 2009-02-07
Also, when I booted from ubuntu cd and checked the partition I wanted to resize there it didn't find any errors

---

### Post by 73ckn797 on 2009-02-08
> **your_brain said:**
> I deleted Linux partitions, added free space to one non-system partition that I wanted to resize, but I still get error 22, even when trying to boot from windows cd

Sounds like you still need to do the "fixmbr" via Windows recovery console. You can also type in "fixboot".

---

