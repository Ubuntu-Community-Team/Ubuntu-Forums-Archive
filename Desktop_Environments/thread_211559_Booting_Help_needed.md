---
title: "Booting Help needed"
date: 2006-07-08
forum: Desktop Environments
---

### Post by anup09 on 2006-07-08
Ok hey.. i had it where is was dual boot Ubuntu and XP Pro Sp2
since XP SP2 messed up i reformated it and now it ask;s me only to boot into XP .. when i run partition Magic.. i see that Ubuntu is still on a patition and i can view the files via file manager on Partition Magic 8.. how do i get GRUB boot loader back installed.

---

### Post by mogelhead on 2006-07-11
I also had this problem when I first installed Ubuntu and then Windows. I used this HOWTO to solve it: [RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

There are a couple of options, I used ["Using the LiveCD and Overwriting the Windows bootloader"]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-5dbdd6b5302831ed4335bd0b7387ffcad2543857").

Also, this command can be handy to list all your partitions:
```
sudo fdisk -l
```

---

