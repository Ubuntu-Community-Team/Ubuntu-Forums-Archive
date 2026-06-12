---
title: "Need to allow usb read/write access to other users"
date: 2009-01-05
forum: General Help
---

### Post by sandjkirkland on 2009-01-05
I am unable to allow read/write access to the usb drive for the other users. I tried sudo Nautilus but it still tells me that I do not have permission. I am the root user. All other drives allow permission but not USB. USB works for me just fine. I am running Ubuntu 7.10. Please help

---

### Post by Crafty Kisses on 2009-01-05
Try the following, press: ```
Alt+F2
```Once the prompt comes up, enter the following command:```
gksudo nautilus
```Then see if you can browse the USB drive. One more thing you need to do, is check what the USB drive is formatted as.

---

### Post by sandjkirkland on 2009-01-06
I've tried Nautilus. The USB drive does not show so I type in the location. I am still unable to change permissions on the USB flashdrive

---

### Post by sandjkirkland on 2009-01-06
Here is the errors I get 
You do not have the permissions necessary to change the group of "disk".
The same error occurs whether I run Nautilus or rugular file browser. 
The file format is FAT.
I can browse the drive, but other users can not.

---

### Post by sandjkirkland on 2009-01-08
Earlier today I decided I would create 3 partitions, 2 partitions for other os's So I have enough primary partitions to have 3 os and 1 extended partition to have the swap and a shared files partition in the extended partition. Other users can now use USB thumbdrive but  they can not use the shared files partition. Me logging in as primary/first user I can use the shared files partition. Even though I have root privileges and even though I use Nautilus; I am still unable to change permissions on whatever is thinks is drive 1. Anybody know why and how to fix this.

Additional info
I formatted all partitions as ext3 except of course for the swap.

---

