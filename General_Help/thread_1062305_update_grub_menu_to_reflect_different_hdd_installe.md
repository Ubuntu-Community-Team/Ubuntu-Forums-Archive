---
title: "update grub menu to reflect different hdd installed."
date: 2009-02-06
forum: General Help
---

### Post by carl99fan on 2009-02-06
I have 2 hdd in my computer. I have removed a secondary hdd that had 8.04 on it. I have replaced my secondary hdd with new one with 8.10 on it.
My grub menu still shows the old hdd and has not updated it. I have searched the forums for answers but others seem to be asking different questions. 

How can I update my grub menu to reflect these changes, allowing me to boot either hdd without using my bios to choose boot.

---

### Post by Yashiro on 2009-02-06
Just add it to grub?

You need to know where the boot image is and what drive it's on. And the kernel name of course. You can replace UUID (which you can get using blkid) with /dev/disk whatever.

> title		Ubuntu Something or other
root		**(hd0,1)**
kernel		/boot/vmlinuz-**2.6.24-23-generic **root=**UUID=ba636202-3275-45ed-b485-da35aa659c61**  ro
initrd		/boot/initrd.img-**2.6.24-23-generic**


As for how, just edit the file /boot/grub/menu.lst from the partition which grub loads.

---

### Post by carl99fan on 2009-02-06
OK, That is a little over my head but I have something to work with and I will figure it out.

---

### Post by Yashiro on 2009-02-06
;) Grub just reads that menu.lst file and creates the menu from that. So you can just edit that file by adding a new section for the new hd.
Just copy the existing details but change the some of the settings (in bold) to match the details of the Ubuntu on the new disk.

For the **hd(0,1)** variable - it that means first drive, second partition. hd(1,2) would be second drive, third partition etc.
You'll find the the numbers required for the kernel version in /boot of the new drive. 
There will be a file called to **vmlinuz-**..whatever. 
The **uuid** you can find out by running the command **blkid** in a **gnome-terminal**.

Alternatively provide all the info here along with pasting your current menu.lst and some bored soul will sort it out.

---

### Post by carl99fan on 2009-02-06
Thank you, I will try this later.
You have explained it very well.
I'm going to do it myself though as this is something I need to learn.
But I Will post it if I fail.

---

### Post by Yashiro on 2009-02-06
Backup menu.lst to say menu.lst.backup before you edit it. 
If you mess up badly, just boot from a LiveCD and restore the old one.

---

