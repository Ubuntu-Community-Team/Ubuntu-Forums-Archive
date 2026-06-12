---
title: "Ubuntu F-Disk Equivalent?"
date: 2006-02-26
forum: Desktop Environments
---

### Post by YellowHat on 2006-02-26
Q-parted? Like what? I need to delete a partition. And I know I"m not able to because when I deleted the partition the grub still started so I need your help. I've been hearing things about low-level format buy how do I do that? Is that covered in Q-parted.

---

### Post by kwaanens on 2006-02-26
qt-parted or gparted both to the same stuff. Use either one, just make sure you delete the right partition(s)!

- Ketil

---

### Post by kwaanens on 2006-02-26
Sorry, didn't read you post properly.
If you want to delete a partition that's been mounted, you could unmount it with gparted or qt-parted (or $ sudo umount /partition) .
If you want to delete a system partition (but I'm not sure why you'd want to do that), you can do that with the Ubuntu Live CD.

- Ketil

---

### Post by steve.horsley on 2006-02-26
What is the problem, exactly? What are you trying to do?

You sound as though you think you did delete the partition. You can verify this with the command **sudo fdisk -l**

Do you also want to remove grub? That's different - grub lives on the BMR, and only its menu lives in a partition. To remove grub, te easiest thing is to use a windows rescue disk and use the command **fdisk /mbr** to but a windows bootloader back.

---

