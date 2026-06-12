---
title: "Can I add labels to my Ubuntu and Zorin systems so they have names in the launch bar?"
date: 2015-08-27
forum: Desktop Environments
---

### Post by Old_Printer on 2015-08-27
I just finished loading Ubunto. I first loaded Windows 7, then Zorin, and now Ubuntu. When I'm in Ubuntu, I can hover my cursor over the hard drive icons in the launch bar and see "Windows" over one of them, and over the other "58 GB Volume" (Zorin).

Question: Why doesn't it say "Zorin" when I hover over the one drive instead of "58 GB Volume"? Can I somehow identify my distros so that they have user-friendly names when I'm on either of my Linux-based desktops?

Old_Printer

---

### Post by oldfred on 2015-08-27
I normally try to label partitions when I create them with gparted so I know what install is in that partition or what partition is storing.
When I forget to do it then, I use Disks or disk Utility and click on gears below partitions for more actions. With gpt there are two descriptions, one is partition and one is file system.
You can see labels:
sudo blkid

       Set Labels for external devices gparted, Disk Utility or command line
[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)
[http://askubuntu.com/questions/147319/how-can-i-give-other-drives-and-partitions-short-meaningful-names-in-nautilus](http://askubuntu.com/questions/147319/how-can-i-give-other-drives-and-partitions-short-meaningful-names-in-nautilus)

---

### Post by Dennis N on 2015-08-27
To have the name of the OS appear instead of "58 GB volume", you need to label the partition the OS is on. You can do it with the command **e2label**.

**sudo e2label /dev/sda6** will show you the label on **sda6** if one exists. If there is none, the command returns a blank line.
```
dmn@Daphne:~$ sudo e2label /dev/sda6
Lubuntu-1404

```
To change to, or create the new label **Xubuntu-1504** on **sda7**
```
dmn@Daphne:~$ sudo e2label /dev/sda7 Xubuntu-1504
```

---

### Post by Old_Printer on 2015-08-27
It worked! Thanks for the posts. O:) I found help from both of them. 

Old_Printer

---

### Post by Dennis N on 2015-08-27
Thanks for the feedback. It's appreciated. You can use the "Thread Tools" just above Post #1 to mark this as solved.

---

