---
title: "Second HD"
date: 2005-08-15
forum: Desktop Environments
---

### Post by larued on 2005-08-15
My second HD is not detected and im not sure how to set it up. Any files needed i need links too. any help is welcome.

---

### Post by jasmuz on 2005-08-15
Is the 2nd drive recognized by your BIOS, what type of partition is it?

Maybe this can help you out: [https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions?highlight=%28windows%29](https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions?highlight=%28windows%29)

---

### Post by larued on 2005-08-15
[QUOTE=jasmuz]Is the 2nd drive recognized by your BIOS, what type of partition is it?

Maybe this can help you out: [https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions?highlight=%28windows%29](https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions?highlight=%28windows%29)[/QUOTE]
 The second HD is recognized by my BIOS but im not sure if it is formatted or whats on it just yet. I need Ubuntu to recognize it so i can format it and put files on it.

---

### Post by jasmuz on 2005-08-16
Umm, you dont know what in it?
You dont need to do anything so ubuntu can recognize it.
If i where you i would type in a terminal, dmesg > a.txt, then look in your home folder, there is a file named "a.txt" in the first rows there is the HdX location of your disk drive, just toy with it or install Gparted to help you format it.

---

