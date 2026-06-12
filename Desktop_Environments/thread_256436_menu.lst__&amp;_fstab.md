---
title: "menu.lst  &amp; fstab?????"
date: 2006-09-13
forum: Desktop Environments
---

### Post by Russty of Oz on 2006-09-13
Hi :) 

I have just been trying to reinstall grub, and when I get to the end of what I am suppose to do, I am told I need to;

" **alter your menu.lst AND you fstab** "

Now what are these and how do I do it?

Russty.

---

### Post by Jussi Kukkonen on 2006-09-13
They are text files, /boot/grub/menu.lst and /etc/fstab.

Without any more information I don't think you'll get more help... Was that really the only advice you were given?

---

### Post by nereid on 2006-09-13
The *menu.lst* is you GRUB configuration file and *fstab* is you file system table.

You can find the first one here: /boot/grub/menu.lst
The second one in the /etc folder.

To change anything in this files you have to use sudo. Something like 

```
gksudo gedit /boot/grub/menu.lst
```

or

```
gksudo gedit /etc/fstab
```

But I don't know what you should change in these files. Beware, any changes to these files are little bit dangerous. You can revert any damage done to these files using a boot disk, so no real problem if you mess things up.

---

### Post by Herman on 2006-09-13
Grub's menu.lst controls how grub boots up your computer, so by editing this text file, you can customize your Grub menu and the way your computer boots. This link might help you a bit with explaining what menu.lst is and how to edit it, [GRUB Page]("http://users.bigpond.net.au/hermanzone/p15.htm")

And here's a link about /etc/fstab, [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)
You might need to edit /etc/fstab if you have added new partitions to your hard disks or changed some partition numbers on existing partitions somehow. (Usually by copying and pasting partitions with partition editing software). 
If you have another partition and you would like your operating system to mount it automatically on bootup you would also edit /etc/fstab with an entry for that partition. [Mounting Page]("http://users.bigpond.net.au/hermanzone/p10.htm")  Editing /etc/fstab customizes the way Ubuntu looks at other filesystems for you. Have fun with Linux,
Regards, Herman :D

---

### Post by Russty of Oz on 2006-09-13
> **Jussi Kukkonen said:**
> They are text files, /boot/grub/menu.lst and /etc/fstab.

Without any more information I don't think you'll get more help... Was that really the only advice you were given?

See this thread and the reply by bulldog,[http://ubuntuforums.org/showthread.php?t=254627]("http://ubuntuforums.org/showthread.php?t=254627") I did all that he suggested and it worked, it is just at the end that he said to do this, I just didn't know what it meant.

Russty

---

### Post by Herman on 2006-09-13
You probably don't need to do anything if you only re- installed Windows and it's still on the same partition number it has before. If your computer is booting okay and it's working alright then don't worry about it. The information is there in case you ever need it though.
Regards, Herman :D

---

