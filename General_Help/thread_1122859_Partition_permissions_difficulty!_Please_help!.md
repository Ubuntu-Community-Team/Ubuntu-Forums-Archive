---
title: "Partition permissions difficulty! Please help!"
date: 2009-04-11
forum: General Help
---

### Post by Pipps on 2009-04-11
I have a fresh installation of Ubuntu, comprising three partitions, as follows:

sda1 - /boot
sda2 - /
sda3 - /save

The '/boot' partition is just the boot sector, as you would expect. 

The '/' (root) partition contains the rest of the whole installation. 

The '/save' partition is my own personal drive which I use to store all my files and documents. The location is '/save/' and the mount-point is '/save'. 

In super-user mode, I created three folders in '/save'. I called these folders: 'Documents', 'Music' and 'Workplace'.

Whenever I use Nautilus to navigate to '/save' and enter that folder, I find that the three folder icons have padlock symbols on them, and I am unable to create any new files or folders within any of those existing folders or their subfolders.

How can I make it so that I automatically have full permissions over this sda3 partition and all files and folders within it?

---

### Post by drs305 on 2009-04-11
Since you created them as root, they are currently owned by root. You want to change the ownership to yourself with the following command. Make sure you get the command correct, chowning the wrong folders is NOT good!
```

sudo chown -R *yourusername:* /save

```
Example: sudo chown -R john: /save
This will cause "save" and everything below it belong to you.

---

### Post by Pipps on 2009-04-11
This works perfectly!

And you answered my question within less than two minutes of me posting it!

Thank you! :KS

---

