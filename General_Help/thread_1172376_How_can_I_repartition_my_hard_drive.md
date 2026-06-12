---
title: "How can I repartition my hard drive?"
date: 2009-05-28
forum: General Help
---

### Post by The Switch Blade on 2009-05-28
It's ext3 with ubuntu 9.04. I want to dual boot windows.

---

### Post by JohnB-nbr on 2009-05-28
You should read [this]("https://help.ubuntu.com/community/WindowsDualBoot") page to learn more about the process of installing Windows after Ubuntu (partitioning tools,boot loaders,etc.)

---

### Post by The Switch Blade on 2009-05-28
Is this difficult?

---

### Post by JohnB-nbr on 2009-05-28
It's not difficult and there are not a lot of steps, but you should read the guide to be sure that you understand what you do and that you do it safely.

---

### Post by The Switch Blade on 2009-05-28
I assume if I want to repartition my main device I can't be on that device at the same time?

i.e.: I'll have to boot into a live disc

---

### Post by merlinus on 2009-05-28
Correct.  If a drive or partition is mounted, you cannot re-partition it.

I suggest the gparted live cd:

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by The Switch Blade on 2009-05-29
[LIST=1]
[*]Backup the boot sector e.g. dd if=/dev/hda of=/mbr.bin bs=512 count=1 
[/LIST]
root@earl-desktop:/home/earl# dd if=/dev/hda of=/mbr.bin bs=512 count=1
dd: opening `/dev/hda': No such file or directory

---

### Post by JohnB-nbr on 2009-05-29
Try /dev/sda instead of /dev/hda

---

