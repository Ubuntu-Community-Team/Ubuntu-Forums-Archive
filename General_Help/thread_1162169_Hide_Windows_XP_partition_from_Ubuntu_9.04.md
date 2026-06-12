---
title: "Hide Windows XP partition from Ubuntu 9.04"
date: 2009-05-17
forum: General Help
---

### Post by zelgadis85 on 2009-05-17
Hi everybody. I'm new to the forums and have a question.

I am dual-booting Windows XP Professional and Ubuntu 9.04 on my desktop. I'd like to hide the Windows partition from ubuntu (so I don't accidentally mess it up in linux) using GRUB.

I have tried hide and unhide commands, but they did me no good.

I am rather new to linux and would appreciate any help.

Below are the (necessary) lines from my /boot/grub/menu.lst file:

```
title        Microsoft Windows XP Professional SP3 (32bit)
unhide        (hd0,0)
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1

title        Ubuntu 9.04 (64bit)
uuid        749d9b73-363a-47a6-8a42-3cc5c26b92f3
kernel        /vmlinuz-2.6.28-11-generic root=UUID=eaf1ec31-e412-4db2-befb-ccc20603bd9b ro quiet splash 
initrd        /initrd.img-2.6.28-11-generic
hide        (hd0,0)
quiet

title        Ubuntu 9.04 (64bit recovery mode)
uuid        749d9b73-363a-47a6-8a42-3cc5c26b92f3
kernel        /vmlinuz-2.6.28-11-generic root=UUID=eaf1ec31-e412-4db2-befb-ccc20603bd9b ro  single
initrd        /initrd.img-2.6.28-11-generic
hide        (hd0,0)

title        Ubuntu 9.04, memtest86+
uuid        749d9b73-363a-47a6-8a42-3cc5c26b92f3
kernel        /memtest86+.bin
quiet

```Thank you in advance.
Zelgadis85

---

### Post by lazman on 2009-05-17
I don't think you want to hide your xp partition in grub, this will only allow you to not be able to choose it from the menu when you boot up.

To be honest, there is no reason to hid it at all. When working in ubunu you have to deliberately access your windows partition. There is really no mistaking what you are doing. If you need to do admin task in Ubunu use the Filesystem, this will only take you to your linux partition. To access your windows partition you have to explicitly go to it on the hard drive. You should be notified you are mounting that part of your hard drive also.

But, if you hide the option in Grub then you will not be able to select it on boot up. If you want to do that then you might as well just use the full hd for Ubuntu and get rid of windows. Because when you setup your partition for Ubuntu it is like having more than one hd installed. As far as the operating system is concerned, you have at least two hard drives installed. One for linux and one for windows. That is what partition is for. That is why when you try to access your windows partition (hard drive) from linux you have to mount it. Mounting a drive is simply accessing it. Just like you can't have access to your car radio unless you open the car door. Opening the car door is like mounting the car, after that you can turn on the radio that is in the car.

---

### Post by zelgadis85 on 2009-05-17
Thanks for your reply.

In fact I am adding new hard drives with different sort of files on them. I want these directories to be "shared" between ubuntu and windows.

The only thing I am after is having similar functionality between Windows and Ubuntu, where you can see all these hard drives and access the files within, but not access the other OS without booting into it.

Like Windows Explorer does not show Linux drives, I'd like an option for Linux not to show Windows drives.

Is there a way I can accomplish this?

Thanks in advance.
Zelgadis85

---

### Post by pastalavista on 2009-05-17
There is no way at all to hide it because it is all on just one physical drive (hd0). You could prevent it from mounting at boot time, but not if the mbr is still on it, and if you remove the mbr, you might not be able to boot Windows. The best way would be to have it on a separate USB or other type of removable drive and then use the BIOS for boot reference.

The best way to not mess something up is just not mess with it.

---

### Post by zelgadis85 on 2009-05-17
Ah, all right, that explains it.

Too bad though I can't install Windows on a separate hard drive since I have limited SATA ports on my motherboard. Guess I'll have to stick to it like this.

Although, I learned quite a bit how GRUB (and Linux) works from this. Thanks :D


Thank you all for your time, I really appreciate it.
Zelgadis85

---

### Post by lazman on 2009-05-17
The systems are setup differently, this is one difference. The reason xp can't see linux files is the format of the files and the partition. XP simply does not have the code to view that type of file system. However, linux has the code to view windows file systems. This is a standard feature of most linux distros. On Ubutnu, you have to log in using an account you created. This means unlike windows, you can't log in with Administrator, in linux it is called Root instead of administrator. But to run commands or programs with administrator privileges in Ubuntu, you log into your normal account and in a shell (kind of like a dos window) you type sudo then your command. This tells linux that you would like to run this command only as root. Only the root account can modify files that are out of the home folder. So, the system is setup so you only have access to modify and use the files in your home folder unless you specificity tell linux you want access to modify using the root account. You can not log into the root account however. 

On windows you are able to log into your root (administrator) account. And access any file you want on the entire hard drive.

If you put a third hard drive in your computer, then you will need to mount that hard drive from linux just like you would have to do with with the windows partition. To my knowledge, there is no way to "hide" the windows partition from linux simply because it can read that type of file system. 

A word or warning. If you want to be able to access the files on the third hard drive from both XP and Ubuntu. You will want to format it with either FAT32 or NTFS. That is the only file systems that XP can read. You might be able to do some searching and find a patch or something that will allow XP to read other file systems but that is your best bet. And if it were me I would use NTFS over FAT32. Simply because XP is built on NTFS.

If you go to my computer in Ubuntu you should see DSK1_VOL1 this will be your windows partition. When you put in a new hard drive, it should say DSK2_VOL1. This is how you can tell what you are mounting. You can also try renaming those in Ubuntu so it will be easy to tell what you are accessing.

---

### Post by bacardiandwatermelon on 2009-05-17
This is just my 2 cents... You can get windows to access ext2 and ext3 file systems if you want..

[http://www.fs-driver.org/download.html](http://www.fs-driver.org/download.html)

---

