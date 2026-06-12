---
title: "Grub error if non-boot drive is not attached"
date: 2008-12-13
forum: General Help
---

### Post by code-breaker on 2008-12-13
I have two drives in my machine, sda and sdb. I have kubuntu installed on sdb, and boot to that. I disconnected sda to attach a different drive, so that I could move files around. But I can't boot unless sda in attached. I get a grub error (I think error 2). How can I fix this?

---

### Post by ajgreeny on 2008-12-13
This is bercause grub is probably installed onto sda1, if you allowed ubuntu to install as default.  Boot to the kubuntu live CD and run the commands shown below.

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
This will tell you where your /boot/grub/stage1 is which is needed to boot ubuntu. If you have more than one linux install you may get more than one answer here.  Use the one from which you want to use grub.  Replace the question marks in the following command with the output of the this last command :
    ```
root (hd?,?)
```
[like : root (hd0,1) ,probably]
then:
    ```
setup (hd0)
```
This is where your windows partition and MBR normally is, but if you want grub on another disk, use hd1, etc as appropriate. It's much easier to use the windows MBR and then just change the default boot system later if others in the family demand windows boots by default.  You can even do this step twice if you want, so grub is on both disks if both are in the machine.
Then:
    ```
quit
```
Finally reboot, and hopefully you will now have a working grub bootloader.

---

### Post by zwygart on 2008-12-15
You can also do this commands (the ones of ajgreeny) from the boot menu. Plug your drive (sda). Press esc if you don't see the boot menu. Then press C and you are at the same shell/prompt as if you run GRUB from UbuntuCD. Make sure you have the grub files on the second drive (sdb), if not you only have to copy the folder /boot/grub from one drive to the other (sda to sdb) and then run the commands said in the previous post.

---

### Post by code-breaker on 2008-12-24
Thanks for the replies. I was away for the Holidays, so I couldn't try out the suggestions right away. 

I have been playing around, and now I can only boot with a live cd. The drive that I have kubuntu installed on (partition HD1,0 aka sdb1) seems to have grub:

```

ubuntu@ubuntu:~$ sudo mkdir /media/drive1
ubuntu@ubuntu:~$ sudo mount /dev/sdb1 /media/drive1
ubuntu@ubuntu:~$ cd /media/drive1/boot/grub
ubuntu@ubuntu:/media/drive1/boot/grub$ ls
default        installed-version  minix_stage1_5     xfs_stage1_5
device.map     jfs_stage1_5       reiserfs_stage1_5
e2fs_stage1_5  menu.lst           stage1
fat_stage1_5   menu.lst~          stage2
ubuntu@ubuntu:/media/drive1/boot/grub$

```

But I still get a grub error (2) when I try to boot. From a terminal within the live os, grub cannot find stage1:

```

grub> find /boot/grub/stage1

Error 15: File not found

grub>

```

I tried this command after starting grub both from home and after cd'ing into /media/drive1/boot/grub. Same error both times. 

And I don't know how to get to a grub prompt at boot to try from there, since I can't get the boot menu (to press 'c' as zwygart suggested) because of the grub error, and the boot menu on the live cd doesn't seem to have this option. 

Any suggestions?

---

