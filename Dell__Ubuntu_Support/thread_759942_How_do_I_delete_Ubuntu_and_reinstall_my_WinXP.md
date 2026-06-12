---
title: "How do I delete Ubuntu and reinstall my WinXP?"
date: 2008-04-19
forum: Dell  Ubuntu Support
---

### Post by wmn on 2008-04-19
I have installed Ubuntu 7.10 in my Dell Inspiron 1000. How do I delete and reinstall my WinXP?

---

### Post by leo_rockway on 2008-04-19
Format the Ubuntu partition with GParted, then fix the mbr with your XP cd.

---

### Post by ubonetu on 2008-04-20
XP pretty much wipes out anything in it's path.  If you just install from your original disks, it should reformat the drive anyway and write the master boot record.

If your MBR still shows a grub menu, I'll be surprised, Windows likes wiping out OS's :-)

Ubonetu

---

### Post by sayakb on 2008-04-20
TO fix the boot record, boot in the XP setup disk and press R to enter recovery mode. There at the console, type in:
```
fixboot
fixmbr
```

---

### Post by sandysandy on 2008-04-20
agree with ubonetu. when u re-install XP 

 - it will list the existing partitions and give u option what to to do with it. just format ubuntu partition (listed as unrecognised file system) to NTFS or delete it and make new partition. 

- once XP installs it will overwrite GRUB in any case.

best of luck. hope[COLOR="Blue"] u r not[/COLOR] leaving ubuntu for good. u can always dual boot XP and Ubuntu.

regards

---

### Post by wmn on 2008-04-20
> **sandysandy said:**
> agree with ubonetu. when u re-install XP 

 - it will list the existing partitions and give u option what to to do with it. just format ubuntu partition (listed as unrecognised file system) to NTFS or delete it and make new partition. 

- once XP installs it will overwrite GRUB in any case.

best of luck. hope[COLOR="Blue"] u r not[/COLOR] leaving ubuntu for good. u can always dual boot XP and Ubuntu.regards

Thank you, I  rather thought that tossing in my Dell XP restore disk would get the job done. Formated many times and computers w/Windows . A simple job. I tried several forums and always got pretty confused w Linux  instructions. See: [http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=4722113](http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=4722113)
I was under the impression that  the install of Ubuntu would simply provide a new partition on HD. But it formatted entire HD . Modem? what can I say . spent $$ $and weeks and weeks and weeks. Reinstall Ubuntu?????
Thanks again,
 Bill

---

