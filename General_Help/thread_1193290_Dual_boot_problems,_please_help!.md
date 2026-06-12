---
title: "Dual boot problems, please help!"
date: 2009-06-21
forum: General Help
---

### Post by bushtangu on 2009-06-21
i have just installed ubuntu 9.04 in my primary hd C: 30Gb for windows and 10gb for Ubuntu. now i have a problem with the boot. when i turn on my pc it directly boot with xp. itried to modify the boot.ini file but nothing work.

```
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
multi(0)disk(0)rdisk(0)partition(2)\GNOME="Ubuntu Linux "Hoary Hedgehog"" 

```


i have made smth wrong but can you help to fix please! thank you

---

### Post by master_kernel on 2009-06-21
Not that I know much about it, but by the looks of it I doubt the boot.ini file knows what 'GNOME' is, so it doesn't even include it. You should use GRUB instead: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by bushtangu on 2009-06-21
i saw the thread and make what it says but nothing changed. it was a thread with 50+ pages did i miss smth else. any other suggestion. can somebody with dual boot only to show me the boot.ini lines. thank you

---

### Post by Bucky Ball on 2009-06-21
You don't change anything in Windows. During the install, you should have installed a grub boot loader. That is there somewhere but your machine is not finding it. Try booting from the live CD, open a terminal and type:

```
locate /boot/grub/stage1
```Find anything?

As mentioned, Windows does not recognise EXT3 linux drives and partitions, so don't touch the Windows files for the moment!

Something that might work for you is Super Grub Disk:

[http://members.iinet.net.au/~herman546/SuperGrubDiskPage.html](http://members.iinet.net.au/~herman546/SuperGrubDiskPage.html)

Download ISO, burn image, boot from it and it will probably at least identify what your problem is, if not fix your grub for you. Good luck.

---

### Post by bushtangu on 2009-06-21
yes, i find the file.

---

### Post by blueridgedog on 2009-06-21
> **bushtangu said:**
> i have just installed ubuntu 9.04 in my primary hd C: 30Gb for windows and 10gb for Ubuntu.

Did you use a liveCD or wubi?

---

### Post by bushtangu on 2009-06-21
i download 9.04 and burned it in a cd. i'm working with the live cd now.

---

### Post by blueridgedog on 2009-06-21
If it found the file, you can re-install grub with the following:

Bootup a live cd, open a terminal and do the following.
```

sudo grub
```

This will result in a "grub>" prompt. At grub>. enter these commands
```

find /boot/grub/stage1
```

This will return a location. If you have more than one, select the installation that you want to use as the source for the new mbr.

Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)

```
root (hd?,?)
```

Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr

```
setup (hd0)
```

Note, if you want to put the new mbr in another hard drive, you will need to adjust it accordingly.

Finally exit the grub shell
```

quit
```

---

### Post by bushtangu on 2009-06-21
```
grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 d (hd0) (hd0)1+17 p (hd1,4)/boot/grub/stage
2 /boot/grub/menu.lst"... succeeded
Done.

```
just made i will give a try. thought work

---

### Post by bushtangu on 2009-06-21
i'm still having the problem , i dont know what is going wrong. i can boot directly to xp not to Ubuntu

---

### Post by bushtangu on 2009-06-21
any other help please, or any guide how to install grub?

---

### Post by blueridgedog on 2009-06-21
> **bushtangu said:**
> i'm still having the problem , i dont know what is going wrong. i can boot directly to xp not to Ubuntu

Do you get an option to boot into Ubuntu and can't or do you boot straight into windows?

If you get the option but can't, what happens?

---

### Post by bushtangu on 2009-06-21
when i modify the boot.ini file and select ubuntu to boot an error appears " cant find system32/hal.dll"

when the boot.ini was in her original stats i can boot directly to windows not option for ubuntu is shown.

---

### Post by rplomantes on 2009-06-21
Try to manually format your ubuntu 9.04 and create 2 partition one for Ext3 and mark it as mount point and the other is swap

---

### Post by egalvan on 2009-06-21
> **bushtangu said:**
> ..., or any guide how to install grub?

Part of a much larger, extremely-well written Linux site...
this is an in-depth look at GRUB.

just follow the steps, on by one...


[http://members.iinet.net.au/~herman546/p15.html#reinstallgrub](http://members.iinet.net.au/~herman546/p15.html#reinstallgrub)


Herman is a regular contributor on this forum.
Excellent information!

---

### Post by blueridgedog on 2009-06-21
> **bushtangu said:**
> when i modify the boot.ini file and select ubuntu to boot an error appears " cant find system32/hal.dll"

when the boot.ini was in her original stats i can boot directly to windows not option for ubuntu is shown.

Once you get to boot.ini, you are not loading grub.  So, when you boot your system, do you get grub at all?

---

### Post by bushtangu on 2009-06-21
no i didnt

---

### Post by blueridgedog on 2009-06-21
You installed grub to your first hard drive.  Do you have more than one hard drive in your system?

While booted on the liveCD, can you post the output of:

```
sudo fsisk -l
```

---

### Post by Bucky Ball on 2009-06-22
One more time, LEAVE BOOT.INI ALONE. It has nothing to do with grub and does not need to be changed, tweaked, touched or tampered with in any way. You are likely to cause way more problems and confuse the issue.

Ubuntu should (and in this case has as you proved by finding the file I asked you to) install its own, totally separate boot loader, Grub Boot Loader, which is what you should be focusing your attention on. The instructions on the last page to boot from the live CD, drop to a terminal and locate /boot/grub/stage1 are the way to go.

If you keep tweaking boot.ini, you will end up not being able to boot to Windows either!

You are very close and it is a learning curve. Think grub at this point. Forget about boot.ini. If Windows boots, boot.ini is just fine. It plays NO PART WHATEVER in booting Ubuntu, or anything but Windows in this instance. :)

---

### Post by StOlEnDeStInY on 2009-06-22
Try this:

[http://www.geocities.com/lode_leroy/grubinstall/](http://www.geocities.com/lode_leroy/grubinstall/)

Also read this
[http://www.knoppix.net/forum/viewtopic.php?p=57201](http://www.knoppix.net/forum/viewtopic.php?p=57201)

Hope this solves :)

---

### Post by Bucky Ball on 2009-06-22
And if you install another grub/stage1, you will then have two grubs which may cause chaos.

All you need to do at this point is point the machine to boot from the grub stage1 you already have installed as outlined on the previous page. :)

---

