---
title: "Just Installed Ubuntu, Can't Re-Install Windows?"
date: 2009-02-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Kryticate on 2009-02-15
I heard from a friend that Ubuntu was a pretty good operating system, so I installed it. Before installing it, I asked him if there was anything that I should know. He said just install Ubuntu and you are good to go. So I installed it on my Dell and I wanted to reinstall back to Windows, so I put in the installation disk.
  When I tried to install Windows, it said it had to be installed on an NTFS drive, which was weird because both of my drives were. Why can't I install Windows?

---

### Post by ridetheteapot on 2009-02-15
They are not anymore :) When you installed ubuntu you reformated some or all of your disk(s) to reisermurder/ext3/xfs/etc
You have got to format them to ntfs, i think the windows disk can do this, but maybe not.
You can use the ubuntu install disk partition manager (gparted) to format the drive either to nothing or to fat32 (but i dont think the disk will create ntfs partitions)
obviously this will delete all data on said drive so make sure that everything important is backed up elsewhere (no going back after)

---

### Post by daniel014 on 2009-02-15
Try booting the Ubuntu Live CD typing

```
sudo gparted
```

into the Terminal.

Then make the hard drive NTFS.

---

### Post by Kryticate on 2009-02-15
I can't seem to find the terminal on the installation disk. Where is it?

---

### Post by jespdj on 2009-02-16
Applications > Accessories > Terminal

Alternatively, you can press Alt + F2 to run the command "gksudo gparted".

---

### Post by Kareeser on 2009-02-16
There's no terminal in the Windows installation CD :)

However, the CD does come with its own partitioning tools. Put the CD in, boot up, and delete the requisite partitions, and create a new one, and format it into NTFS.

---

