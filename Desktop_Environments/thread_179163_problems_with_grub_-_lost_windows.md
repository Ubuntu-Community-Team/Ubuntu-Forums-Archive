---
title: "problems with grub - lost windows"
date: 2006-05-19
forum: Desktop Environments
---

### Post by ec2 on 2006-05-19
i reinstalled ubuntu, but windows option did not appear in the grub menu. I added the lines to menu.1st, but the number is wrong. What number (hd0,1 or something) do i need to insert, if i have windows installed on hda6?

---

### Post by mority on 2006-05-19
I think it should be (hd0,5) cause grub starts counting from 0. The 'a' in 'hda' corresponds to the first harddisk ('0' in grub notation) and the 6 to the 6th partition (5 in grub notation).

Here's a detailed description of the grub naming conventions:
[http://www.gnu.org/software/grub/manual/grub.html#Naming-convention](http://www.gnu.org/software/grub/manual/grub.html#Naming-convention)

---

