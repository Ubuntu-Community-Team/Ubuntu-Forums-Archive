---
title: "GRUB messup..."
date: 2009-05-06
forum: General Help
---

### Post by comradejanus on 2009-05-06
Well, I finally installed 9.04 the other day on a separate partition to my windows vista and 8.10 partitions. 

Anyway I ended up formatting the 9.04 partition as, I got annoyed with it (too many bugs etc). Was guna reinstall.

The issue I forgot was that 9.04 partition had made itself a primary boot partition.

Now when I start up the computer, the first thing it says is GRUB error 15 and doesnt show me a list of boot options.

How do I access the GRUB settings to inform it that I have deleted the partition? Is this even the problem?

Thanks for any help

---

### Post by prem1er on 2009-05-06
If you have a live cd handy boot from that.  You then need to edit your menu.lst config.  You can change your default boot from there.

---

### Post by azmo35 on 2009-05-06
Or press e key and e key again to edit the partition you wanted access.

---

### Post by comradejanus on 2009-05-06
Yup I have been booting with a live cd.

Where do I find that file that I have to modify? which partition will it be on and in which directory?

Thanks so much for the help btw

---

### Post by prem1er on 2009-05-06
It is located at /boot/grub/menu.lst.  I suggest backing it up before you edit it.

```
cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
```

---

### Post by azmo35 on 2009-05-06
Or,
 gksu nautilus
to have access to root and them navigate through /boot/grub/menu.lst, edit make the changes and nautilus will make a backup for you.

---

### Post by caljohnsmith on 2009-05-06
Are you getting the Grub error 15 before seeing a Grub menu on start up? If so, Grub is probably looking for its boot files in the deleted 9.04 partition and of course can't find them. If you still have 8.10 installed on that HDD, you could reinstall Grub to the MBR (Master Boot Record) and point it to the 8.10 partition for its boot files. To do that, you can do the following from the Live CD:
```
sudo grub
grub> find /boot/grub/stage1
```
The command above should return your main Ubuntu 8.10 partition in the form of (hdX,Y) where X and Y are numbers, for example (hd0,2), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Let me know if that helps or if you run into problems.

Cheers,
John

---

### Post by comradejanus on 2009-05-06
I can not thank you enough, this worked!

Panic over.

Your really good at giving advice!

---

### Post by caljohnsmith on 2009-05-06
> **comradejanus said:**
> I can not thank you enough, this worked!

That's great news, I'm glad you can boot again. Cheers and enjoy all your OSes. :)

John

---

