---
title: "How To: Windows in Root"
date: 2008-12-19
forum: General Help
---

### Post by theozzlives on 2008-12-19
I got tired of an icon appearing on my desktop everytime I mounted my NTFS Partition, so I came up with this:

```
sudo mkdir /windows
```
```
sudo gedit /etc/fstab
```
add the following to the fstab:
```
/dev/sdaX /windows ntfs 0 0
```
Where the "X" is, is the number of your NTFS partition. Reboot your system, on 8.10 you can go to Places>Computer>File System, drag the windows folder to your left pane, and windows will show up in your places menu.

On  the other side of the coin, you can  access  your ext3 partitions from Windows by installing the [ext2fsd]("http://www.softpedia.com/get/System/OS-Enhancements/Ext2Fsd.shtml")

Hope this is informative to someone.

---

### Post by taurus on 2008-12-19
> **theozzlives said:**
> 
add the following to the fstab:
```
/dev/sdaX /windows ntfs 0 0
```


I don't think the line in /etc/fstab for windows would work.  You need to include **defaults** after the ntfs though.

---

### Post by theozzlives on 2008-12-19
works on mine

---

