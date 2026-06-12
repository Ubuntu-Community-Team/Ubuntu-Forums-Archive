---
title: "GRUB boot menu"
date: 2008-07-02
forum: Fedora/RedHat and derivatives
---

### Post by RMD94 on 2008-07-02
Hello,

I have a dual boot system with windows vista and ubuntu linux, my brother wanted to temporally install Fedora on my PC for some educational purpose, he told me he would remove it after few weeks but the problem is i can't access to Ubuntu any more, when my system boots up it takes me to the GRUB boot menu but i can't find Ubuntu in it. How can i get Ubuntu on the boot menu list??

---

### Post by scragar on 2008-07-02
I'd mount the ubuntu partion, then search inside it's HD for /boot/grub/menu.lst and copy the lines to boot ubuntu(they tend to be in blocks of about 4 lines), copy and paste into the fedora version, when you remove fedora(if you even want to), you will have to reinstall grub to the ubuntu partition.

---

### Post by ajgreeny on 2008-07-02
If the fedora is only there temporarily, it may be better to reinstate the ubuntu grub, instead of the fedora grub that you probably have now.  Use the ubuntu live CD to do this as follows:-

Boot into the ubuntu live CD
open a terminal and run :
   ```
 sudo grub
```
This gets you to a simple grub command line.
Then:
    ```
find /boot/grub/stage1
```
This will tell you where your /boot/grub/stage1 is which is needed to boot ubuntu.  If you have more than one linux install, use the one that you want the grub to run from.  Replace the question marks in the following command with the output of the this last command :
   ```
 root (hd?,?)
```
[like : root (hdo,1) ,probably]
then:
    ```
setup (hd0)
```
This is where your windows partition and MBR normally is, but if you want grub on another disk, use hd1, etc as appropriate. It's much easier to use the windows MBR and then just change the default boot system later if others in the family demand windows boots by default.
Then:
    ```
quit
```
Finally reboot, and hopefully you will now have a working grub bootloader.

You may now need to add the fedora grub.conf entry to your ubuntu grub menu.lst file, but that should be easy enough to do.  Now when fedora is removed from the system there will still be ubuntu grub to boot from.

---

