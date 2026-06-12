---
title: "GRUB Error 22"
date: 2009-03-11
forum: General Help
---

### Post by ogamer on 2009-03-11
I have deleted the two partitions that were created for ubuntu studio in Windows XP using Norton Partition Magic. Thats the same way i created them. Now i know that this isnt the right way for uninstalling Ubuntu Studio because of GRUB Error 22. What is the simpliest way for removing GRUB and start XP or Ubuntu normally?
Thanks.

---

### Post by Neo_The_User on 2009-03-11
Umm, fresh install would be the normal way. FYI, Grub Error 22 means it can't find the kernel binary.

---

### Post by ogamer on 2009-03-11
there has to be some other way, i dont want to go trough all that setup process again...

---

### Post by pennacook on 2009-03-11
take a look at [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351), on how to install grub (again)

---

### Post by ajgreeny on 2009-03-11
Do you still have both ubuntu and windows on the computer?  If so you can get to a grub, though you may need to edit the menu.lst file afterwards, but using the ubuntu live CD.
Boot into the ubuntu live CD
open a terminal and run :
    ```
sudo grub
```This gets you to a simple grub command line.
Then:
    ```
find /boot/grub/stage1
```This will tell you where your /boot/grub/stage1 is which is needed to boot ubuntu. If you have more than one linux install you may get more than one answer here.  Use the one from which you want to use grub.  Replace the question marks in the following command with the output of the this last command :
    ```
root (hd?,?)
```[like : root (hd0,1) ,probably]
then:
    ```
setup (hd0)
```This is where your windows partition and MBR normally is, but if you want grub on another disk, use hd1, etc as appropriate. It's much easier to use the windows MBR and then just change the default boot system later if others in the family demand windows boots by default.
Then:
    ```
quit
```Finally reboot, and hopefully you will now have a working grub bootloader.

Depending when and how you installed ubuntu-studio, you may then need to edit the partition information in the menu.lst, but with luck, if the ordinary ubuntu grub used to work, it may still do so.

If you do not have ubuntu at all at the moment, you will need to restore the windows MBR to get that to boot.  Use fixmbr in the recovery console after booting the windows CD to do that.

---

### Post by ogamer on 2009-03-11
i fixed it with super grub boot disk, thanks.

---

