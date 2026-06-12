---
title: "Permissions for separate partitions NTFS Fat32"
date: 2009-05-09
forum: General Help
---

### Post by Costas100 on 2009-05-09
I have Ubuntu 8.04 freshly installed as a dual boot with Windows XP.
XP in first partition Ubuntu the next and two more partitions for files, one NTFS for the XP files and one Ext 3 for the Ubuntu files.
Both file partitions at some point and for reasons I do not understand became non accessible to me (the only user).
I managed to access and edit the files in the Ext3 partition using gssudo nautilus command, but I cannot change the NTFS partition permission from root to me.
The strange thing is that the files in the NTFS partition were added from an external hard drive (copy and paste), they were accepted there and on second opening with Computer I was told that "Please ask your system administrator (me) to enable user sharing".
I don't have many folders at the moment and I could possibly move them and reformat from NTFS to ext 3 (I have enough room under XP for files also). But I am simply puzzled.
Is there a simple solution to this small mess.
Thanks you all for the great work
Costas

---

### Post by Costas100 on 2009-05-10
Computers will never seize to amaze me. After a 10 hours rest the problem corrected it self. I guess yesterday was a long day for me and the computer.
I now have full access in both the NTFS and Ext3 partitions without the need of gksudo nautilus
Thanks to all, this issue is now closed
Costas

---

### Post by Costas100 on 2009-05-11
I thought that the problem disappeared but I was wrong. It happens again and I end up using the gksudo nautilus command 4 or more times daily to be able to access files in the NTFS and Fat32 partitions. The latest error I get from Nautilus is:
> Unable to add monitor: Operation not supported
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.
and then:
> Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

If anyone has some ideas and suggestions, I will greatly appreciate it.
Thank you all,
Costas

---

