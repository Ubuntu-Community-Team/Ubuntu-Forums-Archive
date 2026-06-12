---
title: "Trash cant delete file (xubuntu 10.04)"
date: 2010-02-18
forum: Desktop Environments
---

### Post by isosi on 2010-02-18
I used syslinux 4.0 on Xubuntu (10.04) desktop.

After compilation and install like root decided to delete this
syslinux folder. Everything in that folder went to trash, but after that i find out that cant empty trash.

I was able to delete files on trash only by root in terminal at location
/home/username/.local/share/Trash/files.

Why it was possible to move to trash but not delete? is it bug or what?

---

### Post by Brandon Williams on 2010-02-21
Let's say the directory structure is this: A/B/C, where A is a directory owned by you, B is a directory owned by root for which you do not have write permission, and C is a file or directory that could be owned by anyone. You can move B because you have write permission for A, but you cannot delete B because it has contents and you do not have write permission for B, which prevents you from removing B's contents. If you delete C, which must be done as root, then you will be able to delete B as you, since you only need access to A in order to delete B.

---

### Post by isosi on 2010-02-22
just for the test i make like this

sudo -s
pwd
/home/username/Desktop
mkdir test
cd test/
cat > txt.ls
^C
exit

When i try to delete that folder with mouse (normal user permission), the system (Xubuntu 10.04 amd64) popup dialog with: 

Failed to remove "txt.ls". Permission denied. Do you want to skip it?

and i choose "yes to all". 

This makes copy (or link) in Trash:

pwd
/home/username/.local/share/Trash/files
ls
test
cd test
ls
txt.ls

But i still can empty trash without problem :D

No mistery.

But with syslinux folder the system simple  was able to move to trash but not to delete ;D i think it was no any popup dialog window about permission.

---

