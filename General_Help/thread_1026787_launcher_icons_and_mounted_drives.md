---
title: "launcher icons and mounted drives"
date: 2008-12-31
forum: General Help
---

### Post by punkbohemian on 2008-12-31
I would prefer to have a totally clean desktop (no icons) and just run everything from the menus. As is, I only have up to two to three icons that I can't seem to ditch.

1) A launcher for a program I use. In order to get it to work properly, I had to create a launcher/shortcut with parameters added to the command line. If I run it from the applications menu, it runs it without the parameters. Is there any way I can get the link from the apps menu to run a program with extra parameters?

2) Mounted drives. I don't need desktop icons for mounted drives. I have the link under "Places". How do I keep the icons from appearing on my desktop whenever I put in a DVD or mount another drive? Additionally. I have a partitioned hard drive. Is there anyway I can set up Ubuntu to mount one of the other partitions every time I log in?

Thanks.

---

### Post by drs305 on 2008-12-31
1. Edit the Applications menu list. Right click on the Main Menu, Edit or run "alacarte" in terminal. Find the icon, right click, select Properties and then edit the command line to include any swithces/options you want to add. Alternatively, you could make a small bash script with the complete command and just reference that script in your desktop icon.

> **punkbohemian said:**
> Is there anyway I can set up Ubuntu to mount one of the other partitions every time I log in?
2. You can make an entry in fstab so the device mounts at boot. There are plenty of threads about it. If it's an ntfs partition, install and use ntfs-config. If it's an ext3 partitioned device, it is very simple to add an fstab entry. Here is a good guide to fstab:
[https://help.ubuntu.com/community/Fstab]("https://help.ubuntu.com/community/Fstab")

---

### Post by punkbohemian on 2009-01-15
thanks, that did the trick.

(the "mark thread as solved" option has vanished)

---

